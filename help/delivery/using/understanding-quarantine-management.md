---
solution: Campaign Classic
product: campaign
title: 瞭解隔離管理
description: 瞭解隔離管理
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 22f44f5723ab35e95caa438583fe06314c763ba1
workflow-type: tm+mt
source-wordcount: '2605'
ht-degree: 15%

---


# 瞭解隔離管理{#understanding-quarantine-management}

## 關於隔離 {#about-quarantines}

Adobe Campaign 管理隔離地址清單。在執行傳遞分析時，預設情況下將不會向被隔離的收件者的電郵地址傳送內容。例如信箱容量已滿或地址不存在時，您可以隔離電子郵件地址。在任何情況下，隔離程式都符合以下所述的特定規則。

>[!NOTE]
>
>本節適用於線上渠道：電子郵件、簡訊、推播通知。

### 透過隔離最佳化傳送 {#optimizing-your-delivery-through-quarantines}

郵件準備期間會自動排除其電子郵件地址或電話號碼處於隔離狀態的設定檔（請參閱[識別傳送的隔離地址](#identifying-quarantined-addresses-for-a-delivery)）。這會加快傳送速度，因為錯誤率對傳送速度有顯著影響。

如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離可讓您避免被這些提供者添加到拒絕清單。

此外，隔離有助於減少簡訊傳送成本，因為將錯誤的電話號碼排除在遞送服務之外。如需確保傳送安全並最佳化的最佳實務，請參閱[本頁面](../../delivery/using/delivery-best-practices.md)。

### 隔離與拒絕清單{#quarantine-vs-denylist}

**隔離** (Quarantine)　僅適用於地址，而不適用於設定檔本身。這代表如果兩個設定檔具有相同的電子郵件地址，則兩個設定檔在隔離地址時都會受到影響。

同樣地，被隔離的電子郵件地址的設定檔可以更新其設定檔並輸入新地址，然後再次被傳送動作設為目標。

另一方面，如果位於&#x200B;**denylist**，則會導致描述檔不再被任何傳送鎖定，例如在取消訂閱（選擇退出）後。

>[!NOTE]
>
>當使用者回覆SMS訊息時，其關鍵字如「STOP」，以選擇退出SMS傳送時，其個人檔案不會像電子郵件選擇退出程式一樣新增至密文清單。 配置檔案電話號碼會發送到隔離區，以便用戶繼續接收電子郵件消息。

## 識別隔離地址 {#identifying-quarantined-addresses}

可以為特定傳送或整個平台列出隔離的地址。

### 識別傳送的隔離地址 {#identifying-quarantined-addresses-for-a-delivery}

特定傳送的隔離地址在傳送準備階段中列於傳送控制面板的傳送記錄（請參閱[傳送記錄和歷史記錄](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)）中。

### 識別整個平台的隔離地址 {#identifying-quarantined-addresses-for-the-entire-platform}

管理員可以從&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;節點列出隔離整個平台的地址。

>[!NOTE]
>
>此功能表會列出&#x200B;**電子郵件**、**簡訊**&#x200B;和&#x200B;**推播通知**&#x200B;通道的隔離元素。

每個地址都有以下資訊：

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>檢疫數量增加是正常的，與資料庫的「磨損」有關。 例如，如果電子郵件地址的存留期被視為三年，而收件者表每年增加50%，則隔離的增加可以計算如下：
>
>年終1:(1*0.33)/(1+0.5)=22%。
年度結束 2：((1.22*0.33)+0.33)/(1.5+0.75)=32.5%。

### 在傳送報告{#identifying-quarantined-addresses-in-delivery-reports}中標識隔離地址

以下報告提供了有關隔離中地址的資訊：

* 對於每個傳送，**[!UICONTROL Delivery summary]**&#x200B;報告顯示傳送目標中隔離的地址數。 它顯示：

   * 在交貨分析期間，隔離中放置的地址數，

   * 傳送動作後置於隔離中的地址數。

* **[!UICONTROL Non-deliverables and bounces]**&#x200B;報告顯示有關隔離中地址的資訊、遇到的錯誤類型等，以及按域劃分的故障細分。

您可以查詢平台的所有傳送(**[!UICONTROL Home page > Reports]**)或特定傳送的資訊。 您也可以建立自訂報表，並選取要顯示的資訊。

### 標識收件者{#identifying-quarantined-addresses-for-a-recipient}的隔離地址

您可以查看任何收件者的電子郵件地址狀態。 若要這麼做，請選取收件者描述檔，然後按一下&#x200B;**[!UICONTROL Deliveries]**&#x200B;標籤。 對於所有傳送給該收件人的郵件，您可以瞭解地址是否失敗、分析期間是否隔離等。 對於每個資料夾，您只能顯示電子郵件地址處於隔離狀態的收件人。 若要這麼做，請使用&#x200B;**[!UICONTROL Quarantined email address]**&#x200B;應用程式篩選。

![](assets/tech_quarant_recipients_filter.png)

### 刪除隔離地址{#removing-a-quarantined-address}

如果需要，可以手動從隔離清單中刪除地址。 此外，**[!UICONTROL Database cleanup]**&#x200B;工作流還會自動從隔離清單中刪除與特定條件匹配的地址。

要手動從隔離清單中刪除地址，請執行以下操作：

* 您可以從&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;節點將其狀態更改為&#x200B;**[!UICONTROL Valid]**。

   ![](assets/tech_quarant_error_status.png)

* 您也可以將其狀態變更為&#x200B;**[!UICONTROL Allowlisted]**。 在這種情況下，地址仍在隔離清單中，但是，即使遇到錯誤，該地址仍將被系統地定位。

在以下情況下，這些地址將自動從隔離清單中刪除：

* 成功傳送後，**[!UICONTROL With errors]**&#x200B;狀態的地址將從隔離清單中刪除。
* 如果上次軟彈回數發生在10天前，則&#x200B;**[!UICONTROL With errors]**&#x200B;狀態的地址將從隔離清單中刪除。 有關軟錯誤管理的詳細資訊，請參閱[本節](#soft-error-management)。
* 在30天後，會從隔離清單中刪除狀態為&#x200B;**[!UICONTROL With errors]**&#x200B;且因&#x200B;**[!UICONTROL Mailbox full]**&#x200B;錯誤而跳回的地址。

然後其狀態會變更為&#x200B;**[!UICONTROL Valid]**。

>[!IMPORTANT]
即使收到電子郵件，也不會移除狀態為&#x200B;**[!UICONTROL Quarantine]**&#x200B;或&#x200B;**[!UICONTROL On denylist]**&#x200B;的收件者。

您可以修改錯誤數和兩個錯誤之間的句點。 若要這麼做，請變更部署精靈(**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**)中的對應設定。 有關部署嚮導的詳細資訊，請參閱[本節](../../installation/using/deploying-an-instance.md)。

## 將地址傳送到隔離區的條件 {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign會根據傳送失敗類型和錯誤訊息限定期間指派的原因（請參閱[彈回郵件限定](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)）和[傳送失敗類型和原因](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)來管理隔離。

* **忽略錯誤**：忽略的錯誤不會傳送要隔離的地址。
* **硬錯誤**：會立即將相對應的電子郵件地址傳送至隔離區。
* **軟錯誤**：軟錯誤不會立即傳送要隔離的地址，但會增加錯誤計數器。有關詳細資訊，請參閱[軟錯誤管理](#soft-error-management)。

如果使用者將電子郵件歸類為垃圾訊息（[回饋迴路](../../delivery/using/technical-recommendations.md#feedback-loop)），則會自動將訊息重新導向至Adobe管理的技術郵箱。 然後，用戶的電子郵件地址會自動發送到隔離區。

在隔離地址清單中，**[!UICONTROL Error reason]**&#x200B;欄位指明了將選定地址置於隔離中的原因。 Adobe Campaign　中的隔離區會區分大小寫。請務必以小寫匯入電子郵件地址，如此一來，稍後就不會將它們重新設為目標。

![](assets/tech_quarant_error_reasons.png)

### 軟錯誤管理{#soft-error-management}

與硬錯誤相反，軟錯誤不會立即傳送要隔離的地址，而會增加錯誤計數器。

* 當錯誤計數器達到限制閾值時，地址將被隔離。
* 在預設設定中，臨界值會設定為　5　個錯誤，其中　2　個錯誤若相隔至少　24　小時，即為顯著錯誤。會將地址放置到隔離區的第五個錯誤。
* 可以修改錯誤計數器臨界值。有關詳細資訊，請參閱[傳送臨時失敗後重試](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)。

如果上一個重大錯誤發生在10天前，則重新初始化錯誤計數器。 然後，地址狀態將更改為&#x200B;**有效**，並且該狀態將通過&#x200B;**資料庫清理**&#x200B;工作流從隔離清單中刪除。

## 推播通知隔離{#push-notification-quarantines}

推播通知的隔離機制與一般程式的整體相同。 請參閱[關於隔離](#about-quarantines)。 不過，推播通知的某些錯誤管理方式不同。 例如，對於某些軟錯誤，不會在同一傳送內執行任何重試。 推播通知的特定性列於下方。 重試機制（重試次數、頻率）與電子郵件的重試機制相同。

被隔離的項目是設備令牌。

### iOS隔離{#ios-quarantine}

HTTP/V2通訊協定可讓每個推播傳送直接提供意見和狀態。 如果使用HTTP/V2通訊協定連接器，**[!UICONTROL mobileAppOptOutMgt]**&#x200B;工作流程將不再呼叫回饋服務。 解除安裝或重新安裝行動應用程式時，會將Token視為未註冊。

同時，如果APN返回消息的「未註冊」狀態，則目標令牌將立即被隔離。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>藍本</strong><br /> </td> 
   <td> <strong>狀態</strong><br /> </td> 
   <td> <strong>錯誤訊息</strong><br /> </td> 
   <td> <strong>故障類型</strong><br /> </td> 
   <td> <strong>失敗原因</strong><br /> </td> 
   <td> <strong>重試</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 已開啟<br />的目標設備 </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 關閉目標設備<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 使用者停用應用程式的通知<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 消息建立／分析階段——負載太大<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 負載過長<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息建立／分析階段——意外的內容格式問題<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 根據錯誤顯示的各種錯誤消息<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 未定義<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 憑證問題（密碼、損毀等） 並測試與APNs問題的連接<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 根據錯誤顯示的各種錯誤消息<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 發送<br />期間網路連接丟失 </td> 
   <td> 失敗<br /> </td> 
   <td> 連接錯誤<br /> </td> 
   <td> 未定義<br /> </td> 
   <td> 無法訪問<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> APN消息拒絕：取消註冊<br />使用者已移除應用程式或Token已過期<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 未註冊<br /> </td> 
   <td> 硬<br /> </td> 
   <td> 用戶未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> APN消息拒絕：所有其他錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 錯誤拒絕原因將出現在錯誤消息<br />中 </td> 
   <td> Soft<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android隔離{#android-quarantine}

**適用於Android V1**

對於每個通知，Adobe Campaign會直接從FCM伺服器接收同步錯誤。 Adobe促銷活動會即時處理這些錯誤，並根據錯誤的嚴重性產生硬錯誤或軟錯誤，並可執行重試：

* 負載長度已超出，連接問題，服務可用性問題：重試，軟錯誤，失敗原因為&#x200B;**[!UICONTROL Refused]**。
* 超過設備配額：無重試，軟錯誤，失敗原因為&#x200B;**[!UICONTROL Refused]**。
* 無效或未註冊的Token、非預期錯誤、傳送者帳戶問題：無重試，硬錯誤，失敗原因為&#x200B;**[!UICONTROL Refused]**。

**[!UICONTROL mobileAppOptOutMgt]**&#x200B;工作流程每6小時執行一次，以更新&#x200B;**AppSubscriptionRcp**&#x200B;表格。 對於宣告為未註冊或不再有效的Token，欄位&#x200B;**Disabled**&#x200B;會設為&#x200B;**True**，連結至該裝置Token的訂閱會自動排除在未來傳送中。

在傳送分析期間，所有從目標中排除的裝置都會自動新增至&#x200B;**excludeLogAppSubRcp**&#x200B;表格。

>[!NOTE]
對於使用Baidu連接器的客戶，以下是不同類型的錯誤：
* 傳送開始時的連線問題：失敗類型&#x200B;**[!UICONTROL Undefined]**、失敗原因&#x200B;**[!UICONTROL Unreachable]**，將執行重試。
* 傳送期間連線遺失：軟錯誤，故障原因&#x200B;**[!UICONTROL Refused]**，將執行重試。
* Baidu在傳送期間傳回的同步錯誤：硬錯誤，故障原因&#x200B;**[!UICONTROL Refused]**，未執行重試。

Adobe Campaign每10分鐘與Baidu伺服器連絡，以擷取已傳送訊息的狀態並更新廣播。 如果消息被聲明為已發送，則廣播中消息的狀態將設定為&#x200B;**[!UICONTROL Received]**。 如果Baidu宣告錯誤，狀態會設為&#x200B;**[!UICONTROL Failed]**。

**適用於Android V2**

Android V2隔離機制使用與Android V1相同的程式，訂閱和排除更新的程式也相同。 如需詳細資訊，請參閱[Android V1](#android-quarantine)一節。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>藍本</strong><br /> </td> 
   <td> <strong>狀態</strong><br /> </td> 
   <td> <strong>錯誤訊息</strong><br /> </td> 
   <td> <strong>故障類型</strong><br /> </td> 
   <td> <strong>失敗原因</strong><br /> </td> 
   <td> <strong>重試</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 消息建立／分析階段：自訂欄位中使用的非法關鍵字<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 下列關鍵字無法使用：{1}<br /> </td> 
   <td> Soft<br /> </td> 
   <td> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息建立／分析階段：裝載過大<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 通知太重：{1}位，而只有{2}獲得授權<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 發送<br />期間網路連接丟失 </td> 
   <td> 失敗<br /> </td> 
   <td> Firebase Cloud Messaging服務未回應此位址：{1}<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 無法訪問<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒絕：FCM伺服器暫時不可用（例如超時）。<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> Firebase Cloud傳訊服務暫時無法使用<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 無法訪問<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒絕：驗證發件人帳戶時出錯<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無法識別開發人員帳戶，請檢查您的ID和密碼<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒絕：超過設備配額<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> </td> 
   <td> Soft<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒絕：註冊無效／未註冊<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> </td> 
   <td> 硬<br /> </td> 
   <td> 用戶未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒絕：所有其他錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> Firebase Cloud Messaging伺服器傳回未預期的錯誤碼：{1} </td> 
   <td> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
    <tr> 
   <td> FCM消息拒絕：無效引數<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> 已忽略</td> 
   <td> 未定義<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒絕：第三方驗證錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒絕：傳送者ID不符<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> Soft</td>
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
   <td> 無法使用</td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM消息拒絕：意外的錯誤代碼<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 意外錯誤代碼</td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
  <tr> 
   <td> 驗證：連接問題<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無法連接到驗證伺服器 </td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：請求中的未授權客戶機或範圍。<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：客戶端未授權使用此方法檢索訪問Token，或者客戶端未授權任何請求範圍。<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：訪問被拒絕<br /> </td> 
   <td> 失敗<br /> </td>
   <td> access_denied</td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：無效電子郵件<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> invalid_grant </td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：無效的JWT<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> invalid_grant </td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：無效的JWT簽名<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> invalid_grant </td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：提供的OAuth範圍或ID代號對象無效<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> unauthorized_client</td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：OAuth用戶端已停用<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> disabled_client</td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
 </tbody> 
</table>

## SMS隔離{#sms-quarantines}

**針對標準連接器**

SMS消息的隔離機制與一般過程在全局上是相同的。 請參閱[關於隔離](#about-quarantines)。 以下列出SMS的特定性。

>[!NOTE]
**[!UICONTROL Delivery log qualification]**&#x200B;表不適用於&#x200B;**擴展通用SMPP**&#x200B;連接器。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>藍本</strong><br /> </td> 
   <td> <strong>狀態</strong><br /> </td> 
   <td> <strong>錯誤訊息</strong><br /> </td> 
   <td> <strong>故障類型</strong><br /> </td> 
   <td> <strong>失敗原因</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 發送給提供程式<br /> </td> 
   <td> 已發送<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 在行動裝置上收到<br /> </td> 
   <td> 收到<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 提供者傳回的錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 接收資料時出錯（SR或MO）<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 無法訪問<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效的MT確認<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 處理傳送查詢的確認影格時發生錯誤'{1}'<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 無法訪問<br /> </td> 
  </tr> 
  <tr> 
   <td> 發送MT<br />時出錯 </td> 
   <td> 失敗<br /> </td> 
   <td> 發送消息時出錯<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 無法訪問<br /> </td> 
  </tr> 
 </tbody> 
</table>

**對於擴展的通用SMPP連接器**

當使用SMPP協定發送SMS消息時，錯誤管理的處理方式不同。 有關擴展通用SMPP連接器的詳細資訊，請參閱[本頁](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

SMPP連接器從SR（狀態報告）消息中檢索資料，該消息使用規則運算式(regexes)返回以過濾其內容。 然後，此資料會與&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表格中的資訊相符（可透過&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**&#x200B;功能表取得）。

在限定新類型的錯誤之前，故障原因預設設定為&#x200B;**Requisted**。

>[!NOTE]
失敗類型和失敗原因與電子郵件相同。 請參閱[傳送失敗類型和原因](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。
請洽詢您的供應商，以取得狀態和錯誤碼清單，以便在「傳送記錄」資格表中設定正確的失敗類型和失敗原因。

生成的消息示例：

```
SR Generic DELIVRD 000|#MESSAGE#
```

* 所有錯誤消息都以&#x200B;**SR**&#x200B;開頭，以區分SMS錯誤代碼和電子郵件錯誤代碼。
* 錯誤消息的第二部分（本例中的&#x200B;**Generic**）引用SMSC實現的名稱，如SMS外部帳戶的&#x200B;**[!UICONTROL SMSC implementation name]**&#x200B;欄位中定義的名稱。 請參閱[本頁](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

   由於相同的錯誤代碼可能對每個提供程式有不同的含義，因此，此欄位允許您瞭解哪個提供程式生成了錯誤代碼。 然後，您可以在相關供應商的檔案中找到錯誤。

* 該錯誤消息的第三部分（本例中為&#x200B;**DELIVRD**）與使用SMS外部帳戶中定義的狀態抽取規則表從SR檢索的狀態代碼相對應。

   此規則運算式是在外部帳戶的&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;標籤中指定。 請參閱[本頁](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

   ![](assets/tech_quarant_error_regex.png)

   依預設，regex會擷取&#x200B;**stat:**&#x200B;欄位，如&#x200B;**SMPP 3.4規格**&#x200B;的&#x200B;**附錄B**&#x200B;區段所定義。

* 該錯誤消息的第四部分（本例中為&#x200B;**000**）對應於使用在SMS外部帳戶中定義的錯誤代碼提取規則從SR提取的錯誤代碼。

   此規則運算式是在外部帳戶的&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;標籤中指定。 請參閱[本頁](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

   依預設，regex會擷取&#x200B;**err:**&#x200B;欄位，如&#x200B;**SMPP 3.4規格**&#x200B;的&#x200B;**附錄B**&#x200B;區段所定義。

* 垂直號(|)後面的所有內容只顯示在&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表的&#x200B;**[!UICONTROL First text]**&#x200B;列中。 在消息標準化後，此內容始終由&#x200B;**#MESSAGE#**&#x200B;替換。 此程式可避免因類似錯誤而出現多個項目，而且與電子郵件相同。 如需詳細資訊，請參閱[彈回郵件資格](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)。

擴展通用SMPP連接器採用啟發式方法來查找合理的預設值：如果狀態以&#x200B;**DELIV**&#x200B;開頭，則視為成功，因為它符合大多數提供者使用的常見狀態&#x200B;**DELIVRD**&#x200B;或&#x200B;**DELIVERED**。 任何其他狀態都會導致嚴重故障。
