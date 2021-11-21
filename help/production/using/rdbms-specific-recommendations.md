---
product: campaign
title: RDBMS 特定建議
description: RDBMS 特定建議
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 1%

---

# RDBMS 特定建議{#rdbms-specific-recommendations}

![](../../assets/v7-only.svg)

為協助您設定維護計畫，本節列出一些適合Adobe Campaign支援之各種RDBMS引擎的建議和最佳實務。 不過，這些只是建議。 您可自行調整以符合您的需求，並符合內部程式和限制。 您的資料庫管理員有責任構建和執行這些計畫。

## PostgreSQL {#postgresql}

### 檢測大表 {#detecting-large-tables}

1. 您可以將下列檢視新增至資料庫：

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8 / 1024 AS size_mbytes, c2.relfilenode AS filename, 0 AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION 
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8 / 1024 AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as integer) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   ```

1. 您可以運行此查詢來發現大型表和索引：

   ```
   SELECT * FROM uvSpace;
   ```

   或者，您也可以運行此查詢，以集中查看所有索引大小：

   ```
   SELECT
      tablename,
      sum(size_mbytes) AS "sizeMB_all",
      (
         SELECT sum(size_mbytes)
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_data",
      (
         SELECT sum(size_mbytes)
         FROM uvspace 
         AS uv2 
         WHERE
            INDEXNAME IS NOT NULL
            AND uv1.tablename = uv2.tablename
      ) AS "sizeMB_index",
      (
         SELECT ROW_COUNT
         FROM uvspace
         AS uv2
         WHERE
            INDEXNAME IS NULL
            AND uv1.tablename = uv2.tablename
      ) AS ROWS FROM uvspace AS uv1
      GROUP BY tablename
      ORDER BY 2 DESC
   ```

### 簡單維護 {#simple-maintenance}

在PostgreSQL中，您可以使用以下典型關鍵字：

* 真空（完全、分析、詳細）
* 重新索引

要運行QUAM操作，並分析和計時，可以使用以下語法：

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) <table>;
```

強烈建議您不要忽略ANALYZE陳述式。 否則，抽空表將保留為無統計資訊。 原因是建立了新表，然後刪除了舊表。 因此，表的對象ID(OID)會更改，但不計算統計資訊。 因此，您會立即遇到效能問題。

以下是定期執行的SQL維護計畫的典型示例：

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdelivery;
REINDEX TABLE nmsdelivery;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverystat;
REINDEX TABLE nmsdeliverystat;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflow;
REINDEX TABLE xtkworkflow;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowevent;
REINDEX TABLE xtkworkflowevent;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowjob;
REINDEX TABLE xtkworkflowjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowlog;
REINDEX TABLE xtkworkflowlog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowtask;
REINDEX TABLE xtkworkflowtask;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjoblog;
REINDEX TABLE xtkjoblog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjob;
REINDEX TABLE xtkjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsaddress;
REINDEX TABLE nmsaddress;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverypart;
REINDEX TABLE nmsdeliverypart;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsmirrorpageinfo;
REINDEX TABLE nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe建議從較小的表開始：這樣，如果進程在大型表上失敗（故障風險最高），則至少部分維護已完成。
>* Adobe建議您新增資料模型專屬的表格，這些表格可能會經過重大更新。 情況可能是 **NmsRecipient** 如果您有大量的每日資料復寫流程。
>* QAVUM和REINDEX語句將鎖定表，在執行維護時會暫停一些進程。
>* 對於非常大的表（通常高於5 Gb），真空FULL語句可能會變得非常低效，而且需要很長的時間。 Adobe不建議將它用於 **YyyNmsBroadLogXxx** 表格。
>* 此維護操作可透過Adobe Campaign工作流程實作，使用 **[!UICONTROL SQL]** 活動。 如需詳細資訊，請參閱[本章節](../../workflow/using/architecture.md)。請務必為活動時間較短的維護安排，該時間不會與備份窗口衝突。

>


### 重建資料庫 {#rebuilding-a-database}

PostgreSQL不提供執行聯機表重建的簡單方法，因為真空FULL語句鎖定表，從而防止了常規生產。 這表示在未使用表時必須執行維護。 您可以：

* 在Adobe Campaign平台停止時執行維護，
* 停止可能寫入正在重建之表格的各種Adobe Campaign子服務(**nlserver stop wfserver實例名** 以停止工作流程程式)。

以下是使用特定函式生成必要DDL的表碎片整理示例。 以下SQL允許您建立兩個新函式： **GenRebuildTablePart1** 和 **GenRebuildTablePart2**，可用於生成重新建立表所需的DDL。

* 第一個函式允許您建立工作表(** _tmp**此處)，該工作表是原始表的副本。
* 然後，第二個函式將刪除原始表，並更名工作表及其索引。
* 使用兩個函式（而非一個函式）意味著如果第一個函式失敗，您將不會面臨刪除原始表的風險。

```
 -- --------------------------------------------------------------------------
 -- Generate the CREATE TABLE DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenTableDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecFld RECORD;
 vstrDDL text;
 vstrFields text;
 vstrNsTable text;
 vstrTableSpace text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 SELECT
 pg_catalog.quote_ident(n.nspname) || '.' || pg_catalog.quote_ident(c.relname),
 pg_catalog.quote_ident(t.spcname)
 INTO
 vstrNsTable, vstrTableSpace
 FROM
 pg_namespace n, pg_class c left outer join pg_tablespace t on c.reltablespace = t.oid
 WHERE
 n.oid = c.relnamespace AND
 c.relname = vstrTable;
 
 vstrDDL = 'CREATE TABLE ' || vstrNsTable || '_tmp(';
 
 vstrFields = ;
 FOR vrecFld IN
 SELECT
 pg_catalog.quote_ident(a.attname) ||
 ' ' || t.typname ||
 case when t.typname='varchar' then '(' || cast(a.atttypmod-4 as text) || ')'
 when t.typname='numeric' then '(' || cast((a.atttypmod-4)/65536 as text) || ',' || cast((a.atttypmod-4)%65536 as text) || ')'
 else end ||
 case when a.attnotnull then ' not null' else end ||
 case when a.atthasdef then ' default '|| d.adsrc else end as DDL
 FROM
 pg_type t, pg_class c, pg_attribute a LEFT OUTER JOIN pg_attrdef d ON d.adrelid=a.attrelid and d.adnum=a.attnum
 WHERE 
 a.attnum > 0 AND
 a.attrelid = c.oid AND
 t.oid = a.atttypid AND
 c.relname = vstrTable
 ORDER BY
 a.attnum
 LOOP
 IF vstrFields <> THEN
 vstrFields = vstrFields || ',' || chr(10) || ' ';
 ELSE
 vstrFields = vstrFields || chr(10) || ' ';
 END IF;
 vstrFields = vstrFields || vrecFld.DDL;
 END LOOP;
 
 vstrDDL = vstrDDL || vstrFields || chr(10) || ')';
 if vstrTableSpace <> then
 vstrDDL = vstrDDL || ' TABLESPACE ' || vstrTableSpace;
 end if;
 vstrDDL = vstrDDL || ';' || chr(10);
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the CREATE INDEX DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 viFld integer;
 vstrFld text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
 SELECT
 i.indkey, i.indisunique,
 pg_catalog.quote_ident(c.relname) as tablename,
 pg_catalog.quote_ident(ic.relname) as indexname,
 pg_catalog.quote_ident(t.spcname) as tablespace
 FROM
 pg_class c, pg_index i, pg_class ic left outer join pg_tablespace t on ic.reltablespace = t.oid
 WHERE
 i.indexrelid = ic.oid AND
 i.indrelid = c.oid AND
 c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'CREATE ';
  if vrecIndex.indisunique then
  vstrDDL = vstrDDL || 'UNIQUE ';
  end if;
  vstrDDL = vstrDDL ||
   'INDEX ' ||vrecIndex.indexname || '_tmp ON ' ||
   vrecIndex.tablename || '_tmp(';
 
  FOR viFld IN array_lower(vrecIndex.indkey, 1) .. array_upper(vrecIndex.indkey, 1) LOOP
  SELECT pg_catalog.quote_ident(a.attname) INTO vstrFld 
  FROM 
   pg_attribute a, pg_class c
  WHERE 
   a.attnum = vrecIndex.indkey[viFld] AND
   a.attrelid = c.oid AND c.relname=vstrTable;
  
  vstrDDL = vstrDDL || vstrFld;
  if viFld <> array_upper(vrecIndex.indkey, 1) then
   vstrDDL = vstrDDL || ', ';
  end if;
  END LOOP;
  vstrDDL = vstrDDL || ')';
 
  if vrecIndex.tablespace <> then
  vstrDDL = vstrDDL || 'TABLESPACE ' || vrecIndex.tablespace;
  end if;
  vstrDDL = vstrDDL || ';' || chr(10);
 
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the ALTER INDEX RENAME for a table
 -- --------------------------------------------------------------------------
 create or replace function GenRenameIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
  SELECT
  pg_catalog.quote_ident(n.nspname) as namespace,
  pg_catalog.quote_ident(ic.relname) as indexname
  FROM
  pg_namespace n, pg_class c, pg_index i, pg_class ic
  WHERE
  i.indexrelid = ic.oid AND
  n.oid = ic.relnamespace AND
  i.indrelid = c.oid AND
  c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'ALTER INDEX ' || vrecIndex.namespace || '.' || vrecIndex.indexname ||
    '_tmp RENAME TO ' || vrecIndex.indexname ||
    ';' || chr(10);
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Build a copy of a table, with index
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart1(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = ;
 
 SELECT GenTableDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 vstrDDL = vstrDDL|| 'INSERT INTO ' || vstrTable || '_tmp SELECT * FROM ' || vstrTable || ';'||chr(10);
 SELECT GenIndexDDL(vstrTable) INTO vstrTmp;
 
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 vstrDDL = vstrDDL|| 'VACUUM ANALYSE '|| vstrTable || '_tmp;' ||chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
 
 -- --------------------------------------------------------------------------
 -- Drop the original table and rename the copy
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart2(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = 'DROP TABLE ' || vstrTable||';'|| chr(10);
 vstrDDL = vstrDDL|| 'ALTER TABLE ' || vstrTable || '_tmp RENAME TO ' || vstrTable ||';'|| chr(10);
 
 SELECT GenRenameIndexDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
```

以下範例可用於工作流程以重建所需表格，而非使用 **真空/重建** 命令：

```
function sqlGetMemo(strSql)
 {
 var res = sqlSelect("s, m:memo", strSql);
 return res.s.m.toString();
 }

 function RebuildTable(strTable)
 {
 // Rebuild a table_tmp
 var strSql = sqlGetMemo("select GenRebuildTablePart1('"+strTable+"')");
 logInfo("Rebuilding table '"+strTable+"'...");
 // logInfo(strSql);
 sqlExec(strSql);
 
 // If fails, there is an exception thrown and so we do not delete the original table
 strSql = sqlGetMemo("select GenRebuildTablePart2('"+strTable+"')");
 logInfo("Swapping table '"+strTable+"'...");
 //logInfo(strSql);
 sqlExec(strSql);
 }
 
 RebuildTable('nmsrecipient');
 RebuildTable('nmsrcpgrlrel');
 // ... other tables here
```

## Oracle {#oracle}

請與資料庫管理員聯繫，了解最適合您的Oracle版本的過程。

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>對於Microsoft SQL Server，您可以使用 [本頁](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

以下示例涉及Microsoft SQL Server 2005。 如果您使用其他版本，請與資料庫管理員聯繫，了解有關維護過程的資訊。

1. 首先，使用具有管理員權限的登錄連接到Microsoft SQL Server Management Studio。
1. 前往 **[!UICONTROL Management > Maintenance Plans]** ，按一下右鍵並選擇 **[!UICONTROL Maintenance Plan Wizard]**.
1. 按一下 **[!UICONTROL Next]** 第一頁出現時。
1. 選擇要建立的維護計畫類型（為每個任務或整個計畫的單個計劃分開計畫），然後按一下 **[!UICONTROL Change...]** 按鈕。
1. 在 **[!UICONTROL Job schedule properties]** 視窗中，選取所需的執行設定，然後按一下 **[!UICONTROL OK]**，然後按一下 **[!UICONTROL Next]**.
1. 選擇要執行的維護任務，然後按一下 **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >建議您至少執行下列維護任務。 您也可以選擇統計資訊更新任務，儘管該任務已由資料庫清理工作流執行。

1. 在下拉式清單中，選取您要執行的資料庫 **[!UICONTROL Database Check Integrity]** 任務。
1. 選擇資料庫並按一下 **[!UICONTROL OK]**，然後按一下 **[!UICONTROL Next]**.
1. 配置分配給資料庫的最大大小，然後按一下 **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >如果資料庫的大小超過此閾值，維護計畫將嘗試刪除未使用的資料以釋放空間。

1. 重新整理或重建索引：

   * 如果指數碎片率在10%到40%之間，建議進行重組。

      選擇要重新整理的資料庫和對象（表或視圖），然後按一下 **[!UICONTROL Next]**.

      >[!NOTE]
      >
      >根據您的配置，您可以選擇以前選擇的表或資料庫中的所有表。

   * 如果索引碎片率高於40%，則建議重建。

      選擇要應用於索引重建任務的選項，然後按一下 **[!UICONTROL Next]**.

      >[!NOTE]
      >
      >從處理器的使用角度看，重建索引過程更加緊縮，它鎖定了資料庫資源。 選取 **[!UICONTROL Keep index online while reindexing]** 選項。

1. 選取要在活動報表中顯示的選項，然後按一下 **[!UICONTROL Next]**.
1. 檢查為維護計畫配置的任務清單，然後按一下 **[!UICONTROL Finish]**.

   此時將顯示維護計畫的摘要及其各個步驟的狀態。

1. 維護計畫完成後，按一下 **[!UICONTROL Close]**.
1. 在Microsoft SQL Server瀏覽器中，按兩下 **[!UICONTROL Management > Maintenance Plans]** 檔案夾。
1. 選擇Adobe Campaign維護計畫：在工作流程中會詳細說明各種步驟。

   請注意，物件已建立於 **[!UICONTROL SQL Server Agent > Jobs]** 檔案夾。 此物件可讓您啟動維護計畫。 在本例中，只有一個對象，因為所有維護任務都屬於同一計畫的一部分。

   >[!IMPORTANT]
   >
   >要運行此對象，必須啟用Microsoft SQL Server代理。

**為工作表配置單獨的資料庫**

>[!NOTE]
>
>此設定為選用。

此 **WdbcOptions_TempDbName** 選項可讓您為Microsoft SQL Server上的工作表配置單獨的資料庫。 這樣可優化備份和複製。

如果希望在另一個資料庫上建立工作表（例如，在執行工作流期間建立的表），則可以使用此選項。

將選項設定為「tempdb.dbo.」時，將在Microsoft SQL Server的預設臨時資料庫中建立工作表。 資料庫管理員需要允許對tempdb資料庫的寫訪問。

如果設定了該選項，則它將用於在Adobe Campaign（主資料庫和外部帳戶）中配置的所有Microsoft SQL Server資料庫。 請注意，如果兩個外部帳戶共用同一台伺服器，則可能會發生衝突（因為tempdb是唯一的）。 同樣地，如果兩個Campaign執行個體使用相同的MSSQL伺服器，則如果它們使用相同的tempdb，則可能會發生衝突。
