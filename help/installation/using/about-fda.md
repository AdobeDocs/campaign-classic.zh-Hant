---
solution: Campaign Classic
product: campaign
title: 存取外部資料庫
description: 瞭解如何存取和處理外部資料庫中的資料
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
translation-type: tm+mt
source-git-commit: 37802e52f1d1d38d9c3d59c439f23114a594bfef
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# 開始使用同盟資料存取{#about-federated-data-access}

Adobe Campaign提供&#x200B;**Federated Data Access**(FDA)選項，以處理儲存在一個或多個外部資料庫中的資訊：您可以存取外部資料，而不需變更Adobe Campaign資料的結構。

## 必要條件 {#operating-principle}

FDA選項可讓您在協力廠商資料庫中擴充資料模型。 它將自動檢測目標表的結構並使用SQL源中的資料。

若要使用此功能，下列為必要條件：

* **配置**:除Snowflake外，您需要一個 **內部** 或混 **** 合托管模型來設定Federated Data Access。[了解更多](../../installation/using/hosting-models.md)
* **外部資料庫版本**:您需要一個與Adobe Campaign食品藥品管理局模組相容的外部資料庫。資料庫系統和相容版本的清單詳見Campaign [相容性矩陣](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)。
* **權限**:用戶還必須擁有 [Adobe Campaign](../../installation/using/remote-database-access-rights.md) 和外部資料庫的必要權限。

