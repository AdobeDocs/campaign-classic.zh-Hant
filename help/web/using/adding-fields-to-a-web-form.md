---
product: campaign
title: 新增欄位至網路表單
description: 新增欄位至網路表單
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Web Forms, Landing Pages
exl-id: 827b6575-7206-4dfc-b2c6-b95a6d5730b1
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '2373'
ht-degree: 0%

---

# 新增欄位至網路表單{#adding-fields-to-a-web-form}



在Web表單中，欄位可讓使用者輸入資訊並選取選項。 網路表單可提供輸入欄位、選擇欄位、靜態和進階內容（字幕、訂閱等）。

當您使用精靈新增欄位時，系統會根據選取的欄位或儲存體變數自動偵測欄位型別。 您可以使用 **[!UICONTROL Type]** 中的下拉式方塊 **[!UICONTROL General]** 標籤。

![](assets/s_ncs_admin_webform_change_type.png)

使用工具列中的按鈕時，選取您要新增的欄位型別。

可使用下列欄位型別：

* 文字/數字輸入。 另請參閱 [新增輸入欄位](#adding-input-fields).
* 下拉式清單選取專案。 另請參閱 [新增下拉式清單](#adding-drop-down-lists).
* 透過核取方塊進行多項選擇。 另請參閱 [新增核取方塊](#adding-checkboxes).
* 透過選項按鈕進行獨佔選取。 另請參閱 [新增選項按鈕](#adding-radio-buttons).
* 在選項格線中投票。 另請參閱 [新增格點](#adding-grids).
* 數字和日期。 另請參閱 [新增日期和數字](#adding-dates-and-numbers).
* 訂閱/取消訂閱資訊服務。 另請參閱 [訂閱核取方塊](#subscription-checkboxes).
* 驗證碼驗證。 另請參閱 [插入驗證碼](#inserting-a-captcha).
* 下載按鈕。 [上傳檔案](#uploading-a-file).
* 隱藏常數。 另請參閱 [插入隱藏的常數](#inserting-a-hidden-constant).

請指定回應儲存模式：更新資料庫中的欄位（僅儲存最後儲存的值）或儲存在變數中（未儲存答案）。 有關詳細資訊，請參閱 [回應儲存欄位](web-forms-answers.md#response-storage-fields).

>[!NOTE]
>
>依預設，該欄位會插入目前樹狀結構的底部。 使用工具列中的箭頭可將其向上或向下移動。

## 欄位建立精靈 {#field-creation-wizard}

對於表單的每個頁面，您可以透過工具列中的第一個按鈕新增欄位。 若要這麼做，請前往 **[!UICONTROL Add using the wizard]** 功能表。

![](assets/s_ncs_admin_survey_add_field_menu.png)

選取您要建立的欄位型別：您可以選擇在資料庫中新增欄位、變數，或匯入以其他表單建立並在容器中收集的欄位群組。

按一下 **[!UICONTROL Next]** 並選取儲存欄位或變數，或您要匯入的容器。

![](assets/s_ncs_admin_webform_wz_confirm_db.png)

按一下 **[!UICONTROL Finish]** 將選取的欄位插入頁面。

![](assets/s_ncs_admin_webform_wz_insert_field.png)

## 新增輸入欄位 {#adding-input-fields}

若要新增輸入欄位，請按一下 **[!UICONTROL Input control]** 按鈕並選擇您要新增的欄位型別。

![](assets/s_ncs_admin_webform_select_field.png)

### 輸入欄位型別 {#types-of-input-fields}

五種不同型別的文字欄位可以插入表單頁面中：

* **文字**：可讓使用者在一行中輸入文字。

  ![](assets/s_ncs_admin_survey_txt_ex.png)

* **數字**：可讓使用者在一行中輸入數字。 有關詳細資訊，請參閱 [新增數字](#adding-numbers).

  頁面獲得核准後，系統會檢查欄位內容，確保輸入的值與欄位相容。 有關詳細資訊，請參閱 [定義控制設定](form-rendering.md#defining-control-settings).

* **密碼**：可讓使用者在一行中輸入文字。 在文字輸入期間，字元會由句點取代：

  ![](assets/s_ncs_admin_survey_passwd_ex.png)

  >[!CAUTION]
  >
  >密碼會以未加密的方式儲存在資料庫中。

* **多行文字**：可讓使用者在數行中輸入文字。

  ![](assets/s_ncs_admin_survey_txtmulti_ex.png)

  >[!CAUTION]
  >
  >多行文字欄位是可以包含歸位的特定欄位。 它們的儲存空間必須與對應至XML元素的欄位相關聯，而不是XML屬性。
  >   

* **豐富的多行文字**：可讓使用者輸入具有配置的文字，並以HTML格式儲存。

  ![](assets/s_ncs_admin_survey_txthtmli_ex.png)

  您可以選取提供給使用者的編輯器型別。 若要這麼做，請使用 **[!UICONTROL HTML editor]** 中的欄位 **[!UICONTROL Advanced]** 標籤。

  ![](assets/webapp_enrich_text_type.png)

  顯示的圖示數目依編輯器型別而異。 針對 **[!UICONTROL Advanced]** 編輯器中，轉譯將如下所示：

  ![](assets/webapp_enrich_text_max.png)

### 設定輸入欄位 {#configure-input-fields}

所有輸入欄位都是根據相同的模式使用下列選項進行設定：

![](assets/s_ncs_admin_survey_txt_param.png)

此 **[!UICONTROL General]** 索引標籤可讓您輸入欄位名稱，並視需要為其指定預設值。

答案儲存模式可透過 **[!UICONTROL Edit storage...]** 連結。 值可以儲存在資料庫的現有欄位中；或者您可以選擇不將資訊儲存在資料庫中（使用本機變數）。

>[!NOTE]
>
>儲存模式的詳細資訊，請參閱 [回應儲存欄位](web-forms-answers.md#response-storage-fields)

此 **[!UICONTROL Advanced]** tab可讓您定義欄位的顯示引數（標籤的位置、對齊方式等）。 另請參閱 [定義網路表單版面](defining-web-forms-layout.md).

## 新增下拉式清單 {#adding-drop-down-lists}

您可以將下拉式清單插入調查頁面。 這可讓使用者在下拉式選單中，從選件上選取值。

![](assets/s_ncs_admin_survey_dropdown_sample.png)

若要將下拉式方塊新增至表單頁面，請按一下 **[!UICONTROL Selection controls > Drop-down list]** 頁面編輯器工具列中的按鈕。

![](assets/s_ncs_admin_survey_create_dropdown.png)

選取答案儲存模式，並確認您的選擇。

在清單的下半部分定義標籤和值 **[!UICONTROL General]** 標籤。 如果資訊儲存在資料庫的現有欄位中，而且它是列舉欄位，您可以按一下來自動填入值 **[!UICONTROL Initialize the list of values from the database]** ，如下所示：

![](assets/s_ncs_admin_survey_database_values.png)

>[!NOTE]
>
>使用值清單右側的箭頭來變更其順序。

如果資料儲存在連結表格中，您可以選取儲存清單中建議值的欄位。 例如，如果您選取國家/地區表格，請按一下 **[!UICONTROL Initialize the list of values from the database...]** 並選取所需欄位。

![](assets/s_ncs_admin_survey_preload_values.png)

接下來，按一下 **[!UICONTROL Load]** 擷取值的連結：

![](assets/s_ncs_admin_survey_load_button.png)

>[!CAUTION]
>
>每當清單更新時，請重複此作業以重新整理選件上的值。

## 新增核取方塊 {#adding-checkboxes}

為了讓使用者選取選項，您需要使用核取方塊。

![](assets/s_ncs_admin_survey_check_box.png)

若要將核取方塊新增至表單，請按一下 **[!UICONTROL Selection controls > Checkbox...]** 圖示來切換頁面。

選取答案儲存模式，並確認您的選擇。

輸入方塊的標籤，在 **[!UICONTROL Label]** 欄位屬於 **[!UICONTROL General]** 標籤。

![](assets/s_ncs_admin_survey_check_box_edit.png)

核取方塊可讓您根據是否核取方塊，為儲存欄位（或值）指派值。 此 **[!UICONTROL Values]** 區段可讓您輸入如果核取方塊(在 **[!UICONTROL Value]** 欄位)，以及未核取時要指派的值(在 **[!UICONTROL Empty value]** 欄位)。 這些值取決於資料儲存格式。

如果儲存欄位（或變數）是布林值，則系統會自動推匯出未核取方塊時要指派的值。 在此情況下，僅 **[!UICONTROL Value if checked]** 欄位已提供，如下所示：

![](assets/s_ncs_admin_survey_check_box_enum.png)

## 範例：如果核取方塊，則為欄位指派值 {#example--assign-a-value-to-a-field-if-a-box-is-checked}

我們想要將核取方塊插入表單以傳送維護請求，如下所示：

![](assets/s_ncs_admin_survey_check_box_ex.png)

資訊將上傳到資料庫並放入現有欄位(在此案例中， **[!UICONTROL Comment]** 欄位)：

![](assets/s_ncs_admin_survey_check_box_ex_list.png)

如果勾選「需要維護」方塊， **[!UICONTROL Comment]** 欄將包含「需要維護」。 如果未核取此方塊，欄會顯示「不需要維護」。 若要取得此結果，請將下列設定套用至表單頁面上的核取方塊：

![](assets/s_ncs_admin_survey_check_box_ex_edit.png)

## 新增選項按鈕 {#adding-radio-buttons}

選項按鈕可讓您為使用者提供一系列獨佔選項以供選擇。 這些是相同欄位的不同值。

![](assets/s_ncs_admin_survey_radio_button.png)

您可以個別建立選項按鈕（單一按鈕）或透過多選清單，但由於選項按鈕的要點是要選取一個或另一個選項，因此我們一律會建立至少一對選項按鈕，絕不會只建立一個按鈕。

>[!CAUTION]
>
>若要強制進行選取，您必須建立多選清單。

### 新增單一按鈕 {#add-single-buttons}

若要新增選項按鈕至表單頁面，請移至 **[!UICONTROL Selection controls > Radio button]** 功能表，並選擇儲存模式。

![](assets/s_ncs_admin_survey_radio_button_sample.png)

選項按鈕的設定方式與核取方塊類似(請參閱 [新增核取方塊](#adding-checkboxes))。 但是，如果未選取選項，則不會指派任何值。 為了讓多個按鈕具有相依性（即選取一個按鈕會自動取消選取其他按鈕），這些按鈕必須儲存在相同欄位中。 如果它們未儲存在資料庫中，則必須使用相同的本機變數來暫時儲存。 另請參閱 [回應儲存欄位](web-forms-answers.md#response-storage-fields).

### 新增按鈕清單 {#add-a-list-of-buttons}

若要透過清單新增選項按鈕，請前往 **[!UICONTROL Selection controls>Multiple choice]** 頁面編輯器工具列中的功能表。

![](assets/s_ncs_admin_survey_radio_button_sample2.png)

新增標籤一樣多的選項按鈕。 此功能的優點在於，您可以從現有欄位（若為分項欄位）匯入值，並讓使用者選擇一個選項。 不過，按鈕的版面配置較不靈活。

>[!NOTE]
>
>您無法在Web應用程式中啟用多重選取範圍。
>但是，可以插入 **[!UICONTROL Multiple choice]** 在Web應用程式中輸入欄位，但使用者無法選取數個值。

## 新增格點 {#adding-grids}

格線可用來設計Web應用程式中的投票頁面。 這可讓您提供用於回答調查或評估型別Web表單的選項按鈕清單，如下所示：

![](assets/s_ncs_admin_survey_vote_param.png)

若要在表單中使用此型別的元素，請建立簡單的格點，並為要評估的每個元素新增一行。

![](assets/s_ncs_admin_survey_vote_sample.png)

格線每行的選項按鈕數目與簡單格線中定義的值數目相符。

![](assets/s_ncs_admin_survey_vote_ex.png)

每個格線只能選取一個選項。

>[!NOTE]
>
>在我們的範例中，格線的標籤是隱藏的。 若要這麼做，請前往 **[!UICONTROL Advanced]** 標籤， **[!UICONTROL Label position]** 顯示定義為 **[!UICONTROL Hidden]** . 另請參閱 [定義標籤位置](defining-web-forms-layout.md#defining-the-position-of-labels).

## 新增日期和數字 {#adding-dates-and-numbers}

表單欄位的內容可以格式化以符合資料庫中儲存的資料或滿足特定需求。 您可以建立適當的欄位來輸入數字和日期。

### 新增日期 {#adding-dates}

![](assets/s_ncs_admin_survey_date_calendar.png)

若要允許使用者在表單頁面中輸入日期，請新增輸入欄位並選取型別 **[!UICONTROL Date...]**.

輸入欄位的標籤並設定資料儲存模式。

![](assets/s_ncs_admin_survey_date_edit.png)

視窗的下半部可讓您選取此欄位中儲存值的日期和時間格式。

![](assets/s_ncs_admin_survey_date_edit_values.png)

您也可以選擇不顯示日期（或時間）。

日期可透過行事曆或下拉式方塊選取。 您也可以直接在欄位中輸入它們，但它們需要符合上方畫面中指定的格式。

>[!NOTE]
>
>依預設，表單中使用的日期透過日曆輸入。 若是多語言表單，請檢查行事曆是否適用於所有使用的語言。 另請參閱 [轉譯網路表單](translating-a-web-form.md).

但在某些情況下（例如輸入出生日期），使用下拉式清單會比較容易。

![](assets/s_ncs_admin_survey_date_list_select.png)

若要這麼做，請按一下 **[!UICONTROL Advanced]** 標籤並選擇輸入模式，使用 **[!UICONTROL Drop-down lists]**.

![](assets/s_ncs_admin_survey_date_selection.png)

然後，您可以將限制設定為清單中提供的值。

![](assets/s_ncs_admin_survey_date_first_last_y.png)

### 新增數字 {#adding-numbers}

您可以為數字輸入建立適當的欄位。

![](assets/s_ncs_admin_survey_number.png)

在數值欄位中，使用者只能輸入數字。 在核准頁面時，會自動套用專案控制。

視資料儲存於資料庫中的欄位而定，可能會套用特殊格式或某些限制。 您也可以指定最大值和最小值。 此型別的欄位設定如下：

![](assets/s_ncs_admin_survey_number_edit.png)

預設值是發佈表單時欄位中顯示的值。 使用者可加以更正。

您可以透過以下方式將首碼和/或尾碼新增至數值欄位： **[!UICONTROL Advanced]** 標籤，如下所示：

![](assets/s_ncs_admin_survey_number_ex_conf.png)

在表單中，轉譯將如下所示：

![](assets/s_ncs_admin_survey_number_ex.png)

## 訂閱核取方塊 {#subscription-checkboxes}

您可以新增控制項，讓使用者訂閱或取消訂閱一或多個資訊服務（電子報、警告、即時通知等）。 要訂閱，使用者會檢查對應的服務。

若要建立訂閱核取方塊，請按一下 **[!UICONTROL Advanced controls>Subscription]**.

![](assets/s_ncs_admin_survey_subscription_edit.png)

指定核取方塊的標籤，然後使用 **[!UICONTROL Service]** 下拉式方塊。

>[!NOTE]
>
>資訊服務的詳細資訊，請參閱 [此頁面](../../delivery/using/managing-subscriptions.md).

使用者藉由核取相關選項來訂閱服務。

![](assets/s_ncs_admin_survey_subscribe.png)

>[!CAUTION]
>
>如果使用者已經訂閱了資訊服務，且在核准表單時未勾選連結到此服務的方塊，則將取消訂閱。

## 插入驗證碼 {#inserting-a-captcha}

目的 **驗證碼** 測試是為了防止欺騙性使用您的網路表單。

>[!CAUTION]
>
>如果您的表單包含數個頁面，驗證碼必須一律放置在最後一個頁面上，緊接在儲存方塊之前，以防止任何規避安全性措施的情形。

若要將驗證碼插入表單中，請按一下工具列上的第一個按鈕，然後選取 **[!UICONTROL Advanced controls>Captcha]**.

![](assets/s_ncs_admin_survey_add_captcha.png)

輸入欄位的標籤。 此標籤將顯示在驗證碼顯示區域的前面。 您可以變更此標籤在 **[!UICONTROL Advanced]** 標籤。

![](assets/s_ncs_admin_survey_captcha_adv.png)

>[!NOTE]
>
>的 **[!UICONTROL captcha]** 型別控制項，不需要指出儲存欄位或變數。

驗證碼會插入到頁面中，並將輸入欄位放置在視覺效果下。 這兩個元素是不可分離的，且就版面配置而言，會視為單一專案（佔據單一儲存格）。

![](assets/s_ncs_admin_survey_captcha_sample.png)

確認頁面後，如果驗證碼的內容輸入不正確，輸入欄位會顯示為紅色。

![](assets/s_ncs_admin_survey_captcha_error.png)

您可以建立要顯示的錯誤訊息。 若要這麼做，請使用 **[!UICONTROL Personalize the message]** 中的連結 **[!UICONTROL General]** 標籤。

![](assets/s_ncs_admin_survey_captcha_error_msg.png)

>[!NOTE]
>
>字幕長度一律為8個字元。 您無法修改此值。

## 上傳檔案 {#uploading-a-file}

您可以將上傳欄位新增至頁面。 例如，此功能可用於內部網路檔案共用。

![](assets/s_ncs_admin_survey_download_file.png)

若要將上傳欄位插入表單頁面，請選取 **[!UICONTROL Advanced controls > File...]** 頁面編輯器工具列中的功能表。

依預設，上傳的檔案會儲存在可透過存取的資源檔案中 **[!UICONTROL Resources > Online > Public resources]** 功能表。 您可以使用指令碼來變更此行為。 此指令碼可使用中定義的函式 [Campaign JSAPI檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant)，包括與檔案操控有關的作業。

您可以將這些檔案的連結儲存在本機變數或資料庫欄位中。 例如，您可以擴充收件者綱要以新增檔案型資源的連結。

>[!CAUTION]
>
>* 必須將此型別的檔案保留給具有安全存取權（使用認證）的表單。
>* Adobe Campaign無法控制已上傳資源的大小或型別：因此，強烈建議您僅將上傳欄位用於安全型別的內部網路網站。
>* 如果多個伺服器連結至執行個體（負載平衡架構），您必須確定對Web表單的呼叫到達相同的伺服器。
>* 這些實作需要Adobe Campaign諮詢團隊的協助。
>

## 插入隱藏的常數 {#inserting-a-hidden-constant}

當使用者驗證表單的其中一個頁面時，您可以將特定值設定為其設定檔的欄位或變數。

使用者無法看到此欄位，但可用於擴充使用者設定檔中的資料。

若要這麼做，請放置 **常數** ，並指定值和儲存位置。

在以下範例中， **來源** 當使用者核准此頁面時，會自動填寫收件者設定檔的欄位。 常數不會顯示在頁面上。

![](assets/s_ncs_admin_survey_constante.png)
