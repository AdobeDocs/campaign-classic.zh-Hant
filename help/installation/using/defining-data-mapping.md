---
product: campaign
title: 定義外部資料對應
description: 瞭解如何在外部資料庫中對應資料
feature: Installation, Instance Settings
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
TQID: https://experienceleague.adobe.com/9mE5BjrDg-E4FDyFFL0GVAVPof0rlSSOlzyj2zk21ag
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 3%

---

# 定義外部資料對應 {#defining-data-mapping}



Adobe Campaign可讓您定義外部表格中資料的對應。

若要這麼做，在建立外部表格的綱要後，您需要建立新的傳送對應，以使用此表格中的資料作為傳送目標。

若要這麼做，請套用下列步驟：

1. 建立新的傳送對應，並選擇目標維度，例如您剛才建立的結構描述。

   ![](assets/wf_new_mapping_create_fda.png)

1. 表示儲存傳遞資訊的欄位（姓氏、名字、電子郵件、地址等）。

   ![](assets/wf_new_mapping_define_join.png)

1. 指定資訊儲存的引數，包括擴充功能結構的尾碼，以便輕鬆識別。

   ![](assets/wf_new_mapping_define_names.png)

   您可以選擇是否要儲存排除專案(**excludelog**)、包含訊息(**broadlog**)或是在個別的資料表中。

   您也可以選擇是否要管理此傳遞對應(**trackinglog**)的追蹤。

1. 然後選取要考慮的擴充功能。 擴充功能型別取決於平台的引數和選項（檢視您的授權合約）。

   ![](assets/wf_new_mapping_define_extensions.png)

   按一下&#x200B;**[!UICONTROL Save]**&#x200B;按鈕以啟動傳遞對應建立：所有連結表格都會根據選取的引數自動建立。
