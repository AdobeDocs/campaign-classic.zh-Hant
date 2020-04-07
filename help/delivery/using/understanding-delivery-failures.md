---
title: 瞭解傳送故障
seo-title: 瞭解傳送故障
description: 瞭解傳送故障
seo-description: null
page-status-flag: never-activated
uuid: 03a91f84-77fe-40a9-8be9-a6a35a873ae1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 78b58a7a-b387-4d5d-80d5-01c06f83d759
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e5a2ef47108c6779a744197638e2de9d1072cfe3

---


# 瞭解傳送故障{#understanding-delivery-failures}

## 關於傳送失敗 {#about-delivery-failures}

當訊息（電子郵件、SMS、推播通知）無法傳送至描述檔時，遠端伺服器會自動傳送錯誤訊息，該錯誤訊息會由Adobe Campaign平台擷取，並符合資格決定是否應隔離電子郵件地址或電話號碼。 請參閱 [彈回郵件管理](#bounce-mail-management)。

>[!NOTE]
>
>電子郵件錯誤訊息（或「彈回數」）由inMail程式限定。 MTA流程會限定SMS錯誤訊息（或「狀態報告」的「SR」）。

傳送訊息後，傳送記錄檔可讓您檢視每個描述檔的傳送狀態以及相關的失敗類型和原因。

如果地址被隔離或配置檔案被列入黑名單，在準備傳送時也可以排除郵件。 已排除的訊息會列在傳送控制面板中。

**相關主題：**

* [傳送記錄檔和記錄](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)
* [失敗狀態](../../delivery/using/monitoring-a-delivery.md#failed-status)
* [傳送失敗類型和原因](#delivery-failure-types-and-reasons)

## 傳送失敗類型和原因 {#delivery-failure-types-and-reasons}

消息失敗時有三種錯誤類型。 每個錯誤類型都決定是否將地址發送給隔離。 有關詳細資訊，請參 [閱發送地址到隔離的條件](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

* **硬**:「硬」錯誤表示地址無效。 這包含明確指出地址無效的錯誤訊息，例如：&quot;未知用戶&quot;。
* **軟**:這可能是暫時錯誤，或無法分類的錯誤，例如：「無效域」或「郵箱已滿」。
* **已忽略**:這是已知為暫時的錯誤，例如「不在辦公室」，或是技術錯誤，例如，如果傳送者類型是「postmaster」。

傳送失敗的可能原因有：

<table> 
 <tbody> 
  <tr> 
   <td> 錯誤標籤 </td> 
   <td> 錯誤類型 </td> 
   <td> 技術價值 </td> 
   <td> 說明 </td> 
  </tr> 
  <tr> 
   <td> 帳戶已停用 </td> 
   <td> 柔／硬 </td> 
   <td> 4 </td> 
   <td> 連結至該位址的帳戶不再有效。 當Internet訪問提供程式(IAP)檢測到長時間的不活動時，它可以關閉用戶帳戶。 然後，將無法傳送至使用者的位址。 如果帳戶因為6個月的閒置而暫時停用，而且仍可啟動，則會指派「有錯誤」狀態，並重新嘗試帳戶，直到錯誤計數器達到5為止。 如果錯誤信號表明帳戶已永久停用，則它將直接設定為「隔離」。<br /> </td> 
  </tr> 
  <tr> 
   <td> 隔離中的地址 </td> 
   <td> 硬 </td> 
   <td> 9 </td> 
   <td> 地址已置於隔離區。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未指定地址 </td> 
   <td> 硬 </td> 
   <td> 7 </td> 
   <td> 未提供收件者的地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不良地址 </td> 
   <td> 已忽略 </td> 
   <td> 14 </td> 
   <td> 此位址的品質分級太低。<br /> </td> 
  </tr> 
  <tr> 
   <td> 黑名單地址 </td> 
   <td> 硬 </td> 
   <td> 8 </td> 
   <td> 傳送時，地址已列入黑名單。 當將資料匯入Adobe Campaign Quarantine清單時，此狀態用於從外部清單和外部系統匯入資料。<br /> </td> 
  </tr> 
  <tr> 
   <td> 控制地址 </td> 
   <td> 已忽略 </td> 
   <td> 127 </td> 
   <td> 收件者的地址是控制組的一部分。<br /> </td> 
  </tr> 
  <tr> 
   <td> Double </td> 
   <td> 已忽略 </td> 
   <td> 10 </td> 
   <td> 收件者的地址已在此傳送中。<br /> </td> 
  </tr> 
  <tr> 
   <td> 忽略錯誤 </td> 
   <td> 已忽略 </td> 
   <td> 25 </td> 
   <td> 地址已列入白名單。 因此會忽略錯誤，並傳送電子郵件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 仲裁後排除 </td> 
   <td> 已忽略 </td> 
   <td> 12 </td> 
   <td> 「仲裁」類型的促銷活動類型規則排除收件者。<br /> </td> 
  </tr> 
  <tr> 
   <td> 由SQL規則排除 </td> 
   <td> 已忽略 </td> 
   <td> 11 </td> 
   <td> 收件者被「SQL」類型的促銷活動類型規則排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效的域 </td> 
   <td> Soft </td> 
   <td> 2 </td> 
   <td> 電子郵件地址的網域不正確或已不存在。 此描述檔將再次定位，直到錯誤計數達到5。 之後，記錄將設定為「隔離」狀態，不會再重試。<br /> </td> 
  </tr> 
  <tr> 
   <td> 郵箱已滿 </td> 
   <td> Soft </td> 
   <td> 5 </td> 
   <td> 此用戶的郵箱已滿，無法接受更多消息。 此描述檔將再次定位，直到錯誤計數達到5。 之後，記錄將設定為「隔離」狀態，不會再重試。<br /> 此類錯誤由清理進程管理，地址在30天後設定為有效狀態。<br /> 警告：要自動從隔離地址清單中刪除地址，必須啟動資料庫清理技術工作流。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未連接 </td> 
   <td> 已忽略 </td> 
   <td> 6 </td> 
   <td> 當發送消息時，收件者的行動電話關閉或未連接到網路。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未定義 </td> 
   <td> 未定義 </td> 
   <td> 0 </td> 
   <td> 該地址處於限定狀態，因為錯誤尚未增加。 當伺服器傳送新錯誤訊息時，會發生此類錯誤：它可能是孤立的錯誤，但如果再次發生，錯誤計數器會增加，這會提醒技術團隊。 然後，他們可以通過樹結構中的「管理 <span class="uicontrol">/促銷活動管理</span> /非交付 <span class="uicontrol"></span><span class="uicontrol"></span> 件管理」節點，執行消息分析並限定此錯誤。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不符合選件資格 </td> 
   <td> 已忽略 </td> 
   <td> 16 </td> 
   <td> 收件者不符合傳送中選件的資格。<br /> </td> 
  </tr> 
  <tr> 
   <td> 拒絕 </td> 
   <td> 柔／硬 </td> 
   <td> 20 </td> 
   <td> 由於安全反饋是垃圾郵件報告，該地址已被置於隔離狀態。 根據錯誤，地址將再次嘗試，直到錯誤計數器達到5，否則將直接發送給隔離。<br /> </td> 
  </tr> 
  <tr> 
   <td> 目標大小有限 </td> 
   <td> 已忽略 </td> 
   <td> 17 </td> 
   <td> 已達到收件者的最大傳送大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不合格地址 </td> 
   <td> 已忽略 </td> 
   <td> 15 </td> 
   <td> 郵遞區號不符合資格。<br /> </td> 
  </tr> 
  <tr> 
   <td> 無法訪問 </td> 
   <td> 柔／硬 </td> 
   <td> 3 </td> 
   <td> 訊息傳送鏈中發生錯誤。 可能是SMTP中繼上的事件、臨時無法訪問的域等。 根據錯誤，地址將再次嘗試，直到錯誤計數器達到5，否則將直接發送給隔離。<br /> </td> 
  </tr> 
  <tr> 
   <td> 用戶未知 </td> 
   <td> 硬 </td> 
   <td> 1 </td> 
   <td> 地址不存在。 此描述檔不會再嘗試傳送。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳送暫時失敗後重試 {#retries-after-a-delivery-temporary-failure}

如果因為 **Soft** 或 **Ignored** 錯誤而導致消息失敗，則在傳送期間將執行重試。

>[!NOTE]
>
>暫時未傳送的訊息只能與 **Soft** 或 **Ignored** 錯誤相關，但不能與 **Hard** (請參閱 [](#delivery-failure-types-and-reasons)Delivery failure types and reasons)錯誤相關。

若要修改傳送的持續時間，請移至傳送或傳送範本的進階參數，並在對應欄位中指定所需的持續時間。 本節將介紹高級交 [付屬性](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)。

預設配置允許在1小時間隔內重試5次，之後在4天內每天重試1次。 您可以全域變更重試次數（請洽詢您的Adobe技術管理員），或針對每個傳送或傳送範本變更重試次數(請參 [閱本節](../../delivery/using/steps-sending-the-delivery.md#configuring-retries))。

## 同步與非同步錯誤 {#synchronous-and-asynchronous-errors}

消息在發送後可能立即失敗（同步錯誤），或稍後失敗（非同步錯誤）。

* 同步錯誤：由Adobe Campaign傳送伺服器連絡的遠端郵件伺服器會立即傳回錯誤訊息，不允許傳送至描述檔的伺服器。 Adobe Campaign可讓每個錯誤符合資格，以判斷是否應隔離相關電子郵件地址。 請參 [閱Bounce郵件資格](#bounce-mail-qualification)。
* 非同步錯誤：接收伺服器稍後會重新發送彈回郵件或SR。 此郵件已載入到應用程式用於標籤錯誤消息的技術郵箱中。 傳送後一週內，可能會發生非同步錯誤。

   >[!NOTE]
   >
   >本節將詳細介紹彈回郵箱 [的配置](../../installation/using/deploying-an-instance.md#managing-bounced-emails)。

   回饋迴路的運作方式就像反彈電子郵件。 當使用者將電子郵件歸類為垃圾訊息時，您可以在Adobe Campaign中設定電子郵件規則，以封鎖傳送給此使用者的所有內容。 傳送給符合電子郵件垃圾訊息資格的使用者的訊息會自動重新導向至專為此目的而建立的電子郵件方塊。 即使這些使用者未按一下取消訂閱連結，其地址仍會列入黑名單。 地址列在(**NmsAddress**)隔離表中，而不是(**NmsRecipient**)接收者表中。

   >[!NOTE]
   >
   >投訴管理在「交付能力管 [理」一節中詳](../../delivery/using/about-deliverability.md) 細說明。

## 彈回郵件管理 {#bounce-mail-management}

Adobe Campaign平台可讓您透過彈回郵件功能管理電子郵件傳送失敗。 當電子郵件無法傳送給收件者時，遠端訊息伺服器會自動將錯誤訊息（彈回郵件）傳回至專為此目的而設計的技術收件匣。 錯誤訊息由Adobe Campaign平台收集，並由inMail流程加以限定，以豐富電子郵件管理規則清單

### 彈回郵件資格 {#bounce-mail-qualification}

當傳送電子郵件失敗時，Adobe Campaign傳送伺服器會從傳訊伺服器或遠端DNS伺服器收到錯誤訊息。 錯誤清單由遠程伺服器返回的消息中包含的字串組成。 故障類型和原因會分配給每個錯誤消息。

此清單可通過節點使 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** 用。 它包含Adobe Campaign用來限定傳送失敗的所有規則。 這並非完整，而且由Adobe Campaign定期更新，也可由使用者管理。

![](assets/tech_quarant_rules_qualif.png)

* 遠程伺服器在首次出現此錯誤類型時返回的消息顯示在表 **[!UICONTROL First text]** 的列中 **[!UICONTROL Delivery log qualification]** 。 如果未顯示此列，請按一下列 **[!UICONTROL Configure list]** 表右下方的按鈕以選擇它。

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign會篩選此訊息以刪除變數內容（例如ID、日期、電子郵件地址、電話號碼等）並在欄中顯示篩選 **[!UICONTROL Text]** 結果。 變數會取代為 **`#xxx#`**，但地址會取代為 **`*`**。

此程式可讓所有相同類型的故障匯集在一起，並避免在「傳送記錄」資格表中出現類似錯誤時出現多個項目。

>[!NOTE]
>
>欄位 **[!UICONTROL Number of occurrences]** 會顯示清單中訊息的發生次數。 限制為100 000次。 例如，如果您想要重設欄位，可以編輯欄位。

彈回郵件可以具有下列資格狀態：

* **[!UICONTROL To qualify]** :彈回數郵件無法合格。 必須將資格指派給「傳遞能力」團隊，以確保有效率的平台傳遞能力。 只要郵件不符合條件，反彈郵件就不會用來豐富電子郵件管理規則清單。
* **[!UICONTROL Keep]** :彈回郵件已經合格， **** Refresh將會使用它來傳送性工作流程，以便與現有的電子郵件管理規則比較，並豐富清單。
* **[!UICONTROL Ignore]** :「促銷活動MTA」會忽略反彈郵件，這表示此反彈不會造成隔離收件者的位址。 Refresh不會用於傳遞性工 **作流程** ，也不會傳送給用戶端例項。

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>對於代管或混合安裝，如果您已升級至「增強MTA」:
>
>* 表格中的反彈資 **[!UICONTROL Delivery log qualification]** 格不再用於同步傳送失敗錯誤訊息。 「增強型MTA」會決定反彈類型和資格，並將該資訊傳回至「促銷活動」。
   >
   >
* inMail程式仍會透過規則來限定非同步彈 **[!UICONTROL Inbound email]** 回數。 如需詳細資訊，請參閱「電 [子郵件管理規則」](#email-management-rules)。
   >
   >
* 對於不使用 **Webhook/EFS的「增強型MTA」實例****[!UICONTROL Inbound email]** ，規則也將用來處理來自「增強型MTA」的同步彈回電子郵件，使用與非同步彈回電子郵件相同的電子郵件地址。
>
>
如需Adobe Campaign增強型MTA的詳細資訊，請參閱本文 [件](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)。

### 電子郵件管理規則 {#email-management-rules}

郵件規則可通過節點 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 訪問。 電子郵件管理規則會顯示在視窗的下方。

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>平台的預設參數是在部署嚮導中配置的。 For further information, refer to [this section](../../installation/using/deploying-an-instance.md).

預設規則如下。

>[!IMPORTANT]
>
>* 如果參數已變更，則必須重新啟動傳送伺服器(MTA)。
>* 管理規則的修改或建立僅限專業使用者。


#### 傳入電子郵件 {#inbound-email}

這些規則包含可由遠端伺服器傳回的字元字串清單，可讓您限定錯誤(**Hard**、 **Soft** 或 **Ignored**)。

當電子郵件失敗時，遠端伺服器會傳回彈回訊息至平台參數中指定的位址。 Adobe Campaign會將每個彈回郵件的內容與規則清單中的字串進行比較，然後將其指派為三種錯誤 [類型之一](#delivery-failure-types-and-reasons)。

>[!NOTE]
>
>使用者可建立自己的規則。 當匯入套件時，以及透過「重新整理以提供功能」 **工作流程更新資料時** ，會覆寫使用者建立的規則。

有關彈回郵件資格的詳細資訊，請參 [閱本節](#bounce-mail-qualification)。

>[!IMPORTANT]
>
>對於托管或混合安裝，如果您已升級到「增強MTA」，並且實例具有 **Webhook/EFS****[!UICONTROL Inbound email]** ，則不再使用規則來同步發送故障錯誤消息。 For more on this, see [this section](#bounce-mail-qualification).
>
>如需Adobe Campaign增強型MTA的詳細資訊，請參閱本文 [件](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)。

#### 網域管理 {#domain-management}

Adobe Campaign訊息伺服器會將單一網域 **管理規則套用** 至所有網域。

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* 您可以選擇是否激活某些標準和加密密鑰來檢查域名，如 **Sender ID**、 **DomainKeys**、 **DKIM**&#x200B;和 **** S/MIME Juckint。
* 通過 **SMTP中繼參數** ，可以為特定域配置中繼伺服器的IP地址和埠。 For more on this, see [this section](../../installation/using/configuring-campaign-server.md#smtp-relay).

如果您的訊息在Outlook中的傳送者 **[!UICONTROL on behalf of]** 位址中顯示，請確定您未使用傳送者ID **(Sender ID**, Microsoft的過時專屬電子郵件驗證標準)來簽署電子郵件。 如果選 **[!UICONTROL Sender ID]** 項已啟用，請取消勾選對應方塊，並聯絡Adobe Campaign支援。 您的傳遞能力不會受到影響。

>[!IMPORTANT]
>
>對於代管或混合安裝，如果您已升級至「增強MTA」, **[!UICONTROL Domain management]** 則不再使用規則。 **DKIM(DomainKeys Indified Mail)** ，電子郵件驗證簽署由「增強的MTA」針對所有網域的所有訊息完成。 除非在「增強的MTA」 **層級另有指定**，否則不會使用「傳送者ID **」、「網域金鑰**」或「 **S/MIME** 」進行簽署。
>
>如需Adobe Campaign增強型MTA的詳細資訊，請參閱本文 [件](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)。

#### MX管理 {#mx-management}

* MX管理規則可用來規範特定網域的傳出電子郵件流程。 他們會取樣彈回訊息，並在適當時封鎖傳送。

* Adobe Campaign傳訊伺服器會套用網域的特定規則，然後套用規則清單中星號所代表之一般案例規則。

* 要配置MX管理規則，只需設定閾值並選擇某些SMTP參數。 閾 **值** (Threshold)是計算為錯誤百分比的限制，超過該百分比後，所有針對特定域的消息都將被阻止。 例如，一般情況下，至少300則訊息，如果錯誤率達到90%，則會封鎖3小時的電子郵件傳送。

For more on MX management, refer to [this section](../../installation/using/email-deliverability.md#mx-configuration).

>[!IMPORTANT]
>
>對於代管或混合安裝，如果您已升級至「增強MTA」，則不 **[!UICONTROL MX management]** 再使用傳送總處理能力規則。 增強型MTA使用其專屬的MX規則，可讓您根據您過去的電子郵件信譽，以及您傳送電子郵件的網域所提供的即時回應，依網域自訂您的吞吐量。
>
>如需Adobe Campaign增強型MTA的詳細資訊，請參閱本文 [件](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)。
