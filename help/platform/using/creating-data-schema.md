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
source-git-commit: 9a26ec7ed1c8463270ac9f97079f49e00d5b258e

---


# 建立資料架構 {#creating-the-data-schema}

要在外部資料庫上建立模式：

1. 按一下數 **[!UICONTROL New]** 據結構表上方的按鈕並選擇 **[!UICONTROL Access external data]**。

   ![](assets/wf_new_schema_fda.png)

1. 輸入方案的名稱和說明，然後選擇將啟用與資料庫連接的外部帳戶。 這允許訪問外部基礎中可用的表清單。 選擇包含要收集之資料的表格。

   ![](assets/wf_new_schema_select_table_fda.png)

1. Click **[!UICONTROL OK]** to confirm. Adobe Campaign會自動偵測選取表格的結構並產生邏輯架構。 請注意，Adobe Campaign不會產生連結。

1. 按一 **[!UICONTROL Save]** 下以確認建立。

   >[!CAUTION]
   >
   >有了雪花，主鍵是必備的。

   ![](assets/wf_new_schema_generate_fda.png)

在映射表（標準或FDA映射）時，會自動建立索引。
