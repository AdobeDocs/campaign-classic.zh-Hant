---
title: 隱私權和建議
seo-title: 隱私權和建議
description: 隱私權和建議
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
translation-type: tm+mt
source-git-commit: 247d73933991047603b8d61c7489d976c448dd52
workflow-type: tm+mt
source-wordcount: '1804'
ht-degree: 7%

---


# Privacy and Consent{#privacy-and-recommendations}

## 一般性建議 {#general-recommendations}

Adobe Campaign是一套功能強大的工具，可用來收集和處理大量資料，包括個人資訊和敏感資料。 這就是為什麼需要謹慎管理隱私。

* 對個人資訊一律以負責任和道德的方式使用。

* 避免傳送未經請求的電子郵件、推播通知和SMS訊息（「垃圾訊息」）。 Adobe堅信許可行銷的原則能夠培養客戶的終身價值和忠誠度，因此嚴禁使用Adobe Campaign傳送未經請求的訊息。

請前往[安全性和隱私權檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html)，以了解有關安全性和隱私權需要檢查的核心元素。

### 隱私權法規 {#privacy-regulations}

為正確處理隱私權並管理個人資料，請在您所在地區適用的法規範圍內工作。 這些規定包括：
* [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en) （歐洲通用資料保護法規）
* [DPA](https://www.gov.uk/data-protection) （英國實施GDPR）
* [歐洲隱私與電子通訊指令](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM Act](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business) （美國法律規定商業電子郵件的規則與要求）
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5。&amp;part=4。&amp;chapter=&amp;article=) （加州消費者隱私法）
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/) （泰國個人資料保護法）
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) （巴西通用資料保護法）-將於2020年8月16日起生效

