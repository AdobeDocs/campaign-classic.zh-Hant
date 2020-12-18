---
solution: Campaign Classic
product: campaign
title: 表單轉譯
description: 表單轉譯
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 2%

---


# 表單轉譯{#form-rendering}

## 選擇表單轉換模板{#selecting-the-form-rendering-template}

表單設定可讓您選取用來產生頁面的範本。 要訪問它們，請按一下表單詳細資訊工具欄中的&#x200B;**[!UICONTROL Settings]**&#x200B;按鈕，然後選擇&#x200B;**[!UICONTROL Rendering]**&#x200B;頁籤。 預設有許多範本（樣式表）可供使用。

![](assets/s_ncs_admin_survey_rendering_select.png)

編輯器的底部部分允許您查看所選模板的渲染。

縮放功能可讓您編輯選取的範本。

![](assets/s_ncs_admin_survey_render_edit.png)

您可以修改或覆寫這些範本。 要執行此操作，請按一下&#x200B;**[!UICONTROL Page layout...]**&#x200B;連結並個性化資訊。

![](assets/s_ncs_admin_survey_render_edit_param.png)

您可以：

* 變更用作標誌的影像並調整其大小，
* 此外，指定當使用者選取此轉換範本時，存取預覽影像的路徑。

**[!UICONTROL Headers/Footers]**&#x200B;標籤可讓您使用此範本變更每個表單頁面的頁首和頁尾中顯示的資訊。

![](assets/s_ncs_admin_survey_render_edit_header.png)

**[!UICONTROL Page headers]**&#x200B;和&#x200B;**[!UICONTROL Page footers]**&#x200B;區段的每一行都對應於HTML頁面中的一行。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以建立新行。

選擇現有行，然後按一下&#x200B;**[!UICONTROL Detail]**&#x200B;按鈕對其進行個性化。

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

您可以透過相關標籤來變更行的內容、新增邊框和字型屬性。 按一下&#x200B;**[!UICONTROL OK]**&#x200B;確認這些更改。

