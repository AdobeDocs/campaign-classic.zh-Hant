---
title: 變更資料來源
description: 深入瞭解變更資料來源活動
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
> 此 **[!UICONTROL Change data source]** 活動僅適用於 **[!UICONTROL Access to external data (Federated Data Access)]** 封裝。 如需Adobe Campaign Classic內建套件的詳細資訊，請參閱此 [頁面](../../installation/using/installing-campaign-standard-packages.md).

此 **[!UICONTROL Change data source]** 活動可讓您變更工作流程的資料來源 **[!UICONTROL Working table]**. 這為管理不同資料來源（例如FDA、FFDA和本機資料庫）的資料提供更大的彈性。

此 **[!UICONTROL Working table]** 允許Adobe Campaign Classic工作流程處理資料並與工作流程活動共用資料。
根據預設， **[!UICONTROL Working table]** 在與我們查詢的資料來源相同的資料庫中建立。

例如，查詢 **[!UICONTROL Profiles]** 表格，儲存在雲端資料庫中，您將建立 **[!UICONTROL Working table]** 在相同雲端資料庫上。
若要變更此設定，您可以新增 **[!UICONTROL Change Data Source]** 活動，為您的選擇不同的資料來源 **[!UICONTROL Working table]**.

請注意，使用時 **[!UICONTROL Change Data Source]** 活動，您必須切換回雲端資料庫才能繼續執行工作流程。

若要使用 **[!UICONTROL Change Data Source]** 活動：

1. 建立工作流程.

1. 使用查詢目標收件者 **[!UICONTROL Query]** 活動。

   如需詳細資訊，請參閱 **[!UICONTROL Query]** 活動，請參閱此 [頁面](../../workflow/using/query.md#creating-a-query).

1. 從 **[!UICONTROL Targeting]** 索引標籤，新增 **[!UICONTROL Change data source]** 活動。

   ![](assets/change-data-source.png)

1. 連按兩下 **[!UICONTROL Change data source]** 要選取的活動 **[!UICONTROL Default data source]**.

   然後會將包含查詢結果的工作表格移至預設的PostgreSQL資料庫。

   ![](assets/change-data-source_2.png)

1. 從 **[!UICONTROL Actions]** 標籤，拖放 **[!UICONTROL JavaScript code]** 對工作表格執行單一作業的活動。

   如需詳細資訊，請參閱 **[!UICONTROL JavaScript code]** 活動，請參閱 [JavaScript程式碼和進階JavaScript程式碼](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) 頁面。

1. 新增另一個 **[!UICONTROL Change data source]** 活動以切換回雲端資料庫。

1. 連按兩下您的活動並選取 **[!UICONTROL Active FDA external account]** 然後對應於 **[!UICONTROL External database]** 外部帳戶。

   ![](assets/change-data-source_3.png)

1. 您現在可以開始工作流程。
