---
product: campaign
title: 建立新報表
description: 瞭解建立新報告的關鍵步驟
exl-id: 4c2aad47-0e2d-4d0b-8898-b437f4a05e11
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 1%

---

# 建立新報吿{#creating-a-new-report}

![](../../assets/common.svg)

要建立報告，請應用以下步驟：

1. 開啟Adobe Campaign瀏覽器， **[!UICONTROL Administration > Configuration]** ，然後選擇 **[!UICONTROL Reports]** 的子菜單。
1. 按一下 **[!UICONTROL New]** 按鈕。
1. 選取 **[!UICONTROL Create a new report from a template]** 並按一下 **[!UICONTROL Next]**。

   ![](assets/s_ncs_advuser_report_wizard_new_01.png)

1. 在下拉清單中選擇報表模板。

   * 的 **[!UICONTROL Extended report]** 用於建立使用圖表配置的報告。
   * 的 **[!UICONTROL Qualitative distribution]** 報告允許您根據所有類型的資料（公司名稱、電子郵件域等）建立統計資訊。
   * 的 **[!UICONTROL Quantitative distribution]** 報告用於建立可以測量或計數的資料（發票額、收件人年齡等）的統計資訊。

   有關這些報告模板的詳細資訊，請參閱 [此部分](../../reporting/using/about-descriptive-analysis.md)。

1. 在相應欄位中輸入報表名稱及其說明。 指定 **[!UICONTROL schema]** 報告將應用於其中。

   ![](assets/s_ncs_advuser_report_wizard_020.png)

1. 保存此報告。

## 為圖表建模 {#modelizing-the-chart}

保存報告後，應顯示此資訊。 現在，您可以構建報表圖表。

![](assets/s_ncs_user_report_wizard_021.png)

報告的編製圖由一系列活動組成。

![](assets/s_ncs_advuser_report_wizard_031.png)

活動使用由箭頭表示的過渡進行連結。

![](assets/s_ncs_advuser_report_wizard_032.png)

要構建報表，需要根據報表的性質和上下文確定有用的元素並對其邏輯序列進行建模。

1. 使用 **[!UICONTROL Start]** 活動，以實現為構建報告而要執行的第一個進程。 每個報表只能使用其中一個活動。

   如果圖表包含循環，則此參數是必需的。

1. 添加一個或多個 **[!UICONTROL Query]** 活動，以收集對構建報表有用的資料。 可以通過資料庫模式上的查詢直接收集資料，也可以通過導入的清單或現有多維資料集來收集資料。

   有關此內容的詳細資訊，請參閱 [收集要分析的資料](../../reporting/using/collecting-data-to-analyze.md)。

   此資料將根據頁面配置顯示（或不顯示）在報告中。

