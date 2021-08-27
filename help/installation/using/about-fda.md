---
product: campaign
title: 存取外部資料庫
description: 了解如何在外部資料庫中存取和處理資料
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 4%

---

# 開始使用同盟資料存取 {#about-federated-data-access}

![](../../assets/v7-only.svg)

Adobe Campaign提供&#x200B;**同盟資料存取**(FDA)選項，以處理儲存在一或多個外部資料庫中的資訊：您不需變更Adobe Campaign資料的結構，即可存取外部資料。

## 先決條件 {#operating-principle}

FDA選項可讓您擴充協力廠商資料庫中的資料模型。 它將自動檢測目標表的結構，並使用來自SQL源的資料。

若要使用此功能，下列為必要條件：

* **配置**:除了Snowflake外，您需要內 **部部署** 或混 **** 合托管模型來設定同盟資料存取。[深入瞭解](../../installation/using/hosting-models.md)
* **外部資料庫版本**:您需要有與Adobe Campaign FDA模組相容的外部資料庫。Campaign [相容性矩陣](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)中會詳細說明資料庫系統和相容版本清單。
* **權限**:使用者在Adobe Campaign和 [外](../../installation/using/remote-database-access-rights.md) 部資料庫中也必須擁有必要的權限。

