---
product: campaign
title: 瞭解傳遞失敗
description: 瞭解如何瞭解交付失敗
feature: Monitoring, Deliverability
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '2614'
ht-degree: 14%

---

# 瞭解傳遞失敗{#understanding-delivery-failures}

![](../../assets/common.svg)

## 瞭解傳送故障 {#about-delivery-failures}

當無法將消息（電子郵件、SMS、推送通知）發送到配置檔案時，遠程伺服器自動發送錯誤消息，該錯誤消息由Adobe Campaign平台拾取，並被限定用於確定是否應隔離電子郵件地址或電話號碼。 請參閱 [彈出郵件管理](#bounce-mail-management)。

>[!NOTE]
>
>**電子郵件**&#x200B;錯誤訊息（或「退信」）由 Enhanced MTA（同步退信）或 inMail 程序（非同步退信）限定。
>
>**SMS** 錯誤訊息（或 &quot;SR&quot; 作為 &quot;Status Report&quot;）會由 MTA 程序限定。

發送消息後，傳遞日誌允許您查看每個配置檔案的傳遞狀態以及相關的故障類型和原因。

如果地址被隔離或配置檔案在密文清單上，則還可以在傳遞準備期間排除郵件。 已排除的消息列在傳遞儀表板中。

**相關主題：**

* [交付日誌和歷史記錄](delivery-dashboard.md#delivery-logs-and-history)
* [失敗狀態](delivery-performances.md#failed-status)
* [傳送失敗類型和原因](#delivery-failure-types-and-reasons)

## 傳送失敗類型和原因 {#delivery-failure-types-and-reasons}

消息失敗時有三種錯誤類型。 每個錯誤類型都確定是否將地址發送到隔離。 有關此內容的詳細資訊，請參閱 [將地址發送到隔離的條件](understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

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
   <td> 帳戶已禁用 </td> 
   <td> 軟/硬 </td> 
   <td> 4 </td> 
   <td> 連結到地址的帳戶不再處於活動狀態。 當Internet訪問提供程式(IAP)檢測到長時間不活動時，它可以關閉用戶帳戶。 然後，無法向用戶地址交付。 如果帳戶由於六個月的不活動狀態而暫時禁用，並且仍然可以激活，則將分配「有錯誤」狀態，並重試帳戶，直到錯誤計數器達到5。 如果錯誤表明帳戶已永久停用，則它將直接設定為「隔離」。<br /> </td> 
  </tr> 
  <tr> 
   <td> 隔離中的地址 </td> 
   <td> 硬 </td> 
   <td> 9 </td> 
   <td> 地址已置於隔離狀態。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未指定地址 </td> 
   <td> 硬 </td> 
   <td> 7 </td> 
   <td> 未為收件人提供地址。<br /> </td> 
  </tr> 
  <tr> 
   <td> 不良地址 </td> 
   <td> 已忽略 </td> 
   <td> 14 </td> 
   <td> 此地址的質量評級太低。<br /> </td> 
  </tr> 
  <tr> 
   <td> 登錄地址 </td> 
   <td> 硬 </td> 
   <td> 8 </td> 
   <td> 發送時已將地址添加到denylist。 此狀態用於將資料從外部清單和外部系統導入Adobe Campaign隔離清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> 控制地址 </td> 
   <td> 已忽略 </td> 
   <td> 127 </td> 
   <td> 收件人的地址是控制組的一部分。<br /> </td> 
  </tr> 
  <tr> 
   <td> 雙線 </td> 
   <td> 已忽略 </td> 
   <td> 10 </td> 
   <td> 收件人的地址已在此傳遞中。<br /> </td> 
  </tr> 
  <tr> 
   <td> 忽略錯誤 </td> 
   <td> 已忽略 </td> 
   <td> 25 </td> 
   <td> 地址在允許清單中。 因此，將忽略該錯誤，併發送電子郵件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 仲裁後排除 </td> 
   <td> 已忽略 </td> 
   <td> 12 </td> 
   <td> 收件人被「仲裁」類型的市場活動類型規則排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 由SQL規則排除 </td> 
   <td> 已忽略 </td> 
   <td> 11 </td> 
   <td> 收件人被「SQL」類型的市場活動類型規則排除。<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效域 </td> 
   <td> 軟 </td> 
   <td> 2 </td> 
   <td> 電子郵件地址的域不正確或不再存在。 此設定檔將再次定位，直到錯誤計數達到5。之後，記錄將設定為「隔離」狀態，不會再重試。<br /> </td> 
  </tr> 
  <tr> 
   <td> 郵箱已滿 </td> 
   <td> 軟 </td> 
   <td> 5 </td> 
   <td> 此用戶的郵箱已滿，無法接受更多郵件。 此設定檔將再次定位，直到錯誤計數達到5。之後，記錄將設定為「隔離」狀態，不會再重試。<br /> 此類錯誤由清除進程管理，地址在30天後設定為有效狀態。<br /> 警告：要自動從隔離地址清單中刪除地址，必須啟動資料庫清理技術工作流。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未連接 </td> 
   <td> 已忽略 </td> 
   <td> 6 </td> 
   <td> 當發送消息時，收件人的行動電話關閉或未連接到網路。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未定義 </td> 
   <td> 未定義 </td> 
   <td> 0 </td> 
   <td> 該地址處於限定狀態，因為錯誤尚未遞增。 當伺服器傳送新錯誤訊息時，會發生此類錯誤：它可能是孤立的錯誤，但如果再次發生，錯誤計數器會增加，這會提醒技術團隊。然後，他們可以通過 <span class="uicontrol">管理</span> / <span class="uicontrol">市場活動管理</span> / <span class="uicontrol">非交付項管理</span> 樹結構中的節點。<br /> </td> 
  </tr> 
  <tr> 
   <td> 無資格獲得優惠 </td> 
   <td> 已忽略 </td> 
   <td> 16 </td> 
   <td> 收件人無資格在交貨中獲得優惠。<br /> </td> 
  </tr> 
  <tr> 
   <td> 拒絕 </td> 
   <td> 軟/硬 </td> 
   <td> 20 </td> 
   <td> 由於作為垃圾郵件報告的安全反饋，該地址已被隔離。 根據錯誤，將重試該地址，直到錯誤計數器達到5，或直接將其發送到隔離。<br /> </td> 
  </tr> 
  <tr> 
   <td> 目標大小受限 </td> 
   <td> 已忽略 </td> 
   <td> 17 </td> 
   <td> 已達到收件人的最大交貨大小。<br /> </td> 
  </tr> 
  <tr> 
   <td> 未限定地址 </td> 
   <td> 已忽略 </td> 
   <td> 15 </td> 
   <td> 郵政地址未被限定。<br /> </td> 
  </tr> 
  <tr> 
   <td> 無法訪問 </td> 
   <td> 軟/硬 </td> 
   <td> 3 </td> 
   <td> 消息傳遞鏈中出錯。 可能是SMTP中繼上的事件、臨時無法訪問的域等。 根據錯誤，將重試該地址，直到錯誤計數器達到5，或直接將其發送到隔離。<br /> </td> 
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

如果消息因 **軟** 或 **已忽略** 錯誤為臨時錯誤，將在傳遞持續時間內執行重試。

>[!NOTE]
>
>暫時未傳遞的消息只能與 **軟** 或 **已忽略** 錯誤，但不是 **硬** 錯誤(請參見 [交貨失敗類型和原因](#delivery-failure-types-and-reasons))。

>[!IMPORTANT]
>
>對於托管或混合安裝，如果已升級到 [增強的MTA](sending-with-enhanced-mta.md)，市場活動不再使用傳遞中的重試設定。 軟反彈重試次數和它們之間的時間長度由增強MTA根據郵件電子郵件域返回的反彈響應的類型和嚴重性確定。

對於使用傳統市場活動MTA的內部安裝和托管/混合安裝，要修改交貨的持續時間，請轉到交貨或交貨模板的高級參數並在相應欄位中指定所需的持續時間。 請參閱 [定義有效期](steps-sending-the-delivery.md#defining-validity-period)。

預設配置允許每小時重試5次，然後每天重試4天。 可以全局更改重試次數(與Adobe技術管理員聯繫)或每個交付或交付模板。 請參閱 [配置重試次數](steps-sending-the-delivery.md#configuring-retries)。

## 同步與非同步錯誤 {#synchronous-and-asynchronous-errors}

消息在發送後可能立即失敗（同步錯誤），或稍後失敗（非同步錯誤）。

* 同步錯誤：Adobe Campaign傳遞伺服器聯繫的遠程郵件伺服器立即返回錯誤消息，不允許將傳遞發送到配置檔案的伺服器。 Adobe Campaign確認了每個錯誤，以確定是否應隔離相關電子郵件地址。 請參閱[退信資格](#bounce-mail-qualification)。
* 非同步錯誤：接收伺服器稍後會重新發送退回郵件或 SR。此郵件已載入到應用程式用於標籤郵件的技術郵箱中，但出現錯誤。 傳送後一週內，可能會發生非同步錯誤。

   >[!NOTE]
   >
   >反彈郵箱的配置詳見 [此部分](../../installation/using/deploying-an-instance.md#managing-bounced-emails)。

   的 [反饋環](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops) 就像郵件彈跳。 當用戶將電子郵件定義為垃圾郵件時，您可以在Adobe Campaign配置電子郵件規則以阻止向此用戶發送的所有郵件。 發送給已將電子郵件限定為垃圾郵件的用戶的郵件自動重定向到專門為此目的而建立的郵箱。 這些用戶的地址在denylist上，即使他們沒有按一下取消訂閱連結。 地址位於(**NMS地址**)隔離表，而不在(**Nms收件人**)收件人表。

   >[!NOTE]
   >
   >投訴管理詳見 [可交付性管理](about-deliverability.md) 的子菜單。

## 彈出郵件管理 {#bounce-mail-management}

通過Adobe Campaign平台，您可以通過彈送郵件功能管理電子郵件傳遞失敗。

當無法將電子郵件發送給收件人時，遠程消息伺服器會自動將錯誤消息（彈回郵件）返回至專門為此目的設計的技術收件箱。

對於使用舊版市場活動MTA的內部安裝和托管/混合安裝，錯誤消息由Adobe Campaign平台收集，並由inMail流程確定，以豐富電子郵件管理規則清單。

>[!IMPORTANT]
>
>對於托管或混合安裝，如果已升級到 [增強的MTA](sending-with-enhanced-mta.md)，大多數電子郵件管理規則不再使用。 如需詳細資訊，請參閱[本節](#email-management-rules)。

### 退回郵件資格 {#bounce-mail-qualification}

>[!IMPORTANT]
>
>對於托管或混合安裝，如果已升級到 [增強的MTA](sending-with-enhanced-mta.md):
>
>* 在 **[!UICONTROL Delivery log qualification]** 表不再用於 **同步** 傳遞失敗錯誤消息。 「增強的MTA」確定退貨類型和資格，並將該資訊發回市場活動。
>
>* **** inMail 程序仍會透過 **[!UICONTROL Inbound email]** 規則來限定非同步退信。有關此的詳細資訊，請參閱 [電子郵件管理規則](#email-management-rules)。
>
>* 對於使用增強MTA的實例 **不帶Webhooks/EFS**，也請參見Wiki頁。 **[!UICONTROL Inbound email]** 規則還將用於處理來自增強型MTA的同步彈出電子郵件，使用與非同步彈出電子郵件相同的電子郵件地址。


對於使用傳統市場活動MTA的本地安裝和托管/混合安裝，當電子郵件傳送失敗時，Adobe Campaign傳送伺服器從消息傳送伺服器或遠程DNS伺服器接收錯誤消息。 錯誤清單由遠程伺服器返回的消息中包含的字串組成。 故障類型和原因被分配給每個錯誤消息。

此清單可通過 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** 的下界。 它包含Adobe Campaign用於限定交付失敗的所有規則。 它非詳盡無遺，由Adobe Campaign定期更新，也可由用戶管理。

![](assets/tech_quarant_rules_qualif.png)

遠程伺服器在第一次出現此錯誤類型時返回的消息顯示在 **[!UICONTROL First text]** 列 **[!UICONTROL Delivery log qualification]** 的子菜單。 如果未顯示此列，請按一下 **[!UICONTROL Configure list]** 按鈕。

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign會過濾此郵件以刪除變數內容（如ID、日期、電子郵件地址、電話號碼等） 並在 **[!UICONTROL Text]** 的雙曲餘切值。 變數替換為 **`#xxx#`**，但替換為 **`*`**。

此流程允許將同一類型的所有失敗匯集在一起，並避免在「交付日誌」限定表中為類似錯誤輸入多個條目。

>[!NOTE]
>
>的 **[!UICONTROL Number of occurrences]** 欄位顯示清單中消息的出現次數。 最多10萬次。 例如，如果希望重置該欄位，可以編輯該欄位。

退信郵件可具有以下資格狀態：

* **[!UICONTROL To qualify]** :郵寄郵件無法合格。 必須將資格分配給交付能力團隊，以確保高效的平台交付能力。 只要不合格，就不會使用退信郵件來豐富電子郵件管理規則清單。
* **[!UICONTROL Keep]** :郵件是合格的，由 **刷新可交付性** 將工作流與現有電子郵件管理規則進行比較並豐富清單。
* **[!UICONTROL Ignore]** :活動MTA忽略了退信郵件，這意味著此退信永遠不會導致隔離收件人的地址。 它不會被 **刷新可交付性** 工作流，不會將其發送到客戶端實例。

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>在ISP停機時，通過Campaign發送的電子郵件將被錯誤地標籤為退貨。 要更正此問題，您需要更新退貨資格。 如需詳細資訊，請參閱[此頁面](update-bounce-qualification.md)。

### 電子郵件管理規則 {#email-management-rules}

>[!IMPORTANT]
>
>對於托管或混合安裝，如果已升級到 [增強的MTA](sending-with-enhanced-mta.md)，大多數電子郵件管理規則不再使用。 有關詳細資訊，請參閱以下各節。

通過 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 的下界。 電子郵件管理規則顯示在窗口的下半部分。

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>平台的預設參數是在部署嚮導中配置的。 有關詳細資訊，請參閱 [此部分](../../installation/using/deploying-an-instance.md)。

預設規則如下。

>[!IMPORTANT]
>
>* 如果參數已更改，則必須重新啟動傳遞伺服器(MTA)。
>* 管理規則的修改或建立僅針對專家用戶。


#### 入站電子郵件 {#inbound-email}

>[!IMPORTANT]
>
>對於托管或混合安裝，如果已升級到 [增強的MTA](sending-with-enhanced-mta.md)，如果實例 **Webhooks/EFS** 功能， **[!UICONTROL Inbound email]** 規則不再用於同步傳遞失敗錯誤消息。 如需詳細資訊，請參閱[本節](#bounce-mail-qualification)。

對於使用舊版市場活動MTA的內部安裝和托管/混合安裝，這些規則包含可由遠程伺服器返回並允許您限定錯誤的字串清單(**硬**。 **軟** 或 **已忽略**)。

當電子郵件失敗時，遠程伺服器將返回一條返回消息到平台參數中指定的地址。 Adobe Campaign將每封反彈郵件的內容與規則清單中的字串進行比較，然後將其分配為三個字串之一 [錯誤類型](#delivery-failure-types-and-reasons)。

>[!NOTE]
>
>用戶可以建立自己的規則。 導入包和通過 **刷新可交付性** 工作流中，用戶建立的規則將被覆蓋。

有關退信郵件資格的詳細資訊，請參閱 [此部分](#bounce-mail-qualification)。

#### 域管理 {#domain-management}

>[!IMPORTANT]
>
>對於托管或混合安裝，如果已升級到 [增強的MTA](sending-with-enhanced-mta.md)，也請參見Wiki頁。 **[!UICONTROL Domain management]** 不再使用規則。 **DKIM (DomainKeys Indified Mail)** 電子郵件驗證簽署是由 Enhanced MTA 針對所有網域的所有郵件完成。除非在 Enhanced MTA 層級中另外指定，否則不會使用 **Sender ID**、**DomainKeys** 或 **S/MIME** 簽署。

對於使用傳統營銷活動MTA的內部安裝和托管/混合安裝，Adobe Campaign消息伺服器應用一個 **域管理** 規則。

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* 您可以選擇是否激活某些標識標準和加密密鑰以檢查域名，如 **發件人ID**。 **域密鑰**。 **DKIM**, **S/MIME**。
* 的 **SMTP中繼** 參數允許您為特定域配置中繼伺服器的IP地址和埠。 如需詳細資訊，請參閱[本節](../../installation/using/configuring-campaign-server.md#smtp-relay)。

如果您的消息在Outlook中顯示， **[!UICONTROL on behalf of]** 在發件人地址中，確保您沒有使用 **發件人ID**&#x200B;是Microsoft公司過時的專有電子郵件身份驗證標準。 如果 **[!UICONTROL Sender ID]** 選項，取消選中相應的框和聯繫人 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 您的可交付性不會受到影響。

#### MX管理 {#mx-management}

>[!IMPORTANT]
>
>對於托管或混合安裝，如果已升級到 [增強的MTA](sending-with-enhanced-mta.md)，也請參見Wiki頁。 **[!UICONTROL MX management]** 交貨吞吐量規則不再使用。 增強型MTA使用其自己的MX規則，允許它根據您自己的歷史電子郵件信譽以及您發送電子郵件的域的即時反饋，按域定制您的吞吐量。

對於使用舊版市場活動MTA的內部安裝和托管/混合安裝：

* MX管理規則用於規範特定域的傳出電子郵件的流。 他們對彈回消息進行採樣，並在適當時阻止發送。

* Adobe Campaign消息伺服器應用特定於域的規則，然後應用規則清單中星號表示的一般情況規則。

* 要配置MX管理規則，只需設定閾值並選擇某些SMTP參數即可。 A **閾值** 是按錯誤百分比計算的限制，超過該百分比，將阻止指向特定域的所有消息。 例如，在一般情況下，如果錯誤率達到90%，則至少300封郵件的發送被阻止3小時。

有關MX管理的詳細資訊，請參閱 [此部分](../../installation/using/email-deliverability.md#mx-configuration)。
