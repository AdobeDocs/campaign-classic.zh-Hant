---
solution: Campaign Classic
product: campaign
title: Campaign FDA最佳實務與限制
description: 瞭解使用外部資料庫(FDA)時的最佳實務和限制
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 0a92ebd6c9400f8caf43da8f633c7755a3fb77ce
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 4%

---


# 最佳實務和限制

## 建立臨時方案{#create-temporary-schemas}

您可以透過FDA管理對Greenplum外部資料庫的數次存取。 專用選項可讓您在設定外部帳戶時直接建立工作架構。

![](assets/fda_work_table.png)

>[!NOTE]
>
>此選項僅適用於PostgreSQL Greenplum。

## 使用外部資料{#optimizing-email-personalization-with-external-data}最佳化電子郵件個人化

您可以在專屬的工作流程中預先處理訊息個人化。 若要執行此動作，請使用傳送屬性的&#x200B;**[!UICONTROL Analysis]**&#x200B;標籤中提供的&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;選項。

在傳送分析期間，此選項會自動建立並執行將所有連結至目標的資料儲存在暫存表格中的工作流程，包括來自外部資料庫中連結之表格的資料。

此選項可大幅改善執行個人化步驟時的效能。

## 在工作流{#using-data-from-an-external-database-in-a-workflow}中使用外部資料庫的資料

在多個Adobe Campaign工作流活動中，您可以使用儲存在外部資料庫中的資料。

* **篩選外部資料** - 「查詢」 [](../../workflow/using/targeting-data.md#selecting-data) 活動可讓您新增外部資料，並在定義的篩選設定中使用。有關詳細資訊，請參見[此頁面](../../workflow/using/targeting-data.md#selecting-data)。

* **建立子集** - 「拆 [](../../workflow/using/split.md) 分」活動允許您建立子集。您可以使用外部資料來定義要使用的篩選條件。 有關詳細資訊，請參見[此頁面](../../workflow/using/split.md)。

* **載入外部資料庫** -可以在「資料載入 [(RDBMS)」活動中](../../workflow/using/data-loading--rdbms-.md) 使用外部資料。進一步瞭解[本頁](../../workflow/using/data-loading--rdbms-.md)。

* **添加資訊和連結** -  [](../../workflow/using/enrichment.md) Enrichmentactivity允許您向工作流的工作台添加其他資料，以及向外部表的連結。在此上下文中，它可以使用外部資料庫的資料。 進一步瞭解[本頁](../../workflow/using/enrichment.md)。

## FDA限制{#limitations}

FDA選項是用來在工作流程中以批次模式控制外部資料庫中的資料。 為避免效能問題，不建議在單一作業中使用FDA模組，例如：個人化、互動、即時訊息等。

請盡量避免需要同時使用Adobe Campaign和外部資料庫的操作。 若要這麼做，您可以：

* 將Adobe Campaign資料庫導出到外部資料庫，並僅從外部資料庫執行操作，然後再將結果重新導入Adobe Campaign。

* 從外部Adobe Campaign資料庫收集資料並在本地執行操作。

如果您想要使用外部資料庫的資料在傳送中進行個人化，請收集要在工作流程中使用的資料，以便在臨時表格中使用。 然後使用臨時表格中的資料來個人化您的傳送。

FDA選項受您使用的外部資料庫系統的限制。

