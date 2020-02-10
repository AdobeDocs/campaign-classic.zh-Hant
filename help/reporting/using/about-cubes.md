---
title: 關於立方
seo-title: 關於立方
description: 關於立方
seo-description: null
page-status-flag: never-activated
uuid: 429bd5e9-288a-4c71-9b01-c4c5690f5abe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
discoiquuid: 42db3be8-ee02-4158-adcd-846420a32460
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 關於立方{#about-cubes}

透過 **Marketing Analytics模組可探索資料庫中的資** 料。 它可讓您分析和測量資料、計算統計資料、簡化並最佳化報表建立和計算。 除此之外，行銷分析還可讓您建立報表並建立目標人口族群。 在識別這些項目後，這些項目會儲存在可用於Adobe Campaign（定位、分段等）的清單中。

立方可用來產生特定的內建報表，包括傳送報表（傳送追蹤、點按、開啟等）。 基於立方的報告只能用作500萬條資料線以下資料卷的標準。

您可以擴充資料庫探索和分析能力，同時讓最終使用者更容易設定報表和表格：他們只需在建立其報表或表以處理計算、度量和統計資訊時選擇一個現有（完全配置）立方。

建立並設定好立方後，立方便會用於報表查詢方塊和Web應用程式。 它們可在樞紐表內使用和處理。

>[!CAUTION]
>
>**Marketing Analytics** 是Adobe Campaign模組。 它必須安裝在您的例項上，您才能使用下述功能。

透過Marketing Analytics模組，Campaign可讓您：

1. 在以下視圖中建立立方：

   * 將資料匯總並儲存在工作表中，以根據用戶需求預先計算指標，
   * 減少用於報告和查詢的各種計算中涉及的資料量，從而顯著優化指標計算時間，
   * 簡化資料的存取，讓使用者根據不同的維度來控制資料（無論是否預先匯總）。
   For more on this, refer to [Creating indicators](../../reporting/using/creating-indicators.md).

1. 在以下視圖中建立透視表：

   * 探索計算資料，設定測量，
   * 選取要顯示的資料及其顯示模式，
   * 個人化使用的措施和指標，
   * 為不具技術背景的使用者提供互動式分析工具。
   有關詳細資訊，請參閱使 [用立方體來探索資料](../../reporting/using/using-cubes-to-explore-data.md)。

1. 使用立方中計算和聚集的資料構建查詢。
1. 識別人口族群並在清單中加以參照。

## 術語 {#terminology}

使用立方時，必須知道以下概念：

* 立方

   立方體是多維資訊的表示：它為最終用戶提供了專為互動式資料分析而設計的結構。

* 數值表／方案

   事實表（或事實模式）包含分析所依據的原始或基本資料。 這些表主要是大量表（可能包含連結表），計算可能很長。

   例如，事實表可以是：broadlog表、購買表等。

* 維

   維度可讓您將資料分段至群組：建立維後，尺寸將用作分析軸。 在大多數情況下，對於給定維，將定義多個級別。 例如，對於時間維度，層級將是月、日、小時、分鐘等。 這組層代表維層次，並啟用各種級別的資料分析。

* Binning

   對於某些欄位，您可以定義群組值的系結，讓您更容易讀取資訊。 系結會套用至層級

   我們建議您在可能有許多不同的值時定義綁定。

* 測量

   最常用的測量方法有求和、平均、最大、最小、標準差等。

   可計算度量：例如，要約的接受率是其被提出的次數與被接受的次數之比。

## 立方工作區 {#cube-workspace}

立方儲存在節 **[!UICONTROL Administration > Configuration > Cubes]** 點中。

![](assets/s_advuser_cube_node.png)

立方的主要使用上下文如下：

* 資料匯出可直接在Adobe Campaign平台所設計的報 **[!UICONTROL Reports]** 表中進行。

   若要這麼做，請建立新報表並選取您要使用的立方。

   ![](assets/cube_create_new.png)

   立方體的顯示方式與建立報表的範本類似。 選擇範本後，按一下以 **[!UICONTROL Create]** 設定並檢視相符的報表。

   您可以調整測量、變更顯示模式或設定表格，然後使用主按鈕顯示報表。

   ![](assets/cube_display_new.png)

* 您也可以參考報表方塊中的 **[!UICONTROL Query]** 立方體，以使用其指標，如下所示：

   ![](assets/s_advuser_query_using_a_cube.png)

* 您也可以將基於立方的樞紐表插入報表的任何頁面。 要執行此操作，請參考要用於相關頁上透 **[!UICONTROL Data]** 視表頁籤的立方。

   ![](assets/s_advuser_cube_in_report.png)

   如需詳細資訊，請參 [閱探索報表中的資料](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report)。

