---
product: campaign
title: RDBMS 特定建議
description: RDBMS 特定建議
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: a586d70b-1b7f-47c2-a821-635098a70e45
source-git-commit: 624978901943b4c74f50c20298c9596f73b25b1b
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 1%

---

# RDBMS 特定建議{#rdbms-specific-recommendations}



為協助您設定維護計畫，本節列出Adobe Campaign支援之各種RDBMS引擎所調整的一些建議和最佳作法。 不過，這些只是建議。 根據您的內部程式和限制，由您自行調整以符合您的需求。 您的資料庫管理員有責任建立並執行這些計畫。

## PostgreSQL {#postgresql}

### 正在偵測大型資料表 {#detecting-large-tables}

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

1. 您可以執行此查詢來找出大型表格和索引：

   ```
   SELECT * FROM uvSpace;
   ```

   或者，您可以執行此查詢（例如），以共同檢視所有索引大小：

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

### 簡單的維護作業 {#simple-maintenance}

>[!IMPORTANT]
>
>Adobe強烈建議不要在CampaignAdobe託管的資料庫設定上執行VACUUM FULL。建議的維護作業僅適用於ON-PREMISE安裝。 對於自訂表格實作和結構描述，使用VACUUM FULL時，需自行承擔風險，因為VACUUM — 不進行監視 — 可以獨佔鎖定表格，導致查詢逾時，並且在某些情況下會鎖定整個資料庫。

在PostgreSQL中，您可以使用下列一般關鍵字：

* 真空（完整、分析、詳細）

若要執行VACUUM操作並加以分析和計時，您可以使用下列語法：

```
\timing on
VACUUM (FULL, ANALYZE, VERBOSE) <table>;
```

我們強烈建議您不要忽略ANALYZE陳述式。 否則，抽真空的表格將沒有任何統計資料。 原因是建立了新表格，然後刪除了舊表格。 因此，表格的物件ID (OID)會變更，但不會計算統計資料。 因此，您將會立即遇到效能問題。

以下是定期執行的SQL維護計畫的典型範例：

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
>* Adobe建議從較小的表格開始：如此一來，如果程式在大型表格（失敗風險最高的表格）上失敗，至少部分的維護作業已完成。
>* Adobe建議您新增資料模型專屬的表格，這些表格可能會有重大更新。 這種情況可能適用於 **NmsRecipient** 如果您的每日資料複製流程很大。
>* VACUUM陳述式會鎖定表格，在執行維護作業時會暫停某些程式。
>* 對於非常大的表格（通常超過5 Gb），VACUUM FULL陳述式可能會變得相當低效，並需要很長的時間。 Adobe不建議將其用於 **YyynmsBroadLogXxx** 表格。
>* 此維護操作可透過Adobe Campaign工作流程實施，使用 **[!UICONTROL SQL]** 活動。 有關詳細資訊，請參閱 [本節](../../workflow/using/architecture.md). 請確定您排程進行維護作業的時間，以免與備份期間發生衝突。
>

### 重建資料庫 {#rebuilding-a-database}

由於VACUUM FULL陳述式會鎖定資料表，因此無法正常生產，因此PostgreSQL不提供執行線上資料表重建的簡單方法。 這表示維護必須在未使用表格時執行。 您可以：

* 當Adobe Campaign平台停止時，
* 停止各種可能寫入正在重建之表格的Adobe Campaign子服務(**nlserver stop wfserver instance_name** 以停止工作流程程式)。

以下是使用特定函式產生必要DDL的表格重組範例。 下列SQL可讓您建立兩個新函式： **GenRebuildTablePart1** 和 **GenRebuildTablePart2**，可用來產生必要的DDL以重新建立表格。

* 第一個函式可讓您建立工作表(**_tmp**此處)，它是原始表格的副本。
* 然後第二個函式會刪除原始表格並重新命名工作表及其索引。
* 使用兩個函式而非一個函式，表示如果第一個函式失敗，您就不會有刪除原始表格的風險。

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

以下範例可用於工作流程中，以重建所需的表格，而非使用 **真空/重建** 命令：

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

