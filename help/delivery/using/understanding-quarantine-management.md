---
product: campaign
title: 認識隔離管理
description: 認識隔離管理
feature: Monitoring, Deliverability
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '2837'
ht-degree: 10%

---

# 認識隔離管理{#understanding-quarantine-management}

![](../../assets/common.svg)

Adobe Campaign 管理隔離地址清單。在執行傳遞分析時，預設情況下將不會向被隔離的收件者的電郵地址傳送內容。例如信箱容量已滿或地址不存在時，您可以隔離電子郵件地址。無論如何，隔離程式都符合下文所述的具體規則。

>[!NOTE]
>
>本節適用於線上渠道：電子郵件，簡訊，推送通知。

## 通過隔離管理優化您的交付 {#optimizing-your-delivery-through-quarantines}

電子郵件地址或電話號碼處於隔離狀態的配置檔案在郵件準備期間自動排除(請參閱 [確定交貨的隔離地址](#identifying-quarantined-addresses-for-a-delivery))。 這會加快傳送速度，因為錯誤率對傳送速度有顯著影響。

如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離允許您避免被這些提供程式添加到denylist中。

此外，隔離有助於減少簡訊傳送成本，因為將錯誤的電話號碼排除在遞送服務之外。

如需確保傳送安全並最佳化的最佳實務，請參閱[本頁面](delivery-best-practices.md)。

### 隔離與密文清單 {#quarantine-vs-denylist}

隔離和密文清單不適用於同一對象：

* **隔離** 僅適用於 **地址** （或電話號碼等等），而不是個人資料本身。 例如，其電子郵件地址被隔離的配置檔案可以更新其配置檔案並輸入新地址，然後可以再次通過傳遞操作鎖定。 同樣，如果兩個配置檔案的電話號碼相同，則如果隔離該號碼，則兩個配置檔案都會受到影響。

   隔離的地址或電話號碼顯示在 [排除日誌](#identifying-quarantined-addresses-for-a-delivery) （交貨）或 [隔離清單](#identifying-quarantined-addresses-for-the-entire-platform) （適用於整個平台）。

* 在 **密度**，另一方面， **輪廓** 不再被指定渠道的交付所針對，如取消訂閱（選擇退出）後。 例如，如果電子郵件渠道的denylist上的配置檔案有兩個電子郵件地址，則兩個地址都將排除在傳遞之外。

   您可以檢查配置檔案是否位於密鑰清單中，以查看 **[!UICONTROL No longer contact]** 的 **[!UICONTROL General]** 頁籤。 請參閱[本節](../../platform/using/editing-a-profile.md#general-tab)。

>[!NOTE]
>
>隔離包括 **[!UICONTROL Denylisted]** 狀態，當收件人將您的郵件報告為垃圾郵件或使用關鍵字（如「STOP」）回復SMS郵件時，該狀態適用。 在這種情況下，配置檔案的相關地址或電話號碼將與 **[!UICONTROL Denylisted]** 狀態。 有關管理STOP SMS消息的詳細資訊，請參閱 [此部分](../../delivery/using/sms-send.md#processing-inbound-messages)。

## 標識隔離地址 {#identifying-quarantined-addresses}

可以為特定傳送或整個平台列出隔離的地址。

### 確定交貨的隔離地址 {#identifying-quarantined-addresses-for-a-delivery}

特定遞送的隔離地址在遞送準備階段列在遞送儀表板的遞送日誌中(請參閱 [交付日誌和歷史記錄](delivery-dashboard.md#delivery-logs-and-history))。

### 確定整個平台的隔離地址 {#identifying-quarantined-addresses-for-the-entire-platform}

管理員可以從 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 的下界。

>[!NOTE]
>
>此功能表會列出&#x200B;**電子郵件**、**簡訊**&#x200B;和&#x200B;**推播通知**&#x200B;通道的隔離元素。

每個地址都可以獲得以下資訊：

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>檢疫數量的增加是正常的效果，與資料庫的&quot;磨損&quot;有關。 例如，如果電子郵件地址的生存期被認為是三年，而收件人表每年增加50%，則隔離增加的計算方法如下：
>
>年末1:(1*0.33)/(1+0.5)=22%。
年度結束 2：((1.22*0.33)+0.33)/(1.5+0.75)=32.5%。

### 在傳遞報告中標識隔離地址 {#identifying-quarantined-addresses-in-delivery-reports}

以下報告提供了有關隔離中地址的資訊：

* 對於每個交貨， **[!UICONTROL Delivery summary]** 報告顯示交貨目標中隔離的地址數。 它顯示：

   * 在交貨分析期間存放在隔離區中的地址數，

   * 在傳遞操作後置於隔離中的地址數。

* 的 **[!UICONTROL Non-deliverables and bounces]** 報告按域顯示有關隔離中的地址、遇到的錯誤類型等的資訊以及故障細分。

您可以查找此資訊，瞭解平台的所有交付情況(**[!UICONTROL Home page > Reports]**)或特定遞送。 您還可以建立自定義報告並選擇要顯示的資訊。

### 標識收件人的隔離地址 {#identifying-quarantined-addresses-for-a-recipient}

您可以查找任何收件人的電子郵件地址的狀態。 為此，請選擇收件人配置檔案，然後按一下 **[!UICONTROL Deliveries]** 頁籤。 對於向該收件人發送的所有郵件，您可以查明地址是否失敗、是否在分析期間被隔離等。 對於每個資料夾，您只能顯示其電子郵件地址處於隔離狀態的收件人。 要執行此操作，請使用 **[!UICONTROL Quarantined email address]** 應用程式篩選器。

![](assets/tech_quarant_recipients_filter.png)

### 刪除隔離地址 {#removing-a-quarantined-address}

如果需要，可以手動從隔離清單中刪除地址。 此外，與特定條件匹配的地址將由 [資料庫清理](../../production/using/database-cleanup-workflow.md) 工作流。

要手動從隔離清單中刪除地址，請執行以下操作之一。

>[!IMPORTANT]
從隔離區中手動刪除電子郵件地址意味著您將再次開始傳遞到此地址。 因此，這會對您的可交付性和IP信譽造成嚴重影響，最終可能導致您的IP地址或發送域被阻止。 考慮從隔離區中刪除任何地址時，請格外小心。 如有任何疑問，請與交付能力專家聯繫。

* 您可以將其狀態更改為 **[!UICONTROL Valid]** 從 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 的下界。

   ![](assets/tech_quarant_error_status.png)

* 您還可以將其狀態更改為 **[!UICONTROL Allowlisted]**。 在這種情況下，地址仍保留在隔離清單中，但是即使遇到錯誤，它也會被系統性地定向。

在以下情況下，這些地址將自動從隔離清單中刪除：

* 中的地址 **[!UICONTROL With errors]** 成功交貨後，狀態將從隔離清單中刪除。
* 中的地址 **[!UICONTROL With errors]** 如果上次軟反彈發生時間超過10天，則狀態將從隔離清單中刪除。 有關軟錯誤管理的詳細資訊，請參見 [此部分](#soft-error-management)。
* 中的地址 **[!UICONTROL With errors]** 與 **[!UICONTROL Mailbox full]** 30天後將從隔離清單中刪除錯誤。

其狀態隨後更改為 **[!UICONTROL Valid]**。

>[!IMPORTANT]
地址位於 **[!UICONTROL Quarantine]** 或 **[!UICONTROL Denylisted]** 即使收到電子郵件，狀態也永遠不會被刪除。

對於托管或混合安裝，如果已升級到 [增強的MTA](sending-with-enhanced-mta.md)，在 **[!UICONTROL Erroneous]** 現在，重試狀態和最小延遲取決於IP在給定域中的歷史和當前執行情況。

對於使用舊版市場活動MTA的內部安裝和托管/混合安裝，您可以修改錯誤數和兩個錯誤之間的時間段。 為此，請更改 [部署嚮導](../../installation/using/deploying-an-instance.md) (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**)或 [在交貨級別](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)。

## 將地址傳送到隔離區的條件 {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign根據傳遞失敗類型和在錯誤消息限定期間分配的原因管理隔離(請參閱 [退信郵件資格](understanding-delivery-failures.md#bounce-mail-qualification) 和 [交貨失敗類型和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons))。

* **忽略錯誤**：忽略的錯誤不會傳送要隔離的地址。
* **硬錯誤**：會立即將相對應的電子郵件地址傳送至隔離區。
* **軟錯誤**：軟錯誤不會立即傳送要隔離的地址，但會增加錯誤計數器。有關此的詳細資訊，請參閱 [軟錯誤管理](#soft-error-management)。

如果用戶將電子郵件定義為垃圾郵件([反饋環](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops))，該郵件自動重定向到由Adobe管理的技術郵箱。 之後，系統會自動將使用者的電子郵件地址傳送到狀態為　**[!UICONTROL Denylisted]**　的隔離區。此狀態僅指地址，配置檔案不在密碼清單中，因此用戶繼續接收SMS消息和推送通知。

>[!NOTE]
Adobe Campaign　中的隔離區會區分大小寫。請務必以小寫匯入電子郵件地址，如此一來，稍後就不會將它們重新設為目標。

在隔離地址清單中(請參見 [確定整個平台的隔離地址](#identifying-quarantined-addresses-for-the-entire-platform)) **[!UICONTROL Error reason]** 欄位指明將選定地址置於隔離區的原因。

![](assets/tech_quarant_error_reasons.png)

### 軟錯誤管理 {#soft-error-management}

與硬錯誤相比，軟錯誤不會立即發送要隔離的地址，而是增加錯誤計數器。

將在 [交貨期](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)。 當錯誤計數器達到限制臨界值時，該地址就會進入隔離區。有關此內容的詳細資訊，請參閱 [傳遞臨時失敗後重試](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)。

如果上次出現重大錯誤超過10天，則重新初始化錯誤計數器。 地址狀態隨後更改為 **有效** 而且它被從隔離清單中刪除 [資料庫清理](../../production/using/database-cleanup-workflow.md) 工作流。

## 推送通知隔離 {#push-notification-quarantines}

推式通知的隔離機制與一般進程全局相同。 請參閱 [關於隔離](#about-quarantines)。 但是，對於推送通知，某些錯誤的管理方式不同。 例如，對於某些軟錯誤，在同一傳遞內不執行重試。 下面列出了推送通知的特性。 重試機制（重試次數、頻率）與電子郵件相同。

被隔離的項是設備令牌。

### iOS {#ios-quarantine}

HTTP/V2協定允許對每個推送傳遞提供直接反饋和狀態。 如果使用HTTP/V2協定連接器，則反饋服務不再由 **[!UICONTROL mobileAppOptOutMgt]** 工作流。 卸載或重新安裝移動應用程式時，令牌被視為未註冊。

同時，如果APN返回消息的「未註冊」狀態，則目標令牌將立即被隔離。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>方案</strong><br /> </td> 
   <td> <strong>狀態</strong><br /> </td> 
   <td> <strong>錯誤消息</strong><br /> </td> 
   <td> <strong>失敗類型</strong><br /> </td> 
   <td> <strong>失敗原因</strong><br /> </td> 
   <td> <strong>重試</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 已開啟目標設備<br /> </td> 
   <td> 確定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 關閉目標設備<br /> </td> 
   <td> 確定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 用戶禁用應用程式的通知<br /> </td> 
   <td> 確定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 消息建立/分析階段 — 負載太大<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 負載過長<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息建立/分析階段 — 意外的內容格式問題<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 根據錯誤顯示的各種錯誤消息<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 未定義<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 證書頒發（密碼、損壞等） 與APNs問題的test連接<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 根據錯誤顯示的各種錯誤消息<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 發送過程中網路連接丟失<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 連接錯誤<br /> </td> 
   <td> 未定義<br /> </td> 
   <td> 無法訪問<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> APN消息拒絕：取消註冊<br /> 用戶已刪除應用程式或令牌已過期<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 未註冊<br /> </td> 
   <td> 硬<br /> </td> 
   <td> 用戶未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> APN消息拒絕：所有其他錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 錯誤拒絕原因將出現在錯誤消息中<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android隔離 {#android-quarantine}

**對於Android V1**

對於每個通知，Adobe Campaign直接從FCM伺服器接收同步錯誤。 Adobe活動會根據錯誤的嚴重性即時處理這些錯誤並生成硬錯誤或軟錯誤，並且可以執行重試：

* 超出負載長度、連接問題、服務可用性問題：重試執行，軟錯誤，失敗原因 **[!UICONTROL Refused]**。
* 超過設備配額：無重試，軟錯誤，失敗原因 **[!UICONTROL Refused]**。
* 無效或未註冊的令牌，意外錯誤，發件人帳戶問題：無重試，硬錯誤，失敗原因 **[!UICONTROL Refused]**。

的 **[!UICONTROL mobileAppOptOutMgt]** 工作流每6小時運行一次以更新 **AppSubscriptionRcp** 的子菜單。 對於聲明為未註冊或不再有效的令牌，該欄位 **已禁用** 設定為 **真** 連結到該設備令牌的訂閱將自動排除在將來的交付之外。

在傳遞分析期間，從目標中排除的所有設備將自動添加到 **排除LogAppSubRcp** 的子菜單。

>[!NOTE]
對於使用百度連接器的客戶，以下是不同類型的錯誤：
* 交付開始時的連接問題：故障類型 **[!UICONTROL Undefined]**&#x200B;故障原因 **[!UICONTROL Unreachable]**，重試。
* 傳遞過程中連接丟失：軟錯誤，故障原因 **[!UICONTROL Refused]**，重試。
* 百度在發送過程中返回的同步錯誤：硬錯誤，故障原因 **[!UICONTROL Refused]**，未執行重試。
>
Adobe Campaign每隔10分鐘與百度伺服器聯繫，檢索發送消息的狀態，並更新廣播。 如果消息被聲明為已發送，則廣播中消息的狀態將設定為 **[!UICONTROL Received]**。 如果百度聲明錯誤，則狀態設定為 **[!UICONTROL Failed]**。

**對於Android V2**

Android V2隔離機制使用與Android V1相同的過程，同樣適用於訂閱和排除更新。 有關詳情，請參閱 [Android V1](#android-quarantine) 的子菜單。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>方案</strong><br /> </td> 
   <td> <strong>狀態</strong><br /> </td> 
   <td> <strong>錯誤消息</strong><br /> </td> 
   <td> <strong>失敗類型</strong><br /> </td> 
   <td> <strong>失敗原因</strong><br /> </td> 
   <td> <strong>重試</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 消息建立/分析階段：自定義域中使用的非法關鍵字<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無法使用以下關鍵字：{1}<br /> </td> 
   <td> 軟<br /> </td> 
   <td> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息建立/分析階段：負載太大<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 通知太重：{1}位，而僅授權{2}位<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 發送過程中網路連接丟失<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 地址上沒有來自Firebase雲消息服務的響應：{1}<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 無法訪問<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒絕：FCM伺服器暫時不可用（例如超時）。 <br /> </td> 
   <td> 失敗<br /> </td> 
   <td> Firebase雲消息服務暫時不可用<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 無法訪問<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒絕：驗證發件人帳戶時出錯<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無法識別開發人員帳戶，請檢查您的ID和密碼<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒絕：超過設備配額<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> </td> 
   <td> 軟<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒絕：註冊無效/未註冊<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> </td> 
   <td> 硬<br /> </td> 
   <td> 用戶未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒絕：所有其他錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> Firebase雲消息伺服器返回了意外錯誤代碼：{1} </td> 
   <td> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
    <tr> 
   <td> FCM消息拒絕：參數無效<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無效_參數 </td> 
   <td> 已忽略</td> 
   <td> 未定義<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒絕：第三方身份驗證錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 第三方身份驗證錯誤 </td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒絕：發件人ID不匹配<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> 軟</td>
   <td> 用戶未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒絕：未註冊<br /> </td> 
   <td> 失敗<br /> </td>
   <td> 未註冊 </td> 
   <td> 硬</td> 
   <td> 用戶未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒絕：內部<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 內部 </td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒絕：不可用<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 不可用</td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒絕：意外錯誤代碼<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 意外錯誤代碼</td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
  <tr> 
   <td> 身份驗證：連接問題<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無法連接到身份驗證伺服器 </td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> 身份驗證：請求中的未授權客戶端或作用域。<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 未經授權的客戶端 </td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份驗證：客戶端未授權使用此方法檢索訪問令牌，或客戶端未授權請求的任何作用域。<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 未經授權的客戶端 </td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份驗證：拒絕訪問<br /> </td> 
   <td> 失敗<br /> </td>
   <td> 拒絕訪問</td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份驗證：無效電子郵件<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無效授予 </td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份驗證：JWT無效<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無效授予 </td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份驗證：JWT簽名無效<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無效授予 </td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份驗證：提供的OAuth作用域或ID令牌訪問群無效<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 未經授權的客戶端</td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 身份驗證：已禁用OAuth客戶端<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 已禁用客戶端</td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
 </tbody> 
</table>

## SMS隔離 {#sms-quarantines}

**對於標準連接器**

SMS消息的隔離機制與一般進程全局相同。 請參閱 [關於隔離](#about-quarantines)。 下面列出了SMS的特性。

>[!NOTE]
的 **[!UICONTROL Delivery log qualification]** 表不適用於 **擴展通用SMPP** 連接器。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>方案</strong><br /> </td> 
   <td> <strong>狀態</strong><br /> </td> 
   <td> <strong>錯誤消息</strong><br /> </td> 
   <td> <strong>失敗類型</strong><br /> </td> 
   <td> <strong>失敗原因</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 發送到提供程式<br /> </td> 
   <td> 已傳送<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 在移動設備上接收<br /> </td> 
   <td> 已接收<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 提供程式返回的錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 接收資料時出錯（SR或MO）<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 無法訪問<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效的MT確認<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 處理髮送查詢的確認幀時出錯「{1}」<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 無法訪問<br /> </td> 
  </tr> 
  <tr> 
   <td> 發送MT時出錯<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 發送消息時出錯<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 無法訪問<br /> </td> 
  </tr> 
 </tbody> 
</table>

**對於擴展通用SMPP連接器**

當使用SMPP協定發送SMS消息時，錯誤管理被以不同方式處理。 有關擴展通用SMPP連接器的詳細資訊，請參閱 [此頁](sms-set-up.md#creating-an-smpp-external-account)。

SMPP連接器從SR（狀態報告）消息中檢索資料，該消息使用規則運算式(regexes)返回以過濾其內容。 然後，將此資料與在 **[!UICONTROL Delivery log qualification]** 表(通過 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** )的正平方根。

在限定新類型的錯誤之前，故障原因始終設定為 **拒絕** 預設值。

>[!NOTE]
故障類型和故障原因與電子郵件相同。 請參閱 [交貨失敗類型和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)。
請向提供商咨詢狀態和錯誤代碼清單，以便在「交付日誌」限定表中設定正確的故障類型和故障原因。

生成的消息示例：

```
SR Generic DELIVRD 000|#MESSAGE#
```

* 所有錯誤消息以開頭 **SR** 將SMS錯誤代碼與電子郵件錯誤代碼區分開。
* 第二部分(**泛型** 在本示例中)的錯誤消息是指SMSC實現的名稱，如 **[!UICONTROL SMSC implementation name]** SMS外部帳戶的欄位。 請參閱[此頁面](sms-set-up.md#creating-an-smpp-external-account)。

   由於同一錯誤代碼可能對每個提供程式具有不同的含義，因此此欄位允許您知道生成錯誤代碼的提供程式。 然後，您可以在相關提供商的文檔中找到錯誤。

* 第三部分(**德利夫德** 在此示例中)，錯誤消息與使用SMS外部帳戶中定義的狀態提取規則運算式從SR檢索到的狀態代碼相對應。

   此規則運算式在 **[!UICONTROL SMSC specificities]** 的子菜單。 請參閱[此頁面](sms-set-up.md#creating-an-smpp-external-account)。

   ![](assets/tech_quarant_error_regex.png)

   預設情況下，regex將提取 **stat:** 定義的欄位 **附錄B** 的下界 **SMPP 3.4規範**。

* 第四部分(**000** 在本示例中)，錯誤消息與使用SMS外部帳戶中定義的錯誤代碼提取規則運算式從SR提取的錯誤代碼相對應。

   此規則運算式在 **[!UICONTROL SMSC specificities]** 的子菜單。 請參閱[此頁面](sms-set-up.md#creating-an-smpp-external-account)。

   預設情況下，regex將提取 **錯誤：** 定義的欄位 **附錄B** 的下界 **SMPP 3.4規範**。

* 管道符號(|)之後的所有內容僅顯示在 **[!UICONTROL First text]** 列 **[!UICONTROL Delivery log qualification]** 的子菜單。 此內容始終替換為 **#MESSAGE#** 在消息規範化後。 此過程避免出現多個類似錯誤條目，與電子郵件條目相同。 有關此的詳細資訊，請參閱 [退信郵件資格](understanding-delivery-failures.md#bounce-mail-qualification)。

擴展通用SMPP連接器應用啟發式來查找明顯預設值：如果狀態以 **德利夫**，它被認為是成功的，因為它與常用狀態匹配 **德利夫德** 或 **已交付** 供大多數提供商使用。 任何其他狀態都會導致硬故障。
