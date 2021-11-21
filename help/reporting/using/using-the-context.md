---
product: campaign
title: 使用內容
description: 使用內容
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: a19e2843-d3f9-48c3-af72-cc1bc54f6360
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 3%

---

# 使用內容{#using-the-context}

![](../../assets/common.svg)

若您想以 **[!UICONTROL tables]** 或 **[!UICONTROL charts]**，可從兩個來源取用：新查詢(請參閱 [定義資料的直接篩選](#defining-a-direct-filter-on-data))或報表內容(請參閱 [使用內容資料](#using-context-data))。

## 定義資料的直接篩選 {#defining-a-direct-filter-on-data}

### 篩選資料 {#filtering-data}

使用 **[!UICONTROL Query]** 建立報表時，「類型活動」不是必填項目。 您可以直接在組成報表的表格和圖表中篩選資料。

這可讓您選取要直接透過 **[!UICONTROL Page]** 報表的活動。

若要這麼做，請按一下 **[!UICONTROL Filter data...]** 連結 **[!UICONTROL Data]** 標籤：此連結可讓您存取運算式編輯器，以定義要分析之資料的查詢。

![](assets/reporting_filter_data_from_page.png)

### 範例：在圖表中使用篩選器 {#example--use-a-filter-in-a-chart}

在下列範例中，我們希望圖表只顯示居住在法國的收件者設定檔，以及當年購買的收件者設定檔。

若要定義此篩選器，請在圖表中放置頁面並加以編輯。 按一下 **[!UICONTROL Filter data]** 連結，並建立符合您要顯示之資料的篩選器。 如需在Adobe Campaign中建立查詢的詳細資訊，請參閱 [本節](../../platform/using/about-queries-in-campaign.md).

![](assets/s_ncs_advuser_report_wizard_029.png)

在此，我們要依所選收件者的城市來顯示劃分。

![](assets/reporting_graph_with_2vars.png)

呈現會如下所示：

![](assets/reporting_graph_with_2vars_preview.png)

### 範例：在透視表中使用篩選器 {#example--use-a-filter-in-a-pivot-table}

在此範例中，篩選器可讓您在樞紐表格中僅顯示非巴黎客戶，而不預先使用其他查詢。

應用以下步驟：

1. 將頁面放入圖表中並進行編輯。
1. 建立樞紐分析表。
1. 前往 **[!UICONTROL Data]** 頁簽，然後選擇要使用的多維資料集。
1. 按一下 **[!UICONTROL Filter data...]** 連結並定義下列查詢，以從公司清單中移除Adobe。

   ![](assets/s_ncs_advuser_report_display_03.png)

只有符合篩選條件的收件者才會出現在報表中。

![](assets/s_ncs_advuser_report_display_04.png)

## 使用內容資料 {#using-context-data}

以 **[!UICONTROL table]** 或 **[!UICONTROL chart]**，資料可來自報表內容。

在包含表格或圖表的頁面中， **[!UICONTROL Data]** 索引標籤可讓您選取資料來源。

![](assets/s_ncs_advuser_report_datasource_3.png)

* 此 **[!UICONTROL New query]** 選項可讓您建立查詢以收集資料。 有關詳細資訊，請參閱 [定義資料的直接篩選](#defining-a-direct-filter-on-data).
* 此 **[!UICONTROL Context data]** 選項可讓您使用輸入資料：報表的上下文與包含圖表或表格之頁面的入站轉變中包含的資訊一致。 例如，此內容可能包含透過 **[!UICONTROL Query]** 放在 **[!UICONTROL Page]** 活動，而您需要指定報表所關注的表格和欄位。

例如，在查詢方塊中，為收件者建立下列查詢：

![](assets/s_ncs_advuser_report_datasource_2.png)

然後在報表中指出資料的來源，在此情況下： **[!UICONTROL Data from the context]**.

資料位置會自動推斷。 如有必要，您可以強制資料路徑。

![](assets/s_ncs_advuser_report_datasource_4.png)

當您選擇統計資訊將關注的資料時，可用欄位與查詢中指定的資料一致。

![](assets/s_ncs_advuser_report_datasource_1.png)
