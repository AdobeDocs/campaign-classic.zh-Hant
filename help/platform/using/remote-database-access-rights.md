---
title: 訪問外部資料庫
seo-title: 訪問外部資料庫
description: 訪問外部資料庫
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 17eed4f4ead8ce4f424d4fb2681269e888229692

---


# 遠程資料庫訪問權限 {#remote-database-access-rights}

首先，為了讓使用者可以透過FDA對外部資料庫執行作業，後者必須在Adobe Campaign中擁有特定的命名權限。

1. 在Adobe Campaign **[!UICONTROL Administration > Access Management > Named Rights]** 檔案總管中選取節點。
1. 指定您選擇的標籤以建立新的權限。
1. 欄位 **[!UICONTROL Name]** 必須採用下列格式的 **使用者：base@server**，其中：

   * **user** 與外部資料庫中的用戶名相對應。
   * **base** 與外部資料庫的名稱相對應。
   * **伺服器** 與外部資料庫伺服器的名稱相對應。

      >[!NOTE]
      >
      >Oracle **中** :base部件是可選的。

1. 儲存指名的右側，然後從Adobe Campaign檔案總管的節 **[!UICONTROL Administration > Access Management > Operators]** 點將其連結至您選擇的使用者。

然後，若要處理外部資料庫中包含的資料，Adobe Campaign使用者必須在資料庫上至少擁有「寫入」權限，才能建立工作表。 Adobe Campaign會自動刪除這些項目。

一般而言，下列權利是必要的：

* **連接**:連接到遠程資料庫，
* **讀取資料**:只讀存取包含客戶資料的表格，
* **閱讀「中繼資料」**:存取伺服器資料目錄以取得表格結構，
* **載入**:在工作表中成批載入（處理系列和聯接時需要）,
* **CREATE/DROP** for **TABLE/INDEX/PROCEDURE/FUNCTION**,
* **EXPLAIN** （建議）:在遇到問題時監控效能，
* **WRITE Data** （視整合藍本而定）。

資料庫管理員需要使這些權限與每個資料庫引擎的特定權限相匹配。 如需詳細資訊，請參閱以下章節。

## FDA權利 {#fda-rights}

|   | 雪花 | 紅移 | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **連接到遠程資料庫** | 倉庫使用與資料庫權限使用 | 建立連結到AWS帳戶的用戶 | 建立會話權限 | CONNECT權限 | CONNECT權限 | 建立綁定到具有ALL PRIVILEGES的遠程主機的用戶 |
| **建立表** | 建立方案權限表 | CREATE權限 | 建立表權限 | 建立表權限 | CREATE權限 | CREATE權限 |
| **建立索引** | 不適用 | CREATE權限 | 索引或建立任何索引權限 | ALTER權限 | CREATE權限 | INDEX權限 |
| **建立函式** | CREATE FUNCTION ON SCHEMA權限 | USAGE ON LANGUAGE plpythonu特權可調用外部python指令碼 | 建立過程或建立任何過程權限 | CREATE FUNCTION權限 | 使用權限 | 建立常式權限 |
| **建立過程** | 建立方案權限的過程 | USAGE ON LANGUAGE plpythonu特權可調用外部python指令碼 | 建立過程或建立任何過程權限 | 建立過程權限 | USAGE權限（過程是函式） | 建立常式權限 |
| **刪除對象（表、索引、函式、過程）** | 擁有對象 | 擁有對象或是超級用戶 | 刪除任何&lt;對象>權限 | ALTER權限 | 表格：擁有表索引：擁有索引函式：擁有函式 | DROP權限 |
| **監控執行** | 對所需對象的MONITOR權限 | 使用EXPLAIN命令無需權限 | INSERT和SELECT權限以及執行EXPLAIN PLAN所基於的語句的必要權限 | SHOWPLAN權限 | 使用EXPLAIN語句無需權限 | SELECT權限 |
| **寫入資料** | INSERT和／或UPDATE權限（取決於寫操作） | 插入和更新權限 | 插入、更新或插入和更新任何表權限 | 插入和更新權限 | 插入和更新權限 | 插入和更新權限 |
| **將資料載入到表中** | 在架構上建立階段，在目標表權限上選擇並插入 | 選擇和插入權限 | 選擇和插入權限 | 插入、管理批量操作和更改表權限 | 選擇和插入權限 | 檔案權限 |
| **訪問客戶端資料** | 選擇（未來）表或視圖權限 | SELECT權限 | 選擇或選擇任何表權限 | SELECT權限 | SELECT權限 | SELECT權限 |
| **存取中繼資料** | 選擇資訊方案權限 | SELECT權限 | 使用DESCRIBE語句無需權限 | 檢視定義權限 | 使用&quot;\d table&quot;命令不需要權限 | SELECT權限 |

