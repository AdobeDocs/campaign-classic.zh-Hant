---
product: campaign
title: 元素版面
description: 元素版面
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Reporting, Monitoring
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# 元素版面{#element-layout}



除了詳細的[這裡](../../reporting/using/creating-a-chart.md#chart-types-and-variants)的各種圖表之外，您還可以調整顯示方式，並將元素新增至報告頁面。

您可以使用容器：這些容器可讓您連結頁面的數個元素，並在欄及/或儲存格中設定其版面。 在[本節](../../web/using/defining-web-forms-layout.md#creating-containers)中會詳細說明如何使用。

您可以在樹狀結構的根目錄設定報表配置，並針對每個容器多載它。 頁面會排序為欄。 容器也會排序為欄。 只有靜態和圖形專案會排序成儲存格。

## 定義每個頁面的選項 {#defining-the-options-for-each-page}

您可以在報告的每個頁面上使用選項。

**[!UICONTROL General]**&#x200B;索引標籤可讓您變更頁面標題，以及設定圖例位置並在報表頁面之間瀏覽。

![](assets/s_ncs_advuser_report_wizard_022.png)

**[!UICONTROL Title]**&#x200B;欄位可讓您個人化報告頁面標頭中的標籤。 視窗的標題可透過報告的&#x200B;**[!UICONTROL Properties]**&#x200B;視窗來設定。 如需詳細資訊，請參閱[新增頁首和頁尾](#adding-a-header-and-a-footer)。

**[!UICONTROL Display settings]**&#x200B;選項可讓您選取報告頁面中控制標題的位置，並定義頁面上的欄數。 如需頁面配置的詳細資訊，請參閱[此區段](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page)的&#x200B;**專案配置**&#x200B;區段。

在&#x200B;**[!UICONTROL Browse]**&#x200B;區段中選取各種選項，以授權從一個報告頁面瀏覽到另一個報告頁面。 如果選取&#x200B;**[!UICONTROL Disable next page]**&#x200B;或&#x200B;**[!UICONTROL Disable previous page]**&#x200B;選項，**[!UICONTROL Next]**&#x200B;和&#x200B;**[!UICONTROL Previous]**&#x200B;按鈕會從報告頁面中消失。

## 新增頁首和頁尾 {#adding-a-header-and-a-footer}

報表屬性視窗也可讓您定義版面配置元素，例如：視窗標題、頁首與頁尾的HTML內容。

若要存取屬性視窗，請按一下報告的&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕。

![](assets/reporting_properties.png)

**[!UICONTROL Page]**&#x200B;索引標籤可讓您個人化您的顯示。

![](assets/s_ncs_advuser_report_properties_04.png)

在此索引標籤中設定的內容將顯示在所有報告頁面上。

**[!UICONTROL Texts]**&#x200B;子標籤可讓您定義變數內容：如果設計報表以多種語言使用，則會在翻譯週期期間將其列入考量。

這可讓您建立文字片段清單，並將其連結至識別碼：

![](assets/s_ncs_advuser_report_properties_04a.png)

然後，將這些識別碼插入報表的HTML內容中：

![](assets/s_ncs_advuser_report_properties_04b.png)

報表顯示時，會自動以適當的內容取代。

就像HTML文字一樣，此作業模式可讓您集中報表中使用的文字，並管理其翻譯。 此索引標籤中建立的文字會由Adobe Campaign整合式翻譯工具自動收集。
