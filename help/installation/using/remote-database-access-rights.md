---
product: campaign
title: 訪問外部資料庫的權限
description: 外部資料庫訪問權限
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3d43010e-53f8-4aa2-a651-c422a02191fe
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 1%

---

# 遠端資料庫存取權限 {#remote-database-access-rights}

![](../../assets/v7-only.svg)

首先，為使用者能透過FDA對外部資料庫執行操作，後者在Adobe Campaign中必須具有指定的權限。

1. 選取 **[!UICONTROL Administration > Access Management > Named Rights]** 節點。
1. 指定您選取的標籤，以建立新權限。
1. 此 **[!UICONTROL Name]** 欄位必須採用下列格式 **user:base@server**，其中：

   * **使用者** 與外部資料庫中的用戶名相對應。
   * **基礎** 與外部資料庫的名稱相對應。
   * **伺服器** 與外部資料庫伺服器的名稱相對應。

      >[!NOTE]
      >
      >此 **:base** 部分在Oracle中為可選。

1. 儲存已命名的，然後從 **[!UICONTROL Administration > Access Management > Operators]** 節點。

然後，要處理外部資料庫中包含的資料，Adobe Campaign用戶必須在資料庫上至少具有「寫入」權限，才能建立工作表。 這些資料會由Adobe Campaign自動刪除。

一般而言，下列權利是必要的：

* **CONNECT**:連接到遠程資料庫，
* **讀取資料**:對包含客戶資料的表的只讀訪問，
* **閱讀「MetaData」**:訪問伺服器資料目錄以獲取表結構，
* **載入**:在工作表中大量載入（處理集合和聯接時需要）,
* **建立/放置** for **表/索引/過程/函式** (僅適用於Adobe Campaign產生的工作台),
* **說明** （建議）:以監測出現問題時，
* **寫入資料** （視整合案例而定）。

資料庫管理員需要使這些權限與每個資料庫引擎的特定權限相匹配。 如需詳細資訊，請參閱下方的一節。

## FDA權利 {#fda-rights}

|   | Snowflake | 紅移 | Oracle | SQLServer | PostgreSQL | MySQL |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **連接到遠程資料庫** | 倉庫使用、資料庫使用和方案權限使用 | 建立連結至AWS帳戶的使用者 | 建立會話權限 | CONNECT權限 | CONNECT權限 | 建立與具有ALL PRIVILEGES的遠程主機綁定的用戶 |
| **建立表格** | 建立方案權限表 | 建立權限 | 建立表權限 | 建立表權限 | 建立權限 | 建立權限 |
| **建立索引** | N/A | 建立權限 | 索引或建立任何索引權限 | ALTER權限 | 建立權限 | 索引權限 |
| **建立函式** | 建立架構權限的函式 | USAGE ON LANGUAGE plpythonu特權可調用外部python指令碼 | 建立過程或建立任何過程權限 | 建立函式權限 | 使用權限 | 建立常式權限 |
| **建立程式** | 不適用 | USAGE ON LANGUAGE plpythonu特權可調用外部python指令碼 | 建立過程或建立任何過程權限 | 建立過程權限 | 使用權限（過程是函式） | 建立常式權限 |
| **刪除對象（表、索引、函式、過程）** | 擁有對象 | 擁有對象或是超級用戶 | 刪除ANY &lt;對象>權限 | ALTER權限 | 表：擁有表索引：擁有索引函式：擁有函式 | 刪除權限 |
| **監控執行** | 對所需對象的監視權限 | 使用EXPLAIN命令無需任何權限 | INSERT和SELECT權限以及執行EXPLAIN PLAN所基於的語句的必需權限 | SHOWPLAN權限 | 使用EXPLAIN語句無需任何權限 | 選擇權限 |
| **寫入資料** | INSERT和/或UPDATE權限（取決於寫操作） | 插入和更新權限 | 插入和更新或插入和更新任何表權限 | 插入和更新權限 | 插入和更新權限 | 插入和更新權限 |
| **將資料載入表格** | 在架構上建立階段，在目標表權限上選擇並插入 | 選擇和插入權限 | 選擇和插入權限 | 插入、管理批量操作和ALTER TABLE權限 | 選擇和插入權限 | 檔案權限 |
| **訪問客戶端資料** | 選擇「開啟（未來）」表或「查看」權限 | 選擇權限 | 選擇或選擇任何表權限 | 選擇權限 | 選擇權限 | 選擇權限 |
| **存取中繼資料** | 選擇INFORMATION_SCHEMA架構權限 | 選擇權限 | 使用DESCRIBE語句無需任何權限 | 檢視定義權限 | 使用「\d表」命令無需任何權限 | 選擇權限 |

|   | DB2 UDB | teradata | InfiniDB | sybase IQ/Sybase ASE | Netezza | AsterData |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **連接到遠程資料庫** | CONNECT授權 | CONNECT權限 | 建立與具有ALL PRIVILEGES的遠程主機綁定的用戶 | 無需權限即可使用CONNECT語句 | 無權限 | CONNECT權限 |
| **建立表格** | CREATETAB權限 | 建立表或表關鍵字 | 建立權限 | RESOURCE authority和CREATE權限 | 表權限 | 建立權限 |
| **建立索引** | 索引權限 | 建立索引或索引關鍵字 | 索引權限 | RESOURCE authority和CREATE權限 | 索引權限 | 建立權限 |
| **建立函式** | IMPLICIT_SCHEMA權限或CREATEIN權限 | 建立函式或函式關鍵字 | 建立常式權限 | Java函式的RESOURCE權限或DBA權限 | 函式權限 | 建立函式權限 |
| **建立程式** | IMPLICIT_SCHEMA權限或CREATEIN權限 | 建立過程或過程關鍵字 | 建立常式權限 | 資源授權 | 過程權限 | 建立函式權限 |
| **刪除對象（表、索引、函式、過程）** | DROPIN權限或CONTROL權限或擁有對象 | DROP &lt;對象>或對象相關關鍵字 | 刪除權限 | 擁有對象或DBA權限 | 刪除權限 | 擁有對象 |
| **監控執行** | 解釋權限 | 使用EXPLAIN語句無需任何權限 | 選擇權限 | 只有系統管理員可以執行sp_showplan | 使用EXPLAIN語句無需任何權限 | 使用EXPLAIN語句無需任何權限 |
| **寫入資料** | 插入和更新權限或DATAACCESS權限 | 插入和更新權限 | 插入和更新權限 | 插入和更新權限 | 插入和更新權限 | 插入和更新權限 |
| **將資料載入表格** | LOAD授權 | 選擇和插入權限，以分別使用COPY TO和COPY FROM語句 | 檔案權限 | 是表的所有者或ALTER權限。 根據 — gl選項，只有當用戶具有DBA權限時，才可能執行LOAD TABLE | 選擇和插入權限 | 選擇和插入權限 |
| **訪問客戶端資料** | 插入/更新權限或DATAACCESS權限 | 選擇權限 | 選擇權限 | 選擇權限 | 選擇權限 | 選擇權限 |
| **存取中繼資料** | 使用DESCRIBE語句無需授權 | 顯示權限 | 選擇權限 | 無需使用DESCRIBE語句的權限 | 使用「\d表」命令無需任何權限 | 使用SHOW命令無需任何權限 |
