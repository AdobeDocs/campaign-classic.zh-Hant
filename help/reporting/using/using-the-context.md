---
title: 使用上下文
seo-title: 使用上下文
description: 使用上下文
seo-description: null
page-status-flag: never-activated
uuid: ac8c7068-d640-4934-b7f5-bc91b98eab4c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 72fe6df0-0271-48f9-bd6d-bb1ff25fbdf3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 使用上下文{#using-the-context}

當您想要以或的形式表示資 **[!UICONTROL tables]** 料 **[!UICONTROL charts]**&#x200B;時，可從兩個來源取得：新查詢(請參 [閱定義資料的直接篩選](#defining-a-direct-filter-on-data))或報表內容(請參閱使 [用內容資料](#using-context-data))。

## 定義資料的直接篩選 {#defining-a-direct-filter-on-data}

### 篩選資料 {#filtering-data}

建立報 **[!UICONTROL Query]** 表時，使用類型活動並非必要項目。 可直接在組成報表的表格和圖表中篩選資料。

這可讓您選擇要透過報表活動直接顯示在報 **[!UICONTROL Page]** 表中的資料。

若要這麼做，請按一下 **[!UICONTROL Filter data...]** 標籤中的連 **[!UICONTROL Data]** 結：此連結可讓您存取運算式編輯器，以定義要分析之資料的查詢。

![](assets/reporting_filter_data_from_page.png)

### 範例：在圖表中使用篩選 {#example--use-a-filter-in-a-chart}

在下列範例中，我們希望圖表只顯示居住在法國且在年內購買的收件者設定檔。

若要定義此篩選，請將頁面置於圖表中並加以編輯。 按一下 **[!UICONTROL Filter data]** 連結，並建立符合您要顯示之資料的篩選。 如需有關在Adobe Campaign中建立查詢的詳細資訊，請參 [閱本節](../../platform/using/about-queries-in-campaign.md)。

![](assets/s_ncs_advuser_report_wizard_029.png)

在此，我們想要依所選收件者的城市來顯示劃分。

![](assets/reporting_graph_with_2vars.png)

轉換效果會如下所示：

![](assets/reporting_graph_with_2vars_preview.png)

### 範例：在透視表中使用篩選器 {#example--use-a-filter-in-a-pivot-table}

在此範例中，篩選器可讓您在樞紐表中只顯示非巴黎客戶，而不需事先使用其他查詢。

應用以下步驟：

1. 將頁面置於圖表中並加以編輯。
1. 建立透視表。
1. 轉到該 **[!UICONTROL Data]** 頁籤並選擇要使用的立方。
1. 按一下 **[!UICONTROL Filter data...]** 連結並定義下列查詢，將Adobe從公司清單中移除。

   ![](assets/s_ncs_advuser_report_display_03.png)

只有符合篩選條件的收件者才會出現在報表中。

![](assets/s_ncs_advuser_report_display_04.png)

## 使用上下文資料 {#using-context-data}

若要以或的形式表示資 **[!UICONTROL table]** 料， **[!UICONTROL chart]**&#x200B;資料可來自報表內容。

在包含表格或圖表的頁面中，此標 **[!UICONTROL Data]** 簽可讓您選取資料來源。

![](assets/s_ncs_advuser_report_datasource_3.png)

* 選 **[!UICONTROL New query]** 項可讓您建立查詢以收集資料。 有關詳細資訊，請參 [閱定義資料的直接篩選](#defining-a-direct-filter-on-data)。
* 選 **[!UICONTROL Context data]** 項可讓您使用輸入資料：報表的上下文與包含圖表或表格的頁面的傳入轉換中包含的資訊一致。 例如，此內容可能包含透過置於活動之前的 **[!UICONTROL Query]** 活動所收集到的資 **[!UICONTROL Page]** 料，而您需要指定報表所關注的表格和欄位。

例如，在查詢方塊中，為收件者建立下列查詢：

![](assets/s_ncs_advuser_report_datasource_2.png)

然後在報表中指出資料來源，在此案例中： **[!UICONTROL Data from the context]**。

資料位置會自動推斷。 如有必要，您可以強制使用資料路徑。

![](assets/s_ncs_advuser_report_datasource_4.png)

當您選擇統計資料所關注的資料時，可用欄位會與查詢中指定的資料相符。

![](assets/s_ncs_advuser_report_datasource_1.png)

