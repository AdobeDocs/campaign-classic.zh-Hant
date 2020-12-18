---
solution: Campaign Classic
product: campaign
title: 元素版面
description: 元素版面
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 1%

---


# 元素版面{#element-layout}

除了此處詳述的各種圖表外：[圖表類型和變體](../../reporting/using/creating-a-chart.md#chart-types-and-variants)，您可以調整顯示並新增元素至報表頁面。

您可以使用容器：這些功能可讓您連結頁面的數個元素，並在欄和／或儲存格中設定其版面配置。 如何使用它們在[本節](../../web/using/defining-web-forms-layout.md#creating-containers)中有詳細說明。

您可以在樹狀結構的根部設定報表配置，並對每個容器進行過載。 頁面會依欄排序。 容器也會分類為欄。 只有靜態和圖形項目會排序成儲存格。

## 定義每個頁面的選項{#defining-the-options-for-each-page}

您可以使用報表每個頁面上的選項。

**[!UICONTROL General]**&#x200B;標籤可讓您變更頁面標題，以及設定圖例位置和在報表頁面之間瀏覽。

![](assets/s_ncs_advuser_report_wizard_022.png)

**[!UICONTROL Title]**&#x200B;欄位可讓您個人化報表頁面標題中的標籤。 視窗的標題可透過報表的&#x200B;**[!UICONTROL Properties]**&#x200B;視窗來設定。 有關詳細資訊，請參閱[添加頁眉和頁腳](#adding-a-header-and-a-footer)。

**[!UICONTROL Display settings]**&#x200B;選項可讓您選取控制標題在報表頁面中的位置，並定義頁面上的欄數。 如需頁面版面的詳細資訊，請參閱[本節](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page)的&#x200B;**Item layout**&#x200B;章節。

在&#x200B;**[!UICONTROL Browse]**&#x200B;區段中選取各種選項，以授權從一個報表頁面瀏覽至另一個報表頁面。 如果選取&#x200B;**[!UICONTROL Disable next page]**&#x200B;或&#x200B;**[!UICONTROL Disable previous page]**&#x200B;選項，**[!UICONTROL Next]**&#x200B;和&#x200B;**[!UICONTROL Previous]**&#x200B;按鈕會從報表頁面中消失。

## 新增頁首和頁尾{#adding-a-header-and-a-footer}

報表屬性視窗也可讓您定義版面元素，例如：視窗標題、頁首和頁尾的HTML內容。

若要存取屬性視窗，請按一下報表的&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕。

![](assets/reporting_properties.png)

**[!UICONTROL Page]**&#x200B;標籤可讓您個人化您的顯示畫面。

![](assets/s_ncs_advuser_report_properties_04.png)

在此標籤中設定的內容將會顯示在所有報表頁面上。

**[!UICONTROL Texts]**&#x200B;子標籤可讓您定義變數內容：如果報告設計用於多種語言，則在翻譯週期中將考慮到這一點。

這可讓您建立文字片段清單，並將它們連結至識別碼：

![](assets/s_ncs_advuser_report_properties_04a.png)

然後，將這些識別碼插入報表的HTML內容：

![](assets/s_ncs_advuser_report_properties_04b.png)

報表顯示時，會自動以適當的內容取代這些報表。

和HTML文字一樣，此作業模式可讓您集中管理報表中使用的文字並管理其翻譯。 在此標籤中建立的文字會由Adobe Campaign整合翻譯工具自動收集。
