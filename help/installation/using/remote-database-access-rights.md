---
product: campaign
title: 存取外部資料庫的許可權
description: 外部資料庫存取許可權
feature: Installation, Instance Settings, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---

# 遠端資料庫存取許可權 {#remote-database-access-rights}



首先，為了使使用者可以透過FDA在外部資料庫上執行操作，後者必須在Adobe Campaign中具有特定的命名許可權。

1. 在Adobe Campaign總管中選取&#x200B;**[!UICONTROL Administration > Access Management > Named Rights]**&#x200B;節點。
1. 指定您選擇的標籤，以建立新的權利。
1. **[!UICONTROL Name]**&#x200B;欄位必須使用下列格式&#x200B;**user：base@server**，其中：

   * **user**&#x200B;對應於外部資料庫中的使用者名稱。
   * **base**&#x200B;對應到外部資料庫的名稱。
   * **伺服器**&#x200B;對應到外部資料庫伺服器的名稱。

     >[!NOTE]
     >
     >**：base**&#x200B;部分在Oracle中是選用的。

1. 儲存已命名的許可權，然後從Adobe Campaign檔案總管的&#x200B;**[!UICONTROL Administration > Access Management > Operators]**&#x200B;節點將其連結至您選擇的使用者。

然後，若要處理外部資料庫中包含的資料，Adobe Campaign使用者必須至少擁有資料庫的「寫入」許可權，才能建立工作表。 Adobe Campaign會自動刪除這些專案。

一般而言，下列許可權是必要的：

* **CONNECT**：連線到遠端資料庫，
* **讀取資料**：對包含客戶資料的資料表的唯讀存取權，
* **讀取&#39;MetaData&#39;**：存取伺服器資料目錄以取得資料表結構，
* **LOAD**：在工作表中大量載入（處理集合和聯結時需要），
* **TABLE/INDEX/PROCEDURE/FUNCTION**&#x200B;的&#x200B;**建立/卸除** (僅適用於Adobe Campaign產生的工作表)，
* **EXPLAIN** （建議）：若發生問題，請監視效能，
* **寫入資料** （視整合情況而定）。

資料庫管理員需要讓這些許可權與每個資料庫引擎的特定許可權相符。 如需詳細資訊，請參閱下節。

## FDA許可權 {#fda-rights}

|   | Snowflake | Redshift | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **正在連線到遠端資料庫** | 倉儲使用量、資料庫使用量和綱要許可權使用量 | 建立連結至AWS帳戶的使用者 | 建立工作階段許可權 | CONNECT許可權 | CONNECT許可權 | 建立繫結至遠端主機的使用者（具有ALL PRIVILEGES） |
| **正在建立資料表** | 依據綱要許可權建立表格 | CREATE許可權 | CREATE TABLE許可權 | 建立表格許可權 | CREATE許可權 | CREATE許可權 |
| **正在建立索引** | N/A | CREATE許可權 | 索引或建立任何索引許可權 | ALTER許可權 | CREATE許可權 | INDEX許可權 |
| **正在建立函式** | 在綱要許可權上建立函式 | 使用LANGUAGE PLYTHONU許可權可呼叫外部Python指令碼 | CREATE PROCEDURE或CREATE ANY PROCEDURE許可權 | 建立函式許可權 | USAGE許可權 | CREATE ROUTINE許可權 |
| **正在建立程式** | N/A | 使用LANGUAGE PLYTHONU許可權可呼叫外部Python指令碼 | CREATE PROCEDURE或CREATE ANY PROCEDURE許可權 | 建立程式許可權 | USAGE許可權（程式是函式） | CREATE ROUTINE許可權 |
| **移除物件（表格、索引、函式、程式）** | 擁有物件 | 擁有物件或成為超級使用者 | 卸除任何&lt;物件>許可權 | ALTER許可權 | 表格：擁有表格索引：擁有索引函式：擁有函式 | DROP許可權 |
| **監視執行** | 必要物件的MONITOR許可權 | 使用EXPLAIN命令不需要許可權 | INSERT和SELECT許可權以及執行EXPLAIN PLAN所依據之陳述式的必要許可權 | SHOWPLAN許可權 | 使用EXPLAIN陳述式不需要任何許可權 | SELECT許可權 |
| **正在寫入資料** | INSERT和/或UPDATE許可權（視寫入作業而定） | INSERT和UPDATE許可權 | INSERT and UPDATE或INSERT and UPDATE ANY TABLE許可權 | 插入和更新許可權 | INSERT和UPDATE許可權 | INSERT和UPDATE許可權 |
| **正在將資料載入資料表** | 在綱要上建立階段，選取並在目標表格上插入許可權 | SELECT和INSERT許可權 | SELECT和INSERT許可權 | 插入、管理大量作業和變更表格許可權 | SELECT和INSERT許可權 | FILE許可權 |
| **正在存取使用者端資料** | 選取（未來的）表格或檢視許可權 | SELECT許可權 | 選取或選取任何表格許可權 | 選取許可權 | SELECT許可權 | SELECT許可權 |
| **存取中繼資料** | 選取INFORMATION_SCHEMA綱要許可權 | SELECT許可權 | 使用DESCRIBE陳述式不需要許可權 | 檢視定義許可權 | 使用「\d table」命令不需要許可權 | SELECT許可權 |

