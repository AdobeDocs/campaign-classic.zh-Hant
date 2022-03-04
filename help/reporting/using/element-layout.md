---
product: campaign
title: 元素版面
description: 元素版面
feature: Reporting
exl-id: 79d5c901-905b-4a0e-adb9-91fd6acb186f
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 1%

---

# 元素版面{#element-layout}

![](../../assets/common.svg)

除了各種圖表外， [這裡](../../reporting/using/creating-a-chart.md#chart-types-and-variants)，可以調整顯示並將元素添加到報告頁。

可以使用容器：這些功能使您能夠連結頁面的多個元素，並在列和/或單元格中配置其佈局。 如何使用它們，詳見 [此部分](../../web/using/defining-web-forms-layout.md#creating-containers)。

可以在樹的根部配置報告佈局，並使每個容器的報告佈局超載。 頁面按列排序。 容器也按列分類。 只有靜態和圖形項被分類到單元格中。

## 定義每頁的選項 {#defining-the-options-for-each-page}

您可以使用報表每頁上的選項。

的 **[!UICONTROL General]** 頁籤，用於更改頁面標題，以及配置圖例位置和在報告頁之間瀏覽。

![](assets/s_ncs_advuser_report_wizard_022.png)

的 **[!UICONTROL Title]** 欄位中，您可以個性化報表頁標題中的標籤。 窗口的標題可通過 **[!UICONTROL Properties]** 的子菜單。 有關此內容的詳細資訊，請參閱 [添加頁眉和頁腳](#adding-a-header-and-a-footer)。

的 **[!UICONTROL Display settings]** 選項允許您選擇報表頁中控制項標題的位置，並定義頁上的列數。 有關頁面佈局的詳細資訊，請參閱 **物料佈局** 部分 [此部分](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page)。

在 **[!UICONTROL Browse]** 部分，以授權從一個報表頁瀏覽到另一個報表頁。 如果 **[!UICONTROL Disable next page]** 或 **[!UICONTROL Disable previous page]** 選項 **[!UICONTROL Next]** 和 **[!UICONTROL Previous]** 按鈕從報告頁面中消失。

## 添加頁眉和頁腳 {#adding-a-header-and-a-footer}

報告屬性窗口還允許您定義佈局元素，如：窗口的標題、頁眉和頁腳的HTML內容。

要訪問屬性窗口，請按一下 **[!UICONTROL Properties]** 按鈕。

![](assets/reporting_properties.png)

的 **[!UICONTROL Page]** 頁籤，您可以個性化顯示。

![](assets/s_ncs_advuser_report_properties_04.png)

此頁籤中配置的內容將在所有報告頁面上可見。

的 **[!UICONTROL Texts]** 子頁籤允許您定義變數內容：如果報告設計用於多種語言，則在翻譯週期中將予以考慮。

這允許您建立文本片段清單並將它們連結到標識符：

![](assets/s_ncs_advuser_report_properties_04a.png)

然後，將這些標識符插入報表的HTML內容：

![](assets/s_ncs_advuser_report_properties_04b.png)

在顯示報告時，將自動用相應內容替換這些內容。

與HTML文本一樣，此操作模式使您能夠集中報告中使用的文本並管理其翻譯。 在該標籤中建立的文本由Adobe Campaign綜合翻譯工具自動收集。
