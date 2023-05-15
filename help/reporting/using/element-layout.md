---
product: campaign
title: 元素版面
description: 元素版面
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 1%

---

# 元素版面{#element-layout}



除了各種圖表 [此處](../../reporting/using/creating-a-chart.md#chart-types-and-variants)，您可以調整顯示並新增元素至報表頁面。

您可以使用容器：這些功能可讓您連結頁面的數個元素，並在欄和/或儲存格中設定其配置。 如何使用這些參數，在 [本節](../../web/using/defining-web-forms-layout.md#creating-containers).

您可以在樹狀結構的根位置設定報表配置，並針對每個容器將其過載。 頁面會依欄排序。 容器也會分類為欄。 只有靜態和圖形項目會排序成儲存格。

## 定義每個頁面的選項 {#defining-the-options-for-each-page}

您可以在報表的每個頁面上使用選項。

此 **[!UICONTROL General]** 索引標籤可讓您變更頁面標題，以及設定圖例位置和在報表頁面之間瀏覽。

![](assets/s_ncs_advuser_report_wizard_022.png)

此 **[!UICONTROL Title]** 欄位可讓您個人化報表頁面標題中的標籤。 視窗的標題可透過 **[!UICONTROL Properties]** 的下限。 有關詳細資訊，請參閱 [新增頁首和頁尾](#adding-a-header-and-a-footer).

此 **[!UICONTROL Display settings]** 選項可讓您選取報表頁面中控制標題的位置，以及定義頁面上的欄數。 如需頁面配置的詳細資訊，請參閱 **項目配置** 區段 [本節](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

選取 **[!UICONTROL Browse]** 區段來授權從一個報表頁面瀏覽至另一個報表頁面。 若 **[!UICONTROL Disable next page]** 或 **[!UICONTROL Disable previous page]** 選項， **[!UICONTROL Next]** 和 **[!UICONTROL Previous]** 按鈕從報表頁面中消失。

## 新增頁首和頁尾 {#adding-a-header-and-a-footer}

報表屬性視窗也可讓您定義配置元素，例如：視窗的標題、頁首和頁尾的HTML內容。

要訪問屬性窗口，請按一下 **[!UICONTROL Properties]** 按鈕。

![](assets/reporting_properties.png)

此 **[!UICONTROL Page]** 索引標籤可讓您個人化您的顯示。

![](assets/s_ncs_advuser_report_properties_04.png)

此索引標籤中設定的內容將顯示在所有報表頁面上。

此 **[!UICONTROL Texts]** 子索引標籤可讓您定義變數內容：如果在翻譯週期中將報告設計為以多種語文使用，則將考慮該報告。

這可讓您建立文字片段清單，並將它們連結至識別碼：

![](assets/s_ncs_advuser_report_properties_04a.png)

然後，將這些識別碼插入報表的HTML內容中：

![](assets/s_ncs_advuser_report_properties_04b.png)

報表顯示時，系統會自動將其取代為適當的內容。

與HTML文本一樣，此操作模式允許您集中報告中使用的文本並管理其翻譯。 Adobe Campaign整合翻譯工具會自動收集此索引標籤中建立的文字。
