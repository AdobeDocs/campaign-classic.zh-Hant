---
solution: Campaign Classic
product: campaign
title: 建立指標
description: 建立指標
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 1%

---


# 建立指標{#creating-indicators}

要使立方功能化，您需要標識相關維和度量並在立方中建立它們。

要建立立方，請應用以下步驟：

1. 選擇工作表。 請參閱[選擇工作表](#selecting-the-work-table)。
1. 定義尺寸。 請參閱[定義維](#defining-dimensions)。
1. 定義測量。 請參閱[建築指示燈](#building-indicators)。
1. 建立匯整（選用）。 請參閱[計算和使用聚合](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates)。

此範例說明如何快速在報表中建立簡單立方，以匯出其度量。

實施步驟詳述如下。 本章的其他章節提供完整的選項和說明。

## 選擇工作表{#selecting-the-work-table}

要建立立方，請按一下立方清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕。

![](assets/s_advuser_cube_create.png)

選擇數值模式，即包含要瀏覽的元素的模式。 在此示例中，我們將選擇&#x200B;**Recipient**&#x200B;表。

![](assets/s_advuser_cube_wz_02.png)

按一下&#x200B;**[!UICONTROL Save]**&#x200B;建立立方：它將出現在立方的清單中，然後可以使用相應的頁籤進行配置。

按一下&#x200B;**[!UICONTROL Filter the source data...]**&#x200B;連結，將此多維資料集的計算應用到資料庫中的選定資料。

![](assets/s_advuser_cube_wz_03.png)

## 定義維{#defining-dimensions}

Dimension與為每個立方定義的分析軸基於它們的相關事實模式一致。 這些是分析中探索的維度，例如時間（年、月、日……）、產品或合約的分類（家庭、參考等）、人口區段（依城市、年齡組、狀態等）。

這些分析軸在立方的&#x200B;**[!UICONTROL Dimension]**&#x200B;頁籤中定義。

按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以建立新維，然後在&#x200B;**[!UICONTROL Expression field]**&#x200B;中按一下&#x200B;**[!UICONTROL Edit expression]**&#x200B;表徵圖以選擇包含有關資料的欄位。

![](assets/s_advuser_cube_wz_04.png)

* 首先，選擇收件人&#x200B;**年齡**。 對於此欄位，您可以定義系結至群組年齡，讓資訊閱讀更輕鬆。 我們建議在可能有數個個別值時使用二進位。

   若要這麼做，請勾選&#x200B;**[!UICONTROL Enable binning]**&#x200B;選項。 綁定模式在[資料綁定](../../reporting/using/concepts-and-methodology.md#data-binning)中有詳細說明。

   ![](assets/s_advuser_cube_wz_05.png)

* 添加&#x200B;**Date**&#x200B;類型維。 在這裡，我們要顯示收件者描述檔建立日期

   要執行此操作，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選擇收件人表中的&#x200B;**[!UICONTROL Creation date]**&#x200B;欄位。

   ![](assets/s_advuser_cube_wz_06.png)

   您可以選擇日期顯示模式。 若要這麼做，請選取要使用的階層和要產生的層級：

   ![](assets/s_advuser_cube_wz_07.png)

   在我們的範例中，我們只想顯示年份、月份和日期，因為無法同時使用周和學期／月：這些級別不相容。

* 建立另一個維度以分析與收件者所在城市相關的資料

   要執行此操作，請添加新維，並在收件方案的&#x200B;**[!UICONTROL Location]**&#x200B;節點中選擇城市。

   ![](assets/s_advuser_cube_wz_08.png)

   您可以啟用綁定功能，讓資訊讀取更輕鬆，並將值連結至列舉。

   ![](assets/s_advuser_cube_wz_09.png)

   從下拉清單中選擇枚舉

   ![](assets/s_advuser_cube_wz_10.png)

   將只顯示枚舉中的值。 其他項目則會分組在&#x200B;**[!UICONTROL Label of the other values]**&#x200B;欄位中定義的標籤下。

   有關詳細資訊，請參閱[動態管理bins](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins)。

## 建立指標{#building-indicators}

定義維後，您需要為要顯示在單元格中的值指定計算模式。 若要這麼做，請在&#x200B;**[!UICONTROL Measures]**&#x200B;標籤中建立符合的指標：建立將使用立方的報表中顯示的任意多個度量。

若要這麼做，請套用下列步驟：

1. 按一下 **[!UICONTROL Add]** 按鈕。
1. 選擇要應用的度量類型和公式。 在這裡，我們想統計一下接受治療的婦女人數。

   我們的度量基於事實模式，使用&#x200B;**[!UICONTROL Count]**&#x200B;運算子。

   ![](assets/s_advuser_cube_wz_11.png)

   **[!UICONTROL Filter the measure data...]**&#x200B;連結可讓您僅選擇女性。 有關定義度量和可用選項的詳細資訊，請參閱[定義度量](../../reporting/using/concepts-and-methodology.md#defining-measures)。

   ![](assets/s_advuser_cube_wz_12.png)

1. 輸入度量的標籤並保存它。

   ![](assets/s_advuser_cube_wz_13.png)

1. 保存立方。

## 基於立方{#creating-a-report-based-on-a-cube}建立報告

配置立方後，它可用作建立新報告的模板。

操作步驟：

1. 按一下&#x200B;**[!UICONTROL Reports]**&#x200B;頁籤的&#x200B;**[!UICONTROL Create]**&#x200B;按鈕，然後選擇剛建立的立方。

   ![](assets/s_advuser_cube_wz_14.png)

1. 按一下&#x200B;**[!UICONTROL Create]**&#x200B;按鈕確認：這會帶您進入報表設定和檢視頁面。

   依預設，前兩個可用維度會以行和欄提供，但表格中不會顯示任何值。 要生成表，請按一下主表徵圖：

   ![](assets/s_advuser_cube_wz_15.png)

1. 可以切換尺寸軸、刪除它們、添加新測量等。 可能的操作詳細如下：[使用立方體來探索資料](../../reporting/using/using-cubes-to-explore-data.md)。

   若要這麼做，請使用適當的圖示。

   ![](assets/s_advuser_cube_wz_16.png)

