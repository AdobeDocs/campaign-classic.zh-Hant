---
product: campaign
title: Campaign FDA最佳作法和限制
description: 瞭解使用外部資料庫(FDA)時的最佳實務和限制
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 7%

---

# 最佳實務和限制



## 使用外部資料最佳化電子郵件個人化 {#optimizing-email-personalization-with-external-data}

您可以在專屬的工作流程中預先處理訊息個人化。 若要執行此動作，請使用傳遞屬性的&#x200B;**[!UICONTROL Analysis]**&#x200B;索引標籤中的&#x200B;**[!UICONTROL Prepare the personalization data with a workflow]**&#x200B;選項。

在傳遞分析期間，此選項會自動建立並執行工作流程，將所有連結至目標的資料儲存在暫存表格中，包括連結至外部資料庫之表格的資料。

此選項可大幅改善執行個人化步驟時的效能。

## 在工作流程中使用來自外部資料庫的資料 {#using-data-from-an-external-database-in-a-workflow}

在多個Adobe Campaign工作流程活動中，您可以使用儲存在外部資料庫中的資料。

* **篩選外部資料** - [查詢](../../workflow/using/targeting-data.md#selecting-data)活動可讓您新增外部資料，並將其用於定義的篩選設定。 如需詳細資訊，請參閱[此頁面](../../workflow/using/targeting-data.md#selecting-data)。

* **建立子集** - [分割](../../workflow/using/split.md)活動可讓您建立子集。 您可以使用外部資料來定義要使用的篩選條件。 如需詳細資訊，請參閱[此頁面](../../workflow/using/split.md)。

* **載入外部資料庫** — 您可以在[資料載入](../../workflow/using/data-loading-rdbms.md) (RDBMS)活動中使用外部資料。 在[本頁](../../workflow/using/data-loading-rdbms.md)中瞭解更多。

* **新增資訊和連結** - [擴充](../../workflow/using/enrichment.md)活動可讓您新增其他資料至工作流程的工作表，以及外部表格的連結。 在這種情況下，它可以使用來自外部資料庫的資料。 在[本頁](../../workflow/using/enrichment.md)中瞭解更多。

## 護欄和限制 {#fda-limitations}

FDA選項的設計目的，是為了在工作流程中以批次模式操控外部資料庫中的資料。 為了避免效能問題，不建議在單一操作的內容中使用FDA模組，例如：個人化、互動、即時傳訊等。

不支援從某個資料庫定位資料，並使用屬於另一個資料庫的篩選維度來篩選結果。 您無法在一個查詢中聯結位於不同資料來源的表格。 您可以使用其他工作流程活動（例如變更維度）來克服此限制。

儘可能避免需要使用Adobe Campaign和外部資料庫的操作。 最佳實務是：

* 將Adobe Campaign資料庫匯出至外部資料庫，並僅從外部資料庫執行操作，然後再將結果重新匯入Adobe Campaign。

* 從外部Adobe Campaign資料庫收集資料，並在本機執行操作。

如果您想使用外部資料庫中的資料在傳遞中執行個人化，請收集要在工作流程中使用的資料，以便在臨時表格中提供。 然後，使用臨時表格中的資料來個人化您的傳遞。

FDA選項受您使用的外部資料庫系統限制。
