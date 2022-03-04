---
product: campaign
title: 收集資料以進行分析
description: 收集資料以進行分析
feature: Reporting
exl-id: cf621374-88f9-4def-8bea-87e0ea69ecd3
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 3%

---

# 收集資料以進行分析{#collecting-data-to-analyze}

![](../../assets/common.svg)

要用於生成報告的資料可以直接在報告頁中選擇(有關詳細資訊，請參閱 [使用上下文](../../reporting/using/using-the-context.md))或通過一個或多個查詢收集。

本練習提供了三種不同的方法：

1. 使用資料庫中的資料生成查詢。
1. 正在處理清單中包含的資料。
1. 使用現有多維資料集中包含的資料。

方法的選擇取決於計算類型、資料量及其耐久性等。 必須仔細檢查所有這些參數，以避免使Adobe Campaign資料庫超載，並優化建立的報告的生成和操作。 如需詳細資訊，請參閱[此頁面](../../reporting/using/best-practices.md#optimizing-report-creation)。

在所有情況下，通過 **[!UICONTROL Query]** 鍵入活動。

![](assets/reporting_query_edit.png)

當需要使用資料庫中的資料收集或構建報告中的資料時，此資料選擇模式相關。 在某些情況下，還可以從報告中使用的元素中直接選擇資料。 例如，在插入圖表時，可以直接選擇源資料。 有關此內容的詳細資訊，請參閱 [使用上下文](../../reporting/using/using-the-context.md)。

## 使用架構中的資料 {#using-the-data-from-a-schema}

要使用連結到資料庫架構的資料，請在查詢編輯器中選擇相應的選項，並配置要應用的查詢。

以下示例允許您收集資料庫中配置檔案中每個國家/地區的收件人數。 然後，它們可以以表格形式顯示在報告中。

![](assets/reporting_query_from_schema.png)

## 使用導入的清單 {#using-an-imported-list}

要建立報表，可以使用導入資料清單中的資料。

要執行此操作，請選擇 **[!UICONTROL Use an imported list]** 的子菜單。

![](assets/reporting_query_from_list.png)

按一下 **[!UICONTROL Edit query...]** 連結，用於定義要在此清單中的元素之間收集的資料，以便生成報告。

## 使用多維資料集 {#using-a-cube}

可以選擇用於定義查詢的多維資料集。

![](assets/reporting_query_from_cube.png)

立方使您能夠擴展資料庫的勘探和分析能力，同時使最終用戶更容易配置報告和表：只需選擇一個現有的完全配置的多維資料集，並使用其計算、度量和統計資訊。 有關建立立方的詳細資訊，請參閱 [此部分](../../reporting/using/about-cubes.md)。

按一下 **[!UICONTROL Edit query...]** 連結並選擇要在報表中顯示或使用的指示符。

![](assets/reporting_query_from_cube_edit_query.png)

## 篩選查詢中的選項 {#filtering-options-in-the-queries}

為避免對整個資料庫運行查詢，需要過濾資料。

### 簡化的過濾器 {#simplified-filter}

可以選擇 **[!UICONTROL Filter automatically with the context]** 選項，可通過樹的特定節點（如清單、收件人或傳遞）訪問報告。

的 **[!UICONTROL Filter with the folder]** 選項，您可以指定資料夾並僅考慮其內容。 這允許您篩選報告資料，以僅顯示樹中某個資料夾中的資料，如下所示：

![](assets/reporting_control_folder.png)

### 限制收集的資料量 {#limiting-the-amount-of-data-collected}

使用結果限制選項配置要通過查詢提取的記錄數：

* **[!UICONTROL Limit to first record]** 提取一個結果，
* **[!UICONTROL Size]** 提取一組記錄。
