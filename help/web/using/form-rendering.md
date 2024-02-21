---
product: campaign
title: 表單轉譯
description: 表單轉譯
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Web Forms
exl-id: 723a6c47-5323-4914-a014-58be493852cc
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 2%

---

# 表單轉譯{#form-rendering}



## 選取表單轉譯範本 {#selecting-the-form-rendering-template}

表單設定可讓您選取用來產生頁面的範本。 若要存取縮圖，請按一下 **[!UICONTROL Properties]** 按鈕，然後選取 **[!UICONTROL Rendering]** 標籤。 預設有許多範本（樣式表）可供使用。

![](assets/s_ncs_admin_survey_rendering_select.png)

編輯器的底部區段可讓您檢視所選範本的轉譯。

縮放功能可讓您編輯選取的範本。

![](assets/s_ncs_admin_survey_render_edit.png)

您可以修改或覆寫這些範本。 若要這麼做，請按一下 **[!UICONTROL Page layout...]** 連結並個人化資訊。

![](assets/s_ncs_admin_survey_render_edit_param.png)

您可以：

* 變更用作標誌的影像，並調整其大小，
* 同時指定當使用者選取此演算範本時，存取預覽影像的路徑。

此 **[!UICONTROL Headers/Footers]** tab可讓您使用此範本變更每個表單頁面頁首與頁尾中顯示的資訊。

![](assets/s_ncs_admin_survey_render_edit_header.png)

每行 **[!UICONTROL Page headers]** 和 **[!UICONTROL Page footers]** 區段會對應至HTML頁面中的一行。 按一下 **[!UICONTROL Add]** 以建立新行。

選取現有行，然後按一下 **[!UICONTROL Detail]** 按鈕來進行個人化。

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

您可以透過相關標籤變更線條內容、新增框線以及變更字型屬性。 按一下 **[!UICONTROL OK]** 以確認這些變更。

