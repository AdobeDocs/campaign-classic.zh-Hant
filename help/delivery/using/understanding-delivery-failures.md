---
product: campaign
title: 瞭解傳送故障
description: 了解如何了解傳送失敗
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '2614'
ht-degree: 14%

---

# 瞭解傳送故障{#understanding-delivery-failures}

## 瞭解傳送故障{#about-delivery-failures}

當訊息（電子郵件、簡訊、推播通知）無法傳送至設定檔時，遠端伺服器會自動傳送錯誤訊息，此錯誤訊息會由Adobe Campaign平台擷取，並限定為隔離電子郵件地址或電話號碼。 請參閱[退回郵件管理](#bounce-mail-management)。

>[!NOTE]
>
>**電子郵件**&#x200B;錯誤訊息（或「退信」）由 Enhanced MTA（同步退信）或 inMail 程序（非同步退信）限定。
>
>**SMS** 錯誤訊息（或 &quot;SR&quot; 作為 &quot;Status Report&quot;）會由 MTA 程序限定。

傳送訊息後，傳送記錄檔可讓您檢視每個設定檔的傳送狀態，以及相關的失敗類型和原因。

如果地址被隔離或配置檔案被封鎖，在準備傳送時也可以排除郵件。 已排除的訊息會列在傳送控制面板中。

**相關主題：**

* [傳送記錄檔和歷史記錄](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)
* [失敗狀態](../../delivery/using/delivery-performances.md#failed-status)
* [傳送失敗類型和原因](#delivery-failure-types-and-reasons)

## 傳送失敗類型和原因 {#delivery-failure-types-and-reasons}

訊息失敗時有三種錯誤類型。 每個錯誤類型都會決定地址是否傳送至隔離。 有關詳細資訊，請參閱[將地址發送到隔離區的條件](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

* **硬式**：「硬式」錯誤表示地址無效。這包含明確指出地址無效的錯誤訊息，例如：&quot;未知使用者&quot;。
* **軟式**：這可能是暫時錯誤，或無法分類的錯誤，例如：「無效域」或「信箱已滿」。
* **已忽略**：這是已知為暫時的錯誤，例如「不在辦公室」，或是技術錯誤，例如，如果傳送者類型是 &quot;postmaster&quot;。

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
   <td> 軟/硬 </td> 
   <td> 4 </td> 
   <td> 連結至該地址的帳戶已不再有效。 當Internet訪問提供程式(IAP)檢測到長時間的不活動時，它可以關閉用戶的帳戶。 之後無法傳送至使用者位址。 如果帳戶因為6個月的閒置而暫時停用，而且仍可啟動，則會指派狀態「有錯誤」，並再次嘗試帳戶，直到錯誤計數器達到5。 如果錯誤訊號表明帳戶已永久停用，則會直接將其設為Quarantine。<br /> </td> 
  </tr> 
  <tr> 
   <td> 隔離中的地址 </td> 
   <td> 硬 </td> 
   <td> 9 </td> 
   <td> 地址被置於隔離區。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未指定地址 </td> 
   <td> 硬 </td> 
   <td> 7 </td> 
   <td> 未為收件人指定地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不良地址 </td> 
   <td> 已忽略 </td> 
   <td> 14 </td> 
   <td> 此地址的質量等級太低。<br /> </td> 
  </tr> 
  <tr> 
   <td> 拒絕列出的地址 </td> 
   <td> 硬 </td> 
   <td> 8 </td> 
   <td> 地址已在發送時添加到封鎖清單中。 此狀態用於從外部清單和外部系統將資料導入Adobe Campaign隔離清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> 控制地址 </td> 
   <td> 已忽略 </td> 
   <td> 127 </td> 
   <td> 收件人的地址是控制組的一部分。<br /> </td> 
  </tr> 
  <tr> 
   <td> 雙倍 </td> 
   <td> 已忽略 </td> 
   <td> 10 </td> 
   <td> 收件人的地址已在此傳送中。<br /> </td> 
  </tr> 
  <tr> 
   <td> 忽略錯誤 </td> 
   <td> 已忽略 </td> 
   <td> 25 </td> 
   <td> 地址在允許清單中。 因此，會忽略錯誤，並傳送電子郵件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 仲裁後排除 </td> 
   <td> 已忽略 </td> 
   <td> 12 </td> 
   <td> 收件人被「仲裁」類型的促銷活動類型規則排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 由SQL規則排除 </td> 
   <td> 已忽略 </td> 
   <td> 11 </td> 
   <td> 收件者被「SQL」類型的促銷活動類型規則排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效域 </td> 
   <td> 軟 </td> 
   <td> 2 </td> 
   <td> 電子郵件地址的網域不正確或已不存在。 此設定檔將再次定位，直到錯誤計數達到5。之後，記錄將設定為「隔離」狀態，不會再重試。<br /> </td> 
  </tr> 
  <tr> 
   <td> 郵箱已滿 </td> 
   <td> 軟 </td> 
   <td> 5 </td> 
   <td> 此用戶的郵箱已滿，無法接受更多郵件。 此設定檔將再次定位，直到錯誤計數達到5。之後，記錄將設定為「隔離」狀態，不會再重試。<br /> 此類錯誤由清理進程管理，地址在30天後設為有效狀態。<br /> 警告：為了從隔離位址清單自動移除位址，必須啟動「資料庫清理」技術工作流程。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未連接 </td> 
   <td> 已忽略 </td> 
   <td> 6 </td> 
   <td> 當發送消息時，收件人的手機被關閉或未連接到網路。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未定義 </td> 
   <td> 未定義 </td> 
   <td> 0 </td> 
   <td> 該地址正在限定中，因為錯誤尚未增加。 當伺服器傳送新錯誤訊息時，會發生此類錯誤：它可能是孤立的錯誤，但如果再次發生，錯誤計數器會增加，這會提醒技術團隊。然後，他們可以通過樹結構中的<span class="uicontrol">Administration</span> / <span class="uicontrol"> Campaign Management</span> / <span class="uicontrol"> Non deliverables Management</span>節點執行消息分析並限定此錯誤。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不符合優惠方案的資格 </td> 
   <td> 已忽略 </td> 
   <td> 16 </td> 
   <td> 收件者不符合傳送中選件的資格。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已拒絕 </td> 
   <td> 軟/硬 </td> 
   <td> 20 </td> 
   <td> 由於安全反饋是垃圾郵件報告，該地址已被置於隔離狀態。 根據錯誤，將再次嘗試該地址，直到錯誤計數器達到5，或者它將直接發送到隔離區。<br /> </td> 
  </tr> 
  <tr> 
   <td> 目標大小有限 </td> 
   <td> 已忽略 </td> 
   <td> 17 </td> 
   <td> 已達到收件人的最大傳送大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不合格地址 </td> 
   <td> 已忽略 </td> 
   <td> 15 </td> 
   <td> 郵遞區號未限定。<br /> </td> 
  </tr> 
  <tr> 
   <td> 無法聯繫 </td> 
   <td> 軟/硬 </td> 
   <td> 3 </td> 
   <td> 郵件傳送鏈中出錯。 可能是SMTP中繼的事件、暫時無法存取的網域等。 根據錯誤，將再次嘗試該地址，直到錯誤計數器達到5，或者它將直接發送到隔離區。<br /> </td> 
  </tr> 
  <tr> 
   <td> 用戶未知 </td> 
   <td> 硬 </td> 
   <td> 1 </td> 
   <td> 地址不存在。 此設定檔不會再嘗試傳送。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳送暫時失敗後重試 {#retries-after-a-delivery-temporary-failure}

如果訊息因暫時的&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;錯誤而失敗，則在傳送期間將執行重試。

>[!NOTE]
>
>暫時未傳送的訊息只能與&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;錯誤相關，但不能與&#x200B;**Hard**&#x200B;錯誤相關（請參閱[傳送失敗類型和原因](#delivery-failure-types-and-reasons)）。

>[!IMPORTANT]
>
>對於托管或混合安裝，如果您已升級至[Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md),Campaign將不再使用傳送中的重試設定。 軟退信重試次數及兩者之間的時間長度，由Enhanced MTA根據來自訊息電子郵件網域傳回之退信的類型和嚴重性決定。

若要使用舊版Campaign MTA進行內部部署安裝和托管/混合安裝，若要修改傳送的持續時間，請前往傳送或傳送範本的進階參數，並在對應欄位中指定所需的持續時間。 請參閱[定義有效期](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)。

預設設定允許每小時間隔5次重試，之後每天4天重試1次。 可全域變更重試次數(請聯絡您的Adobe技術管理員)，或針對每個傳送或傳送範本（請參閱[設定重試](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)）。

## 同步與非同步錯誤 {#synchronous-and-asynchronous-errors}

訊息可能會立即失敗（同步錯誤），或稍後傳送失敗（非同步錯誤）。

* 同步錯誤：由Adobe Campaign傳送伺服器連絡的遠端郵件伺服器會立即傳回錯誤訊息，不允許將傳送傳送至設定檔的伺服器。 Adobe Campaign會將每個錯誤限定為隔離相關電子郵件地址。 請參閱[退信資格](#bounce-mail-qualification)。
* 非同步錯誤：接收伺服器稍後會重新發送退回郵件或 SR。此郵件已載入到應用程式用於標籤錯誤郵件的技術郵箱中。 傳送後一週內，可能會發生非同步錯誤。

   >[!NOTE]
   >
   >在[此部分](../../installation/using/deploying-an-instance.md#managing-bounced-emails)中詳細說明了退信箱的配置。

   [反饋回圈](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)的運作方式與退信電子郵件類似。 當使用者將電子郵件歸類為垃圾訊息時，您可以在Adobe Campaign中設定電子郵件規則，以封鎖傳送給此使用者的所有內容。 傳送給符合電子郵件垃圾訊息資格的使用者的訊息，會自動重新導向至為此目的專門建立的電子郵件方塊。 即使未點按取消訂閱連結，這些使用者的地址仍會列入封鎖清單。 地址在(**NmsAddress**)隔離表中，而不在(**NmsRecipient**)接收表中。

   >[!NOTE]
   >
   >在[傳遞能力管理](../../delivery/using/about-deliverability.md)一節中詳細說明了投訴管理。

## 退回郵件管理{#bounce-mail-management}

Adobe Campaign平台可讓您透過退信功能管理電子郵件傳送失敗。

當電子郵件無法傳送給收件者時，遠端訊息伺服器會自動將錯誤訊息（退信郵件）傳回至為此目的而設計的技術收件匣。

若為使用舊版Campaign MTA的內部部署安裝和托管/混合式安裝，錯誤訊息會由Adobe Campaign平台收集，並由inMail程式限定，以豐富電子郵件管理規則清單。

>[!IMPORTANT]
>
>若為托管或混合式安裝，如果您已升級至[Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md)，則不再使用大部分的電子郵件管理規則。 如需詳細資訊，請參閱[本節](#email-management-rules)。

### 退回郵件資格 {#bounce-mail-qualification}

>[!IMPORTANT]
>
>對於托管或混合安裝，如果您已升級至[Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md):
>
>* **[!UICONTROL Delivery log qualification]**&#x200B;表格中的退信限定不再用於&#x200B;**synchronous**&#x200B;傳送失敗錯誤訊息。 Enhanced MTA會決定退信類型和資格，並將該資訊傳回至Campaign。
   >
   >
* **** inMail 程序仍會透過 **[!UICONTROL Inbound email]** 規則來限定非同步退信。如需詳細資訊，請參閱[電子郵件管理規則](#email-management-rules)。
   >
   >
* 對於使用Enhanced MTA **而不使用Webhook/EFS**&#x200B;的例項， **[!UICONTROL Inbound email]**&#x200B;規則也將用於處理來自Enhanced MTA的同步退信電子郵件，使用與非同步退信電子郵件相同的電子郵件地址。


若為使用舊版Campaign MTA的內部部署安裝和托管/混合式安裝，當電子郵件傳送失敗時，Adobe Campaign傳送伺服器會收到來自傳訊伺服器或遠端DNS伺服器的錯誤訊息。 錯誤清單由遠程伺服器返回的消息中包含的字串組成。 會為每個錯誤訊息指派失敗類型和原因。

此清單可通過&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**&#x200B;節點使用。 它包含Adobe Campaign用來限定傳送失敗的所有規則。 這並非詳盡無遺，且由Adobe Campaign定期更新，也可由使用者管理。

![](assets/tech_quarant_rules_qualif.png)

遠程伺服器在第一次出現此錯誤類型時返回的消息顯示在&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表的&#x200B;**[!UICONTROL First text]**&#x200B;列中。 如果未顯示此列，請按一下清單右下方的&#x200B;**[!UICONTROL Configure list]**&#x200B;按鈕以選擇它。

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign會篩選此訊息以刪除變數內容（例如ID、日期、電子郵件地址、電話號碼等） 並在&#x200B;**[!UICONTROL Text]**&#x200B;欄中顯示篩選結果。 變數會以&#x200B;**`#xxx#`**&#x200B;取代，但以&#x200B;**`*`**&#x200B;取代的位址除外。

此程式可將相同類型的所有失敗匯總在一起，並避免傳送記錄限定表格中出現類似錯誤的多個項目。

>[!NOTE]
>
>**[!UICONTROL Number of occurrences]**&#x200B;欄位會顯示清單中訊息的發生次數。 最多只能發生100 000次。 如果您想要重設欄位，可以編輯欄位。

退回郵件可具有以下資格狀態：

* **[!UICONTROL To qualify]** :無法限定退信。必須將資格指派給傳遞團隊，以保證有效的平台傳遞能力。 只要不符合條件，退回郵件就不會用於豐富電子郵件管理規則清單。
* **[!UICONTROL Keep]** :退回郵件已合格，將供「重新整理」 **使用，以** 便與現有的電子郵件管理規則進行比較，並讓清單更加豐富。
* **[!UICONTROL Ignore]** :Campaign MTA會忽略退信郵件，這表示此退信不會造成隔離收件者的地址。**重新整理傳遞能力**&#x200B;工作流程將不會使用它，也不會將其傳送至用戶端執行個體。

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>如果ISP中斷，透過Campaign傳送的電子郵件將會錯誤標示為退信。 若要更正此問題，您需要更新退信資格。 如需詳細資訊，請參閱[此頁面](../../delivery/using/update-bounce-qualification.md)。

### 電子郵件管理規則{#email-management-rules}

>[!IMPORTANT]
>
>若為托管或混合式安裝，如果您已升級至[Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md)，則不再使用大部分的電子郵件管理規則。 如需詳細資訊，請參閱下節。

郵件規則通過&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**&#x200B;節點訪問。 電子郵件管理規則會顯示在視窗的下半部。

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>平台的預設參數是在部署嚮導中配置的。 有關詳細資訊，請參閱[此部分](../../installation/using/deploying-an-instance.md)。

預設規則如下。

>[!IMPORTANT]
>
>* 如果參數已變更，則必須重新啟動傳送伺服器(MTA)。
>* 管理規則的修改或建立僅供專家使用者使用。


#### 傳入電子郵件{#inbound-email}

>[!IMPORTANT]
>
>對於托管或混合安裝，如果您已升級到[Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md)，並且您的實例具有&#x200B;**Webhooks/EFS**&#x200B;功能，則&#x200B;**[!UICONTROL Inbound email]**&#x200B;規則不再用於同步傳送失敗錯誤訊息。 如需詳細資訊，請參閱[本節](#bounce-mail-qualification)。

對於使用舊版Campaign MTA的內部部署安裝和托管/混合安裝，這些規則包含可由遠端伺服器傳回的字元字串清單，可讓您限定錯誤（**Hard**、**Soft**&#x200B;或&#x200B;**Ignored**）。

當電子郵件失敗時，遠端伺服器會傳回退信至平台參數中指定的地址。 Adobe Campaign會將每封退信的內容與規則清單中的字串進行比較，然後指派這三種[錯誤類型](#delivery-failure-types-and-reasons)中的一種。

>[!NOTE]
>
>使用者可以建立自己的規則。 匯入套件時，以及透過&#x200B;**重新整理以取得傳遞能力**&#x200B;工作流程更新資料時，會覆寫使用者建立的規則。

有關退信限定的詳細資訊，請參閱[本節](#bounce-mail-qualification)。

#### 域管理{#domain-management}

>[!IMPORTANT]
>
>若為托管或混合安裝，如果您已升級至[Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md)，則不再使用&#x200B;**[!UICONTROL Domain management]**&#x200B;規則。 **DKIM (DomainKeys Indified Mail)** 電子郵件驗證簽署是由 Enhanced MTA 針對所有網域的所有郵件完成。除非在 Enhanced MTA 層級中另外指定，否則不會使用 **Sender ID**、**DomainKeys** 或 **S/MIME** 簽署。

若為使用舊版Campaign MTA的內部部署安裝和托管/混合式安裝，Adobe Campaign傳訊伺服器會將單一&#x200B;**網域管理**&#x200B;規則套用至所有網域。

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* 您可以選擇是否激活某些標識標準和加密密鑰以檢查域名，如&#x200B;**發送者ID**、**域密鑰**、**DKIM**&#x200B;和&#x200B;**S/MIME**。
* **SMTP中繼**&#x200B;參數可讓您為特定網域配置中繼伺服器的IP位址和埠。 如需詳細資訊，請參閱[本節](../../installation/using/configuring-campaign-server.md#smtp-relay)。

如果郵件在Outlook中的發件人地址中顯示為&#x200B;**[!UICONTROL on behalf of]**，請確保您的電子郵件沒有使用&#x200B;**發件人ID**&#x200B;簽名，該ID是Microsoft的過時專有電子郵件身份驗證標準。 如果啟用&#x200B;**[!UICONTROL Sender ID]**&#x200B;選項，請取消勾選對應的方塊，並聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 您的傳遞能力將不會受到影響。

#### MX管理{#mx-management}

>[!IMPORTANT]
>
>對於托管或混合安裝，如果您已升級至[Enhanced MTA](../../delivery/using/sending-with-enhanced-mta.md)，則不再使用&#x200B;**[!UICONTROL MX management]**&#x200B;傳送吞吐量規則。 Enhanced MTA使用其專屬的MX規則，可讓它根據您過去的電子郵件信譽，以及您傳送電子郵件之網域所提供的即時意見，依網域自訂您的輸送量。

若是使用舊版Campaign MTA的內部部署安裝和托管/混合安裝：

* MX管理規則用於規範特定網域的傳出電子郵件的流程。 它們會取樣退信，並在適當時封鎖傳送。

* Adobe Campaign傳訊伺服器會套用網域專屬的規則，然後套用規則清單中星號所表示之一般大小寫的規則。

* 要配置MX管理規則，只需設定閾值並選擇某些SMTP參數即可。 **threshold**&#x200B;是以錯誤百分比計算的限制，超過該錯誤百分比後，將阻止向特定域發送的所有消息。 例如，在一般情況下，若最少有300則訊息，若錯誤率達到90%，則會將電子郵件的傳送封鎖三小時。

有關MX管理的詳細資訊，請參閱[此部分](../../installation/using/email-deliverability.md#mx-configuration)。
