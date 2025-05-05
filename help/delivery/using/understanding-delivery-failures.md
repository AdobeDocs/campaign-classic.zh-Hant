---
product: campaign
title: 瞭解傳遞失敗
description: 瞭解如何瞭解傳送失敗
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '2567'
ht-degree: 12%

---

# 瞭解傳遞失敗{#understanding-delivery-failures}

## 關於傳送失敗 {#about-delivery-failures}

當訊息（電子郵件、簡訊、推播通知）無法傳送至設定檔時，遠端伺服器會自動傳送錯誤訊息，此錯誤訊息會由Adobe Campaign平台擷取，並限定為隔離電子郵件地址或電話號碼。 請參閱[退回郵件管理](#bounce-mail-management)。

>[!NOTE]
>
>**電子郵件**&#x200B;錯誤訊息（或「退信」）由 Enhanced MTA（同步退信）或 inMail 程序（非同步退信）限定。
>
>**簡訊錯誤訊息（或 &quot;SR&quot; 作為 &quot;Status Report&quot;）會由 MTA 程序限定。**

傳送訊息後，傳送記錄檔可讓您檢視每個設定檔的傳送狀態，以及相關的失敗型別和原因。

如果地址被隔離或設定檔位於封鎖清單上，也可以在傳送準備期間排除訊息。 已排除的訊息會列在傳送控制面板中。

**相關主題：**

* [傳遞記錄和歷史記錄](delivery-dashboard.md#delivery-logs-and-history)
* [失敗狀態](delivery-performances.md#failed-status)
* [傳遞失敗型別和原因](#delivery-failure-types-and-reasons)

## 傳遞失敗型別和原因 {#delivery-failure-types-and-reasons}

訊息失敗時有三種型別的錯誤。 每種錯誤型別都會判斷地址是否傳送至隔離區。 如需詳細資訊，請參閱[傳送隔離地址的條件](understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

* **硬式**：「硬式」錯誤表示地址無效。這包含明確指出地址無效的錯誤訊息，例如：&quot;未知使用者&quot;。
* **軟式**：這可能是暫時錯誤，或無法分類的錯誤，例如：「無效域」或「信箱已滿」。
* **已忽略**：這是已知為暫時的錯誤，例如「不在辦公室」，或是技術錯誤，例如，如果傳送者類型是 &quot;postmaster&quot;。

傳送失敗的可能原因有：

<table> 
 <tbody> 
  <tr> 
   <td> 錯誤標籤 </td> 
   <td> 錯誤型別 </td> 
   <td> 技術價值 </td> 
   <td> 說明 </td> 
  </tr> 
  <tr> 
   <td> 帳戶已停用 </td> 
   <td> 軟/硬 </td> 
   <td> 4 </td> 
   <td> 連結至該地址的帳戶已失效。 當網際網路存取提供者(IAP)偵測到長時間的不活動時，它可以關閉使用者的帳戶。 之後將無法傳遞至使用者的位址。 如果帳戶因為6個月的閒置而暫時停用，而且仍然可以啟動，則會指派狀態「發生錯誤」並再次嘗試帳戶，直到錯誤計數器達到5。 如果錯誤訊號表示帳戶已永久停用，則會直接將其設定為隔離。<br /> </td> 
  </tr> 
  <tr> 
   <td> 被隔離的地址 </td> 
   <td> 強烈 </td> 
   <td> 9 </td> 
   <td> 地址已放入隔離區。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未指定地址 </td> 
   <td> 強烈 </td> 
   <td> 7 </td> 
   <td> 未提供收件者的地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> 品質不良的地址 </td> 
   <td> 已忽略 </td> 
   <td> 14 </td> 
   <td> 此地址的品質評等太低。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已加入封鎖清單的地址 </td> 
   <td> 強烈 </td> 
   <td> 8 </td> 
   <td> 地址已在傳送時新增到封鎖清單中。 此狀態用於將外部清單和外部系統的資料匯入Adobe Campaign隔離清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> 控制地址 </td> 
   <td> 已忽略 </td> 
   <td> 127 </td> 
   <td> 收件者的地址是控制組的一部分。<br /> </td> 
  </tr> 
  <tr> 
   <td> 雙精度 </td> 
   <td> 已忽略 </td> 
   <td> 10 </td> 
   <td> 收件者的地址已在此傳遞中。<br /> </td> 
  </tr> 
  <tr> 
   <td> 忽略的錯誤 </td> 
   <td> 已忽略 </td> 
   <td> 25 </td> 
   <td> 地址在允許清單上。 因此會忽略錯誤，並會傳送電子郵件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 仲裁後排除 </td> 
   <td> 已忽略 </td> 
   <td> 12 </td> 
   <td> 收件者已由「仲裁」型別的行銷活動型別規則排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已由 SQL 規則排除 </td> 
   <td> 已忽略 </td> 
   <td> 11 </td> 
   <td> 收件者已由「SQL」型別行銷活動型別規則排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效的網域 </td> 
   <td> 柔光 </td> 
   <td> 2 </td> 
   <td> 電子郵件地址的網域不正確或已不存在。 此設定檔將再次定位，直到錯誤計數達到5。之後，記錄將設定為隔離狀態，不會再重試。<br /> </td> 
  </tr> 
  <tr> 
   <td> 郵箱已滿 </td> 
   <td> 柔光 </td> 
   <td> 5 </td> 
   <td> 此使用者的信箱已滿，無法接受更多郵件。 此設定檔將再次定位，直到錯誤計數達到5。之後，記錄將設定為「隔離」狀態，不會再重試。<br />此型別的錯誤是由清理程式管理，地址在30天後會設定為有效狀態。<br />警告：為了從隔離位址清單自動移除位址，必須啟動資料庫清理技術工作流程。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未連線 </td> 
   <td> 已忽略 </td> 
   <td> 6 </td> 
   <td> 傳送訊息時，收件者的行動電話已關閉或未連線至網路。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未定義 </td> 
   <td> 未定義 </td> 
   <td> 0 </td> 
   <td> 此位址正在限定中，因為錯誤尚未增加。 當伺服器傳送新錯誤訊息時，會發生此類錯誤：它可能是孤立的錯誤，但如果再次發生，錯誤計數器會增加，這會提醒技術團隊。 接著，他們可以透過樹狀結構中的<span class="uicontrol">管理</span> / <span class="uicontrol">Campaign Management</span> / <span class="uicontrol">無法傳遞的專案管理</span>節點，執行訊息分析並限定此錯誤。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不符合優惠方案條件 </td> 
   <td> 已忽略 </td> 
   <td> 16 </td> 
   <td> 收件者不符合傳遞中的優惠方案條件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已拒絕 </td> 
   <td> 軟/硬 </td> 
   <td> 20 </td> 
   <td> 由於安全反饋為垃圾郵件報告，該地址已被置於隔離狀態。 根據錯誤，將再次嘗試此位址，直到錯誤計數器達到5，或直接傳送給隔離。<br /> </td> 
  </tr> 
  <tr> 
   <td> 目標大小受限 </td> 
   <td> 已忽略 </td> 
   <td> 17 </td> 
   <td> 已達到收件者的傳遞大小上限。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不合格的地址 </td> 
   <td> 已忽略 </td> 
   <td> 15 </td> 
   <td> 郵寄地址不合格。<br /> </td> 
  </tr> 
  <tr> 
   <td> 無法聯繫 </td> 
   <td> 軟/硬 </td> 
   <td> 3 </td> 
   <td> 訊息傳遞鏈結中發生錯誤。 可能是SMTP轉送上的事件、暫時無法連線的網域等。 根據錯誤，將再次嘗試此位址，直到錯誤計數器達到5，或直接傳送給隔離。<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用者不明 </td> 
   <td> 強烈 </td> 
   <td> 1 </td> 
   <td> 地址不存在。 此設定檔不會再嘗試傳送。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳送暫時失敗後重試 {#retries-after-a-delivery-temporary-failure}

如果訊息因暫時性的&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;錯誤而失敗，則會在傳遞期間執行重試。

>[!NOTE]
>
>暫時未傳遞的訊息只能與&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;錯誤相關，而非&#x200B;**Hard**&#x200B;錯誤（請參閱[傳遞失敗型別和原因](#delivery-failure-types-and-reasons)）。

>[!IMPORTANT]
>
>對於託管或混合式安裝，如果您已升級至[Enhanced MTA](sending-with-enhanced-mta.md)，Campaign將不再使用傳送中的重試設定。 軟退信重試次數和兩次之間的時間長度由Enhanced MTA根據從訊息的電子郵件網域傳回的退信回應的型別和嚴重性來決定。

對於使用舊版Campaign MTA的內部部署安裝和託管/混合安裝，若要修改傳送的持續時間，請轉至傳送或傳送範本的進階引數，並在對應欄位中指定所需的持續時間。 請參閱[定義有效期間](steps-sending-the-delivery.md#defining-validity-period)。

預設設定允許以一小時間隔重試五次，然後每天重試一次，持續四天。 重試次數可全域變更(請聯絡您的Adobe技術管理員)，或針對每個傳遞或傳遞範本進行變更。 請參閱[設定重試次數](steps-sending-the-delivery.md#configuring-retries)。

## 同步與非同步錯誤 {#synchronous-and-asynchronous-errors}

訊息可能會立即失敗（同步錯誤），或稍後在傳送後失敗（非同步錯誤）。

* 同步錯誤： Adobe Campaign傳送伺服器連絡的遠端郵件伺服器會立即傳回錯誤訊息，不可傳送至設定檔的伺服器。 Adobe Campaign會對每個錯誤進行認證，以決定是否應隔離相關電子郵件地址。 請參閱[退信資格](#bounce-mail-qualification)。
* 非同步錯誤：接收伺服器稍後會重新傳送退回郵件或SR。 此郵件已載入應用程式用來標示有錯誤之郵件的技術信箱。 傳送後一週內，可能會發生非同步錯誤。

  >[!NOTE]
  >
  >在[此區段](../../installation/using/deploying-an-instance.md#managing-bounced-emails)中詳細說明退回信箱的設定。

  [回饋迴路](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=zh-Hant#feedback-loops)的運作方式與退回電子郵件類似。 當使用者將電子郵件歸類為垃圾郵件時，您可以在Adobe Campaign中設定電子郵件規則，以封鎖傳送給此使用者的所有郵件。 傳送給已將電子郵件限定為垃圾訊息之使用者的訊息，會自動重新導向至為此目的特別建立的電子郵件方塊。 這些使用者的位址位於封鎖清單中，即使他們未按一下取消訂閱連結。 地址在(**NmsAddress**)隔離資料表中處於封鎖清單中，而不是在(**NmsRecipient**)收件者資料表中。

  >[!NOTE]
  >
  >申訴管理在[傳遞能力管理](about-deliverability.md)區段中詳細說明。

## 退回郵件管理 {#bounce-mail-management}

Adobe Campaign平台可讓您透過退回郵件功能管理電子郵件傳送失敗。

當電子郵件無法傳送給收件者時，遠端訊息伺服器會自動傳回錯誤訊息（退回郵件）至為此目的而設計的技術收件匣。

對於使用舊版Campaign MTA的內部部署安裝和託管/混合安裝，錯誤訊息會由Adobe Campaign平台收集並由inMail程式限定，以豐富電子郵件管理規則清單。

>[!IMPORTANT]
>
>對於託管或混合式安裝，如果您已升級至[增強型MTA](sending-with-enhanced-mta.md)，則不再使用大部分的電子郵件管理規則。 如需詳細資訊，請參閱[本節](#email-management-rules)。

### 退回郵件資格 {#bounce-mail-qualification}

>[!IMPORTANT]
>
>針對託管或混合式安裝，如果您已升級至[增強型MTA](sending-with-enhanced-mta.md)：
>
>* **[!UICONTROL Delivery log qualification]**&#x200B;資料表中的退信限定不再用於&#x200B;**同步**&#x200B;傳遞失敗錯誤訊息。 增強型MTA會決定退信型別和資格，並將該資訊傳回至Campaign。
>
>* **非同步**&#x200B;退信仍由inMail處理序透過&#x200B;**[!UICONTROL Inbound email]**&#x200B;規則限定。 如需詳細資訊，請參閱[電子郵件管理規則](#email-management-rules)。
>
>* 對於使用不含Webhook的Enhanced MTA **的執行個體，**&#x200B;[!UICONTROL Inbound email]&#x200B;**規則也將用來處理來自Enhanced MTA的同步退信電子郵件，使用的電子郵件地址與非同步退信電子郵件相同。**

對於使用舊版Campaign MTA的內部部署安裝和託管/混合安裝，當電子郵件傳送失敗時，Adobe Campaign傳送伺服器會從傳訊伺服器或遠端DNS伺服器收到錯誤訊息。 錯誤清單是由遠端伺服器傳回之訊息中所包含的字串所組成。 系統會為每個錯誤訊息指定失敗型別和原因。

此清單可透過&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**&#x200B;節點取得。 它包含Adobe Campaign用來限定傳送失敗的所有規則。 內容並非詳盡無遺，且會由Adobe Campaign定期更新，使用者也可自行管理。

![](assets/tech_quarant_rules_qualif.png)

此錯誤型別第一次出現時，遠端伺服器傳回的訊息會顯示在&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;資料表的&#x200B;**[!UICONTROL First text]**&#x200B;資料行中。 如果未顯示此欄，請按一下清單右下方的&#x200B;**[!UICONTROL Configure list]**&#x200B;按鈕以選取它。

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign會篩選此郵件以刪除變數內容（例如ID、日期、電子郵件地址、電話號碼等） 並在&#x200B;**[!UICONTROL Text]**&#x200B;欄中顯示篩選的結果。 變數已取代為&#x200B;**`#xxx#`**，但取代為&#x200B;**`*`**&#x200B;的位址除外。

此程式允許將相同型別的所有失敗集合在一起，並避免傳送記錄資格表格中出現多個類似錯誤的專案。

>[!NOTE]
>
>**[!UICONTROL Number of occurrences]**&#x200B;欄位會顯示清單中訊息的出現次數。 僅限100,000次發生。 例如，如果您想要重設欄位，可以編輯該欄位。

退回郵件可能具有下列資格狀態：

* **[!UICONTROL To qualify]** ：無法限定退回郵件。 資格必須指派給傳遞團隊，以確保有效的平台傳遞能力。 只要不符合，跳出郵件就不會用來擴充電子郵件管理規則的清單。
* **[!UICONTROL Keep]** ：退信已合格，將由&#x200B;**重新整理傳遞能力**&#x200B;工作流程使用，以與現有電子郵件管理規則比較，並擴充清單。
* **[!UICONTROL Ignore]** ：Campaign MTA會忽略退信郵件，這表示此退信絕對不會導致收件者的地址被隔離。 **重新整理傳遞能力**&#x200B;工作流程不會使用此專案，也不會傳送給使用者端執行個體。

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>如果ISP發生中斷，透過Campaign傳送的電子郵件將會錯誤地標示為跳出。 若要修正此問題，您需要更新退回資格。 如需詳細資訊，請參閱[此頁面](update-bounce-qualification.md)。

### 電子郵件管理規則 {#email-management-rules}

>[!IMPORTANT]
>
>對於託管或混合式安裝，如果您已升級至[增強型MTA](sending-with-enhanced-mta.md)，則不再使用大部分的電子郵件管理規則。 如需詳細資訊，請參閱以下章節。

透過&#x200B;**[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]**&#x200B;節點存取郵件規則。 電子郵件管理規則會顯示在視窗的下方。

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>平台的預設引數是在部署精靈中設定的。 如需進一步資訊，請參閱[本節](../../installation/using/deploying-an-instance.md)。

預設規則如下。

>[!IMPORTANT]
>
>* 如果引數已變更，則必須重新啟動傳遞伺服器(MTA)。
>* 管理規則的修改或建立僅供專家使用者使用。

#### 傳入電子郵件 {#inbound-email}

<!--
STATEMENT ONLY TRUE with Momentum and EFS+:
For hosted or hybrid installations, if you have upgraded to the [Enhanced MTA](sending-with-enhanced-mta.md), and if your instance has **Webhooks** functionality, the **[!UICONTROL Inbound email]** rules are no longer used for synchronous delivery failure error messages. For more on this, see [this section](#bounce-mail-qualification).

For on-premise installations and hosted/hybrid installations using the legacy Campaign MTA, these rules contain the list of character strings which can be returned by remote servers and which let you qualify the error (**Hard**, **Soft** or **Ignored**).-->

**[!UICONTROL Inbound email]**&#x200B;規則包含可由遠端伺服器傳回的字元字串清單，可讓您限定錯誤（**Hard**、**Soft**&#x200B;或&#x200B;**Ignored**）。

當電子郵件失敗時，遠端伺服器會傳回退回訊息至[平台引數](../../installation/using/deploying-an-instance.md)中指定的位址。 Adobe Campaign會比較每個退回郵件的內容與規則清單中的字串，然後為其指派三個[錯誤型別](#delivery-failure-types-and-reasons)之一。

>[!NOTE]
>
>使用者可以建立自己的規則。 當匯入套件以及透過&#x200B;**重新整理傳遞能力**&#x200B;工作流程更新資料時，使用者建立的規則會被覆寫。

有關退信限定的詳細資訊，請參閱[本節](#bounce-mail-qualification)。

#### 網域管理 {#domain-management}

>[!IMPORTANT]
>
>對於託管或混合式安裝，如果您已升級至[增強型MTA](sending-with-enhanced-mta.md)，將不再使用&#x200B;**[!UICONTROL Domain management]**&#x200B;規則。 **DKIM (DomainKeys Indified Mail)** 電子郵件驗證簽署是由 Enhanced MTA 針對所有網域的所有郵件完成。除非在 Enhanced MTA 層級中另外指定，否則不會使用 **Sender ID**、**DomainKeys** 或 **S/MIME** 簽署。

對於使用舊版Campaign MTA的內部部署安裝和託管/混合安裝，Adobe Campaign傳訊伺服器會將單一&#x200B;**網域管理**&#x200B;規則套用至所有網域。

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* 您可以選擇是否啟用某些識別標準和加密金鑰來檢查網域名稱，例如&#x200B;**寄件者識別碼**、**網域金鑰**、**DKIM**&#x200B;和&#x200B;**S/MIME**。
* **SMTP轉送**&#x200B;引數可讓您為特定網域設定轉送伺服器的IP位址和連線埠。 如需詳細資訊，請參閱[本節](../../installation/using/configuring-campaign-server.md#smtp-relay)。

如果郵件顯示於Outlook的寄件者地址中有&#x200B;**[!UICONTROL on behalf of]**，請確定您沒有使用&#x200B;**寄件者識別碼**&#x200B;簽署電子郵件，這是Microsoft過時的專有電子郵件驗證標準。 如果&#x200B;**[!UICONTROL Sender ID]**&#x200B;選項已啟用，請取消核取對應的方塊並聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 您的傳遞能力不受影響。

#### MX管理 {#mx-management}

>[!IMPORTANT]
>
>對於託管或混合式安裝，如果您已升級至[Enhanced MTA](sending-with-enhanced-mta.md)，將不再使用&#x200B;**[!UICONTROL MX management]**&#x200B;傳遞輸送量規則。 Enhanced MTA會使用其專屬的MX規則，如此可讓它根據您過去的電子郵件信譽，以及您傳送電子郵件之網域所提供的即時回饋，而依網域來自訂您的輸送量。

對於使用舊版Campaign MTA的內部部署安裝和託管/混合安裝：

* MX管理規則是用來規範特定網域之傳出電子郵件的流程。 他們會對退回訊息進行範例，並在適當時封鎖傳送。

* Adobe Campaign訊息伺服器會套用網域的特定規則，然後套用規則清單中以星號表示的一般案例規則。

* 若要設定MX管理規則，只要設定臨界值並選取某些SMTP引數即可。 **threshold**&#x200B;是以錯誤百分比計算的限制，超過此限制會封鎖向特定網域傳送的所有訊息。 例如，在一般情況下，如果錯誤率達到90%，對於至少300則訊息，電子郵件的傳送會封鎖三個小時。

有關MX管理的詳細資訊，請參閱[本節](../../installation/using/email-deliverability.md#mx-configuration)。
