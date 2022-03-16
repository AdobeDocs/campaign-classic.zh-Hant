---
product: campaign
title: 聯合資料存取入門
description: 瞭解如何訪問和處理外部資料庫中的資料
feature: Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# 聯合資料存取入門 {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign提供 **聯合資料存取** (FDA)選項，用於處理儲存在一個或多個外部資料庫中的資訊：您可以訪問外部資料，而無需更改Adobe Campaign資料的結構。

## 必要條件 {#operating-principle}

FDA選項允許您在第三方資料庫中擴展資料模型。 它將自動檢測目標表的結構並使用SQL源中的資料。

為了使用此功能，以下列出了先決條件：

* **配置**:相容外部資料庫的清單取決於 [宿主模型](../../installation/using/hosting-models.md)。
* **外部資料庫版本**:您需要一個與Adobe CampaignFDA模組相容的外部資料庫。

   市場活動中詳細列出了每個托管模型的資料庫系統和相容版本 [相容性矩陣](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)。

* **權限**:用戶還必須 [必要權限](../../installation/using/remote-database-access-rights.md) 在Adobe Campaign和外部資料庫上。

