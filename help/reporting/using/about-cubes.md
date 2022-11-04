---
product: campaign
title: 開始使用 cubes
description: 開始使用 cubes
feature: Reporting
hide: true
hidefromtoc: true
exl-id: ade4c857-9233-4bc8-9ba1-2fec84b7c3e6
source-git-commit: 1635366b9e1302acd3d8997312bf07d5c1a68982
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 3%

---

# 開始使用 cubes{#about-cubes}

![](../../assets/common.svg)

## 術語 {#terminology}

使用多維度資料集時的特定辭彙列於下方。

* **立方體**  — 多維資料集表示多維資訊：它為最終用戶提供了專為互動式資料分析而設計的結構。

* **數值表/方案**  — 事實表（或事實模式）包含分析所依據的原始或基本資料。 這些表主要是大量表（可能包含連結的表），計算時間可能很長。 例如，事實表可以是：broadlog表格、購買表格等

* **Dimension** -Dimension可讓您將資料分段至群組：建立維後，維將用作分析軸。 在大多數情況下，會針對指定的維度定義數個層級。 例如，對於臨時維度，層級會是月、天、小時、分鐘等。 這組層級代表維度階層，並啟用各種資料分析層級。

* **賓寧**  — 對於某些欄位，您可以定義組值的綁定，並更方便讀取資訊。 系結會套用至層級。 建議您在可能有許多不同值時定義捆綁。

* **測量**  — 最頻繁的措施是和、平均、最大、最小、標準差等。 可以計算度量：例如，要約的接受率是其被呈現的次數與被接受的次數之比。

## 多維資料集工作區 {#cube-workspace}

多維資料集儲存在 **[!UICONTROL Administration > Configuration > Cubes]** 節點。

![](assets/s_advuser_cube_node.png)

多維資料集的主要使用內容如下：

* 資料匯出可直接在報表中執行，此報表設計於 **[!UICONTROL Reports]** 頁簽。

   要執行此操作，請建立新報告並選擇要使用的多維資料集。

   ![](assets/cube_create_new.png)

   立方體的顯示方式與根據建立報表的範本類似。 選擇範本後，按一下 **[!UICONTROL Create]** 設定及檢視相符報表。

   您可以調整測量、變更顯示模式或設定表格，然後使用主按鈕顯示報表。

   ![](assets/cube_display_new.png)

* 您也可以在 **[!UICONTROL Query]** 報表方塊以使用其指標，如下所示：

   ![](assets/s_advuser_query_using_a_cube.png)

* 您也可以根據多維資料集將樞紐表插入報表的任何頁面。 要執行此操作，請參考要在 **[!UICONTROL Data]** 索引標籤（位於相關頁面上）。

   ![](assets/s_advuser_cube_in_report.png)

   有關詳細資訊，請參閱 [探索報表中的資料](../../reporting/using/using-cubes-to-explore-data.md#exploring-the-data-in-a-report).
