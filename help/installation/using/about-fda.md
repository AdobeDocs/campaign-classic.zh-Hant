---
product: campaign
title: 開始使用同盟資料存取
description: 瞭解如何存取及處理外部資料庫中的資料
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 1%

---

# 開始使用同盟資料存取 {#about-federated-data-access}



Adobe Campaign提供 **同盟資料存取** (FDA)選項，以處理儲存在一或多個外部資料庫中的資訊：您不需要變更Adobe Campaign資料的結構即可存取外部資料。

## 必要條件 {#operating-principle}

FDA選項可讓您在協力廠商資料庫中擴充資料模型。 它會自動偵測目標表格的結構，並使用來自SQL來源的資料。

為了使用此功能，先決條件列示如下：

* **設定**：相容的外部資料庫清單取決於 [託管模型](../../installation/using/hosting-models.md).
* **外部資料庫版本**：您需要有與Adobe Campaign FDA模組相容的外部資料庫。

  Campaign中會詳細說明每個託管模型的資料庫系統和相容版本清單 [相容性矩陣](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

* **許可權**：使用者也必須擁有 [必要許可權](../../installation/using/remote-database-access-rights.md) 在Adobe Campaign和外部資料庫中。