|   | DB2 UDB | TeraData | InfiniDB | Sybase IQ / Sybase ASE | 內泰扎 | 青梅 | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **連接到遠程資料庫** | CONNECT授權 | CONNECT權限 | 建立綁定到具有ALL PRIVILEGES的遠程主機的用戶 | 使用CONNECT語句無需權限 | 無需權限 | CONNECT權限 | CONNECT權限 |
| **建立表** | CREATETAB授權 | 建立表或表關鍵字 | CREATE權限 | RESOURCE權限和CREATE權限 | TABLE權限 | CREATE權限 | CREATE權限 |
| **建立索引** | INDEX權限 | CREATE INDEX或INDEX關鍵字 | INDEX權限 | RESOURCE權限和CREATE權限 | INDEX權限 | CREATE權限 | CREATE權限 |
| **建立函式** | IMPLICIT_SCHEMA特權或CREATEIN權限 | CREATE FUNCTION或FUNCTION關鍵字 | 建立常式權限 | Java函式的RESOURCE權限或DBA權限 | FUNCTION權限 | 使用權限 | CREATE FUNCTION權限 |
| **建立過程** | IMPLICIT_SCHEMA特權或CREATEIN權限 | 建立過程或過程關鍵字 | 建立常式權限 | 資源授權 | PROCEDURE權限 | 使用權限 | CREATE FUNCTION權限 |
| **刪除對象（表、索引、函式、過程）** | DROPIN權限或CONTROL權限或對象的所有權 | DROP &lt;對象>或對象相關關鍵字 | DROP權限 | 擁有對象或DBA權限 | DROP權限 | 擁有對象 | 擁有對象 |
| **監控執行** | EXPLAIN授權 | 使用EXPLAIN語句無需權限 | SELECT權限 | 只有系統管理員可以執行sp_showplan | 使用EXPLAIN語句無需權限 | 使用EXPLAIN語句無需權限 | 使用EXPLAIN語句無需權限 |
| **寫入資料** | INSERT和UPDATE權限或DATAACCESS權限 | 插入和更新權限 | 插入和更新權限 | 插入和更新權限 | 插入和更新權限 | 插入和更新權限 | 插入和更新權限 |
| **將資料載入到表中** | LOAD授權 | 選擇和插入權限以分別使用COPY TO和COPY FROM語句 | 檔案權限 | 成為表的所有者或ALTER權限。 根據-gl選項，僅當用戶具有DBA權限時才可能執行LOAD TABLE | 選擇和插入權限 | 選擇和插入權限 | 選擇和插入權限 |
| **訪問客戶端資料** | INSERT/UPDATE權限或DATAACCESS權限 | SELECT權限 | SELECT權限 | SELECT權限 | SELECT權限 | SELECT權限 | SELECT權限 |
| **存取中繼資料** | 使用DESCRIBE語句無需授權 | SHOW權限 | SELECT權限 | 無需使用DESCRIBE語句的權限 | 使用&quot;\d table&quot;命令不需要權限 | 使用&quot;\d table&quot;命令不需要權限 | 使用SHOW命令不需要權限 |