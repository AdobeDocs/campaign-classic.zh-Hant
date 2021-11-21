---
product: campaign
title: 建立指標
description: 建立指標
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
exl-id: e4806bb8-de9d-47e4-8b37-d6c0565b7f5a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 2%

---

# 建立指標{#creating-indicators}

![](../../assets/common.svg)

要使多維資料集功能化，您需要標識相關維和度量並在多維資料集中建立它們。

要建立多維資料集，請應用以下步驟：

1. 選擇工作表。 請參閱 [選擇工作表](#selecting-the-work-table).
1. 定義維度。 請參閱 [定義維度](#defining-dimensions).
1. 定義測量。 請參閱 [建設指標](#building-indicators).
1. 建立匯總（選用）。 請參閱 [計算和使用匯總](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

此示例說明如何快速建立報表中的簡單多維資料集以導出其測量。

實作步驟於下文詳細說明。 本章其他章節提供詳盡的選項和說明。

## 選擇工作表 {#selecting-the-work-table}

要建立多維資料集，請按一下 **[!UICONTROL New]** 按鈕。

![](assets/s_advuser_cube_create.png)

選取事實架構，即包含您要探索之元素的架構。 在此範例中，我們將選取 **收件者** 表格。

![](assets/s_advuser_cube_wz_02.png)

按一下 **[!UICONTROL Save]** 要建立多維資料集：它將出現在多維資料集清單中，然後可以使用相應頁簽進行配置。

按一下 **[!UICONTROL Filter the source data...]** 連結，將此多維資料集的計算應用到資料庫中的資料選擇。

![](assets/s_advuser_cube_wz_03.png)

## 定義維度 {#defining-dimensions}

Dimension與根據每個多維資料集的相關數值模式為每個多維資料集定義的分析軸一致。 這些是分析中探討的維度，例如時間（年、月、日……）、產品或合同的分類（家庭、參考等）、人口區段（依城市、年齡組、狀態等）。

這些分析軸定義於 **[!UICONTROL Dimension]** 多維資料集的頁簽。

按一下 **[!UICONTROL Add]** 按鈕建立新維，然後 **[!UICONTROL Expression field]**，按一下 **[!UICONTROL Edit expression]** 表徵圖，選擇包含相關資料的欄位。

![](assets/s_advuser_cube_wz_04.png)

* 從選取收件者開始 **年齡**. 對於此欄位，您可以定義組合年齡，並讓資訊閱讀更輕鬆。 建議您在可能有數個個別值時使用捆綁。

   若要這麼做，請檢查 **[!UICONTROL Enable binning]** 選項。 在 [資料綁定](../../reporting/using/concepts-and-methodology.md#data-binning).

   ![](assets/s_advuser_cube_wz_05.png)

* 新增 **日期** 類型維度。 在此處，我們要顯示收件者設定檔建立日期

   要執行此操作，請按一下 **[!UICONTROL Add]** ，然後選取 **[!UICONTROL Creation date]** 欄位。

   ![](assets/s_advuser_cube_wz_06.png)

   可以選取日期顯示模式。 要執行此操作，請選取要使用的階層以及要產生的層級：

   ![](assets/s_advuser_cube_wz_07.png)

   在我們的範例中，我們只想顯示年、月和日，因為無法同時使用周和月/月：這些級別不相容。

* 建立另一個維度以分析與收件者城市相關的資料

   若要這麼做，請新增維度並選取 **[!UICONTROL Location]** 收件者架構的節點。

   ![](assets/s_advuser_cube_wz_08.png)

   您可以啟用捆綁，讓資訊讀取更輕鬆，並將值連結至列舉。

   ![](assets/s_advuser_cube_wz_09.png)

   從下拉式清單中選取分項清單

   ![](assets/s_advuser_cube_wz_10.png)

   只會顯示分項清單中的值。 其他項目則會分組在 **[!UICONTROL Label of the other values]** 欄位。

   有關詳細資訊，請參閱 [動態管理Bin](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins).

## 建設指標 {#building-indicators}

定義維度後，您必須為要在儲存格中顯示的值指定計算模式。 若要這麼做，請在 **[!UICONTROL Measures]** 標籤：建立將使用多維資料集的報告中要顯示的列數。

若要這麼做，請套用下列步驟：

1. 按一下 **[!UICONTROL Add]** 按鈕。
1. 選擇要應用的度量類型和公式。 在此，我們要統計受助者中的婦女人數。

   我們的測量以事實架構為基礎，並使用 **[!UICONTROL Count]** 運算元。

   ![](assets/s_advuser_cube_wz_11.png)

   此 **[!UICONTROL Filter the measure data...]** 連結僅可讓您選取女性。 有關定義度量和可用選項的詳細資訊，請參閱 [定義度量](../../reporting/using/concepts-and-methodology.md#defining-measures).

   ![](assets/s_advuser_cube_wz_12.png)

1. 輸入度量的標籤並保存它。

   ![](assets/s_advuser_cube_wz_13.png)

1. 保存多維資料集。

## 根據多維資料集建立報表 {#creating-a-report-based-on-a-cube}

配置多維資料集後，可將其用作建立新報告的模板。

操作步驟：

1. 按一下 **[!UICONTROL Create]** 按鈕 **[!UICONTROL Reports]** 頁簽，然後選擇剛建立的多維資料集。

   ![](assets/s_advuser_cube_wz_14.png)

1. 按一下 **[!UICONTROL Create]** 按鈕以確認：這會帶您前往報表設定和檢視頁面。

   依預設，前兩個可用維度以行和欄提供，但表格中未顯示任何值。 若要產生表格，請按一下主圖示：

   ![](assets/s_advuser_cube_wz_15.png)

1. 您可以切換尺寸的軸、刪除它們、添加新測量等。 可能的操作詳見： [使用立方體來探索資料](../../reporting/using/using-cubes-to-explore-data.md).

   要執行此操作，請使用適當的圖示。

   ![](assets/s_advuser_cube_wz_16.png)
