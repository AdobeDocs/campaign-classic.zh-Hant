---
product: campaign
title: 瞭解隔離管理
description: 瞭解隔離管理
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2613'
ht-degree: 15%

---

# 瞭解隔離管理{#understanding-quarantine-management}

![](../../assets/common.svg)

## 關於隔離 {#about-quarantines}

Adobe Campaign 管理隔離地址清單。在執行傳遞分析時，預設情況下將不會向被隔離的收件者的電郵地址傳送內容。例如信箱容量已滿或地址不存在時，您可以隔離電子郵件地址。在任何情況下，隔離程式都符合下述特定規則。

>[!NOTE]
>
>本節適用於線上頻道：電子郵件、簡訊、推播通知。

### 透過隔離最佳化傳送 {#optimizing-your-delivery-through-quarantines}

郵件準備期間會自動排除其電子郵件地址或電話號碼處於隔離狀態的設定檔（請參閱[識別傳送的隔離地址](#identifying-quarantined-addresses-for-a-delivery)）。這會加快傳送速度，因為錯誤率對傳送速度有顯著影響。

如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離可讓您避免被這些提供者新增至封鎖清單。

此外，隔離有助於減少簡訊傳送成本，因為將錯誤的電話號碼排除在遞送服務之外。如需確保傳送安全並最佳化的最佳實務，請參閱[本頁面](delivery-best-practices.md)。

### 隔離與封鎖清單 {#quarantine-vs-denylist}

**隔離** (Quarantine)　僅適用於地址，而不適用於設定檔本身。這代表如果兩個設定檔具有相同的電子郵件地址，則兩個設定檔在隔離地址時都會受到影響。

同樣地，被隔離的電子郵件地址的設定檔可以更新其設定檔並輸入新地址，然後再次被傳送動作設為目標。

另一方面，位於&#x200B;**denylist**&#x200B;會導致設定檔不再被任何傳送鎖定，例如在取消訂閱（選擇退出）後。

>[!NOTE]
>
>當使用者回覆SMS訊息時，其關鍵字如「STOP」，以選擇退出SMS傳送時，其設定檔不會像電子郵件選擇退出程式一樣新增至封鎖清單。 會將設定檔電話號碼傳送至隔離區，讓使用者繼續收到電子郵件訊息。

## 識別隔離地址 {#identifying-quarantined-addresses}

可以為特定傳送或整個平台列出隔離的地址。

### 識別傳送的隔離地址 {#identifying-quarantined-addresses-for-a-delivery}

在傳送準備階段期間，會在傳送控制面板的傳送記錄中列出特定傳送的隔離地址（請參閱[傳送記錄和歷史記錄](delivery-dashboard.md#delivery-logs-and-history)）。

### 識別整個平台的隔離地址 {#identifying-quarantined-addresses-for-the-entire-platform}

管理員可以從&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;節點列出整個平台的隔離區中的地址。

>[!NOTE]
>
>此功能表會列出&#x200B;**電子郵件**、**簡訊**&#x200B;和&#x200B;**推播通知**&#x200B;通道的隔離元素。

每個地址都有下列資訊：

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>隔離區數量增加是正常的影響，與資料庫的「磨損」有關。 例如，如果電子郵件地址的存留期被視為三年，而收件者表格每年增加50%，則隔離區數量的增加計算如下：
>
>年底1:(1*0.33)/(1+0.5)=22%。
年度結束 2：((1.22*0.33)+0.33)/(1.5+0.75)=32.5%。

### 識別傳送報告中的隔離地址 {#identifying-quarantined-addresses-in-delivery-reports}

下列報告提供隔離中地址的相關資訊：

* 對於每個傳送， **[!UICONTROL Delivery summary]**&#x200B;報表會顯示傳送目標中隔離區中的地址數。 隨即顯示：

   * 在傳送分析期間放在隔離區中的地址數，

   * 傳送動作後置於隔離區中的地址數。

* **[!UICONTROL Non-deliverables and bounces]**&#x200B;報告顯示有關隔離中的地址、遇到的錯誤類型等的資訊，以及按域的故障劃分。

您可以查詢平台(**[!UICONTROL Home page > Reports]**)的所有傳送或特定傳送的此資訊。 您也可以建立自訂報表，並選取要顯示的資訊。

### 識別收件者的隔離地址 {#identifying-quarantined-addresses-for-a-recipient}

您可以查詢任何收件者之電子郵件地址的狀態。 要執行此操作，請選取收件者設定檔，然後按一下&#x200B;**[!UICONTROL Deliveries]**&#x200B;標籤。 對於傳送給該收件者的所有傳送，您可以找出地址是否失敗、在分析期間是否被隔離等。 對於每個資料夾，您只能顯示其電子郵件地址處於隔離狀態的收件者。 要執行此操作，請使用&#x200B;**[!UICONTROL Quarantined email address]**&#x200B;應用程式篩選器。

![](assets/tech_quarant_recipients_filter.png)

### 移除隔離的地址 {#removing-a-quarantined-address}

如有需要，您可以手動從隔離清單中移除地址。 此外，符合特定條件的地址還會由&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流程自動從隔離清單中刪除。

要從隔離清單中手動刪除地址，請執行以下操作：

* 您可以從&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;節點將其狀態變更為&#x200B;**[!UICONTROL Valid]**。

   ![](assets/tech_quarant_error_status.png)

* 您也可以將其狀態變更為&#x200B;**[!UICONTROL Allowlisted]**。 在此情況下，地址仍保留在隔離清單中，但將系統地定位該地址，即使遇到錯誤亦然。

在下列情況下，地址會自動從隔離清單中刪除：

* 成功傳送後，處於&#x200B;**[!UICONTROL With errors]**&#x200B;狀態的地址將從隔離清單中移除。
* 如果上次軟退信發生在10天前，則處於&#x200B;**[!UICONTROL With errors]**&#x200B;狀態的地址將從隔離清單中刪除。 有關軟錯誤管理的詳細資訊，請參閱[此部分](#soft-error-management)。
* 30天後，處於&#x200B;**[!UICONTROL With errors]**&#x200B;狀態且因&#x200B;**[!UICONTROL Mailbox full]**&#x200B;錯誤退回的地址將從隔離清單中移除。

其狀態隨後變更為&#x200B;**[!UICONTROL Valid]**。

>[!IMPORTANT]
即使收到電子郵件，狀態為&#x200B;**[!UICONTROL Quarantine]**&#x200B;或&#x200B;**[!UICONTROL On denylist]**&#x200B;的收件者也不會被移除。

您可以修改錯誤數，以及兩個錯誤之間的句號。 要執行此操作，請變更部署精靈(**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**)中的對應設定。 有關部署嚮導的詳細資訊，請參閱[此部分](../../installation/using/deploying-an-instance.md)。

## 將地址傳送到隔離區的條件 {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign會根據傳送失敗類型和錯誤訊息限定期間指派的原因（請參閱[退信限定](understanding-delivery-failures.md#bounce-mail-qualification)）和[傳送失敗類型和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)來管理隔離。

* **忽略錯誤**：忽略的錯誤不會傳送要隔離的地址。
* **硬錯誤**：會立即將相對應的電子郵件地址傳送至隔離區。
* **軟錯誤**：軟錯誤不會立即傳送要隔離的地址，但會增加錯誤計數器。有關詳細資訊，請參閱[軟錯誤管理](#soft-error-management)。

如果用戶將電子郵件歸類為垃圾郵件（[反饋循環](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)），則該郵件會自動重定向到由Adobe管理的技術郵箱。 接著，系統會自動將使用者的電子郵件地址傳送至隔離區。

在隔離地址清單中， **[!UICONTROL Error reason]**&#x200B;欄位指示所選地址被置於隔離區的原因。 Adobe Campaign　中的隔離區會區分大小寫。請務必以小寫匯入電子郵件地址，如此一來，稍後就不會將它們重新設為目標。

![](assets/tech_quarant_error_reasons.png)

### 軟錯誤管理 {#soft-error-management}

與硬錯誤不同，軟錯誤不會立即傳送要隔離的地址，而會增加錯誤計數器。

* 當錯誤計數器達到限制臨界值時，該地址便會進入隔離區。
* 在預設設定中，臨界值會設定為　5　個錯誤，其中　2　個錯誤若相隔至少　24　小時，即為顯著錯誤。會將地址放置到隔離區的第五個錯誤。
* 可以修改錯誤計數器臨界值。如需詳細資訊，請參閱[傳送暫時失敗後重試](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)。

如果上次出現重大錯誤超過10天，則重新初始化錯誤計數器。 然後，地址狀態將更改為&#x200B;**Valid**，並且該地址將通過&#x200B;**Database cleanup**&#x200B;工作流從隔離清單中刪除。

## 推播通知隔離 {#push-notification-quarantines}

推播通知的隔離機制與一般程式全域相同。 請參閱[關於隔離](#about-quarantines)。 但推播通知的某些錯誤管理方式不同。 例如，針對某些軟錯誤，不會在相同傳送內執行重試。 推播通知的特異性列於下方。 重試機制（重試次數、頻率）與電子郵件的相同。

放入隔離區的項目是裝置代號。

### iOS隔離 {#ios-quarantine}

HTTP/V2通訊協定可針對每個推送傳送提供直接意見和狀態。 如果使用HTTP/V2通訊協定連接器，**[!UICONTROL mobileAppOptOutMgt]**&#x200B;工作流程將不再呼叫反饋服務。 在卸載或重新安裝移動應用程式時，將令牌視為未註冊。

同步地，如果APN返回消息的「未註冊」狀態，則目標令牌將立即被置於隔離狀態。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>藍本</strong><br /> </td> 
   <td> <strong>狀態</strong><br /> </td> 
   <td> <strong>錯誤訊息</strong><br /> </td> 
   <td> <strong>失敗類型</strong><br /> </td> 
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
   <td> 已關閉的目標設備<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 用戶禁用應用程式<br />的通知 </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 消息建立/分析階段 — 負載太大<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 裝載過長<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息建立/分析階段 — 意外的內容格式問題<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 根據錯誤<br />的各種錯誤消息 </td> 
   <td> 軟<br /> </td> 
   <td> 未定義<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 憑證問題（密碼、損毀等） 和測試與APN的連接問題<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 根據錯誤<br />的各種錯誤消息 </td> 
   <td> 軟<br /> </td> 
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
   <td> APN消息拒絕：取消註冊<br />用戶已刪除應用程式或令牌已過期<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 未註冊<br /> </td> 
   <td> 硬<br /> </td> 
   <td> 用戶未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> APN消息拒絕：所有其他錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 錯誤消息<br />中將出現錯誤拒絕原因 </td> 
   <td> 軟<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android隔離 {#android-quarantine}

**針對Android V1**

對於每個通知，Adobe Campaign會直接從FCM伺服器接收同步錯誤。 Adobe促銷活動會即時處理這些錯誤，並根據錯誤的嚴重性產生硬錯誤或軟錯誤，且可執行重試：

* 已超出裝載長度、連線問題、服務可用性問題：重試已執行，軟錯誤，失敗原因為&#x200B;**[!UICONTROL Refused]**。
* 超出設備配額：無重試，軟錯誤，失敗原因為&#x200B;**[!UICONTROL Refused]**。
* 無效或未註冊的令牌，意外錯誤，發件人帳戶問題：無重試，硬錯誤，失敗原因為&#x200B;**[!UICONTROL Refused]**。

**[!UICONTROL mobileAppOptOutMgt]**&#x200B;工作流程每6小時執行一次，以更新&#x200B;**AppSubscriptionRcp**&#x200B;表格。 對於宣告未註冊或不再有效的權杖，欄位&#x200B;**Disabled**&#x200B;會設為&#x200B;**True**，連結至該裝置權杖的訂閱將自動排除在未來傳送之外。

在傳送分析期間，從目標中排除的所有裝置都會自動新增至&#x200B;**excludeLogAppSubRcp**&#x200B;表格。

>[!NOTE]
對於使用Baidu連接器的客戶，以下是不同類型的錯誤：
* 傳送開始時發生連線問題：失敗類型&#x200B;**[!UICONTROL Undefined]**，失敗原因&#x200B;**[!UICONTROL Unreachable]**，請執行重試。
* 傳送期間連線遺失：軟錯誤，故障原因&#x200B;**[!UICONTROL Refused]**，請執行重試。
* Baidu在傳送期間傳回的同步錯誤：硬錯誤，故障原因&#x200B;**[!UICONTROL Refused]**，未執行重試。
Adobe Campaign每10分鐘連絡Baidu伺服器以擷取已傳送訊息的狀態，並更新broadlog。 如果訊息宣告為已傳送，則broadlogs中訊息的狀態會設為&#x200B;**[!UICONTROL Received]**。 如果Baidu聲明錯誤，則狀態設定為&#x200B;**[!UICONTROL Failed]**。

**針對Android V2**

Android V2隔離機制使用的程式與Android V1相同，適用於訂閱和排除更新的程式也相同。 如需詳細資訊，請參閱[Android V1](#android-quarantine)區段。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>藍本</strong><br /> </td> 
   <td> <strong>狀態</strong><br /> </td> 
   <td> <strong>錯誤訊息</strong><br /> </td> 
   <td> <strong>失敗類型</strong><br /> </td> 
   <td> <strong>失敗原因</strong><br /> </td> 
   <td> <strong>重試</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 消息建立/分析階段：自訂欄位<br />中使用的非法關鍵字 </td> 
   <td> 失敗<br /> </td> 
   <td> 下列關鍵字無法使用：{1}<br /> </td> 
   <td> 軟<br /> </td> 
   <td> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 消息建立/分析階段：裝載太大<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 通知過重：{1}位，而僅授權{2}<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 發送<br />期間網路連接丟失 </td> 
   <td> 失敗<br /> </td> 
   <td> 地址上沒有來自Firebase雲端訊息服務的回應：{1}<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 無法訪問<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM報文拒絕：FCM伺服器暫時無法使用（例如逾時）。<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> Firebase雲端訊息服務暫時無法使用<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 無法訪問<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM報文拒絕：驗證發件人帳戶時出錯<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無法識別開發人員帳戶，請檢查您的ID和密碼<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM報文拒絕：已超出設備配額<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> </td> 
   <td> 軟<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM報文拒絕：註冊無效/未註冊<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> </td> 
   <td> 硬<br /> </td> 
   <td> 用戶未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM報文拒絕：所有其他錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> Firebase雲端訊息伺服器傳回未預期的錯誤碼：{1} </td> 
   <td> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
    <tr> 
   <td> FCM報文拒絕：參數<br />無效 </td> 
   <td> 失敗<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> 已忽略</td> 
   <td> 未定義<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM報文拒絕：第三方身份驗證錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM報文拒絕：發件人ID不匹配<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> 軟</td>
   <td> 用戶未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM報文拒絕：未註冊<br /> </td> 
   <td> 失敗<br /> </td>
   <td> 未註冊 </td> 
   <td> 硬</td> 
   <td> 用戶未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM報文拒絕：內部<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 內部 </td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM報文拒絕：不可用<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 不可用</td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM報文拒絕：意外錯誤代碼<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 意外錯誤代碼</td> 
   <td> 已忽略</td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
  <tr> 
   <td> 驗證：連接問題<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無法連接到身份驗證伺服器 </td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：請求中的未授權客戶端或作用域。<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：客戶端未授權使用此方法檢索訪問令牌，或客戶端未授權任何請求的作用域。<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 已忽略</td>
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：拒絕訪問<br /> </td> 
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
   <td> 驗證：提供的OAuth範圍或ID令牌對象無效<br /> </td> 
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

## SMS隔離 {#sms-quarantines}

**標準連接器**

SMS訊息的隔離機制與一般程式全域相同。 請參閱[關於隔離](#about-quarantines)。 SMS的特異性列於下方。

>[!NOTE]
**[!UICONTROL Delivery log qualification]**&#x200B;表不適用於&#x200B;**擴展通用SMPP**&#x200B;連接器。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>藍本</strong><br /> </td> 
   <td> <strong>狀態</strong><br /> </td> 
   <td> <strong>錯誤訊息</strong><br /> </td> 
   <td> <strong>失敗類型</strong><br /> </td> 
   <td> <strong>失敗原因</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 已發送到提供程式<br /> </td> 
   <td> 已發送<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 在行動裝置上收到<br /> </td> 
   <td> 已接收<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 提供程式<br />返回的錯誤 </td> 
   <td> 失敗<br /> </td> 
   <td> 接收資料（SR或MO）時出錯<br /> </td> 
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
   <td> 發送MT<br />時出錯 </td> 
   <td> 失敗<br /> </td> 
   <td> 發送消息時出錯<br /> </td> 
   <td> 軟<br /> </td> 
   <td> 無法訪問<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Extended generic SMPP連接器**

使用SMPP通訊協定傳送SMS訊息時，錯誤管理的處理方式不同。 有關Extended generic SMPP連接器的詳細資訊，請參閱[本頁](sms-set-up.md#creating-an-smpp-external-account)。

SMPP連接器會從SR（狀態報表）訊息中擷取資料，該訊息使用規則運算式(regexes)傳回以篩選其內容。 然後，此資料將與&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表中的資訊（可通過&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**&#x200B;菜單獲得）匹配。

在限定新類型的錯誤之前，預設情況下，失敗原因始終設定為&#x200B;**Recommended**。

>[!NOTE]
失敗類型和原因與電子郵件的相同。 請參閱[傳送失敗類型和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)。
請向提供者索取狀態和錯誤代碼清單，以便在「傳送記錄檔資格」表格中設定正確的失敗類型和失敗原因。

產生的訊息範例：

```
SR Generic DELIVRD 000|#MESSAGE#
```

* 所有錯誤訊息都以&#x200B;**SR**&#x200B;開頭，以區分SMS錯誤碼和電子郵件錯誤碼。
* 錯誤訊息的第二部分（此範例中的&#x200B;**一般**）參照SMS外部帳戶的&#x200B;**[!UICONTROL SMSC implementation name]**&#x200B;欄位中定義的SMSC實作名稱。 請參閱[此頁面](sms-set-up.md#creating-an-smpp-external-account)。

   因為相同的錯誤代碼可能對每個提供程式具有不同的含義，所以此欄位允許您了解生成錯誤代碼的提供程式。 然後，您可以在相關提供者的檔案中找到錯誤。

* 此範例中，錯誤訊息的第三部分(**DELIVRD**)與使用SMS外部帳戶中定義的狀態擷取規則運算式從SR擷取的狀態代碼相對應。

   此規則運算式在外部帳戶的&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;標籤中指定。 請參閱[此頁面](sms-set-up.md#creating-an-smpp-external-account)。

   ![](assets/tech_quarant_error_regex.png)

   預設情況下，規則運算式提取&#x200B;**stat:**&#x200B;欄位，如&#x200B;**SMPP 3.4規範**&#x200B;的&#x200B;**附錄B**&#x200B;部分所定義。

* 錯誤訊息的第四部分（此範例中為&#x200B;**000**）對應於使用SMS外部帳戶中定義的錯誤碼擷取規則運算式從SR擷取的錯誤碼。

   此規則運算式在外部帳戶的&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;標籤中指定。 請參閱[此頁面](sms-set-up.md#creating-an-smpp-external-account)。

   依預設，規則運算式會擷取&#x200B;**err:**&#x200B;欄位，如&#x200B;**SMPP 3.4規格**&#x200B;的&#x200B;**附錄B**&#x200B;區段所定義。

* 直線符號(|)之後的所有內容僅顯示在&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表的&#x200B;**[!UICONTROL First text]**&#x200B;列中。 在對消息進行標準化後，此內容始終由&#x200B;**#MESSAGE#**&#x200B;替換。 此程式可避免因類似錯誤而有多個項目，且與電子郵件的項目相同。 有關詳細資訊，請參閱[退信限定](understanding-delivery-failures.md#bounce-mail-qualification)。

Extended generic SMPP連接器應用啟發式來查找明顯預設值：如果狀態以&#x200B;**DELIV**&#x200B;開頭，則視為成功，因為它符合大多數提供者使用的常見狀態&#x200B;**DELIVRD**&#x200B;或&#x200B;**DELIVED**。 任何其他狀態都會導致硬性失敗。