>[!NOTE]
>
>如需有關GDPR、CCPA、PDPA和LGPD如何套用至Adobe Campaign的詳細資訊，請參 [閱本頁](https://helpx.adobe.com/tw/campaign/kb/campaign-privacy-overview.html#whatisgdpr)。

### Adobe Experience Cloud privacy {#experience-cloud-privacy}

Adobe Campaign是Adobe Experience Cloud解決方案的一部分。 在Campaign中處理隱私權的方式遵循Experience Cloud的一般原則，例如：

* **使用Adobe Experience Cloud時會收集哪些資訊**

   身為使用Adobe Experience Cloud解決方案的公司，您可以選擇要收集哪些資訊並傳送至您的Adobe Experience Cloud帳戶。 可收集的資訊類型範例包括網頁瀏覽活動、IP位址、行動裝置的位置資訊、促銷活動成功率、購買或放入購物車的項目等。

   >[!NOTE]
   >
   >至於所有Adobe產品，Campaign會收集應用程式和網站使用者的相關資訊。 如需詳細資訊，請參閱 [Adobe隱私權政策](https://www.adobe.com/privacy/policy.html)。

* **如何使用Adobe Experience Cloud收集資訊**

   * Adobe Experience Cloud解決方案使用Cookie和類似技術（例如網站信標，又稱為標籤或像素），讓您收集資訊。 如需Adobe Campaign Cookie和追蹤功能的詳細資訊，請參 [閱本節](#tracking-capabilities)。
   * 您也可以在行動應用程式中使用Adobe Experience Cloud技術。 如需使用Campaign傳送行動傳送的詳細資訊，請參 [閱SMS頻道](../../delivery/using/sms-channel.md)[和行動應用程式頻道](../../delivery/using/about-mobile-app-channel.md)。

* **您使用者對於您使用Adobe Experience Cloud的隱私權選擇**

   Adobe要求您提供客戶的隱私權政策，說明：

   * 您與Adobe Experience Cloud相關的隱私權實務
   * 使用者如何針對Adobe Experience Cloud收集或使用其資訊設定偏好設定

   >[!NOTE]
   >
   >至於所有Adobe產品，Campaign使用者可以選擇退出，透過應用程式和網站收集有關他們的資訊。 如需詳細資訊，請參閱 [Adobe Experience Cloud使用資訊常見問答](https://www.adobe.com/privacy/experience-cloud-usage-info-faq.html)。

如需Adobe Experience Cloud隱私權的詳細資訊，請參 [閱本頁](https://www.adobe.com/privacy/marketing-cloud.html)。

## 個人資料與角色 {#personal-data}

在管理隱私權時，請務必定義哪些資料應謹慎處理，以及由誰處理。
* **個人資料** ，是指可直接或間接識別活人的資訊。
* **敏感個人資料** ，是指與個人種族、政治觀點、宗教信仰、犯罪背景、遺傳資訊、健康資料、性偏好、生物識別資訊，以及工會會員相關的資訊。

主 [要法規](#privacy-regulations) ，是指管理資料的不同實體，具體如下：
* 資 **料掌控者** ，是決定收集、使用及分享個人資料之方式與目的的權威。
* 資 **料處理者** ，是指依據資料控制者的指示收集、使用或分享個人資料的任何個人或一方。
* 資 **料主體** ：指任何正在收集、使用或分享個人資料的活人，以及可參照該個人資料直接或間接識別的個人。

因此，身為收集和分享個人資料的公司，您是資料掌控者、客戶是資料主體，而Adobe Campaign在依您的指示處理個人資料時，會當成資料處理者。 請注意，身為資料掌控者，您有責任處理與資料主體的關係，例如管理隱私權 [要求](#privacy-requests)。

將Campaign與其他Experience Cloud解決方案整合時，您需要支付額外的護理，才能保護個人資料，例如 [Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md)、 [Audience Manager或People核心服務、](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md)Campaign Standard [，或透過](../../integrations/using/synchronizing-audiences.md)[](../../platform/using/crm-connectors.md)CRM連接器將受眾從其他解決方案整合。

## 資料擷取 {#data-acquisition}

Adobe Campaign可讓您收集資料，包括個人和敏感資訊。 因此，您必須接收並監控收件者的同意。

* 讓收件者一律同意接收通訊。 為此，請盡快接受退出要求，並透過雙重加入程式驗證同意。 如需詳細資訊，請參 [閱「建立雙重選擇加入的訂閱表單」](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)。
* 請勿匯入詐騙清單，並使用種子位址來檢查您的用戶端檔案是否未被騙用。 有關詳細資訊，請參 [閱關於種子地址](../../delivery/using/about-seed-addresses.md)。
* 透過許可和權限管理，您可以追蹤收件者的偏好設定，並管理組織內誰可以存取哪些資料。 如需詳細資訊，請參閱[本區段](#consent)。
* 協助和管理收件者的隱私權要求。 如需詳細資訊，請參閱[本區段](#privacy-requests)。

## 隱私權管理 {#privacy-management}

隱私權管理是指所有可協助您遵守隱私權法規（GDPR、CCPA等）的程式和工具。 取得本頁隱私權管理的概 [述](https://helpx.adobe.com/tw/campaign/kb/campaign-privacy-overview.html)。

Adobe Campaign提供您專屬於隱私權管理的各種功能：
* 許可管理、資料保留和用戶角色。 請參閱[本區段](#consent)。
* 隱私權要求（存取權與被遺忘權）。 請參閱[本區段](#privacy-requests)。
* 選擇退出銷售個人資訊（CCPA專屬）。 請參閱[本區段](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html#ccpa)。

本節將提供Campaign中的主要隱私權功能及相關角色的 [範例](https://helpx.adobe.com/campaign/kb/campaign-privacy-more.html#gdprpersonasandflow)。


### 同意、保留和角色 {#consent}

Adobe Campaign原本提供對隱私權至關重要的功能：

* **許可管理**:透過訂閱管理程式，您可以管理收件者的偏好設定，並追蹤哪些收件者已選擇加入何種訂閱類型。 如需詳細資訊，請參閱關於 [訂閱](../../delivery/using/about-services-and-subscriptions.md)。
* **資料保留**:所有內置的標準日誌表都具有預設的保留期，通常將其資料儲存限制在6個月或更短。 您可以使用工作流程設定額外的保留期。 如需詳細資訊，請洽詢Adobe顧問或技術管理員。
* **權限管理**:Adobe Campaign可讓您透過不同的預先建立或自訂角色，管理指派給各種Campaign運算子的權限。 這可讓您管理公司內可存取、修改或匯出不同類型資料的人員。 有關詳細資訊，請參 [閱關於訪問管理](../../platform/using/access-management.md)。

如需這些功能以及如何在Adobe Campaign中管理這些功能的詳細資訊，請參 [閱本頁](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html#consent)。

### 隱私權要求 {#privacy-requests}

Adobe Campaign提供其他功能，協助您做為資料掌控者，針對特定隱私權要求做好準備：

* 存 **取權是** 「資料主體」有權從資料掌控者取得有關其個人資料是否正在處理、處理地點及處理原因的確認。

* 被 **遺忘權** （刪除要求）賦予資料主體權利，讓資料掌控者清除其個人資料。

>[!NOTE]
>
>這套工具可協助您符合GDPR、CCPA、PDPA和LGPD的隱私權規範。 如需這些不同法規的詳細資訊，請參 [閱本頁](https://helpx.adobe.com/tw/campaign/kb/campaign-privacy-overview.html#whatisgdpr)。

<!--* **GDPR** (General Data Protection Regulation) is the European Union’s (EU) privacy law that harmonizes and modernizes data protection requirements. GDPR applies to Adobe Campaign customers who hold data for Data Subjects residing in the EU.

* **CCPA** (California Consumer Privacy Act) provides California residents new rights in regards to their personal information and imposes data protection responsibilities on certain entities whom conduct business in California.

* **Thailand's PDPA** (Personal Data Protection Act) is the new privacy law that harmonizes and modernizes data protection requirements for Thailand. This regulation applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.

Brazil's Lei Geral de Proteção de Dados (LGPD) will be effective starting Aug, 16 for all companies collecting or processing personal data in Brazil. This regulation also applies to Adobe Campaign customers who hold data for Data Subjects residing in this country.-->

此頁 **會顯示** 「存取 **」和「刪** 除」請求 [](https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess)。 建立這些請求的實作步驟在本節中 [詳述](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)。 <!--Tutorials are also available [here](https://docs.adobe.com/content/help/en/campaign-standard-learn/tutorials/privacy/privacy-overview.html).-->

## 追蹤功能 {#tracking-capabilities}

### Cookie {#cookies}

由於Adobe Campaign的追蹤功能，您可以使用三種Cookie來追蹤傳送收件者的瀏覽：作業Cookie和兩個永久Cookie。

* A **session cookie**: the **nlid** cookie contains the identifier of the email sent to the contact (**broadlogId**) and the identifier of the message template (**deliveryId**). 連絡人按一下由 Adobe Campaign 傳送的電子郵件中包含的 URL 後即可添加識別碼，並且允許您追蹤他們在網路上的行為。瀏覽器關閉時，將自動清除工作階段 Cookie。連絡人可以將其瀏覽器設定為拒絕 Cookie。

* 永久 **Cookie**:Adobe Experience Cloud解決方 **案之間共用UUID** （通用唯一ID識別碼）Cookie。 它會設定一次，直到產生新值時從用戶端瀏覽器中消失為止。 此Cookie可讓您識別在使用者造訪網站時與Experience Cloud解決方案互動的使用者。 您可以透過登陸頁面（將未知的客戶活動與收件者建立關聯）或傳送來儲存。 此處提供此Cookie的說 [明](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-mc.html)。

<!--The **nllastdelid** cookie (introduced in Campaign Classic 20.3) is a permanent cookie which contains the **deliveryId** of the last delivery that user clicked the link from. This cookie is used - when the session cookie is missing - to identify the tracking table that will be used.-->

《通用資料保護規則》(GDPR)等法規規定，公司在安裝Cookie之前必須取得網站使用者的同意。

* 您必須透過授權要求（例如頁面上出現的）通知使用者您的網站已配備Web追蹤工具，並核取核取方塊來授權使用Cookie，或在其登陸的第一頁頂端新增橫幅等。
* 彈出式視窗通常會被瀏覽器封鎖，因此應避免出現。

### 訊息追蹤 {#message-tracking}

Adobe Campaign可讓您追蹤傳送的電子郵件和傳送收件人的行為：開啟、點按連結、取消訂閱等。 如需詳細資訊，請參閱關於 [訊息追蹤](../../delivery/using/about-message-tracking.md)。

若要這麼做，請將追 [蹤的連結新增至訊息](../../delivery/using/how-to-configure-tracked-links.md)[](../../delivery/using/monitoring-a-delivery.md#tracking-logs) ，以便在傳送控制面板的「追蹤」標籤中測量傳送和收件者行為的影響。 追蹤資料會在「追蹤指 [標」報表中解譯](../../reporting/using/delivery-reports.md#tracking-indicators) 。

### 網路追蹤 {#web-tracking}

Adobe Campaign也可讓您監控收件者瀏覽您網站的方式：插入追蹤標籤，以收集資訊並測量網頁應用程式頁面上的瀏覽。 如需詳細資訊，請參閱 [追蹤Web應用程式](../../web/using/tracking-a-web-application.md)。

本節將介紹Web跟蹤的 [配置](../../configuration/using/about-web-tracking.md)。

為進一步管理追蹤，Adobe Campaign可讓您顯示退出橫幅，以停止追蹤退出行為追蹤的使用者的網路行為。 如需詳細資訊，請參閱 [網頁應用程式追蹤選擇退出](../../web/using/web-application-tracking-opt-out.md)。
