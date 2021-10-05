---
product: campaign
title: 表單轉譯
description: 表單轉譯
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 723a6c47-5323-4914-a014-58be493852cc
source-git-commit: 9b914099f6755d6ae83f98697a3a38f8cfa625e1
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 2%

---

# 表單轉譯{#form-rendering}

![](../../assets/common.svg)

## 選取表單呈現範本 {#selecting-the-form-rendering-template}

表單設定可讓您選取用來產生頁面的範本。 要訪問它們，請按一下表單詳細資訊工具欄中的&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕，然後選擇&#x200B;**[!UICONTROL Rendering]**&#x200B;頁簽。 預設提供許多範本（樣式表）。

![](assets/s_ncs_admin_survey_rendering_select.png)

編輯器的底部區域可讓您檢視所選範本的呈現。

縮放功能可讓您編輯選取的範本。

![](assets/s_ncs_admin_survey_render_edit.png)

您可以修改或覆寫這些範本。 要執行此操作，請按一下&#x200B;**[!UICONTROL Page layout...]**&#x200B;連結並個人化資訊。

![](assets/s_ncs_admin_survey_render_edit_param.png)

您可以：

* 更改用作徽標的影像並調整其大小，
* 還指定當用戶選擇此呈現模板時訪問預覽影像的路徑。

**[!UICONTROL Headers/Footers]**&#x200B;標籤可讓您使用此範本變更每個表單頁面的頁首和頁尾中顯示的資訊。

![](assets/s_ncs_admin_survey_render_edit_header.png)

**[!UICONTROL Page headers]**&#x200B;和&#x200B;**[!UICONTROL Page footers]**&#x200B;區段的每一行都對應於HTML頁面中的一行。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以建立新行。

選取現有行，然後按一下&#x200B;**[!UICONTROL Detail]**&#x200B;按鈕加以個人化。

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

您可以透過相關標籤變更行的內容、新增邊框，以及變更字型屬性。 按一下&#x200B;**[!UICONTROL OK]**&#x200B;確認這些變更。

