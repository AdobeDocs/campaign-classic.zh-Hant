---
product: campaign
title: 建立圖表
description: 瞭解如何設計圖表
feature: Reporting, Monitoring
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
exl-id: d32b614f-82c1-4363-816c-4ebedaa5cfe9
TQID: https://experienceleague.adobe.com/-212hQNHR-f8ktM3kNKiHgYw4C8Ql71dbZtOX7zoKqc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
  - id: cfda811a-e413-43a4-adf0-7370888f5cfc
  - id: afe938ea-bc18-44a4-a3fb-03e1031466cb
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 541
ht-degree: 2%

---

# 建立圖表{#creating-a-chart}



資料庫中的資料也可以收集並顯示在圖表中。 Adobe Campaign提供一組圖形化表示法。 其設定詳述如下。

圖表會透過右鍵功能表或工具列，直接插入報表頁面中。

## 建立步驟 {#creation-steps}

若要在報表中建立圖表，請套用下列步驟：

1. 編輯您要顯示圖表的頁面，並在工具列上選取圖表型別。

   ![](assets/s_advuser_report_page_activity_04.png)

1. 輸入名稱和標題。 如有必要，您可以使用下拉式清單來變更註解的位置。

   ![](assets/s_ncs_advuser_report_wizard_018.png)

1. 按一下&#x200B;**[!UICONTROL Data]**&#x200B;索引標籤以定義資料來源和要計算的序列。

   要顯示在圖表中的統計資料可以根據查詢或內容資料進行計算，也就是目前頁面的輸入轉變所提供的資料（如需詳細資訊，請參閱[使用內容資料](../../reporting/using/using-the-context.md#using-context-data)）。

   * 按一下&#x200B;**[!UICONTROL Filter data...]**&#x200B;連結以定義資料庫中資料的篩選准則。

     ![](assets/reporting_graph_add_filter.png)

   * 若要使用內容資料，請從&#x200B;**[!UICONTROL Source]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Context data]**，然後按一下&#x200B;**[!UICONTROL Advanced settings...]**&#x200B;連結。 然後選取統計資料會關注的資料。

     ![](assets/reporting_graph_from_context.png)

     然後，您就可以存取內容資料，以定義要在圖表中顯示的值：

     ![](assets/reporting_graph_select-from_context.png)

## 圖表型別和變體 {#chart-types-and-variants}

Adobe Campaign提供各種圖形表示型別。 其詳情如下。

圖表型別插入頁面時會加以選取。

![](assets/s_advuser_report_page_activity_04.png)

您也可以透過圖表中&#x200B;**[!UICONTROL General]**&#x200B;索引標籤的&#x200B;**[!UICONTROL Chart type]**&#x200B;區段進行更改。

![](assets/reporting_change_graph_type.png)

變體取決於所選的圖表型別。 已透過&#x200B;**[!UICONTROL Variants...]**&#x200B;連結選取它們。

### 劃分：圓形圖 {#breakdown--pie-charts}

此型別的圖形表示可讓您顯示所測量元素的概觀。

圓餅圖只能讓您分析一個變數。

![](assets/reporting_graph_type_sector_1.png)

**[!UICONTROL Variants]**&#x200B;連結可讓您個人化圖表的整體呈現。

![](assets/reporting_graph_type_sector_2.png)

圓形圖可讓您在適當的欄位中輸入內半徑的值。

例如：

0.00追蹤完整的圓形。

![](assets/s_ncs_advuser_report_sector_exple1.png)

0.40追蹤半徑為40%的圓。

![](assets/s_ncs_advuser_report_sector_exple2.png)

1.00隻追蹤圓圈的外部。

![](assets/s_ncs_advuser_report_sector_exple3.png)

### 演變：曲線和區域 {#evolution--curves-and-areas}

此型別的圖形表示可讓您及時瞭解一或多個量測的演變。

![](assets/reporting_graph_type_curve.png)

### 比較：長條圖 {#comparison--histograms}

長條圖可讓您比較一或多個變數的值。

對於這些型別的圖表，**[!UICONTROL Variants]**&#x200B;視窗中提供下列選項：

![](assets/reporting_select_graph_var.png)

核取&#x200B;**[!UICONTROL Display caption]**&#x200B;選項以顯示圖表的標題，並選擇其位置：

![](assets/reporting_select_graph_legend.png)

在適當的情況下，您可以將值棧疊在一起。

![](assets/reporting_graph_type_histo.png)

如有必要，您可以反轉值顯示順序。 若要這麼做，請選取&#x200B;**[!UICONTROL Reverse stacking]**&#x200B;選項。

### 轉換：funnel {#conversion--funnel}

此型別的圖表可讓您追蹤測量元素的交談率。

## 與圖表的互動 {#interaction-with-the-chart}

您可以定義使用者按一下圖表時的動作。 開啟&#x200B;**[!UICONTROL Interaction events]**&#x200B;視窗並選取您要執行的動作。

可能的互動型別及其設定在[此區段](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)中詳細說明。

![](assets/s_ncs_advuser_report_wizard_017.png)

## 計算統計資料 {#calculating-statistics}

圖表可讓您顯示所收集資料的統計資料。

這些統計資料是透過&#x200B;**[!UICONTROL Data]**&#x200B;索引標籤的&#x200B;**[!UICONTROL Series parameters]**&#x200B;區段定義的。

若要建立新的統計資料，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;圖示並設定適當的視窗。 可用的計算型別詳述如下。

![](assets/reporting_add_statistics.png)

如需詳細資訊，請參閱[本章節](../../reporting/using/using-the-descriptive-analysis-wizard.md#statistics-calculation)。
