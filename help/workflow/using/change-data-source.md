---
title: 變更資料來源
description: 進一步瞭解變更資料來源活動
feature: Workflows, Data Management, Federated Data Access
exl-id: d7bf9d62-6f9e-415f-8160-446210f6392e
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 2%

---

# 變更資料來源 {#change-data-source}

>[!NOTE]
>
> **[!UICONTROL Change data source]**&#x200B;活動只能與&#x200B;**[!UICONTROL Access to external data (Federated Data Access)]**&#x200B;封裝一起使用。 如需Adobe Campaign Classic內建套件的詳細資訊，請參閱此[頁面](../../installation/using/installing-campaign-standard-packages.md)。

**[!UICONTROL Change data source]**&#x200B;活動可讓您變更工作流程&#x200B;**[!UICONTROL Working table]**&#x200B;的資料來源。 這為管理不同資料來源（例如FDA、FFDA和本機資料庫）的資料提供更大的彈性。

**[!UICONTROL Working table]**可讓Adobe Campaign Classic工作流程處理資料，並與工作流程活動共用資料。
根據預設，**[!UICONTROL Working table]**&#x200B;會與我們查詢的資料來源建立在同一資料庫中。

例如，當查詢儲存在雲端資料庫上的&#x200B;**[!UICONTROL Profiles]**&#x200B;資料表時，您將在相同的雲端資料庫上建立&#x200B;**[!UICONTROL Working table]**。
若要變更此專案，您可以新增**[!UICONTROL Change Data Source]**&#x200B;活動，為您的&#x200B;**[!UICONTROL Working table]**&#x200B;選擇不同的資料來源。

請注意，使用&#x200B;**[!UICONTROL Change Data Source]**&#x200B;活動時，您必須切換回雲端資料庫才能繼續執行工作流程。

若要使用&#x200B;**[!UICONTROL Change Data Source]**&#x200B;活動：

1. 建立工作流程。

1. 查詢具有&#x200B;**[!UICONTROL Query]**&#x200B;活動的目標收件者。

   如需&#x200B;**[!UICONTROL Query]**&#x200B;活動的詳細資訊，請參閱此[頁面](../../workflow/using/query.md#creating-a-query)。

1. 從&#x200B;**[!UICONTROL Targeting]**&#x200B;索引標籤，新增&#x200B;**[!UICONTROL Change data source]**&#x200B;活動。

   ![](assets/change-data-source.png)

1. 連按兩下您的&#x200B;**[!UICONTROL Change data source]**&#x200B;活動以選取&#x200B;**[!UICONTROL Default data source]**。

   然後會將包含查詢結果的工作表移至預設PostgreSQL資料庫。

   ![](assets/change-data-source_2.png)

1. 從&#x200B;**[!UICONTROL Actions]**&#x200B;索引標籤，拖放&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動以在工作表格上執行單一作業。

   如需&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動的詳細資訊，請參閱[JavaScript程式碼和進階JavaScript程式碼](../../workflow/using/sql-code-and-javascript-code.md#javascript-code)頁面。

1. 新增其他&#x200B;**[!UICONTROL Change data source]**&#x200B;活動以切換回雲端資料庫。

1. 連按兩下您的活動並選取&#x200B;**[!UICONTROL Active FDA external account]**，然後選取對應的&#x200B;**[!UICONTROL External database]**&#x200B;外部帳戶。

   ![](assets/change-data-source_3.png)

1. 您現在可以開始工作流程。