**[!UICONTROL Position]**&#x200B;欄位可讓您定義元素在頁首和頁尾中的位置。

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>呈現模板儲存在&#x200B;**[!UICONTROL Administration > Configuration > Form rendering]**&#x200B;節點中。\
>如需詳細資訊，請參閱[自訂表單呈現](#customizing-form-rendering)

## 自訂表單轉譯 {#customizing-form-rendering}

### 變更元素的版面 {#changing-the-layout-of-elements}

您可以過載表單中每個元素的樣式表（輸入欄位、影像、選項按鈕等）。

要執行此操作，請使用&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤。

![](assets/s_ncs_admin_survey_advanced_tab.png)

它可讓您定義下列屬性：

* **[!UICONTROL Label position]**:請 [參閱定義標籤的位置](defining-web-forms-layout.md#defining-the-position-of-labels),
* **[!UICONTROL Label format]**:換字或換字，
* **[!UICONTROL Number of cells]** :請參 [閱定位頁面上的欄位](defining-web-forms-layout.md#positioning-the-fields-on-the-page),
* **[!UICONTROL Horizontal alignment]** （左、右、中） **[!UICONTROL Vertical alignment]** 和（高、低、中）,
* **[!UICONTROL Width]** 區域：這可以以百分比表示，或以ems、點或像素（預設值）表示，
* 最大&#x200B;**[!UICONTROL Length]**:允許的字元數上限（對於文本、數字和密碼類型控制項）,
* **[!UICONTROL Lines]**:類型區域的行 **[!UICONTROL Multi-line text]** 數，
* **[!UICONTROL Style inline]**:可讓您使用其他設定來過載CSS樣式表。這些字元會使用&#x200B;**;**&#x200B;字元加以區隔，如下列範例所示：

   ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### 定義頁首和頁尾 {#defining-headers-and-footers}

欄位在樹結構中排序，樹結構的根與頁同名。 選取它以修改名稱。

窗口的標題必須在表單屬性窗口的&#x200B;**[!UICONTROL Page]**&#x200B;頁簽中輸入。 您也可以將設定的內容新增至頁首與頁尾（此資訊會顯示在每個頁面上）。 在&#x200B;**[!UICONTROL Texts]**&#x200B;標籤的相符區段中輸入此內容，如下所示：

![](assets/s_ncs_admin_survey_titles_config.png)

### 新增元素至HTML標題 {#adding-elements-to-html-header}

您可以輸入要插入表單頁面HTML標題的其他元素。 要執行此操作，請在相關頁面的&#x200B;**[!UICONTROL Header]**&#x200B;標籤中輸入元素。

例如，這可讓您參照將顯示在頁面標題列中的圖示。

![](assets/webform_header_page_tab.png)

## 定義控制設定 {#defining-control-settings}

當使用者填入表單時，會根據其格式或設定，對特定欄位自動執行檢查。 這可讓您將某些欄位設為必填欄位（請參閱[定義必填欄位](#defining-mandatory-fields)），或檢查輸入資料的格式（請參閱[檢查資料格式](#checking-data-format)）。 在頁面核准期間會執行檢查（透過按一下可啟用輸出轉變的連結或按鈕）。

### 定義必填欄位 {#defining-mandatory-fields}

若要將某些欄位設為必填欄位，請在建立欄位時選取此選項。

![](assets/s_ncs_admin_survey_required_field.png)

如果使用者未輸入欄位即核准此頁面，則會顯示下列訊息：

![](assets/s_ncs_admin_survey_required_default_msg.png)

您可以按一下&#x200B;**[!UICONTROL Personalize this message]**&#x200B;連結，以個人化此訊息。

![](assets/s_ncs_admin_survey_required_custom_msg.png)

如果使用者未輸入欄位即核准此頁面，則會顯示下列訊息：

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### 檢查資料格式 {#checking-data-format}

對於將其值儲存在資料庫的現有欄位中的表單檢查，將應用儲存欄位的規則。

對於其值儲存在變數中的表單檢查，核准規則取決於變數的格式。

例如，如果您建立&#x200B;**[!UICONTROL Number]**&#x200B;檢查來儲存用戶端號碼，如下所示：

![](assets/s_ncs_admin_survey_choose_format.png)

使用者必須在表單欄位中輸入整數。

## 定義欄位條件式顯示 {#defining-fields-conditional-display}

您可以根據使用者選擇的值，設定要顯示之頁面上的欄位顯示。 這可套用至一個欄位或一組欄位（當這些欄位在容器中分組時）。

對於頁面的每個元素， **[!UICONTROL Visibility]**&#x200B;區段可讓您定義顯示條件。

![](assets/s_ncs_admin_survey_condition_edit.png)

條件可能與資料庫欄位或變數的值有關。

在欄位選取視窗中，您可以從下列資料中選擇：

![](assets/s_ncs_admin_survey_condition_select.png)

* 主樹包含窗體上下文的參數。 預設參數為Identifier（與收件者的加密識別碼相符）、Language（語言）和Origin（原始）。

   如需關於此項目的詳細資訊，請參閱此[頁面](defining-web-forms-properties.md#form-url-parameters)。

* **[!UICONTROL Recipients]**&#x200B;子樹包含插入表單並儲存在資料庫中的輸入欄位。

   有關詳細資訊，請參閱[將資料儲存在資料庫](web-forms-answers.md#storing-data-in-the-database)。

* **[!UICONTROL Variables]**&#x200B;子樹包含此表單的可用變數。 有關詳細資訊，請參閱[將資料儲存在本地變數](web-forms-answers.md#storing-data-in-a-local-variable)。

如需詳細資訊，請參閱以下提供的使用案例：[根據所選值](use-cases--web-forms.md#displaying-different-options-depending-on-the-selected-values)顯示不同的選項。

您也可以使用&#x200B;**[!UICONTROL Test]**&#x200B;物件來限制表單頁面的顯示。 如需關於此項目的詳細資訊，請參閱此[頁面](defining-web-forms-page-sequencing.md#conditional-page-display)。

## 從現有表單匯入元素 {#importing-elements-from-an-existing-form}

可從其他網路表單匯入欄位或容器。 這可讓您建立可重複使用區塊的程式庫，這些區塊會插入表單中，例如位址區塊、電子報訂閱區域等。

若要將元素匯入表單，請套用下列步驟：

1. 編輯要插入一個或多個元素的頁面，然後按一下工具列中的&#x200B;**[!UICONTROL Import an existing block]**。

   ![](assets/s_ncs_admin_survey_import_block.png)

1. 選擇包含要導入的欄位的Web表單，並選擇要導入的容器和欄位。

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >源表單名稱右側的&#x200B;**[!UICONTROL Edit link]**&#x200B;表徵圖允許您查看選定的Web表單。

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以確認插入。

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)
