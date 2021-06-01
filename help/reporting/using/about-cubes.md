---
product: campaign
title: 關於立方體
description: 關於立方體
audience: reporting
content-type: reference
topic-tags: designing-reports-with-cubes
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 10%

---

# 開始使用 cubes{#about-cubes}

透過&#x200B;**Marketing Analytics**&#x200B;模組可探索資料庫中的資料。 它可讓您分析和測量資料、計算統計資料、簡化並最佳化報表建立和計算。 除此之外，Marketing Analytics還可讓您建立報表和建立目標母體。 識別完這些值後，就會儲存在可用於Adobe Campaign（鎖定目標、細分等）的清單中。

立方體可用來產生某些內建報表，包括傳送報表（傳送追蹤、點按、開啟等）。 基於多維資料集的報告只能用作500萬條事實線以下資料卷的標準。

您可以擴充資料庫的探索和分析能力，同時讓最終使用者更容易設定報告和表格：他們只需在建立其報告或表格時，選取現有的（全設定好的）多維度資料集，以處理計算、測量和統計數據。

建立並設定多維度資料集後，便可以用於報告查詢方塊和網頁應用程式；可以在樞紐分析表內使用及操作多維度資料集。

>[!CAUTION]
>
>**行銷** 分析是Adobe Campaign模組。您必須將它安裝在您的執行個體上，才能使用下述功能。

使用Marketing Analytics模組，Campaign可讓您：

1. 在以下視圖中建立立方：

   * 將資料聚合併儲存在工作表中，以根據用戶需求預先計算指標，
   * 減少用於報告和查詢的各種計算中涉及的資料量，從而顯著優化指標計算時間，
   * 簡化資料存取，讓使用者能根據各種維度來控制資料（無論資料是否預先匯總）。

   有關詳細資訊，請參閱[建立指標](../../reporting/using/creating-indicators.md)。

1. 在以下視圖中建立透視表：

   * 探索計算資料，配置測量，
   * 選擇要顯示的資料及其顯示模式，
   * 個人化所使用的措施和指標，
   * 為具有非技術背景的使用者提供互動式分析工具。

   有關詳細資訊，請參閱[使用多維資料集來探索資料](../../reporting/using/using-cubes-to-explore-data.md)。

1. 使用在多維資料集中計算和匯總的資料建立查詢。
1. 識別母體，並在清單中參照母體。

## 術語 {#terminology}

使用多維度資料集時，必須已知下列概念：

* 立方體

   多維資料集是多維資訊的表示：它為最終用戶提供了專為互動式資料分析而設計的結構。

* 數值表/方案

   事實表（或事實模式）包含分析將基於的原始或基本資料。 這些表主要是大量表（可能包含連結的表），計算時間可能很長。

   例如，事實表可以是：broadlog表格、購買表格等

* Dimension

   Dimension可讓您將資料分段至群組：建立維後，維將用作分析軸。 在大多數情況下，會針對指定的維度定義數個層級。 例如，對於臨時維度，層級會是月、天、小時、分鐘等。 這組層級代表維度階層，並啟用各種資料分析層級。

* 賓寧

   對於某些欄位，您可以定義組值的綁定，並更方便讀取資訊。 將綁定應用於級別

   建議您在可能有許多不同值時定義捆綁。

* 測量

   最常見的度量是和、平均、最大、最小、標準差等。

   可以計算度量：例如，要約的接受率是其被呈現的次數與被接受的次數之比。

## 多維資料集工作區{#cube-workspace}

多維資料集儲存在&#x200B;**[!UICONTROL Administration > Configuration > Cubes]**&#x200B;節點中。

![](assets/s_advuser_cube_node.png)

多維資料集的主要使用內容如下：

* 資料匯出可直接在Adobe Campaign平台&#x200B;**[!UICONTROL Reports]**&#x200B;標籤中設計的報表中執行。

   要執行此操作，請建立新報告並選擇要使用的多維資料集。

   ![](assets/cube_create_new.png)

   立方體的顯示方式與根據建立報表的範本類似。 選擇模板後，按一下&#x200B;**[!UICONTROL Create]**&#x200B;以配置和查看匹配的報告。

   您可以調整測量、變更顯示模式或設定表格，然後使用主按鈕顯示報表。

   ![](assets/cube_display_new.png)

* 您也可以參考報表&#x200B;**[!UICONTROL Query]**&#x200B;方塊中的多維資料集，以使用其指標，如下所示：

   ![](assets/s_advuser_query_using_a_cube.png)

* 您也可以根據多維資料集將樞紐表插入報表的任何頁面。 要執行此操作，請參考要在相關頁面上透視表的&#x200B;**[!UICONTROL Data]**&#x200B;索引標籤中使用的多維資料集。

   ![](assets/s_advuser_cube_in_report.png)

   如需詳細資訊，請參閱[探索報表](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report)中的資料。
