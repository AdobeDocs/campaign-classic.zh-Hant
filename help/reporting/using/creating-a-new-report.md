---
solution: Campaign Classic
product: campaign
title: 建立新報表
description: 瞭解建立新報表的關鍵步驟
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 11ff62238a8fb73658f2263c25dbeb27d2e0fb23
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---


# 建立新報表{#creating-a-new-report}

若要建立報表，請套用下列步驟：

1. 開啟「Adobe Campaign資源管理器」並從&#x200B;**[!UICONTROL Administration > Configuration]**&#x200B;節點中，然後選擇&#x200B;**[!UICONTROL Reports]**&#x200B;資料夾。
1. 按一下報表清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕。
1. 選取 **[!UICONTROL Create a new report from a template]** 並按一下 **[!UICONTROL Next]**。

   ![](assets/s_ncs_advuser_report_wizard_new_01.png)

1. 在下拉式清單中選取報表範本。

   * **[!UICONTROL Extended report]**&#x200B;可讓您建立使用圖表設定的報表。
   * **[!UICONTROL Qualitative distribution]**&#x200B;報表可讓您根據所有資料類型（公司名稱、電子郵件網域等）建立統計資料。
   * **[!UICONTROL Quantitative distribution]**&#x200B;報表可讓您建立可測量或計算的資料統計資料（發票金額、收件者年齡等）。

   有關這些報告模板的詳細資訊，請參閱[本節](../../reporting/using/about-descriptive-analysis.md)。

1. 在對應欄位中輸入報表名稱及其說明。 指定將套用報表的&#x200B;**[!UICONTROL schema]**。

   ![](assets/s_ncs_advuser_report_wizard_020.png)

1. 儲存此報表。

## 建模圖表{#modelizing-the-chart}

儲存報表後，應顯示此項。 您現在可以建立報表的圖表。

![](assets/s_ncs_user_report_wizard_021.png)

建立報告的圖表由一系列活動組成。

![](assets/s_ncs_advuser_report_wizard_031.png)

活動使用轉場連結，由箭頭表示。

![](assets/s_ncs_advuser_report_wizard_032.png)

若要建立報表，請視其性質和內容而定，您必須識別有用的元素並建立其邏輯順序的模型。

1. 使用&#x200B;**[!UICONTROL Start]**&#x200B;活動來具體化要執行的建立報表的第一個流程。 每個報表只能使用其中一個活動。

   如果圖表包含回圈，則此為必填項目。

1. 新增一或多個&#x200B;**[!UICONTROL Query]**&#x200B;活動，以收集對建立報表有用的資料。 可以通過資料庫方案上的查詢或通過導入清單或現有多維資料集直接收集資料。

   有關詳細資訊，請參閱[收集資料以分析](../../reporting/using/collecting-data-to-analyze.md)。

   此資料會依頁面設定而顯示（或不顯示）在報表中。

