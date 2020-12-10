---
solution: Campaign Classic
product: campaign
title: 隱私權與同意
description: 進一步瞭解隱私權與同意
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '2043'
ht-degree: 72%

---


# 隱私權與同意{#privacy-and-recommendations}

## 一般性建議 {#general-recommendations}

Adobe Campaign 是一款強大的工具，用於收集和處理包括個人資訊及敏感資料在內的超大資料。這就是需要謹慎管理隱私權的原因。

* 一律以負責任且符合道德的方式使用個人資訊。

* 避免傳送未經請求的電子郵件、推播通知和 SMS 訊息（「垃圾訊息」）。在打造顧客終生價值及忠誠度的過程中，Adobe 篤信許可式行銷原則，因此我們嚴格禁止使用 Adobe Campaign 傳送未經請求的訊息。

請前往[安全性和隱私權檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html)，以了解有關安全性和隱私權需要檢查的核心元素。

### 隱私權法規 {#privacy-regulations}

為正確處理隱私權並管理個人資料，工作時請遵循您營運業務所在地區的適用法規。這些法規包含：
* [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-does-general-data-protection-regulation-gdpr-govern_en)（歐洲一般資料保護規範）
* [DPA](https://www.gov.uk/data-protection)（英國實施 GDPR 之規範）
* [歐洲隱私權與電子通訊指令](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:02002L0058-20091219)
* [CAN-SPAM 法案](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business)（美國法律規定商業電子郵件的規則與要求）
* [CCPA](https://leginfo.legislature.ca.gov/faces/codes_displayText.xhtml?lawCode=CIV&amp;division=3.&amp;title=1.81.5.&amp;part=4.&amp;chapter=&amp;article=)（加州消費者隱私權法案）
* [PDPA](https://secureprivacy.ai/thailand-pdpa-summary-what-businesses-need-to-know/)（泰國個人資料保護法案）
* [LGPD](https://iapp.org/media/pdf/resource_center/Brazilian_General_Data_Protection_Law.pdf) （巴西通用資料保護法）-將於2020年8月16日起生效

>[!NOTE]
>
>如需有關GDPR、CCPA、PDPA和LGPD如何套用至Adobe Campaign的詳細資訊，請參閱[本頁](../../platform/using/privacy-management.md#privacy-management-regulations)。

### Adobe Experience Cloud 隱私權 {#experience-cloud-privacy}

Adobe Campaign 是 Adobe Experience Cloud 解決方案的一部分。在 Campaign 中處理隱私權的方式會依循 Experience Cloud 的一般原則，例如：

* **使用 Adobe Experience Cloud 時會收集哪些資訊**

   身為使用 Adobe Experience Cloud 解決方案的公司，您可以選擇要收集哪些資訊並傳送至您的 Adobe Experience Cloud 帳戶。可收集的資訊類型範例包含網頁瀏覽活動、IP 位址、行動裝置的位置資訊、促銷活動成功率、購買或放入購物車的項目等。

   >[!NOTE]
   >
   >而對於所有 Adobe 產品，Campaign 會收集應用程式和網站使用者的相關資訊。如需此項目的詳細資訊，請參閱 [Adobe 隱私權政策](https://www.adobe.com/privacy/policy.html)。

* **如何使用 Adobe Experience Cloud 收集資訊**

   * Adobe Experience Cloud 解決方案會使用 Cookie 和類似技術（例如網站信標，又稱為標籤或像素），讓您收集資訊。如需 Adobe Campaign Cookie 和追蹤功能的詳細資訊，請參閱[本節](#tracking-capabilities)。
   * 您也可以在行動應用程式中使用 Adobe Experience Cloud 技術。如需使用Campaign傳送行動傳送的詳細資訊，請參閱[SMS頻道](../../delivery/using/sms-channel.md)和[行動應用程式頻道](../../delivery/using/about-mobile-app-channel.md)。

* **使用者對於您使用 Adobe Experience Cloud 的隱私權選擇**

   Adobe 要求您提供客戶的隱私權政策，以說明：

   * 您與 Adobe Experience Cloud 相關聯的隱私權實務
   * 使用者如何針對 Adobe Experience Cloud 收集或使用其資訊進行偏好設定

   >[!NOTE]
   >
   >而對於所有 Adobe 產品，Campaign 使用者可以透過應用程式和網站，選擇退出分享收集關於他們的資訊。如需此項目的詳細資訊，請參閱 [Adobe Experience Cloud 使用資訊常見問答](https://www.adobe.com/privacy/experience-cloud-usage-info-faq.html)。

如需 Adobe Experience Cloud 隱私權的後續詳細資料，請參閱[本頁](https://www.adobe.com/privacy/marketing-cloud.html)。

## 個人資料與角色 {#personal-data}

在管理隱私權時，請務必定義哪些資料應謹慎處理，以及由哪些人員處理。
* **個人資料**&#x200B;是指可直接或間接識別在世個人的資訊。
* **敏感個人資料**&#x200B;是指與個人的種族、政治觀點、宗教信仰、犯罪背景、遺傳資訊、健康資料、性傾向、生物識別資訊，以及工會會員會籍相關的資訊。

將Campaign與其他Experience Cloud解決方案整合時，若觀眾可從一個系統傳輸至另一個系統，例如[Adobe Analytics](../../platform/using/adobe-analytics-data-connector.md)、[Audience Manager或People核心服務](../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md)、[Campaign Standard](../../integrations/using/synchronizing-audiences.md)，或透過[CRM Connectors](../../platform/using/crm-connectors.md)與其他解決方案整合，您需要付費格外注重個人資料保護。

[主要法規](#privacy-regulations)是指管理資料之不同實體，如下所示：
* **資料控制方**&#x200B;是決定收集、使用及分享個人資料之方式與目的的當局機關。
* **資料處理方**&#x200B;是指依據資料控制方的指示收集、使用或分享個人資料的任何個人或一方。
* **資料主體**&#x200B;是指正在收集、使用或分享個人資料的任何在世個人，以及可參照該個人資料直接或間接識別的在世個人。

因此，身為收集和分享個人資料的公司，您是資料控制方、客戶是資料主體，而 Adobe Campaign 在依您的指示處理個人資料時，會作為資料處理方。請注意，身為資料控制方，您有責任處理與資料主體的關係，例如管理[隱私權要求](#privacy-requests)。

### 使用案例情境{#use-case-scenario}

為了說明不同角色如何互動，以下是 GDPR 客戶體驗的高階使用案例。

在此範例中，航空公司是 Adobe Campaign 客戶。該公司是&#x200B;**資料控制方**，而該航空公司的所有客戶為&#x200B;**資料主體**。Laura 在此特定案例中是航空公司的客戶。

以下是此範例中使用的不同角色：

* **Laura** 是&#x200B;**資料主體**。她是收到航空公司訊息的收件人。Laura 可能是常客，但可能會在某個時間點決定不想要收到關於這家航空公司提供的任何個人化廣告或行銷訊息。她會要求航空公司（根據他們的流程）刪除她的常旅客號碼。

* **Anne** 是航空公司的&#x200B;**資料控制方**。她會收到 Laura 的請求，檢索用於識別資料主體的有用 ID，並在 Adobe Campaign 中提交請求。

* **Adobe Campaign** 是&#x200B;**資料處理方**。

![](assets/privacy-gdpr-flow.png)

以下是此使用案例的一般流程：

1. **資料主體** (Laura) 透過電子郵件、客戶服務或網站入口，向&#x200B;**資料控制方**&#x200B;傳送 GDPR 請求。

1. **資料控制方** (Anne) 透過介面或使用 API 將 GDPR 請求推送至 Campaign。

1. 當&#x200B;**資料處理方** (Adobe Campaign) 收到資訊後，會對 GDPR 請求採取行動，並傳送回應或向&#x200B;**資料控制方** (Anne) 進行確認。

1. 然後，**資料控制方** (Anne) 會審查該資訊並將其傳送回&#x200B;**資料主體** (Laura)。

## 資料擷取 {#data-acquisition}

Adobe Campaign 可讓您收集資料，包括個人和敏感資訊。因此，您必須接收並監控收件者的同意。

* 讓收件者一律同意接收通訊。為此，請盡快接受選擇退出要求，並透過雙重選擇加入程式以確認同意。如需詳細資訊，請參閱[建立雙重選擇加入的訂閱表單。](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)
* 請勿匯入詐騙清單，並使用種子位址來檢查您的用戶端檔案是否未被騙用。 有關詳細資訊，請參閱[關於種子地址](../../delivery/using/about-seed-addresses.md)。
* 透過同意與權限管理，您可以追蹤收件者的偏好設定，並管理組織內哪些人員可以存取哪些資料。如需詳細資訊，請參閱[本節](#consent)。
* 加速和管理收件者的隱私權要求。如需詳細資訊，請參閱[本節](#privacy-requests)。

## 隱私權管理 {#privacy-management}

隱私權管理是指可協助您遵守隱私權法規（GDPR、CCPA等）的所有程序及工具。概述[本頁](https://helpx.adobe.com/tw/campaign/kb/campaign-privacy-overview.html)的隱私權管理。

Adobe Campaign 提供專屬於隱私權管理的各種功能：
* 同意管理、資料保留和使用者角色。請參閱[本節](#consent)。
* 隱私權要求（存取權限與被遺忘的權利）。請參閱[本節](#privacy-requests)。
* 選擇退出個人資訊銷售（專屬於 CCPA）。請參閱[本節](../../platform/using/privacy-requests.md#sale-of-personal-information-ccpa)。

[本節](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/privacy/privacy-faq.html?lang=zh-Hant#getting-started)將提供 Campaign 中主要隱私權功能及相關角色的範例。

### 同意、保留和角色 {#consent}

一開始，Adobe Campaign 會提供對隱私權至關重要的功能：

* **同意管理**：透過訂閱管理程序，您可以管理收件者的偏好設定，並追蹤哪些收件者已選擇加入何種訂閱類型。如需詳細資訊，請參閱[關於訂閱](../../delivery/using/about-services-and-subscriptions.md)。
* **資料保留**：所有內建標準記錄表都具有預設的保留期間，通常會將其資料儲存限制在 6 個月或更短時間。您可以使用工作流程設定其他的保留期間。如需此項目的詳細資訊，請洽詢 Adobe 顧問或技術管理員。
* **權限管理**：Adobe Campaign 可讓您透過不同的預先建立或自訂角色，管理指派給各種 Campaign 運算子的權限。這可讓您管理公司內可存取、修改或匯出不同類型資料的人員。有關此項目的詳細資訊，請參閱[關於存取管理](../../platform/using/access-management.md)。

如需這些功能及如何在 Adobe Campaign 中管理這些功能的詳細資訊，請參閱[本節](../../platform/using/privacy-management.md#consent-retention-roles)。

### 隱私權要求 {#privacy-requests}

Adobe Campaign 提供其他功能，協助您作為資料控制方，針對特定隱私權要求預作準備：

* **存取權限**&#x200B;是指資料主體有權從資料控制方取得關於其個人資料是否正在處理、處理地點及處理原因的確認。

* **被遺忘的權利**（刪除要求）為資料主體賦予權利，讓資料控制方得以清除其個人資料。

[本部分](../../platform/using/privacy-management.md#right-access-forgotten)會顯示&#x200B;**存取**&#x200B;及&#x200B;**刪除**&#x200B;要求。

建立這些要求的實作步驟將於[本部分](../../platform/using/privacy-requests.md)詳細說明。

## 追蹤功能 {#tracking-capabilities}

### Cookie {#cookies}

由於Adobe Campaign的追蹤功能，您可以使用三種Cookie來追蹤傳送收件者的瀏覽：作業Cookie和兩個永久Cookie。

* A **session** cookie:**nlid** Cookie包含傳送給連絡人的電子郵件識別碼(**broadlogId**)和訊息範本識別碼(**deliveryId**)。 連絡人按一下由 Adobe Campaign 傳送的電子郵件中包含的 URL 後即可添加識別碼，並且允許您追蹤他們在網路上的行為。瀏覽器關閉時，將自動清除工作階段 Cookie。連絡人可以將其瀏覽器設定為拒絕 Cookie。

* 兩個&#x200B;**permonent** Cookie:
   * **UUID**（通用唯一ID識別碼）Cookie會在Adobe Experience Cloud解決方案之間共用。 它會設定一次，直到產生新值時，從用戶端瀏覽器消失為止。 此Cookie可讓您識別在使用者造訪網站時與Experience Cloud解決方案互動的使用者。 您可以透過登陸頁面（將未知的客戶活動與收件者建立關聯）或傳送來儲存。 此Cookie的說明可在[此頁面](https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-mc.html?lang=en#ec-cookies)取得。
   * **nllastdelid** Cookie（在Campaign Classic 20.3中推出）是永久Cookie，包含使用者點按連結的上次傳送的&#x200B;**deliveryId**。 當作業Cookie遺失時，會使用此Cookie來識別將使用的追蹤表格。

《一般資料保護規範》(GDPR) 等法規規定，公司必須先取得網站使用者的同意，才能安裝 Cookie。

* 您必須透過授權要求（例如頁面上出現的）通知使用者您的網站已配備Web追蹤工具，並核取核取方塊來授權使用Cookie，或在其登陸的第一頁頂端新增橫幅等。
* 彈出式視窗通常會被瀏覽器封鎖，因此應避免出現。

### 消息跟蹤{#message-tracking}

Adobe Campaign可讓您追蹤傳送的電子郵件和傳送收件人的行為：開啟、點按連結、取消訂閱等。 有關詳細資訊，請參閱[關於消息跟蹤](../../delivery/using/about-message-tracking.md)。

若要這麼做，請將[追蹤連結](../../delivery/using/how-to-configure-tracked-links.md)新增至您的訊息，以便在傳送控制面板的[追蹤](../../delivery/using/delivery-dashboard.md#tracking-logs)標籤中測量傳送和收件者行為的影響。 追蹤資料會在[追蹤指標](../../reporting/using/delivery-reports.md#tracking-indicators)報表中解譯。

### 網路追蹤{#web-tracking}

Adobe Campaign也可讓您監控收件者瀏覽您網站的方式：插入追蹤標籤，以收集資訊並測量網頁應用程式頁面上的瀏覽。 如需詳細資訊，請參閱[追蹤Web應用程式](../../web/using/tracking-a-web-application.md)。

網頁追蹤的設定顯示在[本節](../../configuration/using/about-web-tracking.md)中。

為進一步管理追蹤，Adobe Campaign可讓您顯示退出橫幅，以停止追蹤退出行為追蹤的使用者的網路行為。 如需詳細資訊，請參閱[Web應用程式追蹤選擇退出](../../web/using/web-application-tracking-opt-out.md)。