此 **[!UICONTROL Position]** 欄位可讓您定義頁首和頁尾中的元素位置。

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>演算範本儲存在 **[!UICONTROL Administration > Configuration > Form rendering]** 節點。\
>有關詳細資訊，請參閱 [自訂表單轉譯](#customizing-form-rendering)

## 自訂表單轉譯 {#customizing-form-rendering}

### 變更元素版面 {#changing-the-layout-of-elements}

您可以多載表單每個元素（輸入欄位、影像、選項按鈕等）的樣式表。

若要這麼做，請使用 **[!UICONTROL Advanced]** 標籤。

![](assets/s_ncs_admin_survey_advanced_tab.png)

它可讓您定義下列屬性：

* **[!UICONTROL Label position]**：請參閱 [定義標籤位置](defining-web-forms-layout.md#defining-the-position-of-labels)，
* **[!UICONTROL Label format]**：自動換行或不自動換行，
* **[!UICONTROL Number of cells]** ：請參閱 [定位頁面上的欄位](defining-web-forms-layout.md#positioning-the-fields-on-the-page)，
* **[!UICONTROL Horizontal alignment]** （左、右、置中）和 **[!UICONTROL Vertical alignment]** （高、低、中）、
* **[!UICONTROL Width]** 區域的：這可以用百分比或以ems、點或畫素（預設值）表示，
* 最大值 **[!UICONTROL Length]**：允許的字元數上限（適用於文字、數字和密碼型別控制項），
* **[!UICONTROL Lines]**：的行數 **[!UICONTROL Multi-line text]** 文字區域，
* **[!UICONTROL Style inline]**：可讓您使用其他設定多載CSS樣式表。 這些區段使用分隔 **；** 個字元，如下列範例所示：

  ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### 定義頁首和頁尾 {#defining-headers-and-footers}

欄位會以樹狀結構排序，其根目錄與頁面同名。 選取它以修改名稱。

視窗的標題必須輸入於 **[!UICONTROL Page]** 表單屬性視窗的索引標籤。 您也可以新增一組內容至頁首與頁尾（此資訊會顯示在每個頁面上）。 此內容輸入在的相符區段中 **[!UICONTROL Texts]** 標籤，如下所示：

![](assets/s_ncs_admin_survey_titles_config.png)

### 將元素新增至HTML標題 {#adding-elements-to-html-header}

您可以輸入要插入表單頁面HTML標頭中的其他元素。 要執行此操作，請在 **[!UICONTROL Header]** 頁簽的頁簽。

例如，這可讓您參照將顯示在頁面標題列中的圖示。

![](assets/webform_header_page_tab.png)

## 定義控制設定 {#defining-control-settings}

當使用者填寫表單時，將會根據其格式或設定自動對特定欄位執行檢查。 這可讓您將某些欄位設為必填欄位(請參閱 [定義必填欄位](#defining-mandatory-fields))或檢查所輸入資料的格式(請參閱 [檢查資料格式](#checking-data-format))。 在頁面核准期間會執行檢查（按一下可啟用輸出轉換的連結或按鈕）。

### 定義必填欄位 {#defining-mandatory-fields}

若要將某些欄位設為必要欄位，請在建立欄位時選取此選項。

![](assets/s_ncs_admin_survey_required_field.png)

如果使用者未輸入欄位即核准此頁面，將會顯示下列訊息：

![](assets/s_ncs_admin_survey_required_default_msg.png)

您可以按一下 **[!UICONTROL Personalize this message]** 連結。

![](assets/s_ncs_admin_survey_required_custom_msg.png)

如果使用者未輸入欄位即核准此頁面，將會顯示下列訊息：

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### 檢查資料格式 {#checking-data-format}

對於其值儲存在資料庫現有欄位中的表單檢查，將會套用儲存欄位的規則。

對於其值儲存在變數中的表單檢查，核准規則取決於變數的格式。

例如，如果您建立 **[!UICONTROL Number]** 勾選以儲存使用者端號碼，如下所示：

![](assets/s_ncs_admin_survey_choose_format.png)

使用者必須在表單欄位中輸入整數。

## 定義欄位條件式顯示 {#defining-fields-conditional-display}

您可以根據使用者選擇的值，設定要在頁面上顯示的欄位顯示。 這適用於一個欄位或一組欄位（當它們分組在容器中時）。

對於頁面的每個元素， **[!UICONTROL Visibility]** 區段可讓您定義顯示條件。

![](assets/s_ncs_admin_survey_condition_edit.png)

條件可能涉及資料庫欄位或變數的值。

在欄位選取視窗中，您可以從下列資料中選擇：

![](assets/s_ncs_admin_survey_condition_select.png)

* 主樹狀結構包含表單內容的引數。 預設引數為識別碼（符合收件者的加密識別碼）、語言和來源。

  如需關於此項目的詳細資訊，請參閱此[頁面](defining-web-forms-properties.md#form-url-parameters)。

* 此 **[!UICONTROL Recipients]** 子樹狀結構包含插入表單並儲存在資料庫中的輸入欄位。

  有關詳細資訊，請參閱 [將資料儲存在資料庫中](web-forms-answers.md#storing-data-in-the-database).

* 此 **[!UICONTROL Variables]** 子樹狀結構包含此表單可用的變數。 有關詳細資訊，請參閱 [將資料儲存在區域變數中](web-forms-answers.md#storing-data-in-a-local-variable).

如需詳細資訊，請參閱此處提供的使用案例： [根據選取的值顯示不同的選項](use-cases-web-forms.md#displaying-different-options-depending-on-the-selected-values).

您也可以使用設定表格頁面顯示的條件 **[!UICONTROL Test]** 物件。 如需關於此項目的詳細資訊，請參閱此[頁面](defining-web-forms-page-sequencing.md#conditional-page-display)。

## 從現有表單匯入元素 {#importing-elements-from-an-existing-form}

您可以從其他網路表單匯入欄位或容器。 這可讓您建立可重複使用的區塊資料庫，這些區塊會插入至表單中，例如位址區塊、電子報訂閱區域等。

若要將元素匯入表單，請套用下列步驟：

1. 編輯您要插入一或多個元素的頁面，然後按一下 **[!UICONTROL Import an existing block]** （在工具列中）。

   ![](assets/s_ncs_admin_survey_import_block.png)

1. 選取包含要匯入欄位的Web表單，然後選擇要匯入的容器和欄位。

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >此 **[!UICONTROL Edit link]** 來源表單名稱右邊的圖示可讓您檢視選取的網頁表單。

1. 按一下 **[!UICONTROL Ok]** 以確認插入。

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)
