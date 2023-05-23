---
product: campaign
title: RDBMS 特定建議
description: RDBMS 特定建議
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 1%

---

# RDBMS 特定建議{#rdbms-specific-recommendations}



為了幫助您設定維護計畫，本節列出了一些適用於Adobe Campaign支援的各種RDBMS引擎的建議和最佳做法。 不過，這些只是建議。 根據您的內部程式和限制，您應根據您的需要調整這些程式。 您的資料庫管理員有責任構建和執行這些計畫。

## PostgreSQL {#postgresql}

### 檢測大型表 {#detecting-large-tables}

1. 可以將以下視圖添加到資料庫：

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

   或者，您也可以運行此查詢，例如，以集中查看所有索引大小：

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

### 簡單的維護 {#simple-maintenance}

在PostgreSQL中，可以使用以下典型關鍵字：

* 真空（完全、分析、詳細）

要運行DAVOM操作，並對其進行分析和計時，可以使用以下語法：

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) <table>;
```

強烈建議您不要忽略ANALYZE語句。 否則，真空表將保留沒有統計資訊。 原因是生成新表，然後刪除舊表。 因此，表的對象ID(OID)會更改，但不計算統計資訊。 因此，您將立即遇到效能問題。

以下是要定期執行的SQL維護計畫的典型示例：

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdelivery;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverystat;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflow;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowevent;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowlog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkworkflowtask;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjoblog;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) xtkjob;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsaddress;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsdeliverypart;

\timing on
VACUUM (FULL, ANALYZE, VERBOSE) nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe建議從較小的表開始：這樣，如果流程在大型表（故障風險最高）上失敗，則至少部分維護已完成。
>* Adobe建議您添加特定於資料模型的表，這些表可能會受到重大更新的影響。 這可以 **Nms收件人** 如果您有大量的每日資料複製流。
>* DAVOM語句將鎖定表，該表在執行維護時暫停某些進程。
>* 對於非常大的表（通常高於5 Gb），真空FULL語句會變得非常低效，並且需要很長時間。 Adobe不建議將它用於 **YyyNmsBroadLogXxx** 的子菜單。
>* 此維護操作可通過Adobe Campaign工作流實現， **[!UICONTROL SQL]** 的子菜單。 如需詳細資訊，請參閱[本章節](../../workflow/using/architecture.md)。確保將維護時間安排在活動時間不與備份窗口衝突的較短時間。
>


### 重建資料庫 {#rebuilding-a-database}

PostgreSQL不提供執行聯機表重建的簡單方法，因為DAVOM FULL語句鎖定了表，因此無法正常生產。 這意味著在不使用表時必須執行維護。 您可以：

* 在Adobe Campaign平台停止時執行維護，
* 停止可能寫入正在重建的表中的Adobe Campaign各子服務(**nlserver停止wfserver實例名** 停止工作流進程)。

下面是使用特定函式生成必要DDL的表碎片整理的示例。 使用以下SQL可以建立兩個新函式： **GenRebuildTablePart1** 和 **GenRebuildTablePart2**，可用於生成重新建立表所需的DDL。

* 第一個函式用於建立工作表(** _tmp**)，該工作表是原始表的副本。
* 然後，第二個函式刪除原始表並更名工作表及其索引。
* 使用兩個函式而不是一個函式意味著如果第一個函式失敗，則不會存在刪除原始表的風險。

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

以下示例可用於工作流中重建所需的表，而不是使用 **真空/重建** 命令：

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

請與資料庫管理員聯繫，瞭解最適合您的Oracle版本的過程。

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>對於MicrosoftSQL Server，可以使用詳細的維護計畫 [此頁](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html)。

以下示例涉及MicrosoftSQL Server 2005。 如果您使用的是其他版本，請與資料庫管理員聯繫以瞭解有關維護過程的資訊。

1. 首先，使用具有管理員權限的登錄名連接到MicrosoftSQL Server Management Studio。
1. 轉到 **[!UICONTROL Management > Maintenance Plans]** 資料夾，按一下右鍵該資料夾並選擇 **[!UICONTROL Maintenance Plan Wizard]**。
1. 按一下 **[!UICONTROL Next]** 第一頁出來。
1. 選擇要建立的維護計畫類型（為每個任務單獨計畫或整個計畫的單個計畫），然後按一下 **[!UICONTROL Change...]** 按鈕
1. 在 **[!UICONTROL Job schedule properties]** 窗口，選擇所需的執行設定並按一下 **[!UICONTROL OK]**，然後按一下 **[!UICONTROL Next]**。
1. 選擇要執行的維護任務，然後按一下 **[!UICONTROL Next]**。

   >[!NOTE]
   >
   >我們建議至少執行下面所示的維護任務。 您也可以選擇統計資訊更新任務，儘管該任務已由資料庫清理工作流執行。

1. 在下拉清單中，選擇要在其上運行資料庫 **[!UICONTROL Database Check Integrity]** 的子菜單。
1. 選擇資料庫並按一下 **[!UICONTROL OK]**，然後按一下 **[!UICONTROL Next]**。
1. 配置分配給資料庫的最大大小，然後按一下 **[!UICONTROL Next]**。

   >[!NOTE]
   >
   >如果資料庫大小超過此閾值，則維護計畫將嘗試刪除未使用的資料以釋放空間。

1. 重新組織或重建索引：

   * 如果指數碎片化率在10%到40%之間，則建議重組。

      選擇要重新組織的資料庫和對象（表或視圖），然後按一下 **[!UICONTROL Next]**。

      >[!NOTE]
      >
      >根據您的配置，您可以選擇以前選擇的表或資料庫中的所有表。

   * 如果索引碎片率高於40%，則建議重建。

      選擇要應用於索引重建任務的選項，然後按一下 **[!UICONTROL Next]**。

      >[!NOTE]
      >
      >在處理器使用方面，重建索引過程更加緊張，它鎖定了資料庫資源。 選擇 **[!UICONTROL Keep index online while reindexing]** 的子菜單。

1. 選擇要在活動報告中顯示的選項，然後按一下 **[!UICONTROL Next]**。
1. 檢查為維護計畫配置的任務清單，然後按一下 **[!UICONTROL Finish]**。

   此時將顯示維護計畫及其各個步驟的狀態的摘要。

1. 維護計畫完成後，按一下 **[!UICONTROL Close]**。
1. 在MicrosoftSQL Server瀏覽器中，按兩下 **[!UICONTROL Management > Maintenance Plans]** 的子菜單。
1. 選擇Adobe Campaign維護計畫：各個步驟在工作流中詳細介紹。

   請注意，已在 **[!UICONTROL SQL Server Agent > Jobs]** 的子菜單。 此對象允許您啟動維護計畫。 在本例中，由於所有維護任務都屬於同一計畫，因此只有一個對象。

   >[!IMPORTANT]
   >
   >要運行此對象，必須啟用MicrosoftSQL Server代理。

**為工作表配置單獨的資料庫**

>[!NOTE]
>
>此配置是可選的。

的 **WdbcOptions_TempDbName** 選項，用於為MicrosoftSQL Server上的工作表配置單獨的資料庫。 這可優化備份和複製。

如果希望在另一個資料庫上建立工作表（例如，在工作流執行期間建立的表），則可以使用此選項。

將選項設定為&quot;tempdb.dbo.&quot;時，將在MicrosoftSQL Server的預設臨時資料庫上建立工作表。 資料庫管理員需要允許對tempdb資料庫的寫訪問。

如果設定了該選項，則它將用於在Adobe Campaign（主資料庫和外部帳戶）中配置的所有MicrosoftSQL Server資料庫。 請注意，如果兩個外部帳戶共用同一台伺服器，則可能會發生衝突（因為tempdb是唯一的）。 同樣，如果兩個Campaign實例使用同一MSSQL伺服器，則如果它們使用同一tempdb，則可能存在衝突。
