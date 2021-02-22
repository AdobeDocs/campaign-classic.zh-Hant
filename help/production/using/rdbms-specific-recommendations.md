---
solution: Campaign Classic
product: campaign
title: RDBMS 特定建議
description: RDBMS 特定建議
audience: production
content-type: reference
topic-tags: database-maintenance
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 1%

---


# RDBMS 特定建議{#rdbms-specific-recommendations}

為協助您設定維護計畫，本節列出一些適合Adobe Campaign支援的各種RDBMS引擎的建議／最佳實務。 不過，這些只是建議。 您必須依照內部程式和限制，將它們調整為符合您的需求。 您的資料庫管理員負責構建和執行這些計畫。

## PostgreSQL {#postgresql}

### 檢測大表{#detecting-large-tables}

1. 您可以將下列視圖添加到資料庫中：

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

1. 運行以下命令可以發現大型表和索引：

   ```
   select * from uvSpace;
   ```

### 簡單維護{#simple-maintenance}

在PostgreSQL下，您可以使用的典型命令是&#x200B;**真空full**&#x200B;和&#x200B;**reindex**。

以下是使用以下兩個命令定期執行的SQL維護計畫的典型示例：

```
vacuum full nmsdelivery;
 reindex table nmsdelivery;
 
 vacuum full nmsdeliverystat;
 reindex table nmsdeliverystat;
 
 vacuum full xtkworkflow;
 reindex table xtkworkflow;
 
 vacuum full xtkworkflowevent;
 reindex table xtkworkflowevent;
 
 vacuum full xtkworkflowjob;
 reindex table xtkworkflowjob;
 
 vacuum full xtkworkflowlog;
 reindex table xtkworkflowlog;
 
 vacuum full xtkworkflowtask;
 reindex table xtkworkflowtask;
 
 vacuum full xtkjoblog;
 reindex table xtkjoblog;
 
 vacuum full xtkjob;
 reindex table xtkjob;
 
 vacuum full nmsaddress;
 reindex table nmsaddress;

 vacuum full nmsdeliverypart;
 reindex table nmsdeliverypart;
 
 vacuum full nmsmirrorpageinfo;
 reindex table nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe建議從較小的表格開始：這樣，如果大型表上的進程失敗（故障風險最高），則至少已完成部分維護。
>* Adobe會重新命令新增資料模型專屬的表格，這些表格可能會受到重大更新的影響。 如果每日資料複製流量較大，則&#x200B;**NmsRecipient**&#x200B;可能會出現這種情況。
>* **真空**&#x200B;和&#x200B;**re-index**&#x200B;命令將鎖定表，該表在執行維護時會暫停某些進程。
>* 對於超大表（通常高於5 Gb）,**真空完全**&#x200B;會變得相當低效，而且需要很長時間。 Adobe不建議將它用於&#x200B;**YyyNmsBroadLogXxx**&#x200B;表。
>* 此維護作業可透過Adobe Campaign工作流程，使用&#x200B;**[!UICONTROL SQL]**&#x200B;活動來實施（如需詳細資訊，請參閱[本節](../../workflow/using/architecture.md)）。 請確定您排程的維護時間較短，不會與備份視窗發生衝突。
>



### 重建資料庫{#rebuilding-a-database}

由於&#x200B;**真空full**&#x200B;鎖定表，因此PostgreSQL無法提供執行聯機表重建的簡單方法，因此無法正常生產。 這表示在未使用表時必須執行維護。 您可以：

* 在Adobe Campaign平台停止時執行維護，
* 停止可能寫入正在重建的表格的各種Adobe Campaign子服務（**nlserver stop wfserver instance_name**&#x200B;以停止工作流程進程）。

以下是使用特定函式生成所需DDL的表碎片整理示例。 以下SQL可讓您建立兩個新函式：**GenRebuildTablePart1**&#x200B;和&#x200B;**GenRebuildTablePart2**，它們可用於生成必要的DDL以重新建立表。

* 第一個函式可讓您建立工作表（** _tmp**此處），此為原始表格的副本。
* 然後，第二個函式刪除原始表並更名工作表及其索引。
* 使用兩個函式（而非一個函式）表示如果第一個函式失敗，您不會冒刪除原始表格的風險。

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

以下示例可用於工作流以重建所需的表，而不是使用&#x200B;**真空/rebuild**&#x200B;命令：

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

請聯繫您的資料庫管理員以瞭解最適合您的Oracle版本的過程。

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>對於Microsoft SQL Server，可以使用本頁[中詳細說明的維護計畫。](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html)

以下示例涉及Microsoft SQL Server 2005。 如果您使用其他版本，請連絡您的資料庫管理員以瞭解維護程式。

1. 首先，使用具有管理員權限的登錄功能連接到Microsoft SQL Server Management Studio。
1. 前往&#x200B;**[!UICONTROL Management > Maintenance Plans]**&#x200B;資料夾，按一下滑鼠右鍵並選擇&#x200B;**[!UICONTROL Maintenance Plan Wizard]**
1. 第一頁出現時，按一下&#x200B;**[!UICONTROL Next]**。
1. 選擇要建立的維護計畫類型（為每個任務單獨計畫或整個計畫單個計畫），然後按一下&#x200B;**[!UICONTROL Change...]**&#x200B;按鈕。
1. 在&#x200B;**[!UICONTROL Job schedule properties]**&#x200B;視窗中，選取所要的執行設定，然後按一下&#x200B;**[!UICONTROL OK]**，然後按一下&#x200B;**[!UICONTROL Next]**。
1. 選擇要執行的維護任務，然後按一下&#x200B;**[!UICONTROL Next]**。

   >[!NOTE]
   >
   >我們建議至少執行以下所示的維護任務。 您也可以選擇統計資訊更新任務，儘管該任務已由資料庫清理工作流執行。

1. 在下拉清單中，選擇要運行&#x200B;**[!UICONTROL Database Check Integrity]**&#x200B;任務的資料庫。
1. 選擇資料庫並按一下&#x200B;**[!UICONTROL OK]** ，然後按一下&#x200B;**[!UICONTROL Next]**。
1. 配置分配給資料庫的最大大小，然後按一下&#x200B;**[!UICONTROL Next]**。

   >[!NOTE]
   >
   >如果資料庫的大小超過此閾值，維護計畫將嘗試刪除未使用的資料以釋放空間。

1. 重新組織或重建索引：

   * 如果指數碎片化率在10%到40%之間，建議進行重組。

      選擇要重組的資料庫和對象（表或視圖），然後按一下&#x200B;**[!UICONTROL Next]**。

      >[!NOTE]
      >
      >根據您的配置，您可以選擇以前選擇的表或資料庫中的所有表。

   * 如果索引碎片率高於40%，建議重建。

      選擇要應用於索引重建任務的選項，然後按一下&#x200B;**[!UICONTROL Next]**。

      >[!NOTE]
      >
      >從處理器的使用角度看，重建索引過程更加緊張，並鎖定了資料庫資源。 如果希望索引在重建期間可用，請勾選&#x200B;**[!UICONTROL Keep index online while reindexing]**&#x200B;選項。

1. 選取您要在活動報表中顯示的選項，然後按一下&#x200B;**[!UICONTROL Next]**。
1. 檢查為維護計畫配置的任務清單，然後按一下&#x200B;**[!UICONTROL Finish]**。

   此時將顯示維護計畫的概要及其各步驟的狀態。

1. 維護計畫完成後，按一下&#x200B;**[!UICONTROL Close]**。
1. 在Microsoft SQL Server瀏覽器中，按兩下&#x200B;**[!UICONTROL Management > Maintenance Plans]**&#x200B;資料夾。
1. 選擇Adobe Campaign維護計畫：工作流程中會詳細說明各種步驟。

   請注意，**[!UICONTROL SQL Server Agent > Jobs]**&#x200B;資料夾中已建立物件。 此物件可讓您啟動維護計畫。 在我們的示例中，只有一個對象，因為所有維護任務都是同一計畫的一部分。

   >[!IMPORTANT]
   >
   >要運行此對象，必須啟用Microsoft SQL Server代理。

**為工作表配置單獨的資料庫**

>[!NOTE]
>
>此配置是可選的。

**WdbcOptions_TempDbName**&#x200B;選項允許您為Microsoft SQL Server上的工作表配置單獨的資料庫。 這樣可以優化備份和複製。

如果希望在另一個資料庫上建立工作表（例如，在工作流執行期間建立的表），則可使用此選項。

將選項設定為&quot;tempdb.dbo.&quot;時，將在Microsoft SQL Server的預設臨時資料庫上建立工作表。 資料庫管理員需要允許對tempdb資料庫的寫訪問。

如果設定了此選項，它將用於在Adobe Campaign（主資料庫和外部帳戶）中設定的所有Microsoft SQL Server資料庫。 請注意，如果兩個外部帳戶共用同一個伺服器，則可能會發生衝突（因為tempdb將是唯一的）。 同樣地，如果兩個Campaign實例使用相同的MSSQL伺服器，則使用相同的tempdb時可能會發生衝突。
