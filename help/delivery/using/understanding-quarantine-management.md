---
title: 瞭解隔離管理
seo-title: 瞭解隔離管理
description: 瞭解隔離管理
seo-description: null
page-status-flag: never-activated
uuid: 9421e26c-bdcc-4588-8e44-fa6f31051081
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 56cbf48a-eb32-4617-8f80-efbfd05976ea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 527d2dd2296d18c8ca26745b9f87d65c6fdf480a

---


# 瞭解隔離管理{#understanding-quarantine-management}

## 關於隔離 {#about-quarantines}

Adobe Campaign 管理隔離地址的清單。在執行傳遞分析時，預設情況下將不會向被隔離的收件者的電郵地址傳送內容。例如信箱容量已滿或地址不存在時，您可以隔離電子郵件地址。在任何情況下，隔離程式都符合以下所述的特定規則。

>[!NOTE]
>
>本節適用於線上渠道：電子郵件、簡訊、推播通知。

### 透過隔離最佳化傳送 {#optimizing-your-delivery-through-quarantines}

郵件準備期間會自動排除其電子郵件地址或電話號碼處於隔離狀態的配置檔案(請參 [閱標識傳送的隔離地址](#identifying-quarantined-addresses-for-a-delivery))。 這會加快傳送速度，因為錯誤率對傳送速度有顯著影響。

如果無效地址的比率過高，某些Internet訪問提供商會自動將電子郵件視為垃圾郵件。 因此，隔離可讓您避免這些提供者列入黑名單。

此外，隔離有助於減少簡訊發送成本，因為將錯誤的電話號碼排除在遞送服務之外。 如需確保傳送安全並最佳化的最佳實務，請參閱 [本頁](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)。

### 隔離與黑名單 {#quarantine-vs-blacklisting}

**隔離** (Quarantine)僅適用於地址，而不適用於配置檔案本身。 這意味著，如果兩個配置檔案具有相同的電子郵件地址，則兩個配置檔案在隔離地址時都會受到影響。

同樣地，被隔離的電子郵件地址的配置檔案可以更新其配置檔案並輸入新地址，然後再次被傳送操作定位。

**而黑名單**，則會導致描述檔不再被任何傳送鎖定，例如在取消訂閱（選擇退出）後。

>[!NOTE]
>
>當使用者回覆SMS訊息時，其關鍵字如「STOP」，以選擇退出SMS傳送時，其個人檔案不會像電子郵件選擇退出程式一樣列入黑名單。 配置檔案電話號碼會發送到隔離區，以便用戶繼續接收電子郵件消息。

## 標識隔離地址 {#identifying-quarantined-addresses}

可以為特定傳送或整個平台列出隔離的地址。

### 標識傳送的隔離地址 {#identifying-quarantined-addresses-for-a-delivery}

特定傳送的隔離地址在傳送準備階段中列在傳送控制面板的傳送記錄中(請參閱傳送記 [錄和歷史記錄](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history))。

### 識別整個平台的隔離地址 {#identifying-quarantined-addresses-for-the-entire-platform}

管理員可以從節點中列出隔離整個平台的地 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** 址。

>[!NOTE]
>
>此功能表列出電子郵件、 **簡訊和推播通**&#x200B;知通 **道的隔離元素****** 。

每個地址都有以下資訊：

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>檢疫數量增加是正常的，與資料庫的「磨損」有關。 例如，如果電子郵件地址的存留期被視為三年，而收件者表每年增加50%，則隔離的增加可以計算如下：
>
>年終1:(1*0.33)/(1+0.5)=22%。
年終2:((1.22*0.33)+0.33)/(1.5+0.75)=32.5%。

### 在傳送報告中識別隔離地址 {#identifying-quarantined-addresses-in-delivery-reports}

以下報告提供了有關隔離中地址的資訊：

* 對於每個傳送，報 **[!UICONTROL Delivery summary]** 表會顯示傳送目標中隔離的地址數。 它顯示：

   * 在交貨分析期間，隔離中放置的地址數，

   * 傳送動作後置於隔離中的地址數。

* 報 **[!UICONTROL Non-deliverables and bounces]** 表會顯示隔離中的地址、遇到的錯誤類型等資訊，以及按域劃分的故障細分。

您可以查詢平台的所有傳送(首頁>報&#x200B;**表**)或特定傳送的資訊。 您也可以建立自訂報表，並選取要顯示的資訊。

### 標識收件人的隔離地址 {#identifying-quarantined-addresses-for-a-recipient}

您可以查找任何收件者的電子郵件地址狀態。 若要這麼做，請選取收件者描述檔，然後按一下標 **[!UICONTROL Deliveries]** 簽。 對於所有傳送給該收件人的郵件，您可以瞭解地址是否失敗、分析期間是否隔離等。 對於每個資料夾，您只能顯示電子郵件地址處於隔離狀態的收件人。 若要這麼做，請使用應用程 **[!UICONTROL Quarantined email address]** 式篩選。

![](assets/tech_quarant_recipients_filter.png)

### 刪除隔離地址 {#removing-a-quarantined-address}

如果需要從隔離中刪除地址，請將其狀態手動更改為 **[!UICONTROL Valid]**。

![](assets/tech_quarant_error_status.png)

如果您將狀態變更為 **[!UICONTROL Whitelisted]**，則每次都會系統鎖定位址，即使發生錯誤亦然。

>[!CAUTION]
黑名單地址不受隔離系統的關注，也不是目標地址，即使您更改了地址的狀態。

您也可以變更錯誤數和錯誤之間的期間。 若要這麼做，請變更部署精靈的設定（電子郵件頻道／進階設定）。 有關部署嚮導的詳細資訊，請參 [閱本節](../../installation/using/deploying-an-instance.md)。

## 將地址發送到隔離的條件 {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign會根據傳送失敗類型和錯誤訊息限定期間指派的原因(請參閱 [Bounce mail qualification](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification))和傳送失敗類 [型和原因來管理隔離](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。

* **忽略錯誤**:忽略的錯誤不會傳送要隔離的地址。
* **硬錯誤**:對應的電子郵件地址會立即傳送至隔離區。
* **軟錯誤**:軟錯誤不會立即發送要隔離的地址，但會增加錯誤計數器。 如需詳細資訊，請參閱「軟 [體錯誤管理」](#soft-error-management)。

如果使用者將電子郵件歸為垃圾訊息(**回饋迴路**)，則會自動將訊息重新導向至Adobe管理的技術郵箱。 然後，用戶的電子郵件地址會自動發送到隔離區。

在隔離地址清單中，該字 **[!UICONTROL Error reason]** 段指明了將選定地址置於隔離中的原因。 Adobe Campaign中的隔離區區分大小寫。 請務必以小寫匯入電子郵件地址，以便日後不會重新定位。

![](assets/tech_quarant_error_reasons.png)

### 軟錯誤管理 {#soft-error-management}

與硬錯誤相反，軟錯誤不會立即傳送要隔離的地址，而會增加錯誤計數器。

* 當錯誤計數器達到限制閾值時，地址將被隔離。
* 在預設設定中，臨界值會設定為5個錯誤，其中2個錯誤若相隔至少24小時，即顯著。 地址在第五個錯誤處被置於隔離中。
* 可以修改錯誤計數器閾值。 如需詳細資訊，請參閱「傳送暫 [時失敗後重試」](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)。

如果上一個重大錯誤發生在10天前，則重新初始化錯誤計數器。 地址狀態隨後變更為「 **有效** 」，並且會從「資料庫清理」工作流的隔離列 **表中刪除** 。

## 推播通知隔離 {#push-notification-quarantines}

推播通知的隔離機制與一般程式的整體相同。 請參 [閱關於隔離](#about-quarantines)。 不過，推播通知的某些錯誤管理方式不同。 例如，對於某些軟錯誤，不會在同一傳送內執行任何重試。 推播通知的特定性列於下方。 重試機制（重試次數、頻率）與電子郵件的重試機制相同。

被隔離的項目是設備令牌。

### iOS隔離 {#ios-quarantine}

**適用於iOS —— 二進位連接器**

對於每個通知，Adobe Campaign會從APNS伺服器收到同步和非同步錯誤。 對於下列同步錯誤，Adobe Campaign會產生軟性錯誤：

* 裝載長度問題：無重試，失敗原因為 **[!UICONTROL Unreachable]**。
* 憑證到期問題：無重試，失敗原因為 **[!UICONTROL Unreachable]**。
* 傳送期間連線中斷：重試時，失敗原因為 **[!UICONTROL Unreachable]**。
* 服務配置問題（證書無效、證書密碼無效、證書無效）:無重試，失敗原因為 **[!UICONTROL Unreachable]**。

APNS伺服器會以非同步方式通知Adobe Campaign，裝置Token已未註冊（當使用者解除安裝行動應用程式時）。 此工 **[!UICONTROL mobileAppOptOutMgt]** 作流程每6小時執行一次，以聯絡APNS意見服務以更新 **AppSubscriptionRcp** 表。 對於所有已停用的Token, **Disabled** （停用）欄位會設為 **True** ，而連結至該裝置Token的訂閱會自動排除在未來傳送中。

**適用於iOS - HTTP/2連接器**

http/2通訊協定可讓每個推播傳送直接回饋和狀態。 如果使用http/2通訊協定連接器，工作流程將不再呼叫回饋服 **[!UICONTROL mobileAppOptOutMgt]** 務。 未註冊的Token在iOS二進位連接器和iOS http/2連接器之間的處理方式不同。 解除安裝或重新安裝行動應用程式時，會將Token視為未註冊。

同步地，如果APNS返回消息的「未註冊」狀態，則目標Token將立即被隔離。

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
   <td> 已啟動目標裝置<br /> </td> 
   <td> 確定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 關閉目標裝置<br /> </td> 
   <td> 確定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 使用者停用應用程式的通知<br /> </td> 
   <td> 確定<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 消息建立／分析階段——負載過大<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 裝載過長<br /> </td> 
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
   <td> 憑證問題（密碼、損毀等）並測試與APNS問題的連線<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 根據錯誤顯示的各種錯誤消息<br /> </td> 
   <td> Soft<br /> </td> 
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
   <td> APNS消息拒絕：取消註冊<br /> ，使用者已移除應用程式或Token已過期<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 未註冊<br /> </td> 
   <td> 硬<br /> </td> 
   <td> 用戶未知<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> APNS消息拒絕：所有其他錯誤<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 錯誤消息中將顯示錯誤拒絕原因<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Android隔離 {#android-quarantine}

**適用於Android V1**

對於每個通知，Adobe Campaign會直接從FCM伺服器接收同步錯誤。 Adobe促銷活動會即時處理這些錯誤，並根據錯誤的嚴重性產生硬錯誤或軟錯誤，並可執行重試：

* 負載長度已超出，連接問題，服務可用性問題：重試，軟錯誤，失敗原因 **[!UICONTROL Refused]**&#x200B;為。
* 超過設備配額：無重試，軟錯誤，失敗原因 **[!UICONTROL Refused]**&#x200B;為。
* 無效或未註冊的Token、非預期錯誤、傳送者帳戶問題：無重試，硬錯誤，失敗原因 **[!UICONTROL Refused]**&#x200B;為。

工作流程 **[!UICONTROL mobileAppOptOutMgt]** 每6小時執行一次，以更新 **AppSubscriptionRcp** 表格。 對於宣告為未註冊或不再有效的Token, **Disabled** （停用）欄位會設為 **True** ，連結至該裝置Token的訂閱會自動排除在未來傳送中。

在傳送分析期間，所有從目標中排除的裝置都會自動新增至 **excludeLogAppSubRcp** 表格。

>[!NOTE]
對於使用Baidu連接器的客戶，以下是不同類型的錯誤：
* 傳送開始時的連線問題：失敗類 **[!UICONTROL Undefined]**&#x200B;型、失敗原 **[!UICONTROL Unreachable]**&#x200B;因、重試被執行。
* 傳送期間連線遺失：軟錯誤、失敗原 **[!UICONTROL Refused]**&#x200B;因、重試被執行。
* Baidu在傳送期間傳回的同步錯誤：硬錯誤、失敗原 **[!UICONTROL Refused]**&#x200B;因、未執行重試。

Adobe Campaign每10分鐘與Baidu伺服器連絡，以擷取已傳送訊息的狀態並更新廣播。 如果消息被聲明為已發送，則廣播中消息的狀態將設定為 **[!UICONTROL Received]**。 如果Baidu宣告錯誤，狀態會設為 **[!UICONTROL Failed]**。

**適用於Android V2**

Android V2隔離機制使用與Android V1相同的程式，訂閱和排除更新的程式也相同。 如需詳細資訊，請參閱 [Android V1](#android-quarantine) 。

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
   <td> 消息建立／分析階段：負載過大<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 通知太重：{1}位，但僅授權{2}<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 拒絕<br /> </td> 
   <td> 否<br /> </td> 
  </tr> 
  <tr> 
   <td> 發送過程中網路連接丟失<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> Firebase Cloud Messaging服務未回應此位址：{1}<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 無法訪問<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> FCM消息拒絕：FCM伺服器暫時不可用（例如超時）。 <br /> </td> 
   <td> 失敗<br /> </td> 
   <td> Firebase Cloud訊息服務暫時無法使用<br /> </td> 
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
   <td> FCM消息拒絕：已超出設備配額<br /> </td> 
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
 </tbody> 
</table>

## SMS隔離 {#sms-quarantines}

**針對標準連接器**

SMS消息的隔離機制與一般過程在全局上是相同的。 請參 [閱關於隔離](#about-quarantines)。 以下列出SMS的特定性。

>[!NOTE]
該 **[!UICONTROL Delivery log qualification]** 表不適用於 **Extended通用SMPP連接器** 。

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
   <td> 傳送給提供者<br /> </td> 
   <td> 已傳送<br /> </td> 
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
   <td> 發送MT時出錯<br /> </td> 
   <td> 失敗<br /> </td> 
   <td> 發送消息時出錯<br /> </td> 
   <td> Soft<br /> </td> 
   <td> 無法訪問<br /> </td> 
  </tr> 
 </tbody> 
</table>

**對於擴展的通用SMPP連接器**

當使用SMPP協定發送SMS消息時，錯誤管理的處理方式不同。 有關Extended通用SMPP連接器的詳細資訊，請參 [閱本頁](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

SMPP連接器從SR（狀態報告）消息中檢索資料，該消息使用規則運算式(regexes)返回以過濾其內容。 然後，此資料會與表格中的資訊相符 **[!UICONTROL Delivery log qualification]** 合(可透過 **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** >功能表 **[!UICONTROL Non deliverables Management]** 取得)。

在限定新錯誤類型之前，故障原因總是預設設定為「 **Resubled** （拒絕）」。

>[!NOTE]
失敗類型和失敗原因與電子郵件相同。 請參 [閱傳送失敗類型和原因](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)。
請洽詢您的供應商，以取得狀態和錯誤碼清單，以便在「傳送記錄」資格表中設定正確的失敗類型和失敗原因。

生成的消息示例：

```
SR Generic DELIVRD 000|#MESSAGE#
```

* 所有錯誤消息都以 **SR開頭** ，以區分SMS錯誤代碼和電子郵件錯誤代碼。
* 錯誤消息的第二&#x200B;**部分** （在本例中為一般）引用SMSC實現的名稱，如在SMS外部帳戶的字 **[!UICONTROL SMSC implementation name]** 段中定義的名稱。 請參 [閱本頁](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

   由於相同的錯誤代碼可能對每個提供程式有不同的含義，因此，此欄位允許您瞭解哪個提供程式生成了錯誤代碼。 然後，您可以在相關供應商的檔案中找到錯誤。

* 錯誤消息的第三部分(**本例中為** DELIVRD)與使用SMS外部帳戶中定義的狀態抽取regex從SR檢索的狀態代碼相對應。

   此規則運算式是在外部帳 **[!UICONTROL SMSC specificities]** 戶的索引標籤中指定。 請參 [閱本頁](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

   ![](assets/tech_quarant_error_regex.png)

   依預設，regex會擷取 **stat:** 欄位，如 **SMPP 3.4規範的附錄B****部分所定義**。

* 錯誤消息的第四部分(**000** ，在本示例中)與使用SMS外部帳戶中定義的錯誤代碼提取規則從SR中提取的錯誤代碼相對應。

   此規則運算式是在外部帳 **[!UICONTROL SMSC specificities]** 戶的索引標籤中指定。 請參 [閱本頁](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

   依預設，regex會擷取 **錯誤：** 欄位，如 **SMPP 3.4規範的附錄B****部分所定義**。

* 垂直號(|)後面的所有項目只會顯示在 **[!UICONTROL First text]** 表格的欄 **[!UICONTROL Delivery log qualification]** 中。 在訊息標準化後， **此內容一律由** #MESSAGE#取代。 此程式可避免因類似錯誤而出現多個項目，而且與電子郵件相同。 如需此方面的詳細資訊，請參閱「彈 [回郵件資格](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)」。

擴展通用SMPP連接器採用啟發式方法來查找合理的預設值：如果狀態以 **DELIV開頭**，則會視為成功，因為它符合大多數提供者使用的常見狀 **態DELIVRD****或** DELIVERED。 任何其他狀態都會導致嚴重故障。
