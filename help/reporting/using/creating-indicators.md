---
product: campaign
title: 建立指標
description: 建立指標
exl-id: e4806bb8-de9d-47e4-8b37-d6c0565b7f5a
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 2%

---

# 建立指標{#creating-indicators}

![](../../assets/common.svg)

要使立方功能化，需要標識相關維和度量並在立方中建立它們。

要建立立方，請應用以下步驟：

1. 選擇工作表。 請參閱 [選擇工作表](#selecting-the-work-table)。
1. 定義尺寸。 請參閱 [定義尺寸](#defining-dimensions)。
1. 定義度量。 請參閱 [建立指標](#building-indicators)。
1. 建立聚合（可選）。 請參閱 [計算和使用聚合](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates)。

此示例說明如何快速在報表中建立一個簡單多維資料集以導出其度量。

具體實施步驟如下。 本章其他章節提供了詳盡的選項和說明。

## 選擇工作表 {#selecting-the-work-table}

要建立多維資料集，請按一下 **[!UICONTROL New]** 按鈕。

![](assets/s_advuser_cube_create.png)

選擇事實架構，即包含要瀏覽的元素的架構。 在此示例中，我們將選擇 **收件人** 的子菜單。

![](assets/s_advuser_cube_wz_02.png)

按一下 **[!UICONTROL Save]** 建立多維資料集：它將出現在「立方」清單中，然後可以使用相應的頁籤進行配置。

按一下 **[!UICONTROL Filter the source data...]** 連結，用於將此多維資料集的計算應用到資料庫中的選定資料。

![](assets/s_advuser_cube_wz_03.png)

## 定義尺寸 {#defining-dimensions}

Dimension與基於每個多維資料集的相關事實架構定義的分析軸一致。 這些是分析中探討的維度，如時間（年、月、日……）、產品或合同的分類（家庭、參考等）、人口部分（按城市、年齡組、狀態等）。

這些分析軸在 **[!UICONTROL Dimension]** 頁籤。

按一下 **[!UICONTROL Add]** 按鈕，在 **[!UICONTROL Expression field]**，按一下 **[!UICONTROL Edit expression]** 表徵圖以選擇包含相關資料的欄位。

![](assets/s_advuser_cube_wz_04.png)

* 從選擇收件人開始 **年齡**。 對於此欄位，您可以定義組合以分組年齡，並使資訊讀取更容易。 建議在可能存在多個單獨值時使用綁定。

   要執行此操作，請檢查 **[!UICONTROL Enable binning]** 的雙曲餘切值。 綁定模式在 [資料綁定](../../reporting/using/concepts-and-methodology.md#data-binning)。

   ![](assets/s_advuser_cube_wz_05.png)

* 添加 **日期** 類型維。 在此，我們要顯示收件人配置檔案建立日期

   要執行此操作，請按一下 **[!UICONTROL Add]** 的 **[!UICONTROL Creation date]** 的子菜單。

   ![](assets/s_advuser_cube_wz_06.png)

   可以選擇日期顯示模式。 為此，請選擇要使用的層次和要生成的級別：

   ![](assets/s_advuser_cube_wz_07.png)

   在我們的示例中，我們只想顯示年、月和日，因為不可能同時使用周和學期/月：這些級別不相容。

* 建立另一個維以分析與收件人所在城市相關的資料

   要執行此操作，請添加新維，然後在 **[!UICONTROL Location]** 收件人架構的節點。

   ![](assets/s_advuser_cube_wz_08.png)

   您可以啟用綁定，使資訊讀取更容易，並將值連結到枚舉。

   ![](assets/s_advuser_cube_wz_09.png)

   從下拉清單中選擇枚舉

   ![](assets/s_advuser_cube_wz_10.png)

   只顯示枚舉中的值。 其它組將分組到 **[!UICONTROL Label of the other values]** 的子菜單。

   有關此內容的詳細資訊，請參閱 [動態管理框](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins)。

## 建立指標 {#building-indicators}

定義維後，需要為要在單元格中顯示的值指定計算模式。 為此，請在 **[!UICONTROL Measures]** 頁籤：建立將使用立方的報表中顯示的列的數量。

若要這麼做，請套用下列步驟：

1. 按一下 **[!UICONTROL Add]** 按鈕。
1. 選擇要應用的度量類型和公式。 我們想統計一下受助者中的婦女人數。

   我們的度量基於事實模式並使用 **[!UICONTROL Count]** 運算子。

   ![](assets/s_advuser_cube_wz_11.png)

   的 **[!UICONTROL Filter the measure data...]** 連結僅允許您選擇女性。 有關定義度量和可用選項的詳細資訊，請參閱 [定義度量](../../reporting/using/concepts-and-methodology.md#defining-measures)。

   ![](assets/s_advuser_cube_wz_12.png)

1. 輸入度量的標籤並保存。

   ![](assets/s_advuser_cube_wz_13.png)

1. 保存多維資料集。

## 基於多維資料集建立報告 {#creating-a-report-based-on-a-cube}

配置多維資料集後，可將其用作建立新報告的模板。

操作步驟：

1. 按一下 **[!UICONTROL Create]** 按鈕 **[!UICONTROL Reports]** 頁籤，然後選擇您剛建立的多維資料集。

   ![](assets/s_advuser_cube_wz_14.png)

1. 按一下 **[!UICONTROL Create]** 按鈕確認：這將帶您進入報告配置和查看頁面。

   預設情況下，前兩個可用維以行和列提供，但表中不顯示任何值。 要生成表，請按一下主表徵圖：

   ![](assets/s_advuser_cube_wz_15.png)

1. 可以切換尺寸軸、刪除它們、添加新測量等。 可能的操作詳見 [此頁](../../reporting/using/using-cubes-to-explore-data.md)。

   為此，請使用相應的表徵圖。

   ![](assets/s_advuser_cube_wz_16.png)
