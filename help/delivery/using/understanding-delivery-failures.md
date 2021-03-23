---
solution: Campaign Classic
product: campaign
title: 瞭解傳送故障
description: 瞭解如何瞭解交付失敗
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: d1b38acc5209a5c96ab7a35fe9640159141b110f
workflow-type: tm+mt
source-wordcount: '2580'
ht-degree: 14%

---


# 瞭解傳送故障{#understanding-delivery-failures}

## 瞭解傳送故障{#about-delivery-failures}

當無法將郵件（電子郵件、SMS、推播通知）傳送至描述檔時，遠端伺服器會自動傳送錯誤訊息，該錯誤訊息由Adobe Campaign平台擷取，並符合資格決定是否應隔離電子郵件地址或電話號碼。 請參閱[彈回郵件管理](#bounce-mail-management)。

>[!NOTE]
>
>**電子郵件**&#x200B;錯誤訊息（或「退信」）由 Enhanced MTA（同步退信）或 inMail 程序（非同步退信）限定。
>
>**SMS** 錯誤訊息（或 &quot;SR&quot; 作為 &quot;Status Report&quot;）會由 MTA 程序限定。

傳送訊息後，傳送記錄檔可讓您檢視每個描述檔的傳送狀態以及相關的失敗類型和原因。

如果地址被隔離或配置檔案位於拒絕清單中，也可以在準備傳送期間排除郵件。 已排除的訊息會列在傳送控制面板中。

**相關主題：**

* [傳送記錄檔和記錄](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)
* [失敗狀態](../../delivery/using/delivery-performances.md#failed-status)
* [傳送失敗類型和原因](#delivery-failure-types-and-reasons)

## 傳送失敗類型和原因 {#delivery-failure-types-and-reasons}

消息失敗時有三種錯誤類型。 每個錯誤類型都決定是否將地址發送給隔離。 有關詳細資訊，請參閱[發送地址到隔離的條件](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

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
   <td> 柔／硬 </td> 
   <td> 4 </td> 
   <td> 連結至該位址的帳戶不再有效。 當Internet訪問提供程式(IAP)檢測到長時間的不活動時，它可以關閉用戶帳戶。 然後，將無法傳送至使用者的位址。 如果帳戶因為6個月的閒置而暫時停用，而且仍可啟動，則會指派「有錯誤」狀態，並重新嘗試帳戶，直到錯誤計數器達到5為止。 如果錯誤信號表明帳戶已永久停用，則它將直接設定為「隔離」。<br /> </td> 
  </tr> 
  <tr> 
   <td> 隔離中的地址 </td> 
   <td> 硬 </td> 
   <td> 9 </td> 
   <td> 地址已置於隔離中。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未指定地址 </td> 
   <td> 硬 </td> 
   <td> 7 </td> 
   <td> 未提供收件人的地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不良地址 </td> 
   <td> 已忽略 </td> 
   <td> 14 </td> 
   <td> 此地址的質量評級過低。<br /> </td> 
  </tr> 
  <tr> 
   <td> 拒絕列出的地址 </td> 
   <td> 硬 </td> 
   <td> 8 </td> 
   <td> 傳送時，地址已新增至密尼清單。 此狀態用於從外部清單和外部系統將資料導入Adobe Campaign隔離清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> 控制地址 </td> 
   <td> 已忽略 </td> 
   <td> 127 </td> 
   <td> 收件人的地址是控制組的一部分。<br /> </td> 
  </tr> 
  <tr> 
   <td> Double </td> 
   <td> 已忽略 </td> 
   <td> 10 </td> 
   <td> 收件者的地址已在此遞送中。<br /> </td> 
  </tr> 
  <tr> 
   <td> 忽略錯誤 </td> 
   <td> 已忽略 </td> 
   <td> 25 </td> 
   <td> 地址在allowlist上。 因此會忽略錯誤，並傳送電子郵件。<br /> </td> 
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
   <td> 收件者被'SQL'類型促銷活動類型規則排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效的域 </td> 
   <td> Soft </td> 
   <td> 2 </td> 
   <td> 電子郵件地址的網域不正確或已不存在。 此設定檔將再次定位，直到錯誤計數達到5。之後，記錄將設定為「隔離」狀態，不會再重試。<br /> </td> 
  </tr> 
  <tr> 
   <td> 郵箱已滿 </td> 
   <td> Soft </td> 
   <td> 5 </td> 
   <td> 此用戶的郵箱已滿，無法接受更多消息。 此設定檔將再次定位，直到錯誤計數達到5。之後，記錄將設定為「隔離」狀態，不會再重試。<br /> 此類錯誤由清理進程管理，地址在30天後設定為有效狀態。<br /> 警告：要自動從隔離地址清單中刪除地址，必須啟動資料庫清理技術工作流。<br /> </td> 
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
   <td> 該地址處於限定狀態，因為錯誤尚未增加。 當伺服器傳送新錯誤訊息時，會發生此類錯誤：它可能是孤立的錯誤，但如果再次發生，錯誤計數器會增加，這會提醒技術團隊。然後，他們可以通過樹結構中的<span class="uicontrol">管理</span> / <span class="uicontrol">促銷活動管理</span> / <span class="uicontrol">非交付項管理</span>節點執行消息分析並限定此錯誤。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不符合選件資格 </td> 
   <td> 已忽略 </td> 
   <td> 16 </td> 
   <td> 收件者不符合遞送中選件的資格。<br /> </td> 
  </tr> 
  <tr> 
   <td> 拒絕 </td> 
   <td> 柔／硬 </td> 
   <td> 20 </td> 
   <td> 由於安全反饋是垃圾郵件報告，該地址已被置於隔離狀態。 根據錯誤，將重新嘗試該地址，直到錯誤計數器達到5，或直接將其發送給隔離。<br /> </td> 
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
   <td> 郵遞區號不符合條件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 無法訪問 </td> 
   <td> 柔／硬 </td> 
   <td> 3 </td> 
   <td> 訊息傳送鏈中發生錯誤。 可能是SMTP中繼上的事件、臨時無法訪問的域等。 根據錯誤，將重新嘗試該地址，直到錯誤計數器達到5，或直接將其發送給隔離。<br /> </td> 
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

如果消息因為&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;錯誤而失敗，則在傳送期間將執行重試。

>[!NOTE]
>
>暫時未傳送的訊息只能與&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;錯誤相關，但不能與&#x200B;**Hard**&#x200B;錯誤有關（請參閱[Delivery failure types and reas](#delivery-failure-types-and-reasons)）。

>[!IMPORTANT]
>
>對於代管或混合安裝，如果您已升級至[增強的MTA](../../delivery/using/sending-with-enhanced-mta.md)，促銷活動將不再使用傳送中的重試設定。 軟反彈重試次數及其間的時間長度，由增強的MTA根據訊息電子郵件網域傳回的反彈回應類型和嚴重性來決定。

若要使用舊版促銷活動MTA進行內部部署安裝和代管／混合安裝，若要修改傳送的持續時間，請移至傳送或傳送範本的進階參數，並在對應欄位中指定所需的持續時間。 請參閱[定義有效期](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)。

預設配置允許在1小時間隔內重試5次，之後在4天內每天重試1次。 可以全局更改重試次數(請與您的Adobe技術管理員聯繫)或每個交付或交付模板（請參閱[配置重試](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)）。

## 同步與非同步錯誤 {#synchronous-and-asynchronous-errors}

消息在發送後可能立即失敗（同步錯誤），或稍後失敗（非同步錯誤）。

* 同步錯誤：由Adobe Campaign發送伺服器聯繫的遠程郵件伺服器立即返回一條錯誤消息，不允許將發送內容發送到配置檔案的伺服器。 Adobe Campaign使每個錯誤都具有隔離資格，以確定是否應隔離相關電子郵件地址。 請參閱[退信資格](#bounce-mail-qualification)。
* 非同步錯誤：接收伺服器稍後會重新發送退回郵件或 SR。此郵件已載入到應用程式用於標籤錯誤消息的技術郵箱中。 傳送後一週內，可能會發生非同步錯誤。

   >[!NOTE]
   >
   >彈回郵箱的配置詳見[本節](../../installation/using/deploying-an-instance.md#managing-bounced-emails)。

   [回饋回圈](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)的運作方式與彈回電子郵件類似。 當使用者將電子郵件歸類為垃圾訊息時，您可以在Adobe Campaign設定電子郵件規則，以封鎖傳送給此使用者的所有內容。 傳送給符合電子郵件垃圾訊息資格的使用者的訊息會自動重新導向至專為此目的而建立的電子郵件方塊。 這些使用者的位址已列在密文清單中，即使他們未按一下取消訂閱連結。 地址在(**NmsAddress**)隔離表中，而不在(**NmsRecipient**)接收表中。

   >[!NOTE]
   >
   >投訴管理詳見[交付能力管理](../../delivery/using/about-deliverability.md)一節。

## 彈回郵件管理{#bounce-mail-management}

Adobe Campaign平台可讓您透過彈回郵件功能管理電子郵件傳送失敗。

當電子郵件無法傳送給收件者時，遠端訊息伺服器會自動將錯誤訊息（彈回郵件）傳回至專為此目的而設計的技術收件匣。

對於使用舊版Campaign MTA的內部部署安裝和代管／混合安裝，錯誤訊息會由Adobe Campaign平台收集，並由inMail流程加以限定，以豐富電子郵件管理規則清單。

>[!IMPORTANT]
>
>對於代管或混合式安裝，如果您已升級至[增強的MTA](../../delivery/using/sending-with-enhanced-mta.md)，大部分的電子郵件管理規則將不再使用。 如需詳細資訊，請參閱[本節](#email-management-rules)。

### 退回郵件資格 {#bounce-mail-qualification}

>[!IMPORTANT]
>
>對於托管安裝或混合安裝，如果您已升級至[增強的MTA](../../delivery/using/sending-with-enhanced-mta.md):
>
>* **[!UICONTROL Delivery log qualification]**&#x200B;表格中的反彈資格不再用於&#x200B;**synchronous**&#x200B;傳送失敗錯誤訊息。 「增強型MTA」會決定反彈類型和資格，並將該資訊傳回至「促銷活動」。
   >
   >
* **** inMail 程序仍會透過 **[!UICONTROL Inbound email]** 規則來限定非同步退信。有關詳細資訊，請參閱[電子郵件管理規則](#email-management-rules)。
   >
   >
* 對於使用「增強型MTA **而不使用Webhook/EFS**&#x200B;的例項，**[!UICONTROL Inbound email]**&#x200B;規則也將用來處理來自「增強型MTA」的同步彈回電子郵件，使用與非同步彈回電子郵件相同的電子郵件地址。


對於使用舊版Campaign MTA的內部部署安裝和托管／混合安裝，當電子郵件傳送失敗時，Adobe Campaign傳送伺服器會從傳訊伺服器或遠端DNS伺服器接收錯誤訊息。 錯誤清單由遠程伺服器返回的消息中包含的字串組成。 故障類型和原因會分配給每個錯誤消息。

此清單可通過&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**&#x200B;節點使用。 它包含Adobe Campaign用來限定交付失敗的所有規則。 它並非完整，由Adobe Campaign定期更新，也可由用戶管理。

![](assets/tech_quarant_rules_qualif.png)

遠程伺服器在首次出現此錯誤類型時返回的消息顯示在&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表的&#x200B;**[!UICONTROL First text]**&#x200B;列中。 如果未顯示此列，請按一下清單右下方的&#x200B;**[!UICONTROL Configure list]**&#x200B;按鈕以選擇它。

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign會篩選此訊息，以刪除變數內容（例如ID、日期、電子郵件地址、電話號碼等） 並在&#x200B;**[!UICONTROL Text]**&#x200B;欄中顯示篩選結果。 變數會以&#x200B;**`#xxx#`**&#x200B;取代，但以&#x200B;**`*`**&#x200B;取代的位址除外。

此程式可讓所有相同類型的故障匯集在一起，並避免在「傳送記錄」資格表中出現類似錯誤時出現多個項目。

>[!NOTE]
>
>**[!UICONTROL Number of occurrences]**&#x200B;欄位會顯示清單中訊息的發生次數。 限制為100 000次。 例如，如果您想要重設欄位，可以編輯欄位。

彈回郵件可以具有下列資格狀態：

* **[!UICONTROL To qualify]** :彈回數郵件無法合格。必須將資格指派給「傳遞能力」團隊，以確保有效率的平台傳遞能力。 只要郵件不符合條件，反彈郵件就不會用來豐富電子郵件管理規則清單。
* **[!UICONTROL Keep]** :彈回郵件已經合格， **Refresh將用於傳遞** 性工作流程，以與現有電子郵件管理規則比較並豐富清單。
* **[!UICONTROL Ignore]** :「促銷活動MTA」會忽略彈回數郵件，這表示此彈回數不會造成隔離收件者的位址。**Refresh for deliverability**&#x200B;工作流將不使用它，也不會將它發送到客戶端實例。

![](assets/deliverability_qualif_status.png)

### 電子郵件管理規則{#email-management-rules}

>[!IMPORTANT]
>
>對於代管或混合式安裝，如果您已升級至[增強的MTA](../../delivery/using/sending-with-enhanced-mta.md)，大部分的電子郵件管理規則將不再使用。 如需詳細資訊，請參閱以下章節。

郵件規則通過&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**&#x200B;節點訪問。 電子郵件管理規則會顯示在視窗的下方。

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>平台的預設參數是在部署嚮導中配置的。 有關詳細資訊，請參閱[本節](../../installation/using/deploying-an-instance.md)。

預設規則如下。

>[!IMPORTANT]
>
>* 如果參數已變更，則必須重新啟動傳送伺服器(MTA)。
>* 管理規則的修改或建立僅限專業使用者。


#### 入站電子郵件{#inbound-email}

>[!IMPORTANT]
>
>對於托管或混合安裝，如果您已升級至[增強的MTA](../../delivery/using/sending-with-enhanced-mta.md)，且您的實例具有&#x200B;**Webhooks/EFS**&#x200B;功能，則&#x200B;**[!UICONTROL Inbound email]**&#x200B;規則不再用於同步傳送失敗錯誤訊息。 如需詳細資訊，請參閱[本節](#bounce-mail-qualification)。

對於使用舊版促銷活動MTA的內部部署安裝和代管／混合安裝，這些規則包含可由遠端伺服器傳回的字串清單，讓您限定錯誤（**Hard**、**Soft**&#x200B;或&#x200B;**Ignored**）。

當電子郵件失敗時，遠端伺服器會傳回彈回訊息至平台參數中指定的位址。 Adobe Campaign將每個彈回郵件的內容與規則清單中的字串進行比較，然後將其指派為3種[錯誤類型](#delivery-failure-types-and-reasons)中的一種。

>[!NOTE]
>
>使用者可建立自己的規則。 當匯入封裝時，以及透過&#x200B;**重新整理以取得傳遞能力**&#x200B;工作流程更新資料時，會覆寫使用者建立的規則。

有關彈回郵件資格的詳細資訊，請參閱[本節](#bounce-mail-qualification)。

#### 域管理{#domain-management}

>[!IMPORTANT]
>
>對於代管或混合安裝，如果您已升級至[增強的MTA](../../delivery/using/sending-with-enhanced-mta.md)，則不再使用&#x200B;**[!UICONTROL Domain management]**&#x200B;規則。 **DKIM (DomainKeys Indified Mail)** 電子郵件驗證簽署是由 Enhanced MTA 針對所有網域的所有郵件完成。除非在 Enhanced MTA 層級中另外指定，否則不會使用 **Sender ID**、**DomainKeys** 或 **S/MIME** 簽署。

對於使用舊版Campaign MTA的內部部署安裝和托管／混合安裝，Adobe Campaign消息伺服器將單一&#x200B;**域管理**&#x200B;規則應用於所有域。

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* 您可以選擇是否激活某些標識標準和加密密鑰來檢查域名，如&#x200B;**發送者ID**、**域密鑰**、**DKIM**&#x200B;和&#x200B;**S/MIME**。
* **SMTP中繼**&#x200B;參數允許您為特定域配置中繼伺服器的IP地址和埠。 如需詳細資訊，請參閱[本節](../../installation/using/configuring-campaign-server.md#smtp-relay)。

如果您的訊息在Outlook中的傳送者位址中顯示有&#x200B;**[!UICONTROL on behalf of]**，請確定您未使用&#x200B;**傳送者ID**&#x200B;來簽署電子郵件，此為Microsoft的過時專屬電子郵件驗證標準。 如果&#x200B;**[!UICONTROL Sender ID]**&#x200B;選項已啟用，請取消選中相應的框，然後聯繫[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 您的傳遞能力不會受到影響。

#### MX管理{#mx-management}

>[!IMPORTANT]
>
>對於托管或混合安裝，如果您已升級至[增強的MTA](../../delivery/using/sending-with-enhanced-mta.md)，則不再使用&#x200B;**[!UICONTROL MX management]**&#x200B;傳送吞吐量規則。 增強型MTA使用其專屬的MX規則，可讓您根據您過去的電子郵件信譽，以及您傳送電子郵件的網域所提供的即時回應，依網域自訂您的吞吐量。

對於使用舊版Campaign MTA的內部部署安裝和代管／混合安裝：

* MX管理規則可用來規範特定網域的傳出電子郵件流程。 他們會取樣彈回訊息，並在適當時封鎖傳送。

* Adobe Campaign消息伺服器應用特定於域的規則，然後應用規則清單中星號表示的一般大小寫規則。

* 要配置MX管理規則，只需設定閾值並選擇某些SMTP參數。 **threshold**&#x200B;是以錯誤百分比計算的限制，超過該百分比後，所有針對特定域的消息都將被阻止。 例如，一般情況下，至少300則訊息，如果錯誤率達到90%，則會封鎖3小時的電子郵件傳送。

有關MX管理的更多資訊，請參閱[本節](../../installation/using/email-deliverability.md#mx-configuration)。