請連絡您的資料庫管理員，瞭解最適合您Oracle版本的程式。

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>對於Microsoft SQL Server，您可以使用詳細維護計畫 [此頁面](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

以下範例與Microsoft SQL Server 2005有關。 如果您使用其他版本，請連絡資料庫管理員，瞭解維護程式。

1. 首先，以具有管理員許可權的登入名稱連線至Microsoft SQL Server Management Studio。
1. 前往 **[!UICONTROL Management > Maintenance Plans]** 資料夾，在資料夾上按一下滑鼠右鍵，然後選擇 **[!UICONTROL Maintenance Plan Wizard]**.
1. 按一下 **[!UICONTROL Next]** 當第一頁出現時。
1. 選取您要建立的維護計畫型別（每個作業分別排程或整個計畫的單一排程），然後按一下 **[!UICONTROL Change...]** 按鈕。
1. 在 **[!UICONTROL Job schedule properties]** 視窗，選取所需的執行設定並按一下 **[!UICONTROL OK]**，然後按一下 **[!UICONTROL Next]**.
1. 選取您要執行的維護工作，然後按一下 **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >建議您至少執行下列維護任務。 您也可以選取統計資料更新工作，儘管該工作已由資料庫清理工作流程執行。

1. 在下拉式清單中，選取要在其上執行 **[!UICONTROL Database Check Integrity]** 任務。
1. 選取資料庫並按一下 **[!UICONTROL OK]**，然後按一下 **[!UICONTROL Next]**.
1. 設定配置給資料庫的大小上限，然後按一下 **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >如果資料庫的大小超過此臨界值，維護計畫將嘗試刪除未使用的資料以釋放空間。

1. 重新組織或重建索引：

   * 如果索引片段率介於10%到40%之間，建議進行重組。

     選擇要重新組織的資料庫和物件（表格或檢視表），然後按一下 **[!UICONTROL Next]**.

     >[!NOTE]
     >
     >根據您的組態，您可以選擇先前選取的表格或資料庫中的所有表格。

   * 如果索引片段率高於40%，建議重新建置。

     選取要套用至索引重建工作的選項，然後按一下 **[!UICONTROL Next]**.

     >[!NOTE]
     >
     >重新建立索引程式在處理器使用方面更受限制，而且會鎖定資料庫資源。 選取 **[!UICONTROL Keep index online while reindexing]** 選項。

1. 選取您要在活動報表中顯示的選項，然後按一下 **[!UICONTROL Next]**.
1. 檢查為維護計畫設定的任務清單，然後按一下 **[!UICONTROL Finish]**.

   此時會顯示維護計畫摘要及其各個步驟的狀態。

1. 維護計畫完成後，請按一下 **[!UICONTROL Close]**.
1. 在Microsoft SQL Server Explorer中，按兩下 **[!UICONTROL Management > Maintenance Plans]** 資料夾。
1. 選取Adobe Campaign維護計畫：工作流程中會詳細說明各種步驟。

   請注意，物件已建立於 **[!UICONTROL SQL Server Agent > Jobs]** 資料夾。 此物件可讓您啟動維護計畫。 在我們的範例中，只有一個物件，因為所有維護任務都是相同計畫的一部分。

   >[!IMPORTANT]
   >
   >若要執行此物件，必須啟用Microsoft SQL Server代理程式。

**為工作表格設定個別的資料庫**

>[!NOTE]
>
>此設定是選用的。

此 **WdbcOptions_TempDbName** 選項可讓您為Microsoft SQL Server上的工作表格設定個別的資料庫。 如此可最佳化備份與復寫。

如果您要在其他資料庫中建立工作表格（例如，執行工作流程期間建立的表格），可以使用此選項。

將選項設為「tempdb.dbo.」時，會在Microsoft SQL Server的預設暫存資料庫中建立工作表格。 資料庫管理員需要允許對tempdb資料庫的寫入許可權。

如果設定此選項，則會用於在Adobe Campaign中設定的所有Microsoft SQL Server資料庫（主要資料庫和外部帳戶）。 請注意，如果兩個外部帳戶共用相同的伺服器，則可能會發生衝突（因為tempdb是唯一的）。 同樣地，如果兩個Campaign執行個體使用相同的MSSQL伺服器，則他們使用相同的tempdb時可能會發生衝突。
