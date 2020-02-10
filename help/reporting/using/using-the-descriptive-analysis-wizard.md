---
title: 使用描述性分析精靈
seo-title: 使用描述性分析精靈
description: 使用描述性分析精靈
seo-description: null
page-status-flag: never-activated
uuid: 30554909-4b91-46ff-bd8d-fa57ab6304f9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: analyzing-populations
discoiquuid: 18ba04d9-7bab-4eea-8dbb-6c2c138c5293
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 使用描述性分析精靈{#using-the-descriptive-analysis-wizard}

若要建立描述性分析報表，請使用專用精靈。 配置取決於要分析的資料和所需的渲染。

## 分析資料庫中的資料 {#analyzing-data-in-the-database}

描述性分析精靈可透過功能表啟 **[!UICONTROL Tools > Descriptive analysis]** 動：在此情況下，依預設分析會涉及收件者(**nms:recipient**)。 它會套用至Adobe Campaign資料庫中的所有資料。

![](assets/reporting_descriptive_wz_launch.png)

要分析標準收件者(**nms:recipient**)以外的表，請按一下嚮導最後一個階段的連結，然後選擇與您的設定相匹配的表，在本例中， **[!UICONTROL Advanced settings...]** cus:individual ****:

![](assets/reporting_descriptive_other_schema.png)

如果您想要對部分資料產生統計資料，您可以定義篩選：若要這麼做，請按一下 **[!UICONTROL Advanced settings...]** 連結並定義要套用的篩選，如下所示：

![](assets/reporting_descriptive_wz_filter.png)

這項分析只涉及16歲及以上、住在倫敦的資料庫收件者。

## 分析一組資料 {#analyzing-a-set-of-data}

您可以透過不同的上下文使用描述性分析精靈：清單、工作流程轉換、一或多個傳送、收件者選擇等。

它可透過指向收件者表格的Adobe Campaign樹狀結構的數個節點存取。

選擇項目並按一下右鍵，開啟描述性分析嚮導。 只會分析選取的資料。

![](assets/reporting_descriptive_from_recipients.png)

* 對於一組收件 **者**，請選取要分析的收件者，然後按一下滑鼠右鍵並 **[!UICONTROL Actions > Explore...]**&#x200B;選取，如上所示。 如果篩選器套用至收件者清單，則只會分析其內容。

   要選擇資料夾或當前篩選器中的所有收件人，請使用CTRL+A快速鍵。 這表示即使未顯示的收件者也會被選取。

   有關收件者的說明性分析的示例，請參閱：定 [性資料分析](../../reporting/using/use-cases.md#qualitative-data-analysis)。

* 在工作流程的上 **下文中**，將游標置於指向收件者表的過渡上，按一下右鍵並選擇 **[!UICONTROL Analyze target]**。 有關詳細資訊，請參閱分析工作流中 [的過渡目標中的示例](../../reporting/using/use-cases.md#analyzing-a-transition-target-in-a-workflow)。
* 對於 **清單**，請選擇一個或多個清單，並應用與收件人相同的流程。
* 在傳送內容 **中**，選取您要分析其目標的傳送，按一下滑鼠右鍵並選取 **[!UICONTROL Actions > Explore the target]**，如下所示：

   ![](assets/reporting_descriptive_from_deliveries.png)

   此處提供交貨的說明性分析示例：分 [析人口](../../reporting/using/use-cases.md#analyzing-a-population) ，並在此處：分 [析收件者追蹤記錄](../../reporting/using/use-cases.md#analyzing-recipient-tracking-logs)。

## 設定定性分佈範本 {#configuring-the-qualitative-distribution-template}

范 **[!UICONTROL Qualitative distribution]** 本可讓您建立所有資料類型的統計資料（例如公司名稱、電子郵件網域）。

表格中的顯示資料中詳細說明 **[!UICONTROL Qualitative distribution]** 了可用於透過范 [本建立的報表的設定選項](#displaying-data-in-the-table)。 Analysing a populity（分析人口）中詳 [細介紹了完整示例](../../reporting/using/use-cases.md#analyzing-a-population)。

當您使用描述性分析精靈來分析資料時，可用的選項會視所選的設定而定。 以下是詳細說明。

### 資料系結 {#data-binning}

當您選取要顯示的變數時，可以定義資料系結，換言之，可為選取的資料設定分組准則。

![](assets/s_ncs_user_report_wizard_031.png)

>[!NOTE]
>
>當使用集合計算與計算有關的欄位時，檢查以 **[!UICONTROL The data is already aggregated]** 改進效能。

選項會依欄位內容而有所不同：

* **[!UICONTROL None]** :此選項可讓您顯示變數的所有可用值，毋需建立系結。

   >[!CAUTION]
   >
   >此選項應謹慎使用：它會對報表和機器效能產生重大影響。

* **[!UICONTROL Auto]** :此選項可讓您顯示n個最常代表的值。 這些變數會自動計算，每個變數都代表變數與Bin數目的百分比。 對於數值，Adobe Campaign會自動產生n個類別，以將資料排序。
* **[!UICONTROL Manual]** :此選項的運作方式 **[!UICONTROL Auto]** 與選項類似，但您可以手動設定這些值。 要執行此操作，請單 **[!UICONTROL Add]** 擊值表右側的按鈕。

   Adobe Campaign可在個人化前自動初始化值：若要這麼做，請輸入您要產生的Bin數目，然後按一下連 **[!UICONTROL Initialize with]** 結，如下所示：

   ![](assets/reporting_descriptive_initialize.png)

   然後調整內容以符合您的需求：

   ![](assets/reporting_descriptive_initialize_perso.png)

   根據所需的精確度等級，包含日期的欄位可依時間、日、月、年等分組。

   ![](assets/reporting_descriptive_group_by_year.png)

* **[!UICONTROL Modulo]** :可讓您建立數值群組，以備數值之用。 例如，值為10的模可讓您建立值間隔，其間值會依十變更。

   ![](assets/reporting_descriptive_initialize_modulo.png)

   此範例可讓您檢視依年齡群組劃分的收件者。

   ![](assets/reporting_descriptive_initialize_modulo_result.png)

### 在表格中顯示資料 {#displaying-data-in-the-table}

使用工具列個人化表格中的變數顯示：刪除欄、以行顯示資料而非以欄顯示資料、將欄移至左或右、檢視或變更值計算。

![](assets/s_ncs_user_report_wizard_toolbar.png)

視窗的上方區段可讓您選取顯示設定。

您可以顯示或隱藏統計資料的名稱和子總計，並選擇統計資料的方向。 如需詳細資訊，請參閱「分 [析報表顯示設定」](../../reporting/using/processing-a-report.md#analysis-report-display-settings)。

### 在圖表中顯示資料 {#displaying-data-in-the-chart}

在描述性分析精靈的第一個步驟中，您可以選擇只以圖表形式顯示資料，而不使用表格。 在這種情況下，必須在設定圖形時選取變數。 您必須先選取要顯示的變數數目，並從相關資料庫選取欄位。

![](assets/s_ncs_user_report_wizard_023.png)

然後選取所要的圖表類型。

![](assets/s_ncs_user_report_wizard_024.png)

>[!NOTE]
>
>您可以同時在圖表和表格中顯示變數。 若要這麼做，請在視窗中輸入變 **[!UICONTROL Table configuration]** 數。 按一下 **[!UICONTROL Next]** 並在圖表配置窗口中選擇圖表類型。 如果子維在表格中定義，它們不會顯示在圖表中。

按一下該 **[!UICONTROL Variants]** 連結可修改圖表屬性。

![](assets/reporting_descriptive_graphe_options.png)

提供的選項取決於所選圖表的類型。 For more information, refer to [this page](../../reporting/using/creating-a-chart.md#chart-types-and-variants).

### 統計計算 {#statistics-calculation}

說明性分析精靈可讓您計算數種資料的統計資料類型。 預設情況下，僅配置一個簡單計數。

按一 **[!UICONTROL Add]** 下以建立新的統計資料。

![](assets/reporting_descriptive_create_stat.png)

可進行下列操作：

* **[!UICONTROL Count]** 要計算要聚合的欄位的所有非空值，包括重複值（聚合欄位）,
* **[!UICONTROL Average]** 計算數值域中的平均值，
* **[!UICONTROL Minimum]** 計算數值域中的最小值，
* **[!UICONTROL Maximum]** 計算數值域中的最大值，
* **[!UICONTROL Sum]** 計算數值域中的值總和，
* **[!UICONTROL Standard deviation]** 計算傳回值在平均值附近的分佈，
* **[!UICONTROL Row percentage distribution]** 要計算列中值與行中值的比值（僅適用於表）,
* **[!UICONTROL Column percentage distribution]** 要計算行中值與列中值的比值（僅對表可用）,
* **[!UICONTROL Total percentage distribution]** 計算受訪者的分佈，

   ![](assets/s_ncs_user_report_wizard_026.png)

* **[!UICONTROL Calculated field]** 以建立個人化的運算子（僅適用於表格）。 欄位 **[!UICONTROL User function]** 可讓您輸入要套用至資料的計算。

   範例：根據國家／地區和原產地計算每位客戶的平均購買金額

   ![](assets/report_compute_data_sample1.png)

   若要在表格中顯示上述資訊，您必須建立計算欄位，以儲存每位客戶的平均購買金額。

   操作步驟：

   1. 計算購買總計。

      ![](assets/report_compute_data_sample2.png)

   1. 此統計資料不會顯示在表格中。 您必須取消勾選 **[!UICONTROL Display in the table]** 標籤的選 **[!UICONTROL Advanced]** 項。

      ![](assets/report_compute_data_sample3.png)

   1. 建立新類 **[!UICONTROL Calculated field]** 型統計資訊，並在欄位中輸入以下 **[!UICONTROL User function]** 公式： **@purchases/@count**。

      ![](assets/report_compute_data_sample4.png)

### 顯示報表 {#displaying-the-report}

精靈的最後一個步驟可讓您顯示報表，例如已設定的表格或圖表。

當報表包含表格時，計算結果儲存格會變色。 結果越高，顏色越濃。

![](assets/report_compute_data_sample1.png)

您可以變更結果的版面配置。 若要這麼做，請在相關變數上按一下滑鼠右鍵，然後從快捷功能表選取輸入。

![](assets/s_ncs_user_report_wizard_029.png)

當報表包含圖表時，圖例的標籤可讓您篩選顯示的資訊：按一下標籤以啟用／停用圖表中的顯示。

![](assets/report_display_data_in_graph.png)

## 設定量化散發範本 {#configuring-the-quantitative-distribution-template}

要自行生成描述性分析，請從模板選 **項中選擇「新建描述性分析」(New descriptive analysis from a template** )選項（如果預設情況下未設定）。

可 **[!UICONTROL Quantitative distribution]** 讓您產生可測量或計算之資料的統計資料（例如發票金額、收件者年齡）的範本。

透過範本建立的分析報表的設定模式在實 **[!UICONTROL Quantitative distribution]** 作範例「量化資料分析」中 [有詳細說明](../../reporting/using/use-cases.md#quantitative-data-analysis)。

使用描述性分析精靈建立定量報表時，可用的選項如下所述。

首先，選取計算所關注的變數：

![](assets/s_ncs_user_report_wizard_017.png)

依預設，Adobe Campaign會提供一系列統計資料，供您針對選取的資料進行計算。 您可以變更此清單、新增至清單或視需要刪除統計資料。

可進行下列操作：

* **[!UICONTROL Count]** 要計算要聚合的欄位的所有非空值，包括重複值（聚合欄位）,
* **[!UICONTROL Average]** 計算數值域中的平均值，
* **[!UICONTROL Minimum]** 計算數值域中的最小值，
* **[!UICONTROL Maximum]** ，以計算數值欄位中的值最大值。
* **[!UICONTROL Sum]** 計算數值域中的值總和，
* **[!UICONTROL Standard deviation]** 計算傳回值在平均值周圍的分佈。
* **[!UICONTROL Number of missing values]** 來計算沒有定義值的數字欄位數。
* **[!UICONTROL Decile distribution]** 來分發傳回的值，讓每個值代表數值欄位中值的十分之一。
* **[!UICONTROL Custom distribution]** 以根據使用者定義的臨界值來分發傳回的值。

   此按 **[!UICONTROL Detail...]** 鈕可讓您編輯統計資料，並視需要個人化其計算或顯示：

   ![](assets/s_ncs_user_report_wizard_030.png)

   精靈的最後一個步驟會顯示量化分析報表。

   ![](assets/reporting_descriptive_view_report.png)

   若要變更報表，請參閱「處 [理報表」](../../reporting/using/processing-a-report.md)。