|   | teradata | InfiniDB | sybase IQ/Sybase ASE | Netezza | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|
| **正在連線到遠端資料庫** | CONNECT許可權 | 建立繫結至遠端主機的使用者（具有ALL PRIVILEGES） | 使用CONNECT陳述式不需要許可權 | 不需要許可權 | CONNECT許可權 |
| **正在建立資料表** | CREATE TABLE或TABLE關鍵字 | CREATE許可權 | RESOURCE授權和CREATE許可權 | TABLE許可權 | CREATE許可權 |
| **正在建立索引** | CREATE INDEX or INDEX關鍵字 | INDEX許可權 | RESOURCE授權和CREATE許可權 | INDEX許可權 | CREATE許可權 |
| **正在建立函式** | CREATE FUNCTION或FUNCTION關鍵字 | CREATE ROUTINE許可權 | Java函式的RESOURCE授權或DBA授權 | FUNCTION許可權 | CREATE函式許可權 |
| **正在建立程式** | CREATE PROCEDURE or PROCEDURE關鍵字 | CREATE ROUTINE許可權 | 資源授權 | PROCEDURE許可權 | CREATE函式許可權 |
| **移除物件（表格、索引、函式、程式）** | DROP &lt; object >或物件相關關鍵字 | DROP許可權 | 擁有物件或DBA許可權 | DROP許可權 | 擁有物件 |
| **監視執行** | 使用EXPLAIN陳述式不需要任何許可權 | SELECT許可權 | 只有系統管理員可以執行sp_showplan | 使用EXPLAIN陳述式不需要任何許可權 | 使用EXPLAIN陳述式不需要任何許可權 |
| **正在寫入資料** | INSERT和UPDATE許可權 | INSERT和UPDATE許可權 | 插入和更新許可權 | INSERT和UPDATE許可權 | INSERT和UPDATE許可權 |
| **正在將資料載入資料表** | SELECT和INSERT許可權分別使用COPY TO和COPY FROM陳述式 | FILE許可權 | 成為資料表的擁有者或ALTER許可權。 視於 — gl選項而定，只有在使用者具有DBA許可權時，才能執行LOAD TABLE | SELECT和INSERT許可權 | SELECT和INSERT許可權 |
| **正在存取使用者端資料** | SELECT許可權 | 選取許可權 | SELECT許可權 | SELECT許可權 |
| **存取中繼資料** | SHOW許可權 | SELECT許可權 | 使用DESCRIBE陳述式不需要許可權 | 使用「\d table」命令不需要許可權 | 使用SHOW命令不需要任何許可權 |
