---
solution: Campaign Classic
product: campaign
title: 新增欄位至網路表單
description: 新增欄位至網路表單
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '2457'
ht-degree: 1%

---


# 新增欄位至網路表單{#adding-fields-to-a-web-form}

在Web表單中，欄位可讓使用者輸入資訊並選取選項。 Web表格可提供輸入欄位、選擇欄位、靜態和進階內容（擷取、訂閱等）。

當您使用精靈來新增欄位時，會根據選取的欄位或儲存變數自動偵測欄位類型。 您可以使用&#x200B;**[!UICONTROL General]**&#x200B;標籤中的&#x200B;**[!UICONTROL Type]**&#x200B;下拉式方塊來編輯它。

![](assets/s_ncs_admin_webform_change_type.png)

使用工具列中的按鈕時，選擇要添加的欄位類型。

可用欄位類型如下：

* 文字／數字輸入。 請參閱[添加輸入欄位](#adding-input-fields)。
* 下拉式清單選擇。 請參閱[新增下拉式清單](#adding-drop-down-lists)。
* 透過核取方塊進行多選。 請參閱[添加複選框](#adding-checkboxes)。
* 透過選項按鈕的獨家選擇。 請參閱[添加單選按鈕](#adding-radio-buttons)。
* 以選項格線投票。 請參閱[添加網格](#adding-grids)。
* 數字和日期。 請參閱[新增日期和數字](#adding-dates-and-numbers)。
* 訂閱／取消訂閱資訊服務。 請參閱[訂閱核取方塊](#subscription-checkboxes)。
* 驗證碼。 請參閱[插入captcha](#inserting-a-captcha)。
* 下載按鈕。 [上傳檔案](#uploading-a-file)。
* 隱藏常數。 請參閱[插入隱藏常數](#inserting-a-hidden-constant)。

請指定響應儲存模式：更新資料庫中的欄位（僅儲儲存存最後儲存的值）或儲存在變數中（不儲存答案）。 有關詳細資訊，請參閱[響應儲存欄位](../../web/using/web-forms-answers.md#response-storage-fields)。

>[!NOTE]
>
>預設情況下，欄位將插入當前樹的底部。 使用工具列中的箭頭，將其上移或下移。

## 欄位建立嚮導{#field-creation-wizard}

對於表單的每個頁面，您可以透過工具列中的第一個按鈕新增欄位。 若要這麼做，請前往&#x200B;**[!UICONTROL Add using the wizard]**&#x200B;功能表。

![](assets/s_ncs_admin_survey_add_field_menu.png)

選擇要建立的欄位類型：您可以選擇在資料庫中新增欄位、變數，或匯入以其他表單建立並在容器中收集的欄位群組。

按一下&#x200B;**[!UICONTROL Next]**&#x200B;並選取儲存欄位或變數，或您要匯入的容器。

![](assets/s_ncs_admin_webform_wz_confirm_db.png)

按一下&#x200B;**[!UICONTROL Finish]**&#x200B;將選取的欄位插入頁面。

![](assets/s_ncs_admin_webform_wz_insert_field.png)

## 添加輸入欄位{#adding-input-fields}

若要新增輸入欄位，請按一下&#x200B;**[!UICONTROL Input control]**&#x200B;按鈕，然後選擇要新增的欄位類型。

![](assets/s_ncs_admin_webform_select_field.png)

### 輸入欄位類型{#types-of-input-fields}

可將五種不同類型的文本欄位插入到表單頁中：

* **文字**:可讓使用者在一行上輸入文字。

   ![](assets/s_ncs_admin_survey_txt_ex.png)

* **數字**:可讓使用者在一行中輸入數字。有關詳細資訊，請參閱[添加數字](#adding-numbers)。

   當頁面獲得核準時，會檢查欄位內容，以確定輸入的值與欄位相容。 有關詳細資訊，請參閱[定義控制設定](../../web/using/form-rendering.md#defining-control-settings)。

* **密碼**:可讓使用者在單行輸入文字。在輸入文字期間，字元會由句點取代：

   ![](assets/s_ncs_admin_survey_passwd_ex.png)

   >[!CAUTION]
   >
   >口令儲存在資料庫中未加密。

* **多行文字**:可讓使用者在數行上輸入文字。

   ![](assets/s_ncs_admin_survey_txtmulti_ex.png)

   >[!CAUTION]
   >
   >多行文字欄位是可包含歸位的特定欄位。 其儲存空間必須與映射到XML元素上的欄位相關聯，而不是與XML屬性相關聯。 有關方案中資料類型的詳細資訊，請參閱[本部分](../../configuration/using/about-schema-reference.md)中的「方案參考」一章。
   >   
   >如果您使用&#x200B;**Survey**&#x200B;模組，您可以將此類型的欄位儲存在封存的欄位中，並自動調整格式。 如需詳細資訊，請參閱[本章節](../../web/using/about-surveys.md)。

* **豐富的多行文字**:可讓使用者輸入包含版面的文字，而版面將儲存為HTML格式。

   ![](assets/s_ncs_admin_survey_txthtmli_ex.png)

   您可以選取提供給使用者的編輯器類型。 若要這麼做，請使用&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤中&#x200B;**[!UICONTROL HTML editor]**&#x200B;欄位的下拉式方塊。

   ![](assets/webapp_enrich_text_type.png)

   顯示的圖示數視編輯器類型而定。 對於&#x200B;**[!UICONTROL Advanced]**&#x200B;編輯器，演算方式如下：

   ![](assets/webapp_enrich_text_max.png)

### 配置輸入欄位{#configure-input-fields}

輸入欄位都是使用下列選項，根據相同的模式進行設定：

![](assets/s_ncs_admin_survey_txt_param.png)

**[!UICONTROL General]**&#x200B;標籤可讓您輸入欄位名稱，並視需要為其指定預設值。

應答儲存模式可通過&#x200B;**[!UICONTROL Edit storage...]**&#x200B;鏈路更改。 值可以儲存在資料庫的現有欄位中；或者，您可以選擇不將資訊保存在資料庫中（使用本地變數）。

>[!NOTE]
>
>儲存模式在[響應儲存欄位](../../web/using/web-forms-answers.md#response-storage-fields)中有詳細說明

**[!UICONTROL Advanced]**&#x200B;標籤可讓您定義欄位的顯示參數（標籤位置、對齊方式等）。 請參閱[定義Web表單佈局](../../web/using/defining-web-forms-layout.md)。

## 添加下拉清單{#adding-drop-down-lists}

您可以將下拉式清單插入調查頁面。 這可讓使用者從下拉式選單中的選件中選取值。

![](assets/s_ncs_admin_survey_dropdown_sample.png)

若要將下拉式方塊新增至表單頁面，請按一下頁面編輯器工具列中的&#x200B;**[!UICONTROL Selection controls > Drop-down list]**&#x200B;按鈕。

![](assets/s_ncs_admin_survey_create_dropdown.png)

選擇答案儲存模式並確認您的選擇。

在&#x200B;**[!UICONTROL General]**&#x200B;標籤的下部定義清單的標籤和值。 如果資訊儲存在資料庫的現有欄位中，並且是枚舉欄位，則可以通過按一下&#x200B;**[!UICONTROL Initialize the list of values from the database]**&#x200B;自動填寫值，如下所示：

![](assets/s_ncs_admin_survey_database_values.png)

>[!NOTE]
>
>使用值清單右側的箭頭來變更其順序。

如果資料儲存在連結的表格中，您可以選取儲存清單中建議值的欄位。 例如，如果您選取國家／地區表，請按一下&#x200B;**[!UICONTROL Initialize the list of values from the database...]**&#x200B;並選取所要的欄位。

![](assets/s_ncs_admin_survey_preload_values.png)

接著，按一下&#x200B;**[!UICONTROL Load]**&#x200B;連結以擷取值：

![](assets/s_ncs_admin_survey_load_button.png)

>[!CAUTION]
>
>每當更新清單以重新整理選件的值時，請重複此作業。

## 添加複選框{#adding-checkboxes}

為使用者選取選項，您需要使用核取方塊。

![](assets/s_ncs_admin_survey_check_box.png)

若要將核取方塊新增至表格，請按一下頁面編輯器工具列中的&#x200B;**[!UICONTROL Selection controls > Checkbox...]**&#x200B;圖示。

選擇答案儲存模式並確認您的選擇。

在&#x200B;**[!UICONTROL General]**&#x200B;標籤的&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入方塊標籤。

![](assets/s_ncs_admin_survey_check_box_edit.png)

複選框允許您根據是否選中該框為儲存欄位（或值）指定值。 **[!UICONTROL Values]**&#x200B;區段可讓您在勾選方塊時輸入要指派的值（在&#x200B;**[!UICONTROL Value]**&#x200B;欄位中），在未勾選時輸入要指派的值（在&#x200B;**[!UICONTROL Empty value]**&#x200B;欄位中）。 這些值取決於資料儲存格式。

如果儲存欄位（或變數）是布爾型的，則如果未選中該框，將自動推斷要分配的值。 在此情況下，僅提供&#x200B;**[!UICONTROL Value if checked]**&#x200B;欄位，如下所示：

![](assets/s_ncs_admin_survey_check_box_enum.png)

## 範例：如果勾選了方塊，請為欄位指定值{#example--assign-a-value-to-a-field-if-a-box-is-checked}

我們希望在表單中插入核取方塊以傳送維護要求，如下所示：

![](assets/s_ncs_admin_survey_check_box_ex.png)

這些資訊將上傳至資料庫，並傳送至現有欄位（在此例中為&#x200B;**[!UICONTROL Comment]**&#x200B;欄位）:

![](assets/s_ncs_admin_survey_check_box_ex_list.png)

如果選中「Maintenance required（需要維護）」框， **[!UICONTROL Comment]**&#x200B;列將包含「Maintenance required（需要維護）」。 如果未勾選此方塊，則欄會顯示「Maintenance not required」（不需要維護）。 要獲得此結果，請將以下配置應用於表單頁上的複選框：

![](assets/s_ncs_admin_survey_check_box_ex_edit.png)

## 添加單選按鈕{#adding-radio-buttons}

選項按鈕可讓您為使用者提供一系列可供選擇的專屬選項。 這是相同欄位的不同值。

![](assets/s_ncs_admin_survey_radio_button.png)

您可以個別建立選項按鈕（單一按鈕）或透過多選項清單，但是由於選項按鈕的要點是選取一或多個選項，因此我們一律會建立至少一對選項按鈕，而不只是單一按鈕。

>[!CAUTION]
>
>若要強制選擇，您必須建立多選項清單。

### 新增單一按鈕{#add-single-buttons}

要向表單頁添加單選按鈕，請轉至頁面編輯器工具欄中的&#x200B;**[!UICONTROL Selection controls > Radio button]**&#x200B;菜單，然後選擇儲存模式。

![](assets/s_ncs_admin_survey_radio_button_sample.png)

單選按鈕的配置方式與複選框類似（請參閱[添加複選框](#adding-checkboxes)）。 不過，如果未選取選項，則不會指派任何值。 為了使多個按鈕相互依存，例如，選擇一個按鈕會自動取消選擇其他按鈕，這些按鈕必須儲存在同一欄位中。 如果這些變數未儲存在資料庫中，則必須使用相同的本機變數進行暫存。 請參閱[響應儲存欄位](../../web/using/web-forms-answers.md#response-storage-fields)。

### 新增按鈕清單{#add-a-list-of-buttons}

若要透過清單新增選項按鈕，請前往頁面編輯器工具列中的&#x200B;**[!UICONTROL Selection controls>Multiple choice]**&#x200B;選單。

![](assets/s_ncs_admin_survey_radio_button_sample2.png)

新增標籤數目的選項按鈕。 此功能的優點是，您可從現有欄位匯入值（如果是項目化欄位），並讓使用者選擇一個選項。 不過，按鈕的版面不太靈活。

>[!NOTE]
>
>Web表格不授權選取數個值。 只能針對&#x200B;**Survey**&#x200B;類型表單啟用多個選擇。 如需詳細資訊，請參閱[本章節](../../web/using/about-surveys.md)。\
>但是，可以將&#x200B;**[!UICONTROL Multiple choice]**&#x200B;類型欄位插入Web應用程式；但不授權選取數個值：可使用選項按鈕來選取提供的選項。

## 添加網格{#adding-grids}

格線用於設計Web應用程式中的投票頁面。 這可讓您提供答覆調查或評估類型Web表單的選項按鈕清單，如下所示：

![](assets/s_ncs_admin_survey_vote_param.png)

若要在表單中使用此類型的元素，請建立簡單的格線，並為每個要評估的元素新增一行。

![](assets/s_ncs_admin_survey_vote_sample.png)

網格中每行單選按鈕的數量與在簡單網格中定義的值的數量匹配。

![](assets/s_ncs_admin_survey_vote_ex.png)

每個格線只能選取一個選項。

>[!NOTE]
>
>在我們的示例中，網格的標籤是隱藏的。 若要這麼做，請前往&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤，**[!UICONTROL Label position]**&#x200B;顯示會定義為&#x200B;**[!UICONTROL Hidden]**。 請參閱[定義標籤的位置](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels)。

## 添加日期和數字{#adding-dates-and-numbers}

表單域的內容可以格式化以匹配儲存在資料庫中的資料或滿足特定要求。 您可以為輸入數字和日期建立適當的欄位。

### 添加日期{#adding-dates}

![](assets/s_ncs_admin_survey_date_calendar.png)

要允許用戶在表單頁中輸入日期，請添加輸入欄位並選擇類型&#x200B;**[!UICONTROL Date...]**。

輸入欄位的標籤並配置資料儲存模式。

![](assets/s_ncs_admin_survey_date_edit.png)

窗口的下半部分可讓您為此欄位中儲存的值選擇日期和時間格式。

![](assets/s_ncs_admin_survey_date_edit_values.png)

您也可以選擇不顯示日期（或時間）。

您可以透過日曆或下拉式方塊選擇日期。 您也可以直接在欄位中輸入，但必須符合上述畫面中指定的格式。

>[!NOTE]
>
>依預設，表單中使用的日期會透過日曆輸入。 若是多語言表單，請檢查日曆是否提供所有使用的語言版本。 請參閱[轉換Web表單](../../web/using/translating-a-web-form.md)。

但是，在某些情況下（例如輸入出生日期），使用下拉式清單可能會比較容易。

![](assets/s_ncs_admin_survey_date_list_select.png)

要執行此操作，請按一下&#x200B;**[!UICONTROL Advanced]**&#x200B;頁籤，然後使用&#x200B;**[!UICONTROL Drop-down lists]**&#x200B;選擇輸入模式。

![](assets/s_ncs_admin_survey_date_selection.png)

然後，您可以設定清單中提供之值的限制。

![](assets/s_ncs_admin_survey_date_first_last_y.png)

### 添加數字{#adding-numbers}

您可以為數字輸入建立合適的欄位。

![](assets/s_ncs_admin_survey_number.png)

在數值欄位中，使用者只能輸入數字。 當頁面被核準時，會自動套用登入控制。

視資料庫中儲存資料的欄位而定，可能會套用特殊格式或某些限制。 您也可以指定最大值和最小值。 此類型的欄位設定如下：

![](assets/s_ncs_admin_survey_number_edit.png)

預設值是發佈表單時在欄位中顯示的值。 使用者可加以修正。

您可以透過&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤，在數值欄位中新增前置詞和／或後置詞，如下所示：

![](assets/s_ncs_admin_survey_number_ex_conf.png)

在窗體中，渲染方式如下：

![](assets/s_ncs_admin_survey_number_ex.png)

## 訂閱複選框{#subscription-checkboxes}

您可以新增控制項，讓使用者訂閱或取消訂閱一或多項資訊服務（電子報、警告、即時通知等）。 若要訂閱，使用者會檢查對應的服務。

要建立訂閱複選框，請按一下&#x200B;**[!UICONTROL Advanced controls>Subscription]**。

![](assets/s_ncs_admin_survey_subscription_edit.png)

指定複選框的標籤，並使用&#x200B;**[!UICONTROL Service]**&#x200B;下拉框選擇相關的資訊服務。

>[!NOTE]
>
>資訊服務詳見[本頁](../../delivery/using/managing-subscriptions.md)。

使用者透過勾選相關選項訂閱服務。

![](assets/s_ncs_admin_survey_subscribe.png)

>[!CAUTION]
>
>如果使用者已訂閱資訊服務，且連結至此服務的方塊在他們核准表單時未勾選，則會取消訂閱。

[本節](../../web/using/about-surveys.md)提供訂閱和轉介的範例。

## 插入captcha {#inserting-a-captcha}

**captcha**&#x200B;測試的目的是防止詐用您的Web表格。

>[!CAUTION]
>
>如果您的表單包含數頁，則驗證碼必須一律放在儲存方塊之前的最後一頁，以避免規避安全措施。

若要將驗證碼插入表單，請按一下工具列上的第一個按鈕，然後選取&#x200B;**[!UICONTROL Advanced controls>Captcha]**。

![](assets/s_ncs_admin_survey_add_captcha.png)

輸入欄位的標籤。 此標籤將顯示在Captcha顯示區域前面。 您可以在&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤中更改此標籤的位置。

![](assets/s_ncs_admin_survey_captcha_adv.png)

>[!NOTE]
>
>對於&#x200B;**[!UICONTROL captcha]**&#x200B;類型控制項，不需要指出儲存欄位或變數。

Captcha會插入頁面，並在視覺下方放置輸入欄位。 這兩個元素是分不開的，因此在頁面版面配置中會視為單一項目（它們佔據單一儲存格）。

![](assets/s_ncs_admin_survey_captcha_sample.png)

確認頁面後，如果驗證碼的內容未正確輸入，則輸入欄位會以紅色顯示。

![](assets/s_ncs_admin_survey_captcha_error.png)

您可以建立要顯示的錯誤訊息。 若要這麼做，請使用&#x200B;**[!UICONTROL General]**&#x200B;標籤中的&#x200B;**[!UICONTROL Personalize the message]**&#x200B;連結。

![](assets/s_ncs_admin_survey_captcha_error_msg.png)

>[!NOTE]
>
>Captchas總有8個字元。 您不能修改此值。

## 上傳檔案{#uploading-a-file}

您可以新增上傳欄位至頁面。 例如，此功能對於內部網路檔案共用非常有用。

![](assets/s_ncs_admin_survey_download_file.png)

要將上載欄位插入表單頁，請在頁面編輯器工具欄中選擇&#x200B;**[!UICONTROL Advanced controls > File...]**&#x200B;菜單。

預設情況下，上載的檔案儲存在可通過&#x200B;**[!UICONTROL Resources > Online > Public resources]**&#x200B;菜單訪問的資源檔案中。 您可以使用指令碼來變更此行為。 此指令碼可使用[Campaign JSAPI檔案](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)中定義的函式，包括與檔案操作相關的函式。

您可以將這些檔案的連結儲存在本機變數或資料庫欄位中。 例如，您可以擴充收件者結構，以新增檔案資源的連結。

>[!CAUTION]
>
>* 此類型的檔案必須保留給具有安全存取（使用認證）的表單。
>* Adobe Campaign不會控制上傳的資源大小或類型：因此，強烈建議僅針對安全類型的內部網站使用上傳欄位。
>* 如果有數台伺服器連結至該例項（負載平衡架構），您需要確定對Web表單的呼叫會送達同一伺服器。
>* 這些實作需要Adobe Campaign諮詢團隊的協助。
>



## 插入隱藏常數{#inserting-a-hidden-constant}

當使用者驗證表單的其中一個頁面時，您可以將特定值設定至其描述檔的欄位或變數。

此欄位對使用者不可見，但可用於豐富使用者設定檔中的資料。

若要這麼做，請在頁面中放置&#x200B;**常數**，並指定值和儲存位置。

在下列範例中，每當使用者核准此頁面時，收件者描述檔的&#x200B;**origin**&#x200B;欄位就會自動填入。 常數不會顯示在頁面上。

![](assets/s_ncs_admin_survey_constante.png)

