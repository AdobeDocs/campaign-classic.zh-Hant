---
product: campaign
title: 建立新報吿
description: 瞭解建立新報告的關鍵步驟
feature: Reporting
exl-id: 4c2aad47-0e2d-4d0b-8898-b437f4a05e11
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 1%

---

# 建立新報吿{#creating-a-new-report}



若要建立報表，請套用下列步驟：

1. 開啟Adobe Campaign Explorer，並從 **[!UICONTROL Administration > Configuration]** 節點，然後選取 **[!UICONTROL Reports]** 資料夾。
1. 按一下 **[!UICONTROL New]** 按鈕來標籤報表。
1. 選取 **[!UICONTROL Create a new report from a template]** 並按一下 **[!UICONTROL Next]**。

   ![](assets/s_ncs_advuser_report_wizard_new_01.png)

1. 在下拉式清單中選取報表範本。

   * 此 **[!UICONTROL Extended report]** 可讓您建立使用圖表設定的報告。
   * 此 **[!UICONTROL Qualitative distribution]** 報表可讓您根據所有型別的資料（公司名稱、電子郵件網域等）建立統計資料。
   * 此 **[!UICONTROL Quantitative distribution]** 報表可讓您建立可測量或計數的資料統計資料（發票金額、收件者年齡等）。

   如需這些報告範本的詳細資訊，請參閱 [本節](../../reporting/using/about-descriptive-analysis.md).

1. 在對應欄位中輸入報表名稱及其說明。 指定 **[!UICONTROL schema]** 報表將套用的對象。

   ![](assets/s_ncs_advuser_report_wizard_020.png)

1. 儲存此報告。

## 為圖表建模 {#modelizing-the-chart}

儲存報告後，應會顯示此專案。 您現在可以建置報告的圖表。

![](assets/s_ncs_user_report_wizard_021.png)

建立報表的圖表由一系列活動組成。

![](assets/s_ncs_advuser_report_wizard_031.png)

活動會使用以箭頭表示的轉變來連結。

![](assets/s_ncs_advuser_report_wizard_032.png)

若要根據報表的性質與內容來建置報表，您必須識別有用的元素，並將其邏輯順序模組化。

1. 使用 **[!UICONTROL Start]** 將建立報表所執行的第一個程式具體化的活動。 每個報表只能使用其中一個活動。

   如果圖表包含回圈，則是強制性的。

1. 新增一或多個 **[!UICONTROL Query]** 收集有助於建立報表之資料的活動。 您可以透過資料庫結構描述上的查詢直接收集資料，或是透過匯入的清單或現有的Cube收集資料。

   有關詳細資訊，請參閱 [收集資料以進行分析](../../reporting/using/collecting-data-to-analyze.md).

   此資料會根據頁面設定顯示在報表中（或不顯示在報表中）。