1. 放置一個或多個 **[!UICONTROL Page]** 活動，以定義收集資料的圖形表示形式。 可以插入表、圖表、輸入欄位，並設定一個或多個頁面或頁面元素的顯示條件。 所顯示的內容是完全可配置的。

   有關此內容的詳細資訊，請參閱 [靜態元素](#static-elements)。

1. 使用 **[!UICONTROL Test]** 的子菜單。

   有關此內容的詳細資訊，請參閱 [調整頁面顯示](../../reporting/using/defining-a-conditional-content.md#conditioning-page-display)。

1. 如有必要，請通過 **[!UICONTROL Script]** 活動，例如計算報表名稱，過濾特定上下文中結果的顯示等。

   有關此內容的詳細資訊，請參閱 [指令碼活動](../../reporting/using/advanced-functionalities.md#script-activity)。

1. 最後，為了更輕鬆地閱讀複雜報告，可插入一個或多個 **[!UICONTROL Jump]** 鍵。 這樣，您就可以從一個活動轉到另一個活動，而無需對報表上的轉換進行具體化。 的 **[!UICONTROL Jump]** 活動還可用於顯示其他報告。

   有關此內容的詳細資訊，請參閱 [跳轉活動](../../reporting/using/advanced-functionalities.md#jump-activity)。

不能同時執行多個分支。 這意味著這樣構建的報告將不起作用：

![](assets/reporting_graph_sample_ko.png)

但是，您可以放置多個分支。 只執行其中一項：

![](assets/reporting_graph_sample_ok.png)

## 建立頁面 {#creating-a-page}

內容通過圖表中放置的活動進行配置。 有關此內容的詳細資訊，請參閱 [建模圖表](#modelizing-the-chart)。

要配置活動，請按兩下其表徵圖。

顯示的內容在 **頁面** 鍵。

報表可以包含一個或多個頁面。 通過專用編輯器建立頁面，該編輯器允許您在樹結構中插入輸入欄位、選擇欄位、靜態元素、圖表或表。 容器可幫助您定義佈局。 有關此內容的詳細資訊，請參閱 [元素佈局](../../reporting/using/element-layout.md)。

要向頁面添加元件，請使用工具欄左上部分的表徵圖。

![](assets/reporting_add_component_in_page.png)

也可按一下右鍵要添加元件的節點並從清單中選擇它。

![](assets/s_ncs_advuser_report_wizard_09.png)

>[!CAUTION]
>
>如果報表注定以Excel格式導出，建議不要使用複雜的HTML格式。 有關此內容的詳細資訊，請參閱 [導出報告](../../reporting/using/actions-on-reports.md#exporting-a-report)。

A **[!UICONTROL Page]** 可以包括以下元素：

* 條形、餅圖、曲線類型 **[!UICONTROL charts]**&#x200B;的子菜單。
* 透視；包含組或分析的清單 **[!UICONTROL tables]**。
* 文本或數字類型 **[!UICONTROL Input controls]**。
* 下拉清單、複選框、單選按鈕、多選項、日期或矩陣類型 **[!UICONTROL Selection controls]**。
* 連結編輯器、常數、資料夾選擇類型 **[!UICONTROL Advanced controls]**。
* 值、連結、HTML、影像等 **[!UICONTROL Static elements]**。
* **[!UICONTROL Containers]** 用於控制元件佈局。

有關頁面及其元件的配置模式的詳細資訊，請參閱 [此部分](../../web/using/about-web-forms.md)。

使用工具欄可以添加或刪除控制項，並在報告頁中組織其順序。

![](assets/s_ncs_advuser_report_wizard_08.png)

### 靜態元素 {#static-elements}

靜態元素使您能夠在報告中顯示用戶不會與其交互的資訊，如圖形元素或指令碼。 請參閱 [此部分](../../web/using/static-elements-in-a-web-form.md#inserting-html-content) 的子菜單。

![](assets/s_advuser_report_page_activity_03.png)

### 篩選報表中的資訊 {#filtering-information-in-a-report}

通過輸入和選擇控制項，您可以過濾報表中顯示的資訊。 有關實現此類篩選的詳細資訊，請參閱 [篩選查詢中的選項](../../reporting/using/collecting-data-to-analyze.md#filtering-options-in-the-queries)。

有關建立和配置輸入欄位和選擇欄位的詳細資訊，請參閱 [此部分](../../web/using/about-web-forms.md)。

可以將一個或多個輸入控制項整合到報表中。 此類型的控制項允許您根據輸入的值篩選顯示的資訊。

![](assets/reporting_control_text.png)

您還可以將一個或多個選擇控制項整合到報告中。 此類型的控制項允許您根據所選值過濾報告中包含的資訊，例如：

* 通過單選按鈕或複選框：

   ![](assets/reporting_radio_buttons.png)

* 通過下拉清單：

   ![](assets/reporting_control_list.png)

* 通過日曆：

   ![](assets/reporting_control_date.png)

最後，您可以將一個或多個高級控制項整合到報告中。 此類型的控制項使您能夠插入連結、常數或選擇資料夾。

在此，您可以篩選報告中的資料，以僅顯示樹的資料夾之一中包含的資訊：

![](assets/reporting_control_folder.png)