1. 放置一或多個&#x200B;**[!UICONTROL Page]**&#x200B;活動以定義所收集資料的圖形表示。 您可以插入表格、圖表、輸入欄位，並設定一或多個頁面或頁面元素的顯示條件。 所顯示的內容可完全設定。

   有關詳細資訊，請參閱[Static elements](#static-elements)。

1. 使用&#x200B;**[!UICONTROL Test]**&#x200B;活動來定義顯示或存取資料的條件。

   有關詳細資訊，請參閱[Conditioning page display](../../reporting/using/defining-a-conditional-content.md#conditioning-page-display)。

1. 如有必要，請透過&#x200B;**[!UICONTROL Script]**&#x200B;活動新增個人化指令碼，例如計算報表名稱，以篩選結果在特定內容中的顯示，等等。

   有關詳細資訊，請參閱[指令碼活動](../../reporting/using/advanced-functionalities.md#script-activity)。

1. 最後，為了更輕鬆地閱讀複雜報表，您可以插入一或多個&#x200B;**[!UICONTROL Jump]**&#x200B;類型活動。 這可讓您從一個活動移至另一個活動，而不須在報表上實體化轉場。 **[!UICONTROL Jump]**&#x200B;活動也可用來顯示其他報表。

   有關詳細資訊，請參閱[Jump活動](../../reporting/using/advanced-functionalities.md#jump-activity)。

不能同時執行多個分支。 這表示，以此建立的報表將無法運作：

![](assets/reporting_graph_sample_ko.png)

不過，您可放置數個分支。 只會執行其中一項：

![](assets/reporting_graph_sample_ok.png)

## 建立頁面{#creating-a-page}

內容是透過置入圖表中的活動來設定。 有關詳細資訊，請參閱[使用圖表建模。](#modelizing-the-chart)

若要設定活動，請連按兩下其圖示。

顯示的內容在&#x200B;**Page**&#x200B;類型活動中定義。

報表可以包含一或多個頁面。 頁面是透過專用的編輯器建立的，可讓您在樹狀結構中插入輸入欄位、選擇欄位、靜態元素、圖表或表格。 容器可協助您定義版面。 如需詳細資訊，請參閱[元素配置](../../reporting/using/element-layout.md)。

若要將元件新增至頁面，請使用工具列左上方區段中的圖示。

![](assets/reporting_add_component_in_page.png)

您也可以按一下右鍵要添加元件的節點，然後從清單中選擇該元件。

![](assets/s_ncs_advuser_report_wizard_09.png)

>[!CAUTION]
>
>如果報表的匯出目的地是Excel格式，建議不要使用複雜的HTML格式。 有關詳細資訊，請參閱[導出報告](../../reporting/using/actions-on-reports.md#exporting-a-report)。

**[!UICONTROL Page]**&#x200B;可包含下列元素：

* 橫條、圓形、曲線類型&#x200B;**[!UICONTROL charts]**&#x200B;等。
* 樞紐；含群組的清單，或劃分&#x200B;**[!UICONTROL tables]**。
* 文字或數字類型&#x200B;**[!UICONTROL Input controls]**。
* 下拉式清單、核取方塊、選項按鈕、多選項、日期或矩陣類型&#x200B;**[!UICONTROL Selection controls]**。
* 連結編輯器、常數、資料夾選擇類型&#x200B;**[!UICONTROL Advanced controls]**。
* 值、連結、HTML、影像等&#x200B;**[!UICONTROL Static elements]**。
* **[!UICONTROL Containers]** 可讓您控制元件配置。

頁面及其元件的配置模式在[本節](../../web/using/about-web-forms.md)中有詳細說明。

工具列可讓您新增或移除控制項，並在報表頁面中組織其順序。

![](assets/s_ncs_advuser_report_wizard_08.png)

### 靜態元素{#static-elements}

靜態元素可讓您在報表中顯示資訊，例如使用者不會與之互動的圖形元素或指令碼。 如需詳細資訊，請參閱[本節](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)。

![](assets/s_advuser_report_page_activity_03.png)

### 篩選報表{#filtering-information-in-a-report}中的資訊

輸入和選擇控制項可讓您篩選報表中顯示的資訊。 有關實施此類型篩選的詳細資訊，請參閱查詢中的[篩選選項。](../../reporting/using/collecting-data-to-analyze.md#filtering-options-in-the-queries)

要瞭解有關建立和配置輸入欄位和選擇欄位的詳細資訊，請參閱[本節](../../web/using/about-web-forms.md)。

您可將一或多個輸入控制項整合至報表。 此類型的控制項可讓您根據輸入的值來篩選顯示的資訊。

![](assets/reporting_control_text.png)

您也可以將一或多個選擇控制項整合至報表中。 此類型的控制項可讓您根據選取的值，篩選報表中包含的資訊，例如：

* 通過單選按鈕或複選框：

   ![](assets/reporting_radio_buttons.png)

* 透過下拉式清單：

   ![](assets/reporting_control_list.png)

* 透過日曆：

   ![](assets/reporting_control_date.png)

最後，您可將一或多個進階控制項整合至報表中。 此類控制項可讓您插入連結、常數或選取資料夾。

您可以在此處篩選報表中的資料，只顯示樹狀結構其中一個資料夾中所包含的資訊：

![](assets/reporting_control_folder.png)
