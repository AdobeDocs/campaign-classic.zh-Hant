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
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# 遠程資料庫訪問權限 {#remote-database-access-rights}

首先，為了讓使用者可以透過FDA對外部資料庫執行作業，後者必須在Adobe Campaign中擁有特定的指名權。

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

>[!NOTE]
>
>資料庫管理員需要使這些權限與每個資料庫引擎的特定權限相匹配。 有關詳細資訊，請參閱 [RDBMS特定權限](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html)。