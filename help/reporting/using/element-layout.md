---
product: campaign
title: 元素版面
description: 元素版面
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Reporting, Monitoring
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 1%

---

# 元素版面{#element-layout}



除了各種詳細的圖表之外 [此處](../../reporting/using/creating-a-chart.md#chart-types-and-variants)，您可以調整顯示方式，並將元素新增至報表頁面。

您可以使用容器：這些容器可讓您連結頁面的數個元素，並在欄及/或儲存格中設定其版面。 如何使用上述變數，詳情請參閱 [本節](../../web/using/defining-web-forms-layout.md#creating-containers).

您可以在樹狀結構的根目錄設定報表配置，並針對每個容器多載它。 頁面會排序為欄。 容器也會排序為欄。 只有靜態和圖形專案會排序成儲存格。

## 定義每個頁面的選項 {#defining-the-options-for-each-page}

您可以在報告的每個頁面上使用選項。

此 **[!UICONTROL General]** 索引標籤可讓您變更頁面標題，以及設定圖例位置並在報表頁面之間瀏覽。

![](assets/s_ncs_advuser_report_wizard_022.png)

此 **[!UICONTROL Title]** 欄位可讓您個人化報表頁面標頭中的標籤。 視窗的標題可透過以下方式設定： **[!UICONTROL Properties]** 報表的視窗。 有關詳細資訊，請參閱 [新增頁首和頁尾](#adding-a-header-and-a-footer).

此 **[!UICONTROL Display settings]** 選項可讓您選取報表頁面中控制標題的位置，並定義頁面上的欄數。 如需頁面配置的詳細資訊，請參閱 **專案配置** 部分 [本節](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page).

選取中的各種選項 **[!UICONTROL Browse]** 區段來授權從一個報表頁面瀏覽至另一個報表頁面。 如果 **[!UICONTROL Disable next page]** 或 **[!UICONTROL Disable previous page]** 已選取選項，則 **[!UICONTROL Next]** 和 **[!UICONTROL Previous]** 按鈕從報表頁面中消失。

## 新增頁首和頁尾 {#adding-a-header-and-a-footer}

報表屬性視窗也可讓您定義版面配置元素，例如：視窗標題、頁首與頁尾的HTML內容。

若要存取屬性視窗，請按一下 **[!UICONTROL Properties]** 按鈕來建立報表。

![](assets/reporting_properties.png)

此 **[!UICONTROL Page]** 標籤可讓您個人化您的顯示。

![](assets/s_ncs_advuser_report_properties_04.png)

在此索引標籤中設定的內容將顯示在所有報告頁面上。

此 **[!UICONTROL Texts]** 子頁簽可讓您定義可變內容：如果設計報表以多種語言使用，則在翻譯週期中會考慮該內容。

這可讓您建立文字片段清單，並將其連結至識別碼：

![](assets/s_ncs_advuser_report_properties_04a.png)

然後，將這些識別碼插入報表的HTML內容中：

![](assets/s_ncs_advuser_report_properties_04b.png)

報表顯示時，會自動以適當的內容取代。

就像HTML文字一樣，此作業模式可讓您集中報表中使用的文字，並管理其翻譯。 此索引標籤中建立的文字會由Adobe Campaign整合式翻譯工具自動收集。
