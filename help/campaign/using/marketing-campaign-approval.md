---
product: campaign
title: 批准市場營銷活動
description: 瞭解如何管理營銷活動的批准
audience: campaign
exl-id: 8cbb2445-f5e4-4a25-ba7e-56e39ca9d3ce
source-git-commit: d3f5c56078ddac7597925191fd347bdcab61714d
workflow-type: tm+mt
source-wordcount: '2434'
ht-degree: 2%

---

# 設定及管理核准流程 {#approving-marketing-campaigns}

![](../../assets/common.svg)

交付的每個步驟都需經過批准，以確保充分監控和控制活動的各種過程：目標、內容、預算、提取和發送證據。

通知消息被發送給被指定審核者的Adobe Campaign操作員，以通知他們批准請求。 檢查審閱人是否 **適當權限** 以便批准，並且其安全區定義正確。 [了解更多](#selecting-reviewers)。

審批程式在 [此部分](#checking-and-approving-deliveries)。

>[!NOTE]
>
>只有交貨所有者才能啟動交貨。 要使其他運算子（或運算子組）能夠啟動交付，您必須將它們添加為 **[!UICONTROL Delivery start:]** 的子菜單。\
>[了解更多](#selecting-reviewers)。

## 操作原則 {#operating-principle-}

例如，預算審批的標準消息如下：

![](assets/s_user_validation_link_in_mail.png)

然後，審閱者操作員可以選擇是否批准預算。

![](assets/s_user_validation_page_confirm.png)

一旦操作員驗證，作業的批准或拒絕將轉發到交貨控制面板。

![](assets/s_user_validation_link_in_op_board.png)

市場活動的批准日誌中也提供了此資訊。這些日誌通過 **[!UICONTROL Edit > Tracking > Approvals]** 頁籤。

![](assets/s_user_validation_log_in_op_edit_tab.png)

這些通知將發送給對啟用審批的每個流程有影響的操作員。

可以為市場活動模板、每個市場活動或交貨啟用審批。

在市場活動模板中選擇所有需要審批的作業( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** 頁籤)，負責審批的運算子（除非未啟用此選項，否則它們將接收通知）。 如需詳細資訊，請參閱[本章節](#approving-processes)。

可以使用此模板建立的每個市場活動以及每個市場活動交付分別覆蓋這些設定：按一下 **[!UICONTROL Properties]** 按鈕 **[!UICONTROL Approvals]** 頁籤。

在以下示例中，交付內容不需要批准：

![](assets/s_user_validation_select_process_from_del.png)

## 選擇審閱者 {#selecting-reviewers}

對於每種類型的審批，負責審批的操作員或操作員組都從交貨中的下拉清單中進行選擇。 可以使用 **[!UICONTROL Edit...]** 的子菜單。 此窗口還允許您編輯審批截止時間。

![](assets/s_user_validation_add_operator.png)

如果未指定審核者，市場活動經理將負責審批並接收通知。 市場活動經理在 **[!UICONTROL Edit > Properties]** 頁籤：

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>所有其他Adobe Campaign運營商 **[!UICONTROL Administrator]** 權限也可以批准作業，但不會接收通知。\
>預設情況下，如果已定義審批運算子，市場活動經理將無法執行審批或啟動交貨。 您可以修改此行為，並通過建立 **NmsCampaign_Activate_OwnerConfirmation** 選項 **1** 值。

## 審批模式 {#approval-modes}

### 通過儀表板審批 {#approval-via-the-dashboard}

要通過控制台或Web介面批准作業，請按一下市場活動控制面板上的相應連結。 作業也可以通過交貨跟蹤或交貨控制板獲得批准。

![](assets/s_user_validation_from_console.png)

檢查要審批的資訊，選擇是接受還是拒絕審批，並在必要時輸入注釋。 按一下 **[!UICONTROL Ok]** 來保存。

>[!NOTE]
>
>如果某個進程已經由其他操作員批准，則該批准連結不可用。

### 通過通知消息審批 {#approval-via-notification-messages}

按一下通知消息中可用的連結(請參見 [通知](#notifications))。 您需要登錄，如下所示：

![](assets/s_user_validation__log_in.png)

選擇 **[!UICONTROL Accept]** 或 **[!UICONTROL Reject]** 並輸入注釋（如果需要）。

![](assets/s_user_validation_save_target_validation.png)

按一下&#x200B;**[!UICONTROL Validate]**。

>[!NOTE]
>
>如果在流程中引發警告，則通知中將顯示警告。

### 審核跟蹤 {#approval-tracking}

資訊可在以下幾個地方獲得：

* 在市場活動批准日誌中， **[!UICONTROL Approvals]** 頁籤 **[!UICONTROL Edit > Tracking]** 頁籤：

   ![](assets/s_user_validation_log_from_op.png)

* 在市場活動交付日誌中， **[!UICONTROL Deliveries]** 頁籤 **[!UICONTROL Edit > Tracking]** 頁籤：

   ![](assets/s_user_validation_log_from_delivery_list.png)

* 按一下 **[!UICONTROL Hide/show log]** 選項 **[!UICONTROL Summary]** 頁籤。

   ![](assets/s_user_validation_log_delivery.png)

* 此資訊也可以通過 **[!UICONTROL Tracking > Approvals]** 頁籤：

   ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>一旦操作員批准或拒絕了某個作業，其他複查操作員就無法再對批准執行操作。

### 自動和手動審批 {#automatic-and-manual-approval}

在建立目標工作流時，如果批准是自動（預設模式）,Adobe Campaign將顯示批准連結或在需要批准時立即發送通知。

要選擇審批模式（手動或自動），請按一下 **[!UICONTROL Edit > Properties]** 頁籤，然後按一下 **[!UICONTROL Advanced campaign settings...]** 最後 **[!UICONTROL Approvals]** 頁籤。

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>選定的審批模式將應用於市場活動的所有交貨。

在構建目標工作流時，手動審批允許您避免建立審批連結或自動發送通知。 然後，市場活動控制板提供 **[!UICONTROL Submit targeting for approval]** 連結以手動啟動審批流程。

通過確認消息，您可以授權對為此傳遞選擇的作業進行批准。

然後，批准按鈕將顯示在市場活動控制面板（用於此交貨）、交貨控制面板和交貨跟蹤中。 如果啟用通知，則將並行發送。

啟用批准的這種方法使您能夠在不向審閱者發送虛假通知的情況下進行目標確定。

## 通知 {#notifications}

通知是發送給審閱者的特定電子郵件，用於通知他們某個進程正在等待批准。 當操作員按一下消息中的連結時，將顯示驗證頁，在登錄後，操作員可以查看資訊並批准或拒絕作業。 也可以在審批窗口中輸入注釋。

通知電子郵件的內容可以個性化。 請參閱 [通知內容](#notification-content)。

### 啟用/禁用通知 {#enabling-disabling-notification}

預設情況下，如果在市場活動模板、市場活動或交貨中啟用了相關作業的審批，則會發送通知消息。 但是，可以禁用通知，以僅授權控制台的批准。

為此，請編輯市場活動或市場活動模板的審批窗口( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** ) **[!UICONTROL Do not enable notification sending]**。

![](assets/s_user_validation_notif_desactivate.png)

### 通知內容 {#notification-content}

通知內容在特定模板中定義： **[!UICONTROL Notification of validations for the marketing campaign]**。 此模板保存在 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** Adobe Campaign樹的資料夾。

## 審閱和批准交貨 {#checking-and-approving-deliveries}

Adobe Campaign允許您以協作模式為市場營銷活動的主要階段設定審批流程。

對於直接郵寄，Adobe Campaign操作員可以在提取檔案發送到路由器之前查看該檔案，如有必要，他們可以更改格式並重新啟動提取。 請參閱 [批准提取檔案](#approving-an-extraction-file)。

對於您可以批准交付目標的每個市場活動，內容(請參閱： [審核內容](#approving-content))和成本。 可以透過電子郵件形式通知負責核准的 Adobe Campaign 操作者，然後他們可透過主控台或網路連線核准或拒絕核准。請參閱 [批准交貨的步驟](#approving-processes)。

完成這些驗證階段後，可啟動交付。 [了解更多](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery)。

### 批准交貨的步驟 {#approving-processes}

需要批准的階段顯示在市場活動控制面板（通過Web介面的控制台）上。 它們還顯示在交貨跟蹤表和交貨控制板中。

此時，市場活動的狀態為 **[!UICONTROL To validate]**。

>[!NOTE]
>
>要選擇需要審批的流程，請修改市場活動模板。 有關此內容的詳細資訊，請參閱 [市場活動模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>在目標工作流中，如果在消息準備過程中出現連結到配置問題的錯誤， **[!UICONTROL Restart message preparation]** 連結顯示在儀表板上。 更正錯誤並按一下此連結以在繞過目標階段時重新啟動消息準備。

![](assets/s_user_validation_relaunch_message_preparation.png)

對於市場活動中的每個交貨，您都可以審批以下流程：

* **目標、內容和預算**

   當 **[!UICONTROL Enable target approval]**。 **[!UICONTROL Enable content approval]** 或 **[!UICONTROL Enable budget approval]** 選項在「任務審批設定」窗口中選擇，相關連結顯示在市場活動控制面板中相關交貨。

   >[!NOTE]
   >
   >僅當在審批設定窗口中啟用了目標審批時，預算審批才可用。 只有分析目標後，才顯示預算審批連結。 此外，此連結與用於目標審批的連結一起顯示。

   如果 **[!UICONTROL Assign content editing]** 或 **[!UICONTROL External content approval]** 選項在批准設定窗口中選中，控制板將顯示 **[!UICONTROL Available content]** 和 **[!UICONTROL External content approval]** 連結。

   內容批准允許您訪問發送的校樣。

* **提取審批（直接郵寄）**

   當 **[!UICONTROL Enable extraction approval]** 在「批准設定」窗口中選擇，在通知路由器之前必須批准提取的檔案。

   安 **[!UICONTROL Approve content]** 連結在市場活動控制面板上可用，如下所示：

   ![](assets/s_ncs_user_edit_file_valid.png)

   抽取檔案可以通過批准框預覽，然後接受或拒絕。

   ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

   >[!NOTE]
   >
   >抽取檔案預覽僅涉及資料示例。 未載入整個輸出檔案。

* **批准關聯的交貨**

   的 **[!UICONTROL Enable individual approval of each associated delivery]** 選項用於與輔助交貨關聯的一個主交貨。 預設情況下，不會選擇此選項，以便可以執行主交貨的總體批准。 如果選擇此選項，則每個交貨必須單獨審批。

   ![](assets/s_ncs_user_task_valid_associate.png)

### 選擇審批流程 {#choosing-the-processes-to-be-approved}

審批階段與與市場活動關聯的模板一起定義。 必須從模板中選擇要批准的元素，並指定負責這些批准的Adobe Campaign運算子。 有關市場活動模板的詳細資訊，請參閱 [此部分](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

>[!NOTE]
>
>市場活動（或市場活動模板）的審批配置適用於連結到此市場活動的所有將來交貨。 任何配置更改都不會應用於以前的交貨。

可以覆蓋每個市場活動和每個交貨的此資訊。

對於市場活動，按一下 **[!UICONTROL Edit > Properties]** ，則 **[!UICONTROL Advanced campaign settings...]** 連結，最後 **[!UICONTROL Approvals]** 的子菜單。

您可以選擇並取消選擇要審批和指定負責審批的Adobe Campaign操作員的流程。 這些運算子可以是單個運算子、一組運算子或運算子清單。

要選擇運算子清單，請按一下 **[!UICONTROL Edit...]** 連結到指定第一個審閱者的欄位右側，並根據需要添加任意數量的運算子，如下所示：

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* 如果定義了審閱者清單，則當一個審閱者接受該清單時，將批准該作業。 然後，儀表板中不再提供相關批准連結。 啟用通知發送時，如果另一個審閱者按一下通知消息中的批准連結，則通知他們另一個操作員已批准該作業。
>* 您可以在審閱者編輯窗口的下半部分定義市場活動的審批計畫。 預設情況下，審閱人從提交日期開始有三天時間批准流程。 可以配置在批准截止日期前自動發送給相關操作員的提醒。
>* 您可以從此部分添加提醒。
>


![](assets/s_ncs_user_edit_op_valid_calendar.png)

對於每個交貨，按一下 **[!UICONTROL Audit]** 按鈕 **[!UICONTROL Approvals]** 頁籤，查看和編輯審批日期和自動提醒。

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>此頁籤在內容審批流程啟動後可用。

### 批准內容 {#approving-content}

>[!CAUTION]
>
>要批准內容，必須使用證明週期。 校樣允許您批准資訊、個性化資料的顯示，並檢查連結是否正在工作。 瞭解如何在 [此部分](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。
>
>下面詳述的內容批准功能與證明交付有關。

可以配置內容批准週期。 要執行此操作，請選擇 **[!UICONTROL Enable content approval]** 的子菜單。 內容審批週期的主要步驟是：

1. 建立新交貨後，市場活動經理按一下 **[!UICONTROL Submit content]** 連結到市場活動控制面板以啟動內容審批週期。

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Enable the sending of proofs]** 選項（用於電子郵件遞送）或 **[!UICONTROL Enable the sending and approval of proofs]** （對於直接郵寄）選項已在批准設定窗口中選擇，將自動發送校樣。

1. 通知電子郵件將發送給負責內容的人員，此人可以選擇是否批准該內容：

   * 通過通知電子郵件：

      ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

      >[!NOTE]
      >
      >通知電子郵件包含指向已發送的校樣的連結，並且如果已發送的校樣已發送，則可能包含向各種網路郵件的消息的呈現的連結 **可交付性** 選項。

   * 通過控制台或web介面、交付跟蹤、交付控制板或市場活動控制板：

      ![](assets/s_ncs_user_validation_content_bat_op.png)

      >[!NOTE]
      >
      >此市場活動控制面板通過按一下 **[!UICONTROL Inbox rendering...]** 的子菜單。 要查看其內容，請按一下 **[!UICONTROL Detail]** 的子菜單。

      ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. 通知電子郵件被發送給負責市場活動的人員，通知他們內容是否已被批准。

   >[!NOTE]
   >
   >負責市場活動的人員可以隨時重新啟動內容審批週期。 要執行此操作，請按一下 **[!UICONTROL Content status]** 市場活動控制面板的行（在交貨層），然後按一下 **[!UICONTROL Reset content approval to submit it again]**。

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### 分配內容編輯 {#assign-content-editing}

此選項允許您定義負責內容編輯的人員，如網站管理員。 如果 **[!UICONTROL Assign content editing]** 選項，在建立傳遞和將通知電子郵件發送給負責內容的人員之間添加幾個審批步驟：

1. 建立新交貨後，市場活動負責人按一下 **[!UICONTROL Submit content editing]** 連結以啟動內容編輯週期。

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. 負責內容編輯的人員將收到一封電子郵件，告知他們內容可用。

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. 然後，他們可以登錄到控制台，開啟傳送，並使用簡化嚮導編輯它以更改主題、HTML和文本內容，併發送校樣。

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >如果 **[!UICONTROL Enable the sending of proofs]** 選項（用於電子郵件遞送）或 **[!UICONTROL Enable the sending and approval of proofs]** （對於直接郵寄）選項已在批准設定窗口中選擇，將自動發送校樣。

1. 一旦負責內容編輯的人員完成對交付內容的任何更改，他們就可以使內容可用。

   為此，他們可以：

   * 按一下 **[!UICONTROL Available content]** 通過Adobe Campaign控制台連結。

      ![](assets/s_ncs_user_validation_submit_content_available.png)

   * 按一下通知消息中的連結，然後批准內容可用性。

      ![](assets/s_ncs_user_validation_submit_content_available2.png)

      操作員可以在向市場活動負責人提交內容之前添加註釋。

      ![](assets/s_ncs_user_validation_submit_content_available3.png)

      通知消息允許審閱者批准或拒絕內容。

      ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### 外部內容審批 {#external-content-approval}

此選項允許您定義負責批准交付呈現的外部操作員，如品牌通信一致性、費率等。 當 **[!UICONTROL External content approval]** 選項，在內容審批和將通知發送給市場活動負責人之間添加幾個審批步驟：

1. 外部內容管理器接收通知電子郵件，通知他們內容已被批准並請求外部批准。
1. 通知電子郵件包含指向發送的校樣的連結，這些校樣允許您查看交付呈現，以及用於批准或拒絕交付內容的按鈕。

   >[!NOTE]
   >
   >這些連結僅在已發送一個或多個校樣時才可用。 否則，僅通過控制台或Web介面提供交付呈現。

   ![](assets/s_user_validation_external_content.png)

### 批准提取檔案 {#approving-an-extraction-file}

對於離線傳送，Adobe Campaign會生成抽取檔案，並根據其設定方式將其發送到路由器。 其內容取決於使用的導出模板。

當內容、目標和預算獲得批准時，交付將更改為 **[!UICONTROL Extraction pending]** 直到啟動市場活動的抽取工作流。

![](assets/s_ncs_user_waiting_file_extraction.png)

在提取請求日期，建立提取檔案，並將提供狀態更改為 **[!UICONTROL File to approve]**。

![](assets/s_ncs_user_file_extract_to_valid.png)

您可以查看提取的檔案的內容（通過按一下其名稱）、批准它，或者在必要時更改格式，並使用儀表板上的連結重新啟動提取。

檔案獲得批准後，您可以向路由器發送通知電子郵件。 有關此內容的詳細資訊，請參閱 [啟動離線交貨](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery)。
