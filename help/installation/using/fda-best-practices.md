---
product: campaign
title: Campaign FDA最佳作法和限制
description: 了解使用外部資料庫(FDA)時的最佳實務和限制
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 7%

---

# 最佳實務和限制



## 使用外部資料最佳化電子郵件個人化 {#optimizing-email-personalization-with-external-data}

您可以在專用的工作流程中預先處理訊息個人化。 若要執行此作業，請使用 **[!UICONTROL Prepare the personalization data with a workflow]** 選項，可在 **[!UICONTROL Analysis]** 標籤。

在傳遞分析期間，此選項會自動建立並執行工作流程，該工作流程會將連結到目標的所有資料儲存在臨時表中，包括來自連結到外部資料庫的表的資料。

此選項可大幅改善執行個人化步驟時的效能。

## 在工作流程中使用來自外部資料庫的資料 {#using-data-from-an-external-database-in-a-workflow}

在多個Adobe Campaign工作流程活動中，您可以使用儲存在外部資料庫中的資料。

* **篩選外部資料** - [查詢](../../workflow/using/targeting-data.md#selecting-data) 活動可讓您新增外部資料，並在定義的篩選設定中使用。 如需詳細資訊，請參閱[此頁面](../../workflow/using/targeting-data.md#selecting-data)。

* **建立子集** - [分割](../../workflow/using/split.md) 活動可讓您建立子集。 您可以使用外部資料來定義要使用的篩選條件。 如需詳細資訊，請參閱[此頁面](../../workflow/using/split.md)。

* **載入外部資料庫**  — 您可以在 [資料載入](../../workflow/using/data-loading--rdbms-.md) (RDBMS)活動。 在[本頁](../../workflow/using/data-loading--rdbms-.md)中瞭解更多。

* **新增資訊和連結** - [擴充](../../workflow/using/enrichment.md) 活動可讓您新增其他資料至工作流程的工作表，以及連結至外部表格。 在此內容中，它可使用外部資料庫的資料。 在[本頁](../../workflow/using/enrichment.md)中瞭解更多。

## FDA限制 {#limitations}

FDA選項是用來在工作流程中以批次模式處理外部資料庫中的資料。 為避免效能問題，不建議在單一操作的情境下使用FDA模組，例如：個人化、互動、即時訊息傳送等。

請盡量避免同時使用Adobe Campaign和外部資料庫的操作。 若要這麼做，您可以：

* 將Adobe Campaign資料庫匯出至外部資料庫，並在將結果重新匯入Adobe Campaign之前，僅從外部資料庫執行操作。

* 從外部Adobe Campaign資料庫收集資料，並在本機執行操作。

如果您想要使用外部資料庫的資料在傳送中進行個人化，請收集要在工作流程中使用的資料，以便在暫時表格中使用。 然後使用臨時表格中的資料來個人化您的傳送。

FDA選項受您所使用外部資料庫系統的限制。
