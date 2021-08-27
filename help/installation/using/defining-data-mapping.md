---
product: campaign
title: 存取外部資料庫
description: 存取外部資料庫
audience: platform
content-type: reference
topic-tags: connectors
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 9%

---

# 定義資料對應 {#defining-data-mapping}

![](../../assets/v7-only.svg)

Adobe Campaign可讓您定義外部表格中資料的對應。

要執行此操作，建立外部表的架構後，您需要建立新的傳送對應，以將此表中的資料用作傳送目標。

若要這麼做，請套用下列步驟：

1. 建立新的傳送對應並選擇目標維度，例如您剛建立的結構。

   ![](assets/wf_new_mapping_create_fda.png)

1. 指定儲存傳送資訊的欄位（姓氏、名字、電子郵件、地址等）。

   ![](assets/wf_new_mapping_define_join.png)

1. 指定資訊儲存的參數，包括擴充功能結構的尾碼，以便輕鬆識別。

   ![](assets/wf_new_mapping_define_names.png)

   您可以選擇是儲存包含訊息(**broadlog**)的排除項目(**excludelog**)，還是儲存在個別表格中。

   您也可以選擇是否管理此傳送對應的追蹤(**trackinglog**)。

1. 然後選取要考慮的擴充功能。 擴充功能類型取決於您平台的參數和選項（檢視您的授權合約）。

   ![](assets/wf_new_mapping_define_extensions.png)

   按一下&#x200B;**[!UICONTROL Save]**&#x200B;按鈕以啟動傳送對應建立：所有連結表都會根據所選參數自動建立。
