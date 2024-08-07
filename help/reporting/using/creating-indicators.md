---
product: campaign
title: 建立指標
description: 建立指標
feature: Reporting, Monitoring
hide: true
hidefromtoc: true
exl-id: e4806bb8-de9d-47e4-8b37-d6c0565b7f5a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 2%

---

# 建立指標{#creating-indicators}



若要讓立方結構發揮作用，您必須識別相關的維度和測量，並在立方結構中建立它們。

若要建立立方結構，請套用下列步驟：

1. 選取工作表。 請參閱[選取工作表](#selecting-the-work-table)。
1. 定義維度。 請參閱[定義維度](#defining-dimensions)。
1. 定義測量。 參考[建置指標](#building-indicators)。
1. 建立彙總（選用）。 請參閱[計算並使用彙總](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates)。

此範例說明如何在報表中快速建立簡單的立方結構以匯出其測量。

實作步驟詳述如下。 本章的其他章節提供詳盡的選項和說明。

## 選取工作表 {#selecting-the-work-table}

若要建立Cube，請按一下立方結構清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕。

![](assets/s_advuser_cube_create.png)

選取事實結構描述，即包含您要探索之元素的結構描述。 在此範例中，我們將選取&#x200B;**收件者**&#x200B;資料表。

![](assets/s_advuser_cube_wz_02.png)

按一下&#x200B;**[!UICONTROL Save]**&#x200B;建立Cube：它會出現在Cube清單中，然後可以使用適當的索引標籤進行設定。

按一下&#x200B;**[!UICONTROL Filter the source data...]**&#x200B;連結，將此Cube的計算套用至資料庫中選取的資料。

![](assets/s_advuser_cube_wz_03.png)

## 定義維度 {#defining-dimensions}

Dimension與根據相關事實結構描述為每個立方結構定義的分析軸一致。 這些是在分析中探索的維度，例如時間（年、月、日期……）、產品或合約的分類（家庭、參考資料等）、人口區段（依城市、年齡群組、狀態等）。

這些分析軸是在Cube的&#x200B;**[!UICONTROL Dimension]**&#x200B;索引標籤中定義。

按一下「**[!UICONTROL Add]**」按鈕以建立新維度，然後在&#x200B;**[!UICONTROL Expression field]**&#x200B;中，按一下「**[!UICONTROL Edit expression]**」圖示以選取包含相關資料的欄位。

![](assets/s_advuser_cube_wz_04.png)

* 從選取收件者&#x200B;**年齡**&#x200B;開始。 對於此欄位，您可以定義量化以分組年齡，並讓資訊閱讀更容易。 當存在數個獨立值的可能性時，我們建議使用量化。

  若要這麼做，請核取&#x200B;**[!UICONTROL Enable binning]**&#x200B;選項。 在[資料量化](../../reporting/using/concepts-and-methodology.md#data-binning)中詳細說明量化模式。

  ![](assets/s_advuser_cube_wz_05.png)

* 新增&#x200B;**日期**&#x200B;型別維度。 在這裡，我們要顯示收件者設定檔建立日期

  若要這麼做，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選取收件者表格中的&#x200B;**[!UICONTROL Creation date]**&#x200B;欄位。

  ![](assets/s_advuser_cube_wz_06.png)

  您可以選取日期顯示模式。 若要這麼做，請選取要使用的階層以及要產生的層次：

  ![](assets/s_advuser_cube_wz_07.png)

  在我們的範例中，我們只想要顯示年、月和日，因為無法同時使用周和半年/月：這些層級不相容。

* 建立另一個維度以分析相對於收件者城市的資料

  若要這麼做，請新增維度，並在收件者結構描述的&#x200B;**[!UICONTROL Location]**&#x200B;節點中選取城市。

  ![](assets/s_advuser_cube_wz_08.png)

  您可以啟用量化以使資訊讀取更容易，並將值連結到分項清單。

  ![](assets/s_advuser_cube_wz_09.png)

  從下拉式清單中選取分項清單

  ![](assets/s_advuser_cube_wz_10.png)

  只會顯示分項清單中的值。 其他則將在&#x200B;**[!UICONTROL Label of the other values]**&#x200B;欄位中定義的標籤下分組。

  如需詳細資訊，請參閱[動態管理回收筒](../../reporting/using/concepts-and-methodology.md#dynamically-managing-bins)。

## 建立指標 {#building-indicators}

定義維度後，您需要為要在儲存格中顯示的值指定計算模式。 若要這麼做，請在&#x200B;**[!UICONTROL Measures]**&#x200B;索引標籤中建立相符的指標：建立與報告中有欄數一樣多的計量，這些欄將使用Cube。

若要這麼做，請套用下列步驟：

1. 按一下 **[!UICONTROL Add]** 按鈕。
1. 選取要套用的測量型別和公式。 在此處，我們要計算收件者中女性的數量。

   我們的量值是以事實結構描述為基礎，並使用&#x200B;**[!UICONTROL Count]**&#x200B;運運算元。

   ![](assets/s_advuser_cube_wz_11.png)

   **[!UICONTROL Filter the measure data...]**&#x200B;連結可讓您僅選取女性。 如需定義測量與可用選項的詳細資訊，請參閱[定義測量](../../reporting/using/concepts-and-methodology.md#defining-measures)。

   ![](assets/s_advuser_cube_wz_12.png)

1. 輸入測量的標籤並儲存。

   ![](assets/s_advuser_cube_wz_13.png)

1. 儲存立方體。

## 根據立方體建立報告 {#creating-a-report-based-on-a-cube}

在設定立方結構後，就可以將它當作建立新報告的範本。

操作步驟：

1. 按一下&#x200B;**[!UICONTROL Reports]**&#x200B;索引標籤的&#x200B;**[!UICONTROL Create]**&#x200B;按鈕，然後選取您剛建立的Cube。

   ![](assets/s_advuser_cube_wz_14.png)

1. 按一下&#x200B;**[!UICONTROL Create]**&#x200B;按鈕以確認：這會將您導向至報告設定和檢視頁面。

   依預設，前兩個可用尺寸以行和欄提供，但表格中不顯示任何值。 若要產生表格，請按一下主圖示：

   ![](assets/s_advuser_cube_wz_15.png)

1. 您可以切換尺寸的軸、刪除它們、新增測量等。 在[此頁面](../../reporting/using/using-cubes-to-explore-data.md)中詳細說明可能的作業。

   要執行此操作，請使用適當的圖示。

   ![](assets/s_advuser_cube_wz_16.png)
