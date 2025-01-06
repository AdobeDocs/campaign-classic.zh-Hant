---
product: campaign
title: 認識隔離管理
description: 認識隔離管理
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '2987'
ht-degree: 8%

---

# 認識隔離管理{#understanding-quarantine-management}

Adobe Campaign 管理隔離地址清單。在執行傳遞分析時，預設情況下將不會向被隔離的收件者的電郵地址傳送內容。舉例來說，信箱已滿或地址不存在時，可以隔離電子郵件地址。 在任何情況下，隔離程式都符合下述的特定規則。

>[!NOTE]
>
>本節適用於線上頻道：電子郵件、簡訊、推播通知。

## 透過隔離管理最佳化您的傳遞 {#optimizing-your-delivery-through-quarantines}

郵件準備期間會自動排除其電子郵件地址或電話號碼處於隔離狀態的設定檔（請參閱[識別傳送的隔離地址](#identifying-quarantined-addresses-for-a-delivery)）。 這會加快傳送速度，因為錯誤率對傳送速度有顯著影響。

如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離可讓您避免被這些提供者新增到封鎖清單中。

此外，隔離有助於減少簡訊傳送成本，因為將錯誤的電話號碼排除在遞送服務之外。

如需確保傳送安全並最佳化的最佳實務，請參閱[本頁面](delivery-best-practices.md)。

### 隔離與封鎖清單 {#quarantine-vs-denylist}

隔離和封鎖清單不適用於相同的物件：

* **隔離**&#x200B;只適用於&#x200B;**位址** （或電話號碼等），不適用於設定檔本身。 例如，被隔離的電子郵件地址的設定檔可以更新其設定檔並輸入新地址，然後再次被傳送動作設為目標。 同樣地，如果兩個設定檔碰巧擁有相同的電話號碼，則兩個設定檔在隔離該號碼時都會受到影響。

  隔離的地址或電話號碼會顯示在[排除記錄](#identifying-quarantined-addresses-for-a-delivery) （針對傳遞）或[隔離清單](#identifying-quarantined-addresses-for-the-entire-platform) （針對整個平台）中。

* 另一方面，如果位於&#x200B;**封鎖清單**，則會導致&#x200B;**設定檔**&#x200B;不再被傳遞設為目標，例如在特定頻道的取消訂閱（選擇退出）之後。 例如，如果電子郵件頻道封鎖清單上的設定檔有兩個電子郵件地址，則兩個地址都會從傳送中排除。

  您可以在設定檔的&#x200B;**[!UICONTROL General]**&#x200B;索引標籤的&#x200B;**[!UICONTROL No longer contact]**&#x200B;區段中，檢查設定檔是否位於一或多個頻道的封鎖清單中。 請參閱[本節](../../platform/using/editing-a-profile.md#general-tab)。

>[!NOTE]
>
>隔離包括&#x200B;**[!UICONTROL Denylisted]**&#x200B;狀態，當收件者將您的訊息回報為垃圾訊息，或回覆具有如「STOP」之類關鍵字的SMS訊息時，就會套用此狀態。 在這種情況下，會將設定檔的相關地址或電話號碼傳送到隔離區，且狀態為&#x200B;**[!UICONTROL Denylisted]**。 如需管理STOP SMS訊息的詳細資訊，請參閱[本節](../../delivery/using/sms-send.md#processing-inbound-messages)。

## 識別隔離的地址 {#identifying-quarantined-addresses}

可以為特定傳送或整個平台列出隔離的地址。

### 識別傳送的隔離地址 {#identifying-quarantined-addresses-for-a-delivery}

在傳送準備階段期間，會將特定傳送的隔離地址列在傳送儀表板的傳送記錄中（請參閱[傳送記錄與歷史記錄](delivery-dashboard.md#delivery-logs-and-history)）。

### 識別整個平台的隔離地址 {#identifying-quarantined-addresses-for-the-entire-platform}

管理員可以列出來自&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;節點的整個平台之隔離區中的地址。

>[!NOTE]
>
>此功能表會列出&#x200B;**電子郵件**、**簡訊**&#x200B;和&#x200B;**推播通知**&#x200B;通道的隔離元素。

每個位址都有以下資訊：

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>隔離區數量的增加是正常效果，與資料庫的「磨損」有關。 例如，如果電子郵件地址的存留期被視為三年，而收件者表格每年增加50%，則隔離區數量的增加計算如下：
>
>年度結束1：(1&#42;0.33)/(1+0.5)=22%。
>
年度結束2：((1.22&#42;0.33)+0.33)/(1.5+0.75)=32.5%。

### 識別傳遞報表中的隔離地址 {#identifying-quarantined-addresses-in-delivery-reports}

下列報表提供關於隔離中地址的資訊：

* 對於每個傳遞，**[!UICONTROL Delivery summary]**&#x200B;報告都會顯示傳遞目標中隔離的地址數量。 它顯示：

   * 傳遞分析期間被置於隔離的地址數量；

   * 進行傳送動作後置於隔離區的地址數。

* **[!UICONTROL Non-deliverables and bounces]**&#x200B;報告會顯示隔離中地址、遇到的錯誤型別等資訊，以及依網域劃分的失敗資訊。

您可以查詢此資訊以取得平台(**[!UICONTROL Home page > Reports]**)的所有傳遞或特定傳遞。 您也可以建立自訂報表，並選取要顯示的資訊。

### 識別收件者的隔離地址 {#identifying-quarantined-addresses-for-a-recipient}

您可以查詢任何收件者之電子郵件地址的狀態。 若要這麼做，請選取收件者設定檔，然後按一下&#x200B;**[!UICONTROL Deliveries]**&#x200B;標籤。 對於傳送給該收件者的所有郵件，您可以檢視該地址是否失敗、在分析期間是否被隔離等。 對於每個資料夾，您只能顯示其電子郵件地址處於隔離狀態的收件者。 若要這麼做，請使用&#x200B;**[!UICONTROL Quarantined email address]**&#x200B;應用程式篩選器。

![](assets/tech_quarant_recipients_filter.png)


## 將地址傳送到隔離區的條件 {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign會根據傳送失敗型別和錯誤訊息限定期間指派的原因來管理隔離區（請參閱[退回郵件限定](understanding-delivery-failures.md#bounce-mail-qualification)和[傳送失敗型別和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)）。

* **忽略錯誤**：忽略的錯誤不會傳送要隔離的地址。
* **硬錯誤**：會立即將相對應的電子郵件地址傳送至隔離區。
* **軟錯誤**：軟錯誤不會立即傳送要隔離的地址，但會增加錯誤計數器。如需詳細資訊，請參閱[軟性錯誤管理](#soft-error-management)。

如果使用者將電子郵件歸類為垃圾訊息（[回饋迴路](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)），郵件會自動重新導向至由Adobe管理的技術信箱。 之後，系統會自動將使用者的電子郵件地址傳送到狀態為　**[!UICONTROL Denylisted]**　的隔離區。此狀態僅適用於地址，而且設定檔不在封鎖清單中，因此使用者會繼續收到SMS訊息和推播通知。

>[!NOTE]
>
Adobe Campaign　中的隔離區會區分大小寫。請務必以小寫匯入電子郵件地址，如此一來，稍後就不會將它們重新設為目標。

在隔離地址清單中（請參閱[識別整個平台的隔離地址](#identifying-quarantined-addresses-for-the-entire-platform)），**[!UICONTROL Error reason]**&#x200B;欄位會指出所選地址被置於隔離狀態的原因。

![](assets/tech_quarant_error_reasons.png)

### 軟性錯誤管理 {#soft-error-management}

與硬錯誤相反，軟錯誤不會立即傳送要隔離的地址，而是會增加錯誤計數器。

將在[傳遞期間](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)執行重試。 當錯誤計數器達到限制臨界值時，該地址就會進入隔離區。如需詳細資訊，請參閱[傳送暫時失敗後重試](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)。

如果最後一次重大錯誤發生在10天以前，則會重新初始化錯誤計數器。 然後，位址狀態會變更為&#x200B;**有效**，而且會由[資料庫清理](../../production/using/database-cleanup-workflow.md)工作流程從隔離清單中刪除該位址。


對於託管或混合安裝，如果您已升級至[增強型MTA](sending-with-enhanced-mta.md)，在&#x200B;**[!UICONTROL Erroneous]**&#x200B;狀態的情況下要執行的最大重試次數和重試之間的最小延遲，現在取決於IP在歷史和目前指定網域的執行狀況。

對於使用舊版Campaign MTA的內部部署安裝和託管/混合安裝，您可以修改錯誤數量和兩個錯誤之間的期間。 若要這麼做，請變更[部署精靈](../../installation/using/deploying-an-instance.md) (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**)或傳遞層級](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)的[中的對應設定。


## 從隔離中移除地址 {#removing-a-quarantined-address}

### 自動更新 {#unquarantine-auto}

符合特定條件的地址會由[資料庫清理](../../production/using/database-cleanup-workflow.md)工作流程自動從隔離清單中刪除。

在下列情況下，地址會自動從隔離清單中移除：

* 成功傳送後，會從隔離清單中移除&#x200B;**[!UICONTROL With errors]**&#x200B;狀態的地址。
* 如果最後一次軟退信發生於10天以前，則會從隔離清單中移除&#x200B;**[!UICONTROL With errors]**&#x200B;狀態的地址。 如需軟性錯誤管理的詳細資訊，請參閱[本節](#soft-error-management)。
* 狀態為&#x200B;**[!UICONTROL With errors]**&#x200B;且出現&#x200B;**[!UICONTROL Mailbox full]**&#x200B;錯誤退信的地址將在30天後從隔離清單中移除。

其狀態然後變更為&#x200B;**[!UICONTROL Valid]**。

>[!IMPORTANT]
>
位址處於&#x200B;**[!UICONTROL Quarantine]**&#x200B;或&#x200B;**[!UICONTROL Denylisted]**&#x200B;狀態的收件者即使收到電子郵件，也不會被移除。

### 手動更新 {#unquarantine-manual}

您也可以手動解除隔離地址。 若要從隔離清單手動移除地址，請將其狀態從&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**&#x200B;節點變更為&#x200B;**[!UICONTROL Valid]**。

![](assets/tech_quarant_error_status.png)

### 大量更新 {#unquarantine-bulk}

您可能需要對隔離清單執行大量更新，例如ISP中斷的情況。 在這種情況下，電子郵件會錯誤標籤為退回，因為它們無法成功傳遞給收件者。 必須從隔離清單中移除這些地址。

若要執行此動作，請建立工作流程，並在隔離表格上新增&#x200B;**[!UICONTROL Query]**&#x200B;活動，以篩選出所有受影響的收件者。 識別後，可將它們從隔離清單中移除，並包含在未來的Campaign電子郵件傳送中。

以下是此查詢的建議准則：

* 對於在隔離清單的&#x200B;**[!UICONTROL Error text]**&#x200B;欄位中有傳入電子郵件規則資訊的Campaign Classic v7環境：

   * **錯誤文字（隔離文字）**&#x200B;包含「Momen_Code10_InvalidRecipient」
   * **電子郵件網域(@domain)**&#x200B;等於domain1.com或&#x200B;**電子郵件網域(@domain)**&#x200B;等於domain2.com或&#x200B;**電子郵件網域(@domain)**&#x200B;等於domain3.com
   * 在`MM/DD/YYYY HH:MM:SS AM`或之後的&#x200B;**更新狀態(@lastModified)**
   * 在`MM/DD/YYYY HH:MM:SS PM`或之前的&#x200B;**更新狀態(@lastModified)**

* 對於在隔離清單的&#x200B;**[!UICONTROL Error text]**&#x200B;欄位中有SMTP退回回應資訊的Campaign Classicv7執行個體：

   * **錯誤文字（隔離文字）**&#x200B;包含「550-5.1.1」且&#x200B;**錯誤文字（隔離文字）**&#x200B;包含「support.ISP.com」

  其中「support.ISP.com」可以是：例如「support.apple.com」或「support.google.com」

   * 在`MM/DD/YYYY HH:MM:SS AM`或之後的&#x200B;**更新狀態(@lastModified)**
   * 在`MM/DD/YYYY HH:MM:SS PM`或之前的&#x200B;**更新狀態(@lastModified)**

取得受影響的收件者清單後，請新增&#x200B;**[!UICONTROL Update data]**&#x200B;活動以將其電子郵件地址狀態設定為&#x200B;**[!UICONTROL Valid]**，以便透過&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流程將其從隔離清單中移除。 您也可以從隔離表中刪除它們。

## 推播通知隔離 {#push-notification-quarantines}

推播通知的隔離機制與一般程式整體相同。 不過，推播通知的特定錯誤會以不同方式管理。 例如，對於某些軟錯誤，不會在同一傳送中執行重試。 推播通知的特定性列於下方。 重試機制（重試次數、頻率）與電子郵件的相同。

被隔離的專案是裝置代號。

### iOS隔離 {#ios-quarantine}

HTTP/V2通訊協定允許每個推播傳遞有直接的回饋和狀態。 如果使用HTTP/V2通訊協定聯結器，**[!UICONTROL mobileAppOptOutMgt]**&#x200B;工作流程將不再呼叫意見回饋服務。 解除安裝或重新安裝行動應用程式時，Token會視為已解除註冊。

同步時，如果APN針對訊息傳回「未註冊」狀態，則目標Token會立即置於隔離中。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>案例</strong><br /> </td> 
   <td> <strong>狀態</strong><br /> </td> 
   <td> <strong>錯誤訊息</strong><br /> </td> 
   <td> <strong>失敗型別</strong><br /> </td> 
   <td> <strong>失敗原因</strong><br /> </td> 
   <td> <strong>重試</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 目標裝置已開啟<br /> </td> 
   <td> 確定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 目標裝置已關閉<br /> </td> 
   <td> 確定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 使用者停用應用程式<br />的通知 </td> 
   <td> 確定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 訊息建立/分析階段 — 承載太大<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 承載太長<br /> </td> 
   <td> 軟式<br /> </td> 
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 訊息建立/分析階段 — 非預期的內容格式問題<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 根據錯誤<br />的各種錯誤訊息 </td> 
   <td> 軟式<br /> </td> 
   <td> 未定義<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 憑證問題（密碼、損毀等）和測試與APNs的連線問題<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 根據錯誤<br />的各種錯誤訊息 </td> 
   <td> 軟式<br /> </td> 
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送期間網路連線中斷<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 連線錯誤<br /> </td> 
   <td> 未定義<br /> </td> 
   <td> 無法連線<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> APN訊息拒絕：取消註冊<br />使用者已移除應用程式或權杖已過期<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 已取消登入<br /> </td> 
   <td> 硬式<br /> </td> 
   <td> 使用者不明<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> APNs訊息拒絕：所有其他錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 錯誤訊息<br />中出現錯誤拒絕原因 </td> 
   <td> 軟式<br /> </td> 
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android隔離 {#android-quarantine}

適用於Android V1 **的**

對於每個通知，Adobe Campaign會直接從FCM伺服器接收同步錯誤。 Adobe行銷活動會即時處理這些錯誤，並根據錯誤的嚴重性產生硬或軟錯誤，且可執行重試：

* 已超過承載長度、連線問題、服務可用性問題：已執行重試、軟錯誤、失敗原因為&#x200B;**[!UICONTROL Refused]**。
* 超過裝置配額：沒有重試、軟錯誤、失敗原因為&#x200B;**[!UICONTROL Refused]**。
* 無效的或未登入權杖、未預期的錯誤、寄件者帳戶問題：無重試、硬錯誤、失敗原因為&#x200B;**[!UICONTROL Refused]**。

**[!UICONTROL mobileAppOptOutMgt]**&#x200B;工作流程每6小時執行一次，以更新&#x200B;**AppSubscriptionRcp**&#x200B;資料表。 對於宣告為未登入或不再有效的權杖，**Disabled**&#x200B;欄位設為&#x200B;**True**，而且連結至該裝置權杖的訂閱將會自動從未來的傳遞中排除。

在傳遞分析期間，所有從目標排除的裝置都會自動新增至&#x200B;**excludeLogAppSubRcp**&#x200B;表格。

>[!NOTE]
>
對於使用百度聯結器的客戶，以下是不同型別的錯誤：
>
* 傳遞開始時的連線問題：失敗型別&#x200B;**[!UICONTROL Undefined]**，失敗原因&#x200B;**[!UICONTROL Unreachable]**，已執行重試。
* 傳遞期間連線中斷：軟錯誤，失敗原因&#x200B;**[!UICONTROL Refused]**，已執行重試。
* 百度在傳送期間傳回同步錯誤：硬錯誤，失敗原因&#x200B;**[!UICONTROL Refused]**，不執行重試。
>
Adobe Campaign每10分鐘會連絡百度伺服器以擷取已傳送訊息的狀態，並更新broadlog。 如果訊息宣告為已傳送，broadlogs中訊息的狀態會設為&#x200B;**[!UICONTROL Received]**。 如果百度宣告錯誤，狀態會設為&#x200B;**[!UICONTROL Failed]**。

適用於Android V2 **的**

Android V2隔離機制使用與Android V1相同的流程，同樣適用於訂閱和排除更新。 如需詳細資訊，請參閱[Android V1](#android-quarantine)區段。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>案例</strong><br /> </td> 
   <td> <strong>狀態</strong><br /> </td> 
   <td> <strong>錯誤訊息</strong><br /> </td> 
   <td> <strong>失敗型別</strong><br /> </td> 
   <td> <strong>失敗原因</strong><br /> </td> 
   <td> <strong>重試</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 訊息建立/分析階段：在自訂欄位<br />中使用的關鍵字不合法 </td> 
   <td> 失敗<br /> </td> 
   <td> 無法使用下列關鍵字： {1}<br /> </td> 
   <td> 軟式<br /> </td> 
   <td> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 訊息建立/分析階段：承載太大<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 通知太重： {1}位元，而只有{2}是授權的<br /> </td> 
   <td> 軟式<br /> </td> 
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送期間網路連線中斷<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 沒有來自位址{1}<br />上Firebase Cloud Messaging服務的回應 </td> 
   <td> 軟式<br /> </td> 
   <td> 無法連線<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM訊息拒絕： FCM伺服器暫時無法使用（例如逾時）。<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> Firebase Cloud Messaging服務暫時無法使用<br /> </td> 
   <td> 軟式<br /> </td> 
   <td> 無法連線<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM郵件拒絕：驗證寄件者帳戶<br />時發生錯誤 </td> 
   <td> 失敗<br /> </td> 
   <td> 無法識別開發人員帳戶，請檢查您的識別碼和密碼<br /> </td> 
   <td> 軟式<br /> </td> 
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM訊息拒絕：超過裝置配額<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> </td> 
   <td> 軟式<br /> </td> 
   <td> 已拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM訊息拒絕：註冊無效/未註冊<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> </td> 
   <td> 硬式<br /> </td> 
   <td> 使用者不明<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM訊息拒絕：所有其他錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> Firebase Cloud Messaging伺服器傳回未預期的錯誤碼： {1} </td> 
   <td> </td> 
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
    <tr> 
   <td> FCM訊息拒絕：無效的引數<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> 已忽略</td> 
   <td> 未定義<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM訊息拒絕：協力廠商驗證錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> 已忽略</td>
   <td> 已拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM訊息拒絕：寄件者識別碼不符<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> 柔光</td>
   <td> 使用者不明<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM訊息拒絕：已取消註冊<br /> </td> 
   <td> 失敗<br /> </td>
   <td> 未註冊 </td> 
   <td> 強烈</td> 
   <td> 使用者不明<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> FCM訊息拒絕：內部<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 內部 </td> 
   <td> 已忽略</td> 
   <td> 已拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM訊息拒絕：無法使用<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無法使用</td> 
   <td> 已忽略</td> 
   <td> 已拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> FCM訊息拒絕：未預期的錯誤碼<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 未預期的錯誤碼</td> 
   <td> 已忽略</td> 
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
  <tr> 
   <td> 驗證：連線問題<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 無法連線到驗證伺服器 </td> 
   <td> 已忽略</td>
   <td> 已拒絕<br /> </td> 
   <td> 是<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：要求中有未經授權的使用者端或範圍。<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 已忽略</td>
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：使用者端未獲授權，無法使用此方法擷取存取權杖，或是使用者端未獲授權使用任何要求的範圍。<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> unauthorized_client </td> 
   <td> 已忽略</td>
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：存取遭拒<br /> </td> 
   <td> 失敗<br /> </td>
   <td> access_denied</td> 
   <td> 已忽略</td>
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：無效的電子郵件<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> invalid_grant </td> 
   <td> 已忽略</td> 
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：無效的JWT<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> invalid_grant </td> 
   <td> 已忽略</td> 
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：無效的JWT簽章<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> invalid_grant </td> 
   <td> 已忽略</td> 
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證：提供的OAuth範圍或ID權杖對象無效<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> unauthorized_client</td> 
   <td> 已忽略</td> 
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
    <tr> 
   <td> 驗證： OAuth使用者端已停用<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> disabled_client</td> 
   <td> 已忽略</td> 
   <td> 已拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr>
 </tbody> 
</table>

## SMS隔離 {#sms-quarantines}

**適用於標準聯結器**

SMS訊息的隔離機制與一般程式在整體上相同。 請參閱[關於隔離](#about-quarantines)。 簡訊的特定性列於下方。

>[!NOTE]
>
**[!UICONTROL Delivery log qualification]**&#x200B;資料表不適用於&#x200B;**Extended generic SMPP**&#x200B;聯結器。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>案例</strong><br /> </td> 
   <td> <strong>狀態</strong><br /> </td> 
   <td> <strong>錯誤訊息</strong><br /> </td> 
   <td> <strong>失敗型別</strong><br /> </td> 
   <td> <strong>失敗原因</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 已傳送給提供者<br /> </td> 
   <td> 已傳送<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 已在行動裝置<br />上收到 </td> 
   <td> 已接收<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 提供者傳回的錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 接收資料（SR或MO）時發生錯誤<br /> </td> 
   <td> 軟式<br /> </td> 
   <td> 無法連線<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效的MT通知<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 處理傳送查詢<br />的認可框架時發生錯誤'{1}' </td> 
   <td> 軟式<br /> </td> 
   <td> 無法連線<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送MT<br />時發生錯誤 </td> 
   <td> 失敗<br /> </td> 
   <td> 傳送訊息時發生錯誤<br /> </td> 
   <td> 軟式<br /> </td> 
   <td> 無法連線<br /> </td> 
  </tr> 
 </tbody> 
</table>

延伸通用SMPP聯結器的&#x200B;****

使用SMPP通訊協定傳送SMS訊息時，錯誤管理的處理方式不同。 如需有關Extended generic SMPP聯結器的詳細資訊，請參閱[此頁面](sms-set-up.md#creating-an-smpp-external-account)。

SMPP聯結器會擷取使用規則運算式（規則運算式）傳回之SR （狀態報告）訊息的資料，以篩選其內容。 然後，此資料會與&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;資料表中的資訊進行比對（可透過&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**&#x200B;功能表取得）。

在限定新型別的錯誤之前，失敗原因預設一律設為&#x200B;**已拒絕**。

>[!NOTE]
>
失敗型別和失敗原因與電子郵件相同。 檢視[傳遞失敗型別和原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)。
>
請要求您的提供者提供狀態和錯誤碼的清單，以便在傳遞記錄資格表中設定適當的失敗型別和失敗原因。

產生的訊息範例：

```
SR Generic DELIVRD 000|#MESSAGE#
```

* 所有錯誤訊息都以&#x200B;**SR**&#x200B;開頭，以區分SMS錯誤碼與電子郵件錯誤碼。
* 錯誤訊息的第二部分（**Generic**，在此範例中）參考SMSC實作的名稱，例如SMS外部帳戶的&#x200B;**[!UICONTROL SMSC implementation name]**&#x200B;欄位中定義的名稱。 請參閱[此頁面](sms-set-up.md#creating-an-smpp-external-account)。

  由於對於每個提供者，相同的錯誤碼可能有不同的含義，因此此欄位可讓您知道產生錯誤碼的提供者。 然後您可以在相關提供者的檔案中找到錯誤。

* 錯誤訊息的第三部分（此範例中為&#x200B;**DELIVRD**）對應於使用SMS外部帳戶中定義的狀態擷取規則運算式從SR擷取的狀態代碼。

  此規則運算式指定於外部帳戶的&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;索引標籤中。 請參閱[此頁面](sms-set-up.md#creating-an-smpp-external-account)。

  ![](assets/tech_quarant_error_regex.png)

  依預設，規則運算式會擷取&#x200B;**SMPP 3.4規格**&#x200B;的&#x200B;**附錄B**&#x200B;區段所定義的&#x200B;**stat：**&#x200B;欄位。

* 錯誤訊息的第四部分(**000**)對應於使用SMS外部帳戶中定義的錯誤碼擷取規則運算式從SR擷取的錯誤碼。

  此規則運算式指定於外部帳戶的&#x200B;**[!UICONTROL SMSC specificities]**&#x200B;索引標籤中。 請參閱[此頁面](sms-set-up.md#creating-an-smpp-external-account)。

  依預設，規則運算式會擷取&#x200B;**SMPP 3.4規格**&#x200B;的&#x200B;**附錄B**&#x200B;區段所定義的&#x200B;**err：**&#x200B;欄位。

* 直立線符號(|)後面的所有專案只會顯示在&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表格的&#x200B;**[!UICONTROL First text]**&#x200B;欄中。 訊息標準化之後，此內容一律會由&#x200B;**#MESSAGE#**&#x200B;取代。 此程式會避免因類似錯誤而出現多個專案，與電子郵件的情況相同。 如需詳細資訊，請參閱[退回郵件資格](understanding-delivery-failures.md#bounce-mail-qualification)。

Extended generic SMPP聯結器會套用啟發式來尋找合理的預設值：如果狀態以&#x200B;**DELIV**&#x200B;開頭，則會被視為成功，因為它符合大多數提供者使用的一般狀態&#x200B;**DELIVRD**&#x200B;或&#x200B;**DELIVERED**。 任何其他狀態都會導致硬失敗。
