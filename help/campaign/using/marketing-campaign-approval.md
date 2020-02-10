---
title: 核准行銷促銷活動
seo-title: 核准行銷宣傳
description: 核准行銷宣傳
seo-description: null
page-status-flag: never-activated
uuid: 842b501f-7d65-4450-b7ab-aff3942fb96f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: 8d076211-10a6-4a98-b0d2-29dad154158c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---

# 核准行銷促銷活動 {#approving-marketing-campaigns}

## 核准程式 {#approval-process}

傳送的每個步驟都需經過核准，以確保完整監控和控制促銷活動的各種程式：鎖定、內容、預算、擷取和傳送證明。

>[!NOTE]
>
>您需要檢查審核者是否擁有核准的適當權限。 另請檢查其安全區是否已正確定義。

通知電子郵件會傳送給Adobe Campaign營運商，這些營運商是指定的審閱者，以通知他們核准要求。

核准程式顯示在「檢查 [和批准交貨」中](#checking-and-approving-deliveries)。

>[!NOTE]
>
>只有傳送擁有者才能開始傳送。 為了讓其他運算元（或運算元群組）能夠開始傳送，您必須在欄位中新增為審核 **[!UICONTROL Delivery start:]** 者。\
>另請參閱「選 [取審核者」](#selecting-reviewers)。

### 操作原則 {#operating-principle-}

例如，用於預算審批的標準電子郵件如下：

![](assets/s_user_validation_link_in_mail.png)

然後，審閱者操作員可以選擇是否批准相關步驟。

![](assets/s_user_validation_page_confirm.png)

當營運商核准其選擇後，作業的核准或拒絕會轉送至傳送控制面板。

![](assets/s_user_validation_link_in_op_board.png)

促銷活動的核准記錄檔中也提供這些資訊(透過標籤存 **[!UICONTROL Edit > Tracking > Approvals]** 取):

![](assets/s_user_validation_log_in_op_edit_tab.png)

這些通知會傳送至每個已啟用核准的程式所受影響的運算子。

您可以針對促銷活動範本、個別針對每個促銷活動或針對傳送啟用核准。

所有需要核准的工作都會在促銷活動範本( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** tab)中選取，負責核准的營運商也會選取（除非未啟用此選項，否則他們會收到通知）。 For more on this, refer to [Approving processes](#approving-processes).

使用此範本建立的每個促銷活動，以及每個促銷活動傳送，都可以覆寫這些設定：按一下按 **[!UICONTROL Properties]** 鈕，然後按一下標 **[!UICONTROL Approvals]** 簽。

在下列範例中，傳送內容不需要核准：

![](assets/s_user_validation_select_process_from_del.png)

### 選取審核者 {#selecting-reviewers}

對於每種審批類型，負責審批的運算元或運算元群組會從傳送的下拉式清單中選取。 可使用連結新增其他運 **[!UICONTROL Edit...]** 算子。 此視窗也可讓您編輯核准期限。

![](assets/s_user_validation_add_operator.png)

如果未指定審核者，促銷活動管理員將負責核准，並會收到通知。 促銷活動管理員是在促銷活動 **[!UICONTROL Edit > Properties]** 的標籤中指定：

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>所有其他具有權限的Adobe Campaign **[!UICONTROL Administrator]** 營運商也可以核准工作，但不會收到通知。\
>依預設，如果已定義核准運算子，促銷活動管理員將無法執行核准或啟動傳送。 您可以修改此行為並授權促銷活動管理員，以建立 **NmsCampaign_Activate_OwnerConfirmation** 選項 **1** 作為值來核准／開始傳送。

### 核准模式 {#approval-modes}

#### 透過控制面板核准 {#approval-via-the-dashboard}

若要透過主控台或網頁介面核准工作，請按一下促銷活動控制面板上的適當連結。 作業也可以透過傳送追蹤或傳送控制面板來核准。

![](assets/s_user_validation_from_console.png)

檢查要批准的資訊，選擇是否接受或拒絕批准，並在需要時輸入注釋。 按一 **[!UICONTROL Ok]** 下以儲存。

>[!NOTE]
>
>如果某個程式已經由其他運算元核准，則無法使用核准連結。

#### 透過通知訊息進行核准 {#approval-via-notification-messages}

按一下通知訊息中可用的連結(請參 [閱通知](#notifications))。 系統會要求您識別自己，如下所示：

![](assets/s_user_validation__log_in.png)

選擇 **[!UICONTROL Accept]** 或 **[!UICONTROL Reject]** ，並在需要時輸入注釋。

![](assets/s_user_validation_save_target_validation.png)

按一下 **[!UICONTROL Validate]**.

>[!NOTE]
>
>如果在處理過程中出現警告，通知中會顯示警告。

#### 核准追蹤 {#approval-tracking}

這些資訊可在數個地方取得：

* 在促銷活動核准記錄中， **[!UICONTROL Approvals]** 標籤的子標籤 **[!UICONTROL Edit > Tracking]** 為：

   ![](assets/s_user_validation_log_from_op.png)

* 在促銷活動傳送記錄中， **[!UICONTROL Deliveries]** 標籤的子標籤 **[!UICONTROL Edit > Tracking]** 為：

   ![](assets/s_user_validation_log_from_delivery_list.png)

* 您可以按一下標籤的選項，來檢視每 **[!UICONTROL Hide/show log]** 個傳送的核准 **[!UICONTROL Summary]** 狀態。

   ![](assets/s_user_validation_log_delivery.png)

* 您也可以透過每個傳送的標籤 **[!UICONTROL Tracking > Approvals]** 來存取這項資訊：

   ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>一旦操作員批准或拒絕了作業，其他複查操作員就無法再對批准執行操作。

#### 自動和手動審批 {#automatic-and-manual-approval}

在建立定位工作流程時，如果核准是自動（預設模式）,Adobe Campaign會顯示核准連結，或在需要核準時傳送通知。

若要選擇核准模式（手動或自動），請按一下促銷 **[!UICONTROL Edit > Properties]** 活動或促銷活動範本的標籤，然後按一 **[!UICONTROL Advanced campaign settings...]** 下最後一 **[!UICONTROL Approvals]** 個標籤。

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>選取的核准模式會套用至促銷活動的所有傳送。

建立定位工作流程時，手動核准可讓您避免建立核准連結或自動傳送通知。 然後，促銷活動控制面板會提 **[!UICONTROL Submit targeting for approval]** 供一個連結，以手動啟動核准程式。

確認訊息可讓您授權核准為此傳送選取的工作。

然後，核准按鈕會顯示在促銷活動控制面板（針對此傳送）、傳送控制面板和傳送追蹤中。 如果通知已啟用，則會同時傳送通知。

此啟用核准的方法可讓您進行鎖定，而不需傳送假通知給審核者。

### 通知 {#notifications}

通知是寄送給審核者的特定電子郵件訊息，通知他們有待核准的程式。 當運算子按一下訊息中的連結時，會出現驗證頁面，在登入後，運算子可以檢視資訊並核准或拒絕工作。 您也可以在核准視窗中輸入註解。

通知電子郵件的內容可以個人化。 請參閱 [通知內容](#notification-content)。

#### 啟用／禁用通知 {#enabling-disabling-notification}

依預設，如果促銷活動範本、促銷活動或傳送中啟用相關工作的核准，則會傳送通知訊息。 不過，通知可以停用，以僅授權從主控台核准。

若要這麼做，請編輯促銷活動或促銷活動範本的核准視窗( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** >標 **[!UICONTROL Approvals]** 簽)並選取 **[!UICONTROL Do not enable notification sending]**。

![](assets/s_user_validation_notif_desactivate.png)

#### 通知內容 {#notification-content}

通知內容在特定範本中定義： **[!UICONTROL Notification of validations for the marketing campaign]**。 此範本會儲存在Adobe Campaign **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 樹狀結構的資料夾中。

## 核准傳送 {#checking-and-approving-deliveries}

Adobe Campaign可讓您以協作模式，設定行銷活動主要階段的核准程式。

對於直接郵寄，Adobe Campaign營運商可以在擷取檔案傳送至路由器之前先加以檢視，如有需要，也可以變更格式並重新啟動擷取。 請參 [閱批准抽取檔案](#approving-an-extraction-file)。

對於每個促銷活動，您可以核准傳送目標、內容(請參 [閱核准內容](#approving-content))和成本。 可以以電子郵件的形式通知負責核准的 Adobe Campaign 操作者，然後他們可透過主控台或網路連線核准或拒絕核准。請參閱 [核准程式](#approving-processes)。

當這些驗證階段完成時，就可啟動傳送。 請參 [閱開始傳送](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)。

>[!NOTE]
>
>如需核准模式和追蹤的詳細資訊，請參閱核 [準程式](#approval-process)。

### 核准程式 {#approving-processes}

需要核准的階段會顯示在促銷活動控制面板上（透過Web介面的主控台）。 它們也會出現在傳送追蹤表格和傳送控制面板中。

此時，促銷活動的狀態為 **[!UICONTROL To validate]**。

>[!NOTE]
>
>* 若要選取要核准的流程，請修改促銷活動範本。 For more on this, refer to [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).
   >
   >
* 另請參閱「核准」程式 [一節](#approval-process)。



![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>在定位工作流程中，如果在準備訊息時發生連結至設定問題的錯誤，該連 **[!UICONTROL Restart message preparation]** 結會顯示在控制面板上。 更正錯誤，然後按一下此連結，在略過定位階段時重新啟動訊息準備。

![](assets/s_user_validation_relaunch_message_preparation.png)

對於促銷活動中的每個傳送，您可以核准下列程式：

* **目標鎖定、內容與預算**

   當在任 **[!UICONTROL Enable target approval]**&#x200B;務審批設 **[!UICONTROL Enable content approval]** 置窗口中選 **[!UICONTROL Enable budget approval]** 擇或選項時，相關連結將顯示在相關交貨的促銷活動控制面板中。

   >[!NOTE]
   >
   >只有在「審批設定」視窗中啟用了目標審批時，預算審批才可用。 只有在分析目標後，才會顯示預算核准的連結。 此外，此連結會與要進行目標核准的連結一起顯示。

   如果在 **[!UICONTROL Assign content editing]** 核准 **[!UICONTROL External content approval]** 設定視窗中選取或選項，控制面板會顯示 **[!UICONTROL Available content]** 和連結 **[!UICONTROL External content approval]** 。

   內容核准可讓您存取傳送的校樣。

* **提取核准（直接郵寄）**

   當在 **[!UICONTROL Enable extraction approval]** 批准設定窗口中選擇時，必須先批准提取的檔案，才能通知路由器。

   促銷 **[!UICONTROL Approve content]** 活動控制面板上提供連結，如下所示：

   ![](assets/s_ncs_user_edit_file_valid.png)

   擷取檔案可透過核准方塊預覽，然後接受或拒絕。

   ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

   >[!NOTE]
   >
   >擷取檔案預覽僅涉及資料範例。 不載入整個輸出檔案。

* **核准相關的傳送**

   此選項 **[!UICONTROL Enable individual approval of each associated delivery]** 用於與輔助交貨關聯的一個主交貨。 依預設，不會選取此選項，以執行主傳送的整體核准。 如果選取此選項，則必須個別核准每個傳送。

   ![](assets/s_ncs_user_task_valid_associate.png)

#### 選擇要批准的進程 {#choosing-the-processes-to-be-approved}

核准階段會以與促銷活動關聯的範本來定義。 您必須從範本中選取要核准的元素，並指定負責這些核准的Adobe Campaign運算子。 For more on this, refer to [Campaign templates](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

>[!NOTE]
>
>促銷活動或促銷活動範本的核准設定將會套用至連結至此促銷活動的所有未來傳送。 任何組態變更都不會套用至先前的傳送。

您可以覆寫每個促銷活動和每個傳送的這項資訊。

對於促銷活動，請按一 **[!UICONTROL Edit > Properties]** 下標籤、連結 **[!UICONTROL Advanced campaign settings...]** ，最後按一下子標 **[!UICONTROL Approvals]** 簽以存取核准設定頁面。

您可以選取和取消選取要核准和指定負責核准的Adobe Campaign營運商的程式。 這些運算子可以是個別運算子、運算子群組或運算子清單。

要選擇運算子清單，請按一下 **[!UICONTROL Edit...]** 指定第一個審閱者的欄位右側的連結，然後根據需要添加任意數量的運算子，如下所示：

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* 如果定義了審核者清單，則在一個審核者接受該清單後，將立即批准該作業。 然後控制面板中將不再提供相關的核准連結。 在啟用通知發送時，如果另一個審核者按一下通知消息中的批准連結，則會通知他們另一個操作員已經批准了作業。
>* 您可以在審核者編輯視窗的下方區段，定義促銷活動的核准排程。 依預設，審核者自提交日期起有三天時間可核准程式。 您可以設定提醒，提醒會在核准截止日期之前自動傳送給相關的營運商。
>* 您可以新增本節的提醒。
>



![](assets/s_ncs_user_edit_op_valid_calendar.png)

對於每次傳送，按一下 **[!UICONTROL Audit]** 按鈕和標籤 **[!UICONTROL Approvals]** 以檢視和編輯核准日期及自動提醒。

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>內容核准程式啟動後，此標籤即可使用。

### 核准內容 {#approving-content}

>[!CAUTION]
>
>若要核准內容，「校對」週期為強制性。 校樣可讓您核准資訊的顯示、個人化資料，並檢查連結是否正常運作。 有關建立證明及其生命週期的詳細資訊，請參閱「發送 [消息](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) 」部分。
>
>下文詳述的內容批准功能旨在添加到證明交付中。

您可以設定內容核准週期。 若要這麼做，請在核准 **[!UICONTROL Enable content approval]** 設定視窗中選取選項。 內容核准週期的主要步驟為：

1. 建立新傳送後，促銷活動管理員會按一下促 **[!UICONTROL Submit content]** 銷活動控制面板上的連結，以開始內容核准週期。

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >如果在 **[!UICONTROL Enable the sending of proofs]** 核准設定視窗中選取 **[!UICONTROL Enable the sending and approval of proofs]** 了選項（電子郵件傳送）或（直接郵件傳送），則會自動傳送校樣。

1. 系統會傳送通知電子郵件給負責內容的人員，由他們選擇是否要核准：

   * 透過通知電子郵件：

      ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

      >[!NOTE]
      >
      >通知電子郵件包含已傳送校樣的連結，如果此例項已啟用 **Deliverability** （傳送功能）選項，則可能會轉譯各種網頁郵件的訊息。

   * 透過主控台或Web介面、傳送追蹤、傳送控制面板或促銷活動控制面板：

      ![](assets/s_ncs_user_validation_content_bat_op.png)

      >[!NOTE]
      >
      >此促銷活動控制面板可讓您按一下連結，檢視已傳送的校樣清 **[!UICONTROL Inbox rendering...]** 單。 若要檢視其內容，請按一 **[!UICONTROL Detail]** 下清單右側的圖示。

      ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. 系統會傳送通知電子郵件給負責促銷活動的人員，通知他們內容是否已獲核准。

   >[!NOTE]
   >
   >負責促銷活動的人員可隨時重新啟動內容核准週期。 若要這麼做，請按一下促銷活動控 **[!UICONTROL Content status]** 制面板行上的連結（在傳送層級），然後按一下 **[!UICONTROL Reset content approval to submit it again]**。

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### 指派內容編輯 {#assign-content-editing}

此選項可讓您定義負責內容編輯的人員，例如網站管理員。 如果在 **[!UICONTROL Assign content editing]** 批准設定窗口中選擇了該選項，則在發送建立和將通知電子郵件發送給負責內容的人員之間將添加幾個批准步驟：

1. 建立新傳送後，負責促銷活動的人員會按一下促銷活動控 **[!UICONTROL Submit content editing]** 制面板中的連結，以開始內容編輯週期。

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. 負責內容編輯的人員將會收到電子郵件，告知他們內容已可供使用。

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. 然後，他們可以登入主控台、開啟傳送內容，並使用簡化的精靈加以編輯，以變更主旨、HTML和文字內容，並傳送校樣。

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >如果在 **[!UICONTROL Enable the sending of proofs]** 核准設定視窗中選取 **[!UICONTROL Enable the sending and approval of proofs]** 了選項（電子郵件傳送）或（直接郵件傳送），則會自動傳送校樣。

1. 當負責內容編輯的人員完成對傳送內容所做的任何變更後，他們就可以提供內容。

   為此，他們可以：

   * 按一 **[!UICONTROL Available content]** 下透過Adobe Campaign主控台的連結。

      ![](assets/s_ncs_user_validation_submit_content_available.png)

   * 按一下通知訊息中的連結，然後核准內容可用性。

      ![](assets/s_ncs_user_validation_submit_content_available2.png)

      營運商可在將內容提交給促銷活動負責人之前新增意見。

      ![](assets/s_ncs_user_validation_submit_content_available3.png)

      通知訊息可讓審核者核准或拒絕內容。

      ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### 外部內容核准 {#external-content-approval}

此選項可讓您定義負責核准傳送轉譯的外部營運商，例如品牌通訊一致性、費率等。 當在 **[!UICONTROL External content approval]** 核准設定視窗中選取選項時，在內容核准和將通知傳送給促銷活動負責人之間會新增數個核准步驟：

1. 外部內容管理員會收到通知電子郵件，通知他們內容已獲核准，並請求外部核准。
1. 通知電子郵件包含傳送之校樣的連結，可讓您檢視傳送轉換，以及用於核准或拒絕傳送內容的按鈕。

   >[!NOTE]
   >
   >只有在傳送一或多個校樣時，這些連結才可用。 否則，傳送演算只能透過主控台或網頁介面使用。

   ![](assets/s_user_validation_external_content.png)

### 批准抽取檔案 {#approving-an-extraction-file}

對於離線傳送，Adobe Campaign會產生擷取檔案，並依設定方式將其傳送至路由器。 其內容取決於所使用的匯出範本。

當內容、定位和預算獲得核准後，傳送會變更為，直 **[!UICONTROL Extraction pending]** 到促銷活動的擷取工作流程啟動為止。

![](assets/s_ncs_user_waiting_file_extraction.png)

在提取請求日期，將建立提取檔案，並將傳送狀態更改為 **[!UICONTROL File to approve]**。

![](assets/s_ncs_user_file_extract_to_valid.png)

您可以檢視擷取檔案的內容（按一下檔案名稱）、核准檔案，或視需要變更格式，並使用控制面板上的連結重新啟動擷取。

檔案獲得批准後，您可以向路由器發送通知電子郵件。 如需詳細資訊，請參閱「開 [始離線傳送」](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery)。
