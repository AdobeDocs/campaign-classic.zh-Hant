---
title: 變更資料來源
description: 深入了解變更資料來源活動
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: 31483bdd2e0a2dd0676ef391c5484e4b778317c1
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---

# 變更資料來源 {#change-data-source}

>[!NOTE]
>
> 此 **[!UICONTROL Change data source]** 活動僅可搭配使用 **[!UICONTROL Access to external data (Federated Data Access)]** 包。 如需Adobe Campaign Classic內建套件的詳細資訊，請參閱 [頁面](../../installation/using/installing-campaign-standard-packages.md).

此 **[!UICONTROL Change data source]** 活動可讓您變更工作流程的資料來源 **[!UICONTROL Working table]**. 這可提供更大的彈性，可管理不同資料來源的資料，例如FDA、FFDA和本機資料庫。

此 **[!UICONTROL Working table]** 可讓Adobe Campaign Classic工作流程處理資料，並與工作流程活動共用資料。
依預設， **[!UICONTROL Working table]** 會在與我們查詢之資料來源相同的資料庫中建立。

例如，查詢 **[!UICONTROL Profiles]** 表，儲存在雲端資料庫上，您將建立 **[!UICONTROL Working table]** 在同一個雲端資料庫上。
若要變更此項目，您可以新增 **[!UICONTROL Change Data Source]** 為您的 **[!UICONTROL Working table]**.

請注意，使用 **[!UICONTROL Change Data Source]** 活動中，您需要切換回雲端資料庫以繼續執行工作流程。

若要使用 **[!UICONTROL Change Data Source]** 活動：

1. 建立工作流程.

1. 使用 **[!UICONTROL Query]** 活動。

   如需 **[!UICONTROL Query]** 活動，請參閱 [頁面](../../workflow/using/query.md#creating-a-query).

1. 從 **[!UICONTROL Targeting]** 標籤，新增 **[!UICONTROL Change data source]** 活動。

   ![](assets/change-data-source.png)

1. 按兩下您的 **[!UICONTROL Change data source]** 選擇活動 **[!UICONTROL Default data source]**.

   然後，將包含查詢結果的工作表移至預設的PostgreSQL資料庫。

   ![](assets/change-data-source_2.png)

1. 從 **[!UICONTROL Actions]** 標籤，拖放 **[!UICONTROL JavaScript code]** 在工作表上執行統一操作的活動。

   如需 **[!UICONTROL JavaScript code]** 活動，請參閱 [JavaScript程式碼和進階JavaScript程式碼](../../workflow/using/sql-code-and-javascript-code.md#javascript-code) 頁面。

1. 添加其他 **[!UICONTROL Change data source]** 切換回雲端資料庫的活動。

1. 連按兩下您的活動並選取 **[!UICONTROL Active FDA external account]** 然後 **[!UICONTROL External database]** 外部帳戶。

   ![](assets/change-data-source_3.png)

1. 您現在可以開始工作流程。
