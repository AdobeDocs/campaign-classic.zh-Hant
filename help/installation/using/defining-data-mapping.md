---
product: campaign
title: 定義外部資料對應
description: 瞭解如何在外部資料庫中對應資料
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
exl-id: a7253ca7-47e5-4def-849d-3ce1c9b948fb
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '201'
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

   您可以選擇是否儲存排除專案(**excludelog**)，包含訊息(**broadlog**)或是在另一個表格中。

   您也可以選擇是否要管理此傳遞對應的追蹤(**trackinglog**)。

1. 然後選取要考慮的擴充功能。 擴充功能型別取決於平台的引數和選項（檢視您的授權合約）。

   ![](assets/wf_new_mapping_define_extensions.png)

   按一下 **[!UICONTROL Save]** 啟動傳遞對應建立的按鈕：所有連結的表格都會根據選取的引數自動建立。
