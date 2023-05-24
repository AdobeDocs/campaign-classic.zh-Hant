---
product: campaign
title: 設定及管理核准流程
description: 瞭解如何管理行銷活動的核准
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Approvals, Campaigns
exl-id: 8cbb2445-f5e4-4a25-ba7e-56e39ca9d3ce
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '2438'
ht-degree: 2%

---

# 設定及管理核准流程 {#approving-marketing-campaigns}


傳遞的每個步驟都可能受到核准，以確保完全監控和控制活動的各種流程：目標定位、內容、預算、擷取和傳送證明。

通知訊息會傳送給Adobe Campaign操作員，由他們指定稽核者，通知他們核准請求。 檢查檢閱者是否擁有 **適當的許可權** 以進行核准，並確認其安全區域已正確定義。 [了解更多](#selecting-reviewers)。

核准程式在中顯示 [本節](#checking-and-approving-deliveries).

>[!NOTE]
>
>只有傳遞擁有者可以開始傳遞。 為了讓其他操作員（或操作員群組）能夠開始傳遞，您必須將他們新增為中的稽核者 **[!UICONTROL Delivery start:]** 欄位。\
>[了解更多](#selecting-reviewers)。

## 操作原則 {#operating-principle-}

例如，預算核准的標準訊息如下：

![](assets/s_user_validation_link_in_mail.png)

檢閱者操作員可以選擇是否核准預算。

![](assets/s_user_validation_page_confirm.png)

操作員驗證後，工作的核准或拒絕會轉送到傳遞儀表板。

![](assets/s_user_validation_link_in_op_board.png)

此資訊也可在行銷活動的核准記錄中取得。這些記錄可透過 **[!UICONTROL Edit > Tracking > Approvals]** 標籤。

![](assets/s_user_validation_log_in_op_edit_tab.png)

這些通知會傳送給每個已啟用核准之程式受影響的操作者。

可以為行銷活動範本、每個行銷活動個別或傳遞啟用核准。

所有需要核准的工作都會在行銷活動範本中選取( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** 標籤)，負責核准的操作員亦然（除非未啟用此選項，否則他們會收到通知）。 如需詳細資訊，請參閱[本章節](#approving-processes)。

您可以針對使用此範本建立的每個行銷活動，以及個別針對每個行銷活動傳送覆寫這些設定：按一下 **[!UICONTROL Properties]** 按鈕，然後 **[!UICONTROL Approvals]** 標籤。

在下列範例中，傳遞內容不需要核准：

![](assets/s_user_validation_select_process_from_del.png)

## 選取檢閱者 {#selecting-reviewers}

對於每種核准型別，都會從傳送的下拉式清單中選取負責核准的操作員或操作員群組。 可使用新增更多運運算元 **[!UICONTROL Edit...]** 連結。 此視窗也可讓您編輯核准期限。

![](assets/s_user_validation_add_operator.png)

如果未指定稽核者，則行銷活動經理將負責核准並將收到通知。 行銷活動管理員指定於 **[!UICONTROL Edit > Properties]** 行銷活動的索引標籤：

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>所有其他的Adobe Campaign運運算元，搭配 **[!UICONTROL Administrator]** 許可權也可以核准工作，但不會收到通知。\
>依預設，如果已定義核准操作員，則行銷活動經理無法執行核准或開始傳送。 您可以修改此行為，並透過建立 **NmsCampaign_Activate_OwnerConfirmation** 選項，搭配 **1** 作為值。

## 核准模式 {#approval-modes}

### 透過儀表板核准 {#approval-via-the-dashboard}

若要透過主控台或網頁介面核准工作，請按一下行銷活動控制面板上的適當連結。 也可以透過傳遞追蹤或傳遞控制面板來核准工作。

![](assets/s_user_validation_from_console.png)

檢查要核准的資訊，選擇是否接受或拒絕核准，並視需要輸入註解。 按一下 **[!UICONTROL Ok]** 以儲存。

>[!NOTE]
>
>如果某個程式已由其他操作員核准，則無法使用核准連結。

### 透過通知訊息核准 {#approval-via-notification-messages}

按一下通知訊息中可用的連結(請參閱 [通知](#notifications))。 您必須登入，如下所示：

![](assets/s_user_validation__log_in.png)

選取 **[!UICONTROL Accept]** 或 **[!UICONTROL Reject]** 並視需要輸入註解。

![](assets/s_user_validation_save_target_validation.png)

按一下&#x200B;**[!UICONTROL Validate]**。

>[!NOTE]
>
>如果處理期間出現警告，通知中會顯示警告。

### 核准追蹤 {#approval-tracking}

此資訊提供在以下幾個位置：

* 在行銷活動核准記錄檔中， **[!UICONTROL Approvals]** 的子標籤 **[!UICONTROL Edit > Tracking]** 標籤：

   ![](assets/s_user_validation_log_from_op.png)

* 在行銷活動傳遞記錄檔中， **[!UICONTROL Deliveries]** 的子標籤 **[!UICONTROL Edit > Tracking]** 標籤：

   ![](assets/s_user_validation_log_from_delivery_list.png)

* 按一下 **[!UICONTROL Hide/show log]** 的選項 **[!UICONTROL Summary]** 標籤。

   ![](assets/s_user_validation_log_delivery.png)

* 此資訊也可透過 **[!UICONTROL Tracking > Approvals]** 每個傳遞的索引標籤：

   ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>一旦操作員核准或拒絕工作，其他稽核操作員就不能再對核准採取行動。

### 自動和手動核准 {#automatic-and-manual-approval}

建立目標定位工作流程時，如果核准是自動的（預設模式），Adobe Campaign會顯示核准連結，或在需要核準時立即傳送通知。

若要選擇核准模式（手動或自動），請按一下 **[!UICONTROL Edit > Properties]** 行銷活動或行銷活動範本的標籤，然後按一下 **[!UICONTROL Advanced campaign settings...]** 最後是 **[!UICONTROL Approvals]** 標籤。

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>選取的核准模式將套用至行銷活動的所有傳遞。

建立目標定位工作流程時，手動核准可讓您避免自動建立核准連結或傳送通知。 行銷活動控制面板接著提供 **[!UICONTROL Submit targeting for approval]** 連結以手動啟動核准流程。

確認訊息可讓您針對為此傳遞選取的工作，授權核准。

核准按鈕隨即會顯示在行銷活動控制面板（針對此傳遞）、傳遞控制面板及傳遞追蹤中。 如果已啟用通知，則會同時傳送通知。

此啟用核准的方法可讓您進行目標定位，而不會傳送虛假通知給稽核者。

## 通知 {#notifications}

通知是傳送給稽核者的特定電子郵件訊息，以通知他們流程正在等候核准。 當操作員按一下訊息中的連結時，驗證頁面就會顯示，在登入之後，操作員就可以檢視資訊，並核准或拒絕工作。 您也可以在核准視窗中輸入註解。

通知電子郵件的內容可以個人化。 另請參閱 [通知內容](#notification-content).

### 啟用/停用通知 {#enabling-disabling-notification}

根據預設，如果在行銷活動範本、行銷活動或傳遞中啟用相關工作的核准，則會傳送通知訊息。 但是，可以停用通知，以便僅從主控台授權核准。

若要這麼做，請編輯行銷活動或行銷活動範本的核准視窗( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** 標籤)並選取 **[!UICONTROL Do not enable notification sending]**.

![](assets/s_user_validation_notif_desactivate.png)

### 通知內容 {#notification-content}

通知內容是在特定範本中定義的： **[!UICONTROL Notification of validations for the marketing campaign]**. 此範本儲存在 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** Adobe Campaign樹的資料夾。

## 檢閱和核准傳遞 {#checking-and-approving-deliveries}

Adobe Campaign可讓您以合作模式，為行銷活動的主要階段設定核准流程。

如果是直接郵件傳送，Adobe Campaign操作員可在解壓縮檔案傳送至路由器前檢視解壓縮檔案，並可視需要變更格式及重新啟動解壓縮。 另請參閱 [核准擷取檔案](#approving-an-extraction-file).

您可以針對每個行銷活動核准傳遞目標、內容(請參閱 [核准內容](#approving-content))和成本。 可以透過電子郵件形式通知負責核准的 Adobe Campaign 操作者，然後他們可透過主控台或網路連線核准或拒絕核准。另請參閱 [核准傳遞的步驟](#approving-processes).

完成這些驗證階段後，即可啟動傳送。 [了解更多](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)。

### 核准傳遞的步驟 {#approving-processes}

需要核准的階段會顯示在行銷活動控制面板上（透過網頁介面的主控台）。 它們也會顯示在傳送追蹤表格和傳送控制面板上。

此時，行銷活動的狀態為 **[!UICONTROL To validate]**.

>[!NOTE]
>
>若要選取需要核准的程式，請修改行銷活動範本。 有關詳細資訊，請參閱 [行銷活動範本](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>在目標定位工作流程中，如果在訊息準備期間發生連結至設定問題的錯誤， **[!UICONTROL Restart message preparation]** 連結會顯示在控制面板上。 更正錯誤，然後按一下此連結，在略過目標階段時重新啟動訊息準備。

![](assets/s_user_validation_relaunch_message_preparation.png)

對於行銷活動中的每個傳遞，您可以核准以下流程：

* **目標定位、內容和預算**

   當 **[!UICONTROL Enable target approval]**， **[!UICONTROL Enable content approval]** 或 **[!UICONTROL Enable budget approval]** 在「工作核准設定」視窗中選取選項，相關連結會顯示在相關傳送的促銷活動控制面板中。

   >[!NOTE]
   >
   >只有在核准設定視窗中啟用目標核準時，才可使用預算核准。 只有在分析目標之後，才會顯示預算核准連結。 此外，此連結會與供目標核准的連結一起顯示。

   如果 **[!UICONTROL Assign content editing]** 或 **[!UICONTROL External content approval]** 在核准設定視窗中選取選項，儀表板將顯示 **[!UICONTROL Available content]** 和 **[!UICONTROL External content approval]** 連結。

   內容核准可讓您存取已傳送的校樣。

* **摘取核准（直接郵件傳送）**

   時間 **[!UICONTROL Enable extraction approval]** 在核准設定視窗中選取時，擷取的檔案必須先經過核准，才能通知路由器。

   一個 **[!UICONTROL Approve content]** 行銷活動控制面板上的可用連結，如下所示：

   ![](assets/s_ncs_user_edit_file_valid.png)

   擷取檔案可透過核准方塊預覽，然後接受或拒絕。

   ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

   >[!NOTE]
   >
   >擷取檔案預覽僅涉及資料範例。 未載入整個輸出檔案。

* **核准關聯的傳遞**

   此 **[!UICONTROL Enable individual approval of each associated delivery]** 選項適用於與次要傳遞相關聯的主要傳遞。 依預設，不會選取此選項，以便執行主要傳送的整體核准。 如果選取此選項，則必須個別核准每個傳遞。

   ![](assets/s_ncs_user_task_valid_associate.png)

### 選取核准的程式 {#choosing-the-processes-to-be-approved}

核准階段會使用與行銷活動相關聯的範本來定義。 您必須從範本中選取要核准的元素，並指定負責這些核准的Adobe Campaign運運算元。 如需行銷活動範本的詳細資訊，請參閱 [本節](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

>[!NOTE]
>
>行銷活動（或行銷活動範本）的核准設定會套用至連結至此行銷活動的所有未來傳遞。 任何設定變更都不會套用至先前的傳遞。

可針對每個行銷活動和每個傳遞覆寫此資訊。

若為促銷活動，請按一下 **[!UICONTROL Edit > Properties]** 標籤，然後 **[!UICONTROL Advanced campaign settings...]** 連結，最後是 **[!UICONTROL Approvals]** 子標籤以存取「核准設定」頁面。

您可以選取和取消選取要核准的程式，並指定負責核准的Adobe Campaign操作員。 這些可以是個別運運算元、一組運運算元或運運算元清單。

若要選取運運算元清單，請按一下 **[!UICONTROL Edit...]** 指向欄位右側的連結，指定第一個稽核者，並視需要新增運運算元，如下所示：

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* 如果已定義稽核者清單，當稽核者接受工作時，就會核准工作。 然後，控制面板中就不會再提供相關的核准連結。 啟用通知傳送後，如果其他稽核者按一下通知訊息中的核准連結，系統會通知他們其他操作員已核准該工作。
>* 您可以在稽核者編輯視窗的下半部定義行銷活動的核准排程。 依預設，稽核者從提交日期起有三天時間來核准流程。 您可以設定提醒，在核准期限之前自動傳送給相關操作員。
>* 您可以從此區段新增提醒。
>


![](assets/s_ncs_user_edit_op_valid_calendar.png)

對於每個傳送，按一下 **[!UICONTROL Audit]** 按鈕和 **[!UICONTROL Approvals]** 標籤以檢視和編輯核准日期和自動提醒。

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>內容核准程式啟動後，即可使用此索引標籤。

### 核准內容 {#approving-content}

>[!CAUTION]
>
>若要核准內容，校訂週期是強制性的。 校樣可讓您核准顯示資訊、個人化資料並檢查連結是否正常運作。 瞭解如何在中建立校訂 [本節](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).
>
>下文詳述的內容核准功能與證明傳送有關。

您可以設定內容核准週期。 若要這麼做，請選取 **[!UICONTROL Enable content approval]** 選項。 內容核准週期的主要步驟如下：

1. 建立新傳送後，行銷活動經理按一下 **[!UICONTROL Submit content]** 行銷活動控制面板上的連結，以開始內容核准週期。

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Enable the sending of proofs]** 選項（用於電子郵件傳遞）或 **[!UICONTROL Enable the sending and approval of proofs]** （針對直接郵件傳送）選項已在核准設定視窗中選取，則會自動傳送校樣。

1. 系統會傳送通知電子郵件給負責內容的人，由他們選擇是否核准：

   * 透過通知電子郵件：

      ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

      >[!NOTE]
      >
      >通知電子郵件包含已傳送校樣的連結，而且如果 **傳遞能力** 選項已針對此執行個體啟用。

   * 透過主控台或網頁介面、傳遞追蹤、傳遞控制面板或行銷活動控制面板：

      ![](assets/s_ncs_user_validation_content_bat_op.png)

      >[!NOTE]
      >
      >此行銷活動儀表板可讓您按一下 **[!UICONTROL Inbox rendering...]** 連結。 若要檢視其內容，請按一下 **[!UICONTROL Detail]** 圖示加以顯示。

      ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. 系統會傳送通知電子郵件給行銷活動的負責人，通知他們內容是否已核准。

   >[!NOTE]
   >
   >行銷活動的負責人可以隨時重新開始內容核准週期。 若要這麼做，請按一下 **[!UICONTROL Content status]** 行銷活動控制面板的行（在傳遞層級），然後按一下 **[!UICONTROL Reset content approval to submit it again]**.

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### 指派內容編輯 {#assign-content-editing}

此選項可讓您定義負責內容編輯的人員，例如網站管理員。 如果 **[!UICONTROL Assign content editing]** 在「核准設定」視窗中選取選項，在建立傳遞與將通知電子郵件傳送給負責內容之人員之間會新增數個核准步驟：

1. 建立新傳送後，行銷活動的負責人按一下 **[!UICONTROL Submit content editing]** 行銷活動控制面板中的連結，以開始內容編輯週期。

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. 負責內容編輯的人員會收到電子郵件，通知他們內容可用。

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. 接著，他們可以登入主控台、開啟傳遞，並使用簡化的精靈進行編輯，以變更主題、HTML和文字內容，以及傳送校樣。

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Enable the sending of proofs]** 選項（用於電子郵件傳遞）或 **[!UICONTROL Enable the sending and approval of proofs]** （針對直接郵件傳送）選項已在核准設定視窗中選取，則會自動傳送校樣。

1. 一旦負責內容編輯的人員完成對傳送內容的任何變更，他們就可以提供內容。

   要執行此操作，他們可以：

   * 按一下 **[!UICONTROL Available content]** 透過Adobe Campaign主控台連結。

      ![](assets/s_ncs_user_validation_submit_content_available.png)

   * 按一下通知訊息中的連結，然後核准內容可用性。

      ![](assets/s_ncs_user_validation_submit_content_available2.png)

      操作員可在將內容提交至行銷活動負責人之前新增註解。

      ![](assets/s_ncs_user_validation_submit_content_available3.png)

      通知訊息可讓稽核者核准或拒絕內容。

      ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### 外部內容核准 {#external-content-approval}

此選項可讓您定義負責核准傳遞呈現（例如品牌通訊一致性、費率等）的外部運運算元。 當 **[!UICONTROL External content approval]** 在「核准設定」視窗中選取選項，在內容核准與將通知傳送給行銷活動負責人之間會新增數個核准步驟：

1. 外部內容管理員會收到通知電子郵件，告知他們內容已核准並請求外部核准。
1. 通知電子郵件包含已傳送校樣的連結（可讓您檢視傳遞呈現），以及核准或拒絕傳遞內容的按鈕。

   >[!NOTE]
   >
   >只有在已傳送一或多個校樣時，才可使用這些連結。 否則，傳遞呈現只能透過主控台或Web介面使用。

   ![](assets/s_user_validation_external_content.png)

### 核准擷取檔案 {#approving-an-extraction-file}

離線傳送時，Adobe Campaign會產生擷取檔案，並依據其設定方式傳送至路由器。 其內容取決於所使用的匯出範本。

內容、目標定位和預算獲得核准後，傳遞內容會變更為 **[!UICONTROL Extraction pending]** 直到啟動行銷活動的擷取工作流程為止。

![](assets/s_ncs_user_waiting_file_extraction.png)

在擷取請求日期，會建立擷取檔案並變更傳遞狀態 **[!UICONTROL File to approve]**.

![](assets/s_ncs_user_file_extract_to_valid.png)

您可以檢視解壓縮檔案的內容（按一下其名稱）、核准檔案，或視需要變更格式，然後使用控制面板上的連結重新開始解壓縮。

一旦檔案獲得核准，您就可以將通知電子郵件傳送給路由器。 有關詳細資訊，請參閱 [開始離線傳遞](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery).