**[!UICONTROL Position]**&#x200B;欄位可讓您定義元素在頁首和頁尾中的位置。

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>渲染模板儲存在&#x200B;**[!UICONTROL Administration > Configuration > Form rendering]**&#x200B;節點中。\
>有關詳細資訊，請參閱[自定義表單轉換](#customizing-form-rendering)

## 自訂表單演算{#customizing-form-rendering}

### 變更元素{#changing-the-layout-of-elements}的版面配置

您可以過載表單中每個元素的樣式表（輸入欄位、影像、選項按鈕等）。

若要這麼做，請使用&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤。

![](assets/s_ncs_admin_survey_advanced_tab.png)

它可讓您定義下列屬性：

* **[!UICONTROL Label position]**:請參 [閱定義標籤的位置](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels),
* **[!UICONTROL Label format]**:換行或不換行，
* **[!UICONTROL Number of cells]** :請 [參閱定位頁面上的欄位](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page),
* **[!UICONTROL Horizontal alignment]** （左、右、居中） **[!UICONTROL Vertical alignment]** 和（高、低、中）,
* **[!UICONTROL Width]** 區域：這可以表示為百分比或EMS、點或像素（預設值）,
* 最大&#x200B;**[!UICONTROL Length]**:允許的字元數上限（適用於文字、數字和密碼類型控制）,
* **[!UICONTROL Lines]**:類型區域的行 **[!UICONTROL Multi-line text]** 數、
* **[!UICONTROL Style inline]**:可讓您使用其他設定，讓CSS樣式表過載。這些字元使用&#x200B;**;**&#x200B;字元分隔，如下例所示：

   ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### 定義頁首和頁尾{#defining-headers-and-footers}

在樹結構中對欄位進行排序，樹結構的根與頁同名。 選擇它可修改名稱。

窗口的標題必須輸入到表單屬性窗口的&#x200B;**[!UICONTROL Page]**&#x200B;頁籤中。 您也可以新增設定內容至頁首和頁尾（此資訊會顯示在每個頁面）。 在&#x200B;**[!UICONTROL Texts]**&#x200B;標籤的匹配部分中輸入此內容，如下所示：

![](assets/s_ncs_admin_survey_titles_config.png)

### 新增元素至HTML標題{#adding-elements-to-html-header}

您可以輸入要插入表單頁面HTML頁首的其他元素。 若要這麼做，請在相關頁面的&#x200B;**[!UICONTROL Header]**&#x200B;標籤中輸入元素。

例如，這可讓您參考將顯示在頁面標題列中的圖示。

![](assets/webform_header_page_tab.png)

## 定義控制設定{#defining-control-settings}

當使用者填入表單時，會根據特定欄位的格式或設定，自動對其執行檢查。 這可讓您將某些欄位設為必填（請參閱[定義必填欄位](#defining-mandatory-fields)）或檢查輸入資料的格式（請參閱[檢查資料格式](#checking-data-format)）。 檢查會在頁面核准期間執行（透過按一下啟用輸出轉換的連結或按鈕）。

### 定義必填欄位{#defining-mandatory-fields}

若要將某些欄位設為必填，請在建立欄位時選取此選項。

![](assets/s_ncs_admin_survey_required_field.png)

如果使用者未輸入欄位即核准此頁面，則會顯示下列訊息：

![](assets/s_ncs_admin_survey_required_default_msg.png)

您可以按一下&#x200B;**[!UICONTROL Personalize this message]**&#x200B;連結，將此訊息個人化。

![](assets/s_ncs_admin_survey_required_custom_msg.png)

如果使用者未輸入欄位即核准此頁面，則會顯示下列訊息：

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### 正在檢查資料格式{#checking-data-format}

對於將其值儲存在資料庫現有欄位中的表單檢查，將應用儲存欄位的規則。

對於將值儲存在變數中的表單檢查，核准規則取決於變數的格式。

例如，如果您建立&#x200B;**[!UICONTROL Number]**&#x200B;檢查以儲存客戶機號，如下所示：

![](assets/s_ncs_admin_survey_choose_format.png)

用戶必須在表單欄位中輸入整數。

## 定義欄位條件顯示{#defining-fields-conditional-display}

您可以根據使用者選擇的值，設定要顯示之頁面上欄位的顯示。 這可套用至一個欄位或一組欄位（當欄位在容器中分組時）。

對於頁面的每個元素，**[!UICONTROL Visibility]**&#x200B;區段可讓您定義顯示條件。

![](assets/s_ncs_admin_survey_condition_edit.png)

條件可以涉及資料庫欄位或變數的值。

在欄位選擇視窗中，您可以從下列資料中選擇：

![](assets/s_ncs_admin_survey_condition_select.png)

* 主樹包含表單上下文的參數。 預設參數為「識別碼」（與收件者的加密識別碼相符）、「語言」和「來源」。

   如需關於此項目的詳細資訊，請參閱此[頁面](../../web/using/defining-web-forms-properties.md#form-url-parameters)。

* **[!UICONTROL Recipients]**&#x200B;子樹包含插入到表單中並儲存在資料庫中的輸入欄位。

   有關詳細資訊，請參閱[將資料儲存在資料庫中](../../web/using/web-forms-answers.md#storing-data-in-the-database)。

* **[!UICONTROL Variables]**&#x200B;子樹包含此表單的可用變數。 有關詳細資訊，請參閱[將資料儲存在本地變數](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable)中。

有關此功能的詳細資訊，請參閱此處提供的使用案例：[根據所選值顯示不同的選項](../../web/using/use-cases--web-forms.md#displaying-different-options-depending-on-the-selected-values)。

您也可以使用&#x200B;**[!UICONTROL Test]**&#x200B;物件來限制表單頁面的顯示。 如需關於此項目的詳細資訊，請參閱此[頁面](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display)。

## 從現有表單{#importing-elements-from-an-existing-form}匯入元素

您可從其他Web表單匯入欄位或容器。 這可讓您建立可重複使用的區塊庫，這些區塊將插入表單中，例如地址區塊、電子報訂閱區域等。

若要將元素匯入表單，請套用下列步驟：

1. 編輯要插入一個或多個元素的頁面，然後按一下工具欄中的&#x200B;**[!UICONTROL Import an existing block]**。

   ![](assets/s_ncs_admin_survey_import_block.png)

1. 選擇包含要導入的欄位的Web表單，然後選擇要導入的容器和欄位。

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >源表單名稱右側的&#x200B;**[!UICONTROL Edit link]**&#x200B;表徵圖允許您查看選定的Web表單。

1. 按一下&#x200B;**[!UICONTROL Ok]**&#x200B;確認插入。

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)

