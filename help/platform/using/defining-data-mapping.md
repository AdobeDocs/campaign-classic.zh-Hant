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


# 定義資料映射 {#defining-data-mapping}

Adobe Campaign可讓您定義外部表格中資料的對應。

為此，在建立外部表的模式後，您需要建立新的傳送映射以將此表中的資料用作傳送目標。

若要這麼做，請套用下列步驟：

1. 建立新的傳送對應並選擇您剛建立的定位維度，例如。

   ![](assets/wf_new_mapping_create_fda.png)

1. 指出儲存傳送資訊的欄位（姓氏、名字、電子郵件、地址等）。

   ![](assets/wf_new_mapping_define_join.png)

1. 指定資訊儲存的參數，包括擴充功能架構的字尾，以方便辨識。

   ![](assets/wf_new_mapping_define_names.png)

   您可以選擇是將排除(排除&#x200B;**日誌**)、消息(**broadlog**)或單獨的表中儲存。

   您也可以選擇是否管理此傳送對應的追蹤(**trackinglog**)。

1. 然後，選擇要考慮的擴展。 擴充功能類型視您平台的參數和選項而定（檢視您的授權合約）。

   ![](assets/wf_new_mapping_define_extensions.png)

   按一下按 **[!UICONTROL Save]** 鈕以啟動傳送對應建立：所有連結的表都會基於所選參數自動建立。
