---
product: campaign
title: 設定及管理核准流程
description: 了解如何管理行銷活動的核准
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Approvals, Campaigns
exl-id: 8cbb2445-f5e4-4a25-ba7e-56e39ca9d3ce
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '2438'
ht-degree: 2%

---

# 設定及管理核准流程 {#approving-marketing-campaigns}


傳遞的每個步驟都需經過核准，以確保完整監控及控制促銷活動的各種程式：鎖定目標、內容、預算、擷取和傳送校樣。

通知訊息會傳送給指定審核者的Adobe Campaign運算子，以通知他們核准請求。 檢查審核者是否擁有 **適當權限** ，且其安全區域已正確定義。 [了解更多](#selecting-reviewers)。

批准程式於 [本節](#checking-and-approving-deliveries).

>[!NOTE]
>
>只有傳送擁有者才能開始傳送。 為了讓其他運算子（或運算子群組）能夠開始傳送，您必須在 **[!UICONTROL Delivery start:]** 欄位。\
>[了解更多](#selecting-reviewers)。

## 操作原則 {#operating-principle-}

例如，用於預算審批的標準消息如下：

![](assets/s_user_validation_link_in_mail.png)

然後，審核者操作員可以選擇批准預算。

![](assets/s_user_validation_page_confirm.png)

一旦運算子驗證，作業的核准或拒絕即會轉送至傳送控制面板。

![](assets/s_user_validation_link_in_op_board.png)

此資訊也可在促銷活動的核准記錄中取得。這些記錄檔可透過 **[!UICONTROL Edit > Tracking > Approvals]** 標籤。

![](assets/s_user_validation_log_in_op_edit_tab.png)

這些通知會傳送給對每個已啟用核准的程式造成影響的運算子。

可針對促銷活動範本、個別針對每個促銷活動或傳送啟用核准。

在促銷活動範本中選取所有需要核准的作業( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** 標籤)，負責核准的運算子也一樣（除非未啟用此選項，否則他們會收到通知）。 如需詳細資訊，請參閱[本章節](#approving-processes)。

使用此範本建立的每個促銷活動，以及每個促銷活動傳送的個別設定，都可以覆寫這些設定：按一下 **[!UICONTROL Properties]** 按鈕，然後 **[!UICONTROL Approvals]** 標籤。

在下列範例中，傳送內容不需要核准：

![](assets/s_user_validation_select_process_from_del.png)

## 選擇審閱者 {#selecting-reviewers}

對於每種類型的批准，負責批准的運算子或運算子組將從傳送的下拉清單中選擇。 可使用 **[!UICONTROL Edit...]** 連結。 此窗口還允許您編輯審批截止日期。

![](assets/s_user_validation_add_operator.png)

如果未指定審核者，則行銷活動管理員將負責核准並接收通知。 促銷活動管理員是在 **[!UICONTROL Edit > Properties]** 行銷活動的標籤：

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>所有其他Adobe Campaign運算子(含 **[!UICONTROL Administrator]** 權限也可以核准工作，但不會收到通知。\
>依預設，如果已定義核准運算子，則促銷活動管理員無法執行核准或開始傳送。 您可以修改此行為，並透過建立 **NmsCampaign_Activate_OwnerConfirmation** 選項 **1** 作為值。

## 核准模式 {#approval-modes}

### 透過控制面板進行核准 {#approval-via-the-dashboard}

若要透過主控台或Web介面核准作業，請按一下促銷活動控制面板上的適當連結。 作業也可以透過傳遞追蹤或傳遞控制面板來核准。

![](assets/s_user_validation_from_console.png)

檢查要批准的資訊，選擇是否接受或拒絕批准，並在必要時輸入備注。 按一下 **[!UICONTROL Ok]** 儲存。

>[!NOTE]
>
>如果某個流程已經由其他操作員批准，則該批准連結不可用。

### 透過通知訊息進行核准 {#approval-via-notification-messages}

按一下通知訊息中可用的連結(請參閱 [通知](#notifications))。 您需要登入，如下所示：

![](assets/s_user_validation__log_in.png)

選擇 **[!UICONTROL Accept]** 或 **[!UICONTROL Reject]** 並視需要輸入注釋。

![](assets/s_user_validation_save_target_validation.png)

按一下&#x200B;**[!UICONTROL Validate]**。

>[!NOTE]
>
>如果在處理期間引發警告，則通知中會顯示警告。

### 核准追蹤 {#approval-tracking}

此資訊可在數個位置取得：

* 在促銷活動核准記錄中， **[!UICONTROL Approvals]** 的子標籤 **[!UICONTROL Edit > Tracking]** 標籤：

   ![](assets/s_user_validation_log_from_op.png)

* 在促銷活動傳送記錄中， **[!UICONTROL Deliveries]** 的子標籤 **[!UICONTROL Edit > Tracking]** 標籤：

   ![](assets/s_user_validation_log_from_delivery_list.png)

* 您可以按一下 **[!UICONTROL Hide/show log]** 選項 **[!UICONTROL Summary]** 標籤。

   ![](assets/s_user_validation_log_delivery.png)

* 此資訊也可透過 **[!UICONTROL Tracking > Approvals]** 索引標籤：

   ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>一旦操作員批准或拒絕了某個作業，其他審閱操作員就無法再對批准執行操作。

### 自動和手動核准 {#automatic-and-manual-approval}

建立目標工作流程時，如果核准是自動（預設模式）,Adobe Campaign會顯示核准連結，或在需要核準時立即傳送通知。

若要選擇核准模式（手動或自動），請按一下 **[!UICONTROL Edit > Properties]** 標籤，然後按一下 **[!UICONTROL Advanced campaign settings...]** 最後 **[!UICONTROL Approvals]** 標籤。

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>選取的核准模式將套用至促銷活動的所有傳送。

建立目標工作流程時，手動核准可讓您避免建立核准連結或自動傳送通知。 然後，促銷活動控制面板會提供 **[!UICONTROL Submit targeting for approval]** 連結以手動啟動核准程式。

確認訊息可讓您授權核准為此傳送選取的作業。

然後核准按鈕會顯示在促銷活動控制面板（針對此傳送）、傳遞控制面板和傳遞追蹤中。 如果啟用通知，則會同時傳送。

此啟用核准的方法可讓您處理鎖定目標作業，而不傳送假通知給審核者。

## 通知 {#notifications}

通知是傳送給審核者的特定電子郵件訊息，以通知他們某個程式正在等待核准。 當操作員按一下消息中的連結時，將顯示驗證頁，在登錄後，操作員可以查看資訊並批准或拒絕作業。 也可以在審批窗口中輸入注釋。

通知電子郵件的內容可個人化。 請參閱 [通知內容](#notification-content).

### 啟用/禁用通知 {#enabling-disabling-notification}

依預設，如果在促銷活動範本、促銷活動或傳送中啟用相關工作的核准，則會傳送通知訊息。 但是，可以禁用通知，以便僅從控制台授權批准。

要執行此操作，請編輯促銷活動或促銷活動範本的核准視窗( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** 頁簽) **[!UICONTROL Do not enable notification sending]**.

![](assets/s_user_validation_notif_desactivate.png)

### 通知內容 {#notification-content}

通知內容在特定範本中定義： **[!UICONTROL Notification of validations for the marketing campaign]**. 此範本會儲存在 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** Adobe Campaign樹的資料夾。

## 檢閱及核准傳送 {#checking-and-approving-deliveries}

Adobe Campaign可讓您以協作模式，為行銷活動的主要階段設定核准程式。

對於直接郵件傳遞，Adobe Campaign操作員可以在將解壓縮檔案發送到路由器之前查看該檔案，如有必要，他們可以更改格式並重新啟動解壓縮。 請參閱 [核准解壓縮檔案](#approving-an-extraction-file).

對於每個行銷活動，您可以核准傳送目標，內容(請參閱 [核准內容](#approving-content))和成本。 可以透過電子郵件形式通知負責核准的 Adobe Campaign 操作者，然後他們可透過主控台或網路連線核准或拒絕核准。請參閱 [核准傳送的步驟](#approving-processes).

完成這些驗證階段後，即可啟動傳送。 [了解更多](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)。

### 核准傳送的步驟 {#approving-processes}

需要核准的階段會顯示在促銷活動控制面板上（透過網頁介面的主控台）。 它們也會出現在傳送追蹤表格和傳送控制面板中。

此時，促銷活動的狀態為 **[!UICONTROL To validate]**.

>[!NOTE]
>
>若要選取需要核准的程式，請修改促銷活動範本。 有關詳細資訊，請參閱 [行銷活動範本](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>在目標工作流程中，如果在訊息準備期間發生連結至設定問題的錯誤，則 **[!UICONTROL Restart message preparation]** 連結會顯示在控制面板上。 請更正錯誤，然後按一下此連結以在略過定位階段時重新啟動訊息準備。

![](assets/s_user_validation_relaunch_message_preparation.png)

對於促銷活動中的每個傳送，您可以核准下列程式：

* **目標、內容和預算**

   當 **[!UICONTROL Enable target approval]**, **[!UICONTROL Enable content approval]** 或 **[!UICONTROL Enable budget approval]** 選項，相關連結會顯示在相關傳送的促銷活動控制面板中。

   >[!NOTE]
   >
   >只有在「審批設定」窗口中啟用了目標審批時，才可使用預算審批。 只有分析目標後，才會顯示預算核准連結。 此外，此連結會與要進行目標核准的連結一起顯示。

   若 **[!UICONTROL Assign content editing]** 或 **[!UICONTROL External content approval]** 選項，控制面板將顯示 **[!UICONTROL Available content]** 和 **[!UICONTROL External content approval]** 連結。

   內容核准可讓您存取傳送的校樣。

* **提取核准（直接郵件傳送）**

   當 **[!UICONTROL Enable extraction approval]** 在「批准設定」窗口中選中，則必須先批准提取的檔案，然後才能通知路由器。

   安 **[!UICONTROL Approve content]** 連結可在促銷活動控制面板上使用，如下所示：

   ![](assets/s_ncs_user_edit_file_valid.png)

   解壓縮檔案可透過核准方塊預覽，然後接受或拒絕。

   ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

   >[!NOTE]
   >
   >擷取檔案預覽僅涉及資料範例。 未載入整個輸出檔案。

* **核准相關傳遞**

   此 **[!UICONTROL Enable individual approval of each associated delivery]** 選項會用於與次要傳送相關聯的主要傳送。 依預設，不會選取此選項，以執行主要傳送的整體核准。 如果選取此選項，則每個傳送都必須個別核准。

   ![](assets/s_ncs_user_task_valid_associate.png)

### 選擇審批流程 {#choosing-the-processes-to-be-approved}

核准階段會與與促銷活動相關聯的範本一起定義。 您必須從範本中選取要核准的元素，並指定負責這些核准的Adobe Campaign運算子。 如需促銷活動範本的詳細資訊，請參閱 [本節](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

>[!NOTE]
>
>促銷活動（或促銷活動範本）的核准設定會套用至連結至此促銷活動的所有未來傳送。 任何設定變更都不會套用至先前的傳送。

可針對每個促銷活動和每個傳送覆寫此資訊。

若為促銷活動，請按一下 **[!UICONTROL Edit > Properties]** ，然後 **[!UICONTROL Advanced campaign settings...]** 連結，最後 **[!UICONTROL Approvals]** 頁簽，訪問「批准配置」頁。

您可以選取和取消選取流程，以核准和指定負責核准的Adobe Campaign運算子。 這些可以是個別運算子、運算子群組或運算子清單。

若要選取運算子清單，請按一下 **[!UICONTROL Edit...]** 連結至指定第一個審核者的欄位右側，並視需要新增多個運算子，如下所示：

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* 如果定義了審核者清單，則當一個審核者接受該清單時，將批准該作業。 控制面板中就不再提供相關的核准連結。 啟用通知發送時，如果另一個審核者按一下通知消息中的批准連結，則通知他們另一個操作員已批准該作業。
>* 您可以在審核者編輯視窗的下半部定義促銷活動的核准排程。 依預設，審核者自提交日期起有三天時間核准程式。 可以配置提醒，該提醒在批准截止日期之前自動發送給相關操作員。
>* 您可以從此部分添加提醒。
>


![](assets/s_ncs_user_edit_op_valid_calendar.png)

對於每個傳送，按一下 **[!UICONTROL Audit]** 按鈕和 **[!UICONTROL Approvals]** 頁簽來查看和編輯批准日期和自動提醒。

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>內容核准程式啟動後，即可使用此標籤。

### 核准內容 {#approving-content}

>[!CAUTION]
>
>若要核准內容，校樣週期是必填的。 校樣可讓您核准資訊、個人化資料的顯示，並檢查連結是否運作中。 了解如何在 [本節](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).
>
>下文詳述的內容核准功能與證明傳送有關。

您可以設定內容核准週期。 若要這麼做，請選取 **[!UICONTROL Enable content approval]** 選項。 內容核准週期的主要步驟為：

1. 建立新傳遞後，行銷活動管理員按一下 **[!UICONTROL Submit content]** 連結至促銷活動控制面板，以啟動內容核准週期。

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >若 **[!UICONTROL Enable the sending of proofs]** 選項（用於電子郵件傳送）或 **[!UICONTROL Enable the sending and approval of proofs]** （針對直接郵件傳送）選項（在核准設定視窗中選取）時，會自動傳送校樣。

1. 系統會傳送通知電子郵件給負責內容的人員，由他們選擇是否要核准：

   * 透過通知電子郵件：

      ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

      >[!NOTE]
      >
      >通知電子郵件包含已傳送校樣的連結，若 **傳遞能力** 選項。

   * 透過主控台或網頁介面、傳遞追蹤、傳遞控制面板或行銷活動控制面板：

      ![](assets/s_ncs_user_validation_content_bat_op.png)

      >[!NOTE]
      >
      >此促銷活動控制面板可讓您按一下 **[!UICONTROL Inbox rendering...]** 連結。 若要檢視其內容，請按一下 **[!UICONTROL Detail]** 表徵圖。

      ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. 系統會傳送通知電子郵件給負責促銷活動的人員，通知他們內容是否已核准。

   >[!NOTE]
   >
   >負責促銷活動的人員可隨時重新啟動內容核准週期。 若要這麼做，請按一下 **[!UICONTROL Content status]** 行（在傳送層級），然後按一下 **[!UICONTROL Reset content approval to submit it again]**.

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### 指派內容編輯 {#assign-content-editing}

此選項可讓您定義負責內容編輯的人員，例如網站管理員。 若 **[!UICONTROL Assign content editing]** 選項，則在傳送建立和傳送通知電子郵件給內容負責人之間會新增數個核准步驟：

1. 建立新傳送後，負責促銷活動的人員會點按 **[!UICONTROL Submit content editing]** 在促銷活動控制面板中連結，以開始內容編輯週期。

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. 負責內容編輯的人員會收到電子郵件，告知他們內容可供使用。

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. 然後，他們就可以登入主控台、開啟傳送，並使用簡化精靈加以編輯，以變更主旨、HTML和文字內容，並傳送校樣。

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >若 **[!UICONTROL Enable the sending of proofs]** 選項（用於電子郵件傳送）或 **[!UICONTROL Enable the sending and approval of proofs]** （針對直接郵件傳送）選項（在核准設定視窗中選取）時，會自動傳送校樣。

1. 負責內容編輯的人員完成對傳送內容的任何變更後，即可使用該內容。

   若要這麼做，他們可以：

   * 按一下 **[!UICONTROL Available content]** 透過Adobe Campaign主控台連結。

      ![](assets/s_ncs_user_validation_submit_content_available.png)

   * 按一下通知訊息中的連結，然後核准內容可用性。

      ![](assets/s_ncs_user_validation_submit_content_available2.png)

      運算子可以先新增留言，再將內容提交給行銷活動的負責人。

      ![](assets/s_ncs_user_validation_submit_content_available3.png)

      通知訊息可讓審核者核准或拒絕內容。

      ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### 外部內容核准 {#external-content-approval}

此選項可讓您定義負責核准傳遞轉譯的外部運算子，例如品牌通訊一致性、比率等。 當 **[!UICONTROL External content approval]** 選項，則內容核准和將通知傳送給行銷活動負責人之間會新增數個核准步驟：

1. 外部內容管理員會收到通知電子郵件，告知他們內容已獲核准，並請求外部核准。
1. 通知電子郵件包含傳送之校樣的連結，可讓您檢視傳送呈現，以及核准或拒絕傳送內容的按鈕。

   >[!NOTE]
   >
   >只有已傳送一或多個校樣時，這些連結才可用。 否則，傳遞呈現只能透過主控台或Web介面使用。

   ![](assets/s_user_validation_external_content.png)

### 核准解壓縮檔案 {#approving-an-extraction-file}

對於離線傳遞，Adobe Campaign會產生解壓縮檔案，該檔案會根據設定方式傳送至路由器。 其內容取決於使用的匯出範本。

當內容、目標和預算獲得核准後，傳送會變更為 **[!UICONTROL Extraction pending]** 直到啟動促銷活動的擷取工作流程為止。

![](assets/s_ncs_user_waiting_file_extraction.png)

提取請求日期時，會建立提取檔案，且傳送狀態變更為 **[!UICONTROL File to approve]**.

![](assets/s_ncs_user_file_extract_to_valid.png)

您可以檢視擷取的檔案內容（按一下檔案名稱）、核准檔案，或視需要變更格式，然後使用控制面板上的連結重新啟動擷取。

檔案獲得批准後，您就可以向路由器發送通知電子郵件。 有關詳細資訊，請參閱 [開始離線傳送](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery).
