---
product: campaign
title: 開始使用同盟資料存取
description: 瞭解如何存取及處理外部資料庫中的資料
feature: Installation, Federated Data Access
exl-id: 9d8d1e9c-63e4-40c4-8338-b921d08ea405
TQID: 'https://experienceleague.adobe.com/X-VyiKlGatskoXtPoLYhb8HrAgCRLLHxTbwXDFmg8jI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: ee3dfd63-9a21-4961-9f24-ea3385284a21
    internal-label: Federated Data Access
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%
---
# 開始使用同盟資料存取 {#about-federated-data-access}



Adobe Campaign提供&#x200B;**同盟資料存取** (FDA)選項，以處理儲存在一或多個外部資料庫中的資訊：您不需要變更Adobe Campaign資料的結構就可以存取外部資料。

## 先決條件 {#operating-principle}

FDA選項可讓您在協力廠商資料庫中擴充資料模型。 它會自動偵測目標表格的結構，並使用來自SQL來源的資料。

為了使用此功能，先決條件列示如下：

* **組態**：相容的外部資料庫清單取決於您的[託管模型](../../installation/using/hosting-models.md)。
* **外部資料庫版本**：您必須有與Adobe Campaign FDA模組相容的外部資料庫。

  Campaign [相容性矩陣](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)中詳細列出每個託管模型的資料庫系統和相容版本。

* **許可權**：使用者也必須擁有Adobe Campaign和外部資料庫中的[必要許可權](../../installation/using/remote-database-access-rights.md)。

