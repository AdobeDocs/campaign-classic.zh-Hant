---
title: 元素版面
seo-title: 元素版面
description: 元素版面
seo-description: null
page-status-flag: never-activated
uuid: 60dc80d9-f81b-48ce-9341-f975daaf5ebc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 8fdda764-3e42-4972-a9c9-63567588931e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 元素版面{#element-layout}

除了此處詳述的各種圖表外：圖 [表類型和變數](../../reporting/using/creating-a-chart.md#chart-types-and-variants)，您可以調整顯示並新增元素至報表頁面。

您可以使用容器：這些功能可讓您連結頁面的數個元素，並在欄和／或儲存格中設定其版面配置。 本節將詳細說明如何使用 [這些工具](../../web/using/defining-web-forms-layout.md#creating-containers)。

您可以在樹狀結構的根部設定報表配置，並對每個容器進行過載。 頁面會依欄排序。 容器也會分類為欄。 只有靜態和圖形項目會排序成儲存格。

## 定義每個頁面的選項 {#defining-the-options-for-each-page}

您可以使用報表每個頁面上的選項。

此標 **[!UICONTROL General]** 簽可讓您變更頁面的標題，以及設定圖例位置和在報表頁面之間瀏覽。

![](assets/s_ncs_advuser_report_wizard_022.png)

欄位 **[!UICONTROL Title]** 可讓您個人化報表頁面標題中的標籤。 視窗的標題可透過報表的視 **[!UICONTROL Properties]** 窗加以設定。 有關詳細資訊，請參 [閱添加頁眉和頁腳](#adding-a-header-and-a-footer)。

選 **[!UICONTROL Display settings]** 項可讓您選取報表頁面中控制標題的位置，並定義頁面上的欄數。 如需頁面版面的詳細資訊，請參閱本 **節的「項目** 」 [版面區段](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page)。

選取區段中的各種選 **[!UICONTROL Browse]** 項，以授權從一個報表頁面瀏覽至另一個報表頁面。 如果選 **[!UICONTROL Disable next page]** 取或 **[!UICONTROL Disable previous page]** 選項，報表頁 **[!UICONTROL Next]** 面中的和 **[!UICONTROL Previous]** 按鈕會消失。

## 新增頁首和頁尾 {#adding-a-header-and-a-footer}

報表屬性視窗也可讓您定義版面元素，例如：視窗標題、頁首和頁尾的HTML內容。

若要存取屬性視窗，請按一下報 **[!UICONTROL Properties]** 表的按鈕。

![](assets/reporting_properties.png)

此標 **[!UICONTROL Page]** 簽可讓您個人化展示。

![](assets/s_ncs_advuser_report_properties_04.png)

在此標籤中設定的內容將會顯示在所有報表頁面上。

子標 **[!UICONTROL Texts]** 簽可讓您定義變數內容：如果報告設計用於多種語言，則在翻譯週期中將考慮到這一點。

這可讓您建立文字片段清單，並將它們連結至識別碼：

![](assets/s_ncs_advuser_report_properties_04a.png)

然後，將這些識別碼插入報表的HTML內容：

![](assets/s_ncs_advuser_report_properties_04b.png)

報表顯示時，會自動以適當的內容取代這些報表。

和HTML文字一樣，此作業模式可讓您集中管理報表中使用的文字並管理其翻譯。 在此標籤中建立的文字會由Adobe Campaign整合翻譯工具自動收集。
