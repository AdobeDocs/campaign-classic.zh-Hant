---
title: 變更資料來源
description: 瞭解有關更改資料源活動的詳細資訊
feature: Workflows, Data Management, Federated Data Access
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---

# 變更資料來源 {#change-data-source}

>[!NOTE]
>
> 的 **[!UICONTROL Change data source]** 活動僅可用於 **[!UICONTROL Access to external data (Federated Data Access)]** 檔案。 有關Adobe Campaign Classic內置軟體包的詳細資訊，請參閱 [頁](../../installation/using/installing-campaign-standard-packages.md)。

的 **[!UICONTROL Change data source]** 活動允許您更改工作流的資料源 **[!UICONTROL Working table]**。 這為跨不同資料源（如FDA、FFDA和本地資料庫）管理資料提供了更大的靈活性。

的 **[!UICONTROL Working table]** 允許Adobe Campaign Classic工作流處理資料並與工作流活動共用資料。
預設情況下， **[!UICONTROL Working table]** 建立的資料庫與我們查詢的資料的源資料庫相同。

例如，查詢 **[!UICONTROL Profiles]** 表，儲存在雲資料庫上，您將建立 **[!UICONTROL Working table]** 在同一雲資料庫上。
要更改此項，可以添加 **[!UICONTROL Change Data Source]** 活動，為您的 **[!UICONTROL Working table]**。

請注意，當使用 **[!UICONTROL Change Data Source]** 活動，您需要切換回雲資料庫以繼續執行工作流。

使用 **[!UICONTROL Change Data Source]** 活動：

1. 建立工作流程.

1. 使用 **[!UICONTROL Query]** 的子菜單。

   有關 **[!UICONTROL Query]** 活動，請參閱 [頁](../../workflow/using/query.md#creating-a-query)。

1. 從 **[!UICONTROL Targeting]** 頁籤，添加 **[!UICONTROL Change data source]** 的子菜單。

   ![](assets/change-data-source.png)

1. 按兩下 **[!UICONTROL Change data source]** 活動，選擇 **[!UICONTROL Default data source]**。

   包含查詢結果的工作表隨後將移到預設的PostgreSQL資料庫。

   ![](assets/change-data-source_2.png)

1. 從 **[!UICONTROL Actions]** 頁籤，拖放 **[!UICONTROL JavaScript code]** 活動，以在工作表上執行單一操作。

   有關 **[!UICONTROL JavaScript code]** 活動，請參閱 [JavaScript代碼和高級JavaScript代碼](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) 的子菜單。

1. 添加其他 **[!UICONTROL Change data source]** 活動以切換回雲資料庫。

1. 按兩下活動並選擇 **[!UICONTROL Active FDA external account]** 然後 **[!UICONTROL External database]** 外部帳戶。

   ![](assets/change-data-source_3.png)

1. 現在可以啟動工作流。
