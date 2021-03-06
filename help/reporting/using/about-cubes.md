---
product: campaign
title: 開始使用 cubes
description: 開始使用 cubes
feature: Reporting
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 11%

---

# 開始使用 cubes{#about-cubes}

![](../../assets/common.svg)

資料庫中的資料通過 **營銷分析** 中。 它使您能夠分析和測量資料、計算統計資訊、簡化和優化報表建立和計算。 除此之外，營銷分析還使您能夠建立報告和構建目標群體。 一旦識別了這些資訊，它們就儲存在可在Adobe Campaign使用的清單中（目標、細分等）。

立方用於生成某些內置報告，包括交付報告（交付跟蹤、按一下、開啟等）。 基於立方的報告只能用作500萬條事實線以下資料卷的標準。

您可以擴充資料庫的探索和分析能力，同時讓最終使用者更容易設定報告和表格：他們只需在建立其報告或表格時，選取現有的（全設定好的）多維度資料集，以處理計算、測量和統計數據。

建立並設定多維度資料集後，便可以用於報告查詢方塊和網頁應用程式；可以在樞紐分析表內使用及操作多維度資料集。

>[!CAUTION]
>
>**營銷分析** 是Adobe Campaign艙。 它需要安裝在實例上，以便您可以使用下面描述的功能。

使用「市場活動營銷分析」模組可以：

1. 建立立方

   * 將資料匯總並儲存到工作表中，根據用戶需求預計算指標，
   * 減少用於報告和查詢的各種計算中涉及的資料量，從而顯著優化指標計算時間，
   * 簡化對資料的訪問，使用戶能夠根據不同的維度來操作資料（無論資料是否預聚合）。

   有關此內容的詳細資訊，請參閱 [建立指標](../../reporting/using/creating-indicators.md)。

1. 建立透視表

   * 瀏覽計算資料，配置測量，
   * 選擇要顯示的資料及其顯示模式，
   * 使用的措施和指標個性化，
   * 為具有非技術背景的用戶提供互動式分析工具。

   有關此內容的詳細資訊，請參閱 [使用多維資料集來瀏覽資料](../../reporting/using/using-cubes-to-explore-data.md)。

1. 使用在多維資料集中計算和聚合的資料生成查詢。
1. 確定總量並在清單中引用它們。

## 術語 {#terminology}

下面列出了使用立方時的特定術語。

* **立方**  — 多維資料集是多維資訊的表示：它為最終用戶提供了設計用於互動式資料分析的結構。

* **事實表/架構**  — 事實表（或事實架構）包含分析所基於的原始或基本資料。 這些表主要是具有可能長計算的大型卷表（可能與連結表一起）。 例如，事實表可以是：廣播表、購買表等。

* **Dimension** -Dimension允許您將資料分段到組：建立這些尺寸後，這些尺寸將用作分析軸。 在大多數情況下，對於給定維，將定義多個級別。 例如，對於臨時維，級別將為月、天、小時、分鐘等。 這組級別表示維層次，並啟用各種資料分析級別。

* **賓寧**  — 對於某些欄位，您可以定義組合到組值，並使讀取資訊更容易。 綁定應用於級別。 我們建議您在可能存在許多不同值時定義綁定。

* **度量**  — 最頻繁的措施是求和、平均、最大值、最小值、標準差等。 可以計算度量：例如，要約的接受率是它被提出的次數與它被接受的次數之比。

## 多維資料集工作區 {#cube-workspace}

立方儲存在 **[!UICONTROL Administration > Configuration > Cubes]** 的下界。

![](assets/s_advuser_cube_node.png)

立方的主要使用上下文如下：

* 資料導出可直接在報告中執行， **[!UICONTROL Reports]** 頁籤。

   為此，請建立新報告並選擇要使用的多維資料集。

   ![](assets/cube_create_new.png)

   立方顯示為基於其建立報告的模板。 選擇模板後，按一下 **[!UICONTROL Create]** 以配置和查看匹配的報告。

   您可以調整測量、更改顯示模式或配置表，然後使用主按鈕顯示報告。

   ![](assets/cube_display_new.png)

* 也可以在 **[!UICONTROL Query]** 報告框，以使用其指標，如下所示：

   ![](assets/s_advuser_query_using_a_cube.png)

* 您還可以將基於多維資料集的透視表插入到報表的任何頁面。 為此，請引用要在 **[!UICONTROL Data]** 對話框。

   ![](assets/s_advuser_cube_in_report.png)

   有關此內容的詳細資訊，請參閱 [瀏覽報告中的資料](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report)。