1. 放置一或多個 **[!UICONTROL Page]** 活動，定義所收集資料的圖形表示。 您可以插入表格、圖表、輸入欄位，並設定顯示一或多個頁面或頁面元素的條件。 顯示的內容可完全設定。

   有關詳細資訊，請參閱 [靜態元素](#static-elements).

1. 使用 **[!UICONTROL Test]** 活動，定義顯示或存取資料的條件。

   有關詳細資訊，請參閱 [調整頁面顯示](../../reporting/using/defining-a-conditional-content.md#conditioning-page-display).

1. 如有必要，請透過以下方式新增個人化指令碼： **[!UICONTROL Script]** 活動，例如計算報表名稱、篩選特定內容中結果的顯示等。

   有關詳細資訊，請參閱 [指令碼活動](../../reporting/using/advanced-functionalities.md#script-activity).

1. 最後，為了更輕鬆閱讀複雜報表，您可以插入一或多個 **[!UICONTROL Jump]** 型別活動。 這可讓您從一個活動移至另一個活動，而不需在報表上具體化轉變。 此 **[!UICONTROL Jump]** 活動也可用來顯示其他報表。

   有關詳細資訊，請參閱 [跳轉活動](../../reporting/using/advanced-functionalities.md#jump-activity).

您無法同時執行多個分支。 這表示以此方式建立的報表無法運作：

![](assets/reporting_graph_sample_ko.png)

不過，您可以放置多個分支。 將只執行其中一個：

![](assets/reporting_graph_sample_ok.png)

## 建立頁面 {#creating-a-page}

內容是透過圖表中的活動來設定。 有關詳細資訊，請參閱 [模型化圖表](#modelizing-the-chart).

若要設定活動，請連按兩下其圖示。

顯示的內容定義於 **頁面** 型別活動。

報表可包含一或多個頁面。 頁面是透過專用編輯器建立的，可讓您以樹狀結構插入輸入欄位、選取欄位、靜態元素、圖表或表格。 容器可協助您定義版面。 有關詳細資訊，請參閱 [元素版面](../../reporting/using/element-layout.md).

若要將元件新增至頁面，請使用工具列左上角的圖示。

![](assets/reporting_add_component_in_page.png)

您也可以以滑鼠右鍵按一下要新增元件的節點，然後從清單中選取它。

![](assets/s_ncs_advuser_report_wizard_09.png)

>[!CAUTION]
>
>如果報表預計要以Excel格式匯出，建議您不要使用複雜的HTML格式。 有關詳細資訊，請參閱 [匯出報告](../../reporting/using/actions-on-reports.md#exporting-a-report).

A **[!UICONTROL Page]** 可包含下列元素：

* 長條圖、圓形圖、曲線型別 **[!UICONTROL charts]**&#x200B;等。
* 樞紐分析；具有群組或劃分的清單 **[!UICONTROL tables]**.
* 文字或數字型別 **[!UICONTROL Input controls]**.
* 下拉式清單、核取方塊、選項按鈕、多項選擇、日期或矩陣型別 **[!UICONTROL Selection controls]**.
* 連結編輯器、常數、資料夾選擇型別 **[!UICONTROL Advanced controls]**.
* 值、連結、HTML、影像等。 **[!UICONTROL Static elements]**.
* **[!UICONTROL Containers]** 可讓您控制元件配置。

頁面及其元件的設定模式詳見 [本節](../../web/using/about-web-forms.md).

工具列可讓您新增或移除控制項，以及組織控制項在報表頁面中的順序。

![](assets/s_ncs_advuser_report_wizard_08.png)

### 靜態元素 {#static-elements}

靜態元素可讓您在報表中顯示使用者不會互動的資訊，例如圖形元素或指令碼。 請參閱 [本節](../../web/using/static-elements-in-a-web-form.md#inserting-html-content) 以取得詳細資訊。

![](assets/s_advuser_report_page_activity_03.png)

### 篩選報告中的資訊 {#filtering-information-in-a-report}

輸入和選取控制項可讓您篩選報表中顯示的資訊。 如需實作此類篩選的詳細資訊，請參閱 [篩選查詢中的選項](../../reporting/using/collecting-data-to-analyze.md#filtering-options-in-the-queries).

若要進一步瞭解如何建立和設定輸入欄位和選取欄位，請參閱 [本節](../../web/using/about-web-forms.md).

您可以將一或多個輸入控制項整合至報表中。 此型別的控制項可讓您根據輸入的值篩選顯示的資訊。

![](assets/reporting_control_text.png)

您也可以將一或多個選取範圍控制項整合至報表中。 此型別的控制項可讓您根據選取的值篩選報表中包含的資訊，例如：

* 透過選項按鈕或核取方塊：

   ![](assets/reporting_radio_buttons.png)

* 透過下拉式清單：

   ![](assets/reporting_control_list.png)

* 透過行事曆：

   ![](assets/reporting_control_date.png)

最後，您可以將一或多個進階控制項整合至報表中。 此控制項型別可讓您插入連結、常數或選取資料夾。

您可以在此處篩選報告中的資料，以僅顯示樹狀結構其中一個資料夾中包含的資訊：

![](assets/reporting_control_folder.png)
