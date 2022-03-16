---
product: campaign
title: 為FDA建立資料模式
description: 瞭解如何為FDA建立資料架構
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 2%

---

# 建立資料結構綱要 {#creating-the-data-schema}

![](../../assets/v7-only.svg)

要在外部資料庫上建立架構：

1. 按一下 **[!UICONTROL New]** 按鈕，然後選擇 **[!UICONTROL Access external data]**。

   ![](assets/wf_new_schema_fda.png)

1. 輸入 **[!UICONTROL Namespace]** 和  **[!UICONTROL Name]** 選擇 **[!UICONTROL External account]** 將啟用與資料庫的連接。 這允許訪問外部基中可用的表清單。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 從 **[!UICONTROL Table name]** 欄位中，選擇包含要收集的資料的表。

   使用Snowflake，如果已授予資料庫用戶正確的權限，則可以在此處選擇您的視圖。 請注意，在使用視圖時，Adobe Campaign將無法自動生成XML架構，您必須自己建立它。 有關視圖的詳細資訊，請參閱 [Snowflake文檔](https://docs.snowflake.com/en/user-guide/views-introduction.html)。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 按一下 **[!UICONTROL OK]** 確認。 Adobe Campaign自動檢測所選表的結構並生成邏輯架構。 請注意，Adobe Campaign未生成連結。

1. 按一下 **[!UICONTROL Save]** 確認建立。

   >[!CAUTION]
   >
   >對於Snowflake，主鍵是必需的。

   ![](assets/wf_new_schema_generate_fda.png)

在映射表（標準或FDA映射）時，會自動建立索引。
