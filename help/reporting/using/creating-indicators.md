---
product: campaign
title: 建立指標
description: 建立指標
feature: Reporting
hide: true
hidefromtoc: true
exl-id: e4806bb8-de9d-47e4-8b37-d6c0565b7f5a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 2%

---

# 建立指標{#creating-indicators}



若要讓立方結構發揮作用，您必須識別相關的維度和計量，並在立方結構中建立它們。

若要建立立方結構，請套用下列步驟：

1. 選取工作表。 請參閱 [選取工作表](#selecting-the-work-table).
1. 定義維度。 請參閱 [定義維度](#defining-dimensions).
1. 定義量值。 請參閱 [建置指標](#building-indicators).
1. 建立彙總（選用）。 請參閱 [計算及使用彙總](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

此範例說明如何在報表中快速建立簡易的多維資料庫，以匯出其測量。

實作步驟詳述如下。 本章的其他章節提供詳盡的選項和說明。

## 選取工作表 {#selecting-the-work-table}

若要建立立方結構，請按一下 **[!UICONTROL New]** 「立方體」清單上方的按鈕。

![](assets/s_advuser_cube_create.png)

選取事實結構描述，即包含您要探索之元素的結構描述。 在此範例中，我們將選取 **收件者** 表格。

![](assets/s_advuser_cube_wz_02.png)

按一下 **[!UICONTROL Save]** 建立立方結構：它會出現在立方結構清單上，然後可以使用適當的頁簽進行設定。

按一下 **[!UICONTROL Filter the source data...]** 此連結可將此Cube的計算套用至資料庫中選取的資料。

![](assets/s_advuser_cube_wz_03.png)

## 定義維度 {#defining-dimensions}

Dimension與根據相關事實結構描述為每個Cube定義的分析軸一致。 這些是在分析中探索的維度，例如時間（年、月、日期……）、產品或合約的分類（家庭、參考資料等）、人口區段（依城市、年齡群組、狀態等）。

這些分析軸定義於 **[!UICONTROL Dimension]** Cube的頁簽。

按一下 **[!UICONTROL Add]** 按鈕以建立新維度，然後在 **[!UICONTROL Expression field]**，按一下 **[!UICONTROL Edit expression]** 圖示以選取包含相關資料的欄位。

![](assets/s_advuser_cube_wz_04.png)

* 從選取收件者開始 **年齡**. 對於此欄位，您可以定義量度歸組年齡，讓資訊閱讀更輕鬆。 當可能有數個單獨值時，我們建議使用量化。

   若要這麼做，請核取 **[!UICONTROL Enable binning]** 選項。 有關量化模式的詳情，請參閱 [資料量化](../../reporting/using/concepts-and-methodology.md#data-binning).

   ![](assets/s_advuser_cube_wz_05.png)

* 新增 **日期** 型別維度。 在這裡，我們要顯示收件者設定檔建立日期

   若要這麼做，請按一下 **[!UICONTROL Add]** 並選取 **[!UICONTROL Creation date]** 收件者表格中的欄位。

   ![](assets/s_advuser_cube_wz_06.png)

   您可以選取日期顯示模式。 若要這麼做，請選取要使用的階層以及要產生的層次：

   ![](assets/s_advuser_cube_wz_07.png)

   在我們的範例中，我們只想要顯示年、月和日，因為無法同時使用周和半年/月：這些層級不相容。

* 建立另一個維度以分析相對於收件者城市的資料

   若要這麼做，請新增維度，並選取 **[!UICONTROL Location]** 收件者綱要的節點。

   ![](assets/s_advuser_cube_wz_08.png)

   您可以啟用量化，讓資訊閱讀更輕鬆，並將值連結至分項清單。

   ![](assets/s_advuser_cube_wz_09.png)

   從下拉式清單中選取分項清單

   ![](assets/s_advuser_cube_wz_10.png)

   只會顯示分項清單中的值。 其他則會在中定義的標籤下分組。 **[!UICONTROL Label of the other values]** 欄位。

   有關詳細資訊，請參閱 [動態管理回收筒](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins).

## 建置指標 {#building-indicators}

定義維度後，您需要為儲存格中顯示的值指定計算模式。 若要這麼做，請在 **[!UICONTROL Measures]** 索引標籤：建立要顯示在報表中且使用cube之資料欄的量值。

若要這麼做，請套用下列步驟：

1. 按一下 **[!UICONTROL Add]** 按鈕。
1. 選取要套用的測量型別和公式。 在這裡，我們要計算收件者中的女性人數。

   我們的測量以事實結構描述為基礎，並使用 **[!UICONTROL Count]** 運運算元。

   ![](assets/s_advuser_cube_wz_11.png)

   此 **[!UICONTROL Filter the measure data...]** 連結可讓您只選取女性。 有關定義測量和可用選項的詳細資訊，請參閱 [定義測量](../../reporting/using/concepts-and-methodology.md#defining-measures).

   ![](assets/s_advuser_cube_wz_12.png)

1. 輸入測量的標籤並儲存。

   ![](assets/s_advuser_cube_wz_13.png)

1. 儲存立方體。

## 根據立方體建立報告 {#creating-a-report-based-on-a-cube}

在設定多維資料庫之後，它就可以用來作為建立新報告的範本。

操作步驟：

1. 按一下 **[!UICONTROL Create]** 的按鈕 **[!UICONTROL Reports]** 頁簽並選取您剛建立的cube。

   ![](assets/s_advuser_cube_wz_14.png)

1. 按一下 **[!UICONTROL Create]** 按鈕以確認：這會將您帶往報告設定和檢視頁面。

   依預設，前兩個可用尺寸以行和欄提供，但表格中未顯示任何值。 若要產生表格，請按一下主圖示：

   ![](assets/s_advuser_cube_wz_15.png)

1. 您可以切換尺寸的軸、刪除它們、新增測量等。 中會詳細說明可能的操作 [此頁面](../../reporting/using/using-cubes-to-explore-data.md).

   要執行此操作，請使用適當的圖示。

   ![](assets/s_advuser_cube_wz_16.png)
