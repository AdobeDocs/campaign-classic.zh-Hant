---
title: 宣傳活動提供最佳實務
seo-title: 提供最佳實務
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f599bc5483779ae62dd4d5eb1936cbc2760639b5
workflow-type: tm+mt
source-wordcount: '4348'
ht-degree: 4%

---


# 提供最佳實務 {#delivery-best-practices}

## 最佳化傳送 {#optimize-delivery}

在開始建立傳送之前，您可以採取數個動作來保護並最佳化上游傳送程式。

以下章節概述最佳化Adobe Campaign設定的最佳實務和建議程式。 遵循這些實務可將下游可能遇到的問題降到最低。

### 平台效能

數個因素會直接影響伺服器效能並減緩平台速度：

* 個人化元素的數量和類型： 電子郵件中的個人化會從資料庫中提取每個收件者的資料。 如果有許多個人化元素，會增加準備傳送所需的資料量。  在本節中進一步瞭解個 [人化](../../delivery/using/about-personalization.md)

* 伺服器載入： 當行銷伺服器同時處理許多不同的工作時，可能會降低效能。 行銷伺服器需要協調所有傳送的所有傳入和傳出資料，以確保資料正確且準時。

   **TIP** —— 為避免此問題，請與團隊中的其他成員協調交貨的排程，以確保最佳效能。

* 工作流執行： 監控工作流程是避免平台效能問題的關鍵。 請遵循本檔案 [中所列的准則](../../workflow/using/workflow-best-practices.md#execution-and-performance)。

* 身為代管客戶，您可運用「促銷活動控 [制面板」功能](https://docs.adobe.com/content/help/en/control-panel/using/discover-control-panel/key-features.html) ，使用效能監控功 [能來監控平台](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) 。

### 檢查網路配置 {#network-config}

若要在處理大量電子郵件時最佳化傳送，並避免被誤認為是垃圾郵件發送者，請確定您有合法的網路組態，不會嘗試隱藏伺服器的身分。

**提示**:  使用與您品牌網站對應的透明寄件者位址。 例如，這家旅行社管理著華倫天奴連鎖酒店。 它擁有其網站的valentino.com網域。 為推廣巴黎的華倫天奴酒店，它使用paris.valentino.com子網域。 因此，相關的發件人地址可以是hotel@paris.valentino.com。

### 可傳遞性管理 {#deliverability-management}

若要在不反彈或標示為垃圾訊息的情況下進入收件者的收件匣，您必須改善訊息的傳遞率。

* 什麼是傳遞能力？

   * 它是指決定電子郵件是否能被收件者伺服器接受的因素。 ISP（網際網路服務供應商）會過濾掉其識別為垃圾訊息的電子郵件，或封鎖影像下載。 如果他們判斷某個網域傳送的電子郵件過多，他們會設定接受該寄件者寄送之電子郵件的數量限制。

   * 在檢查您的電子郵件是否具有傳遞能力時，您想要專注於四個主要類別： 資料品質、訊息和內容、傳送基礎架構和聲譽。 有關本主題的深入探討，請參 [閱本節](../../delivery/using/about-deliverability.md)。

* 套用本檔案中詳 [細的建議](../../delivery/using/deliverability-key-points.md)。

* 請連絡您的Adobe代表以取得協助。

### 隔離管理 {#quarantine-management}

維護良好的隔離管理流程符合您的最大利益。

當您開始在新平台上傳送電子郵件時，可能會使用未完全限定的位址清單。 如果您發送到無效地址或蜜罐地址（郵箱僅用於誘騙垃圾郵件發送者），這將開始削弱您平台的聲譽。 良好的隔離管理流程有助於： 維持位址品質、避免網際網路存取供應商的封鎖清單，並降低錯誤率、加速傳送和總處理能力。

**提示**

* 如果您有無效地址的清單，Adobe建議您通過> **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** >將其導入隔離表 **[!UICONTROL Non deliverables and addresses]**。

* 在傳送分析期間，預設會排除隔離地址的收件者： 它們不是目標。 這會加快傳送速度，因為錯誤率對傳送速度有顯著影響。例如，當收件箱已滿或地址不存在時，可以隔離電子郵件地址。 [進一步瞭解](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign會根據傳回的錯誤類型管理錯誤位址。 如需詳細資訊，請參閱[本區段](../../delivery/using/understanding-quarantine-management.md)。


* 如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離可讓您避免被這些提供者添加到塊清單中。

* 隔離管理也有助於降低SMS傳送成本，將錯誤的電話號碼排除在傳送途中。

### 雙重加入機制 {#double-opt-in}

為避免傳送訊息至無效位址、限制不當通訊並改善寄件者信譽，Adobe建議實作訂閱後確認的雙重選擇加入機制。 這有助於確保收件者有意訂閱。

本節將說明實作此機制的 [詳細資訊](../../web/using/use-cases--web-forms.md)。

## 使用範本 {#use-templates}

提供範本可針對大多數常見活動類型提供現成的藍本，以提高效率。 使用範本，行銷人員可以在較短的時間內，以最少的自訂方式部署新的促銷活動。

在本節中進一步瞭解傳送 [範本](../../delivery/using/creating-a-delivery-template.md)。

### 開始使用傳送範本 {#gs-templates}

交 [貨範本](../../delivery/using/creating-a-delivery-template.md) ，可讓您定義一組符合您需求且可重複使用於未來交貨的技術和功能屬性。 然後，您就可以節省時間，並視需要標準化傳送。

當您在Adobe Campaign中管理多個品牌時，Adobe建議每個品牌擁有一個子網域。 例如，銀行可以有多個子域，對應其每個區域機構。 如果銀行擁有bluebank.com網域，其子網域可以是@ny.bluebank.com、@ma.bluebank.com、@ca.bluebank.com等。 每個子網域有一個傳送範本，讓您隨時針對每個品牌使用正確的預先設定參數，以避免錯誤並節省您的時間。

**提示**:  為避免Campaign Standard中的設定錯誤，建議您複製原生範本並變更其屬性，而非建立新範本。

**配置地址**

* 傳送者的地址是強制性的，以允許傳送電子郵件。

* 某些ISP（Internet服務提供商）在接受消息之前檢查發件人地址的有效性。

* 錯誤形成的地址可能導致接收伺服器拒絕。 您必須確定地址正確無誤。

* 地址必須明確標識發件人。 域必須由發送者擁有並註冊。

* Adobe建議建立與傳送和回覆所指定之位址對應的電子郵件帳戶。 請洽詢您的訊息系統管理員。

若要在促銷活動介面中設定位址，請遵循下列步驟：

1. 在傳送 [範本中](../../delivery/using/creating-a-delivery-template.md)，按一下 **[!UICONTROL From]** 連結。 在視窗 **[!UICONTROL Email header parameters]** 中，填寫下列欄位：

   ![](assets/d_best_practices_email_header.png)

1. 在欄位 **[!UICONTROL Sender address]** 中，請確定位址網域與您委派給Adobe的子網域相同。 您可以變更&#39;@&#39;前的部分，但不能變更網域位址。

1. 在欄位 **[!UICONTROL From]** 中，使用收件者可輕易辨識的名稱（例如您的品牌名稱），以提高您的交貨的開業率。 若要進一步改善收件者的體驗，您可以新增人名，例如「Emma from Megastore」。

1. 在欄位 **[!UICONTROL Reply address text]** 中，預設會使用傳送者的位址來回覆。 不過，Adobe建議使用現有的實際地址，例如您品牌的客戶服務。 在這種情況下，如果收件者傳送回覆，客戶服務將能夠處理。

**設定控制群組**

傳送傳送後，您可以比較已排除的收件者與已接收傳送的收件者的行為。 然後，您可以衡量促銷活動的效率。 請進一步瞭解本節中 [的控制群組](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group)。

若要設定控制群組，請按一下連 **[!UICONTROL To]** 結。 在窗口 **[!UICONTROL Select target]** 中，選擇該選 **[!UICONTROL Control group]** 項卡。 您可以擷取目標的一部分，例如5%的隨機樣本。

![](assets/d_best_practices_control_group.png)

**使用類型套用篩選或控制規則**

類型學包含分析階段期間在傳送任何訊息之前套用的檢查規則。

在範本 **[!UICONTROL Typology]** 屬性的索引標籤中，根據您的需求變更預設類型。

例如，為了更好地控制對外流量，您可以定義每個子網域可使用一個相似性，並為每個相似性建立一個類型，以定義哪些IP位址。 相關性在實例的配置檔案中定義。 請洽詢您的Adobe Campaign管理員。

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

## 設計和個人化 {#design-and-personalize}

在設計訊息內容時，請盡量避免可能導致您無法執行傳送的常見問題。 大部分時候，可能的錯誤都與個人化、格 [式化](../../delivery/using/about-personalization.md)[和影像](../../delivery/using/defining-the-email-content.md#message-content) 有 [關](../../delivery/using/defining-the-email-content.md#adding-images)。

### 最佳化個人化 {#optimize-personalization}

為避免常見問題，避免您無法執行傳送作業，並改善收件者的體驗，Adobe Campaign可讓您個人化您的訊息。

您可以使用儲存在Adobe Campaign資料庫中或透過追蹤、登陸頁面、訂閱等方式收集的收件者資料。
本節將介紹個人化 [基本概念](../../delivery/using/personalization-fields.md)。

請確定您的訊息內容已正確設計，以避免任何通常與個人化相關的錯誤。

**提示**: 在來自第三方廠商提供之外部檔案的個人化欄位中，外部HTML內容可能錯誤。 若要避免此情況，請檢查語法、使用標籤、字元等。 例如，Adobe Campaign個人化標籤一律有下清單格： &lt;%=table.field%>。 如需詳細資訊，請參閱[本區段](../../delivery/using/about-personalization.md)。

在個人化區塊中使用參數不正確可能是個問題。 例如，JavaScript中的變數應使用如下：

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

有關個人化區塊的詳細資訊，請參 [閱本節](../../delivery/using/personalization-blocks.md)。

您可以在工作流程中準備個人化資料，以改善傳送準備分析。 如果個人化資料是透過Federated Data Access(FDA)來自外部表格，則應特別使用。 本節將介紹此選 [項](../../delivery/using/personalization-fields.md#optimizing-personalization)

### 建立最佳化內容 {#optimize-content}

在建立電子郵件時，請牢記以下一般最佳實務。

* 讓設計更簡單

* 讓行動使用者注意

* 避免完全以影像為基礎的電子郵件

* 使用電子郵件安全字型

* 編碼特殊字元

**主題行** -在主題行上 [工作](../../delivery/using/defining-the-email-content.md#message-content) ，以改進開放率：

* 避免主題過長。 最多使用50個字元

* 避免重複使用「免費」或「選件」等可視為垃圾訊息的字詞

* 避免使用大寫字母和特殊字元，例如&quot;!&quot;、&quot;£&quot;、&quot;€&quot;、&quot;$&quot;

**鏡像頁** -始終包含鏡像頁連結。 首選位置是電子郵件的頂端。 [進一步瞭解](../../delivery/using/sending-messages.md#generating-the-mirror-page)

**取消訂閱連結** -取消訂閱連結是必要的。 它必須可見且有效，而且表單必須正常運作。 依預設，在分析訊息時，排 [版規則會檢查是否已包含選擇退出連結](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) ，並在遺失時產生警告。

**提示**: 由於人為錯誤總是可能發生，因此每次傳送前請先檢查退出連結是否正常運作。 例如，傳送證明時，請確定連結有效、表單是線上的，以及「不再與此收件者聯絡」欄位已變更為「是」。

瞭解如何在本節中插入退出 [連結](../../delivery/using/personalization-blocks.md#personalization-blocks-example)。

**電子郵件大小** -為避免效能或傳遞性問題，建議電子郵件的最大大小約為 **35KB**。 若要檢查訊息大小，請前往標 **[!UICONTROL Preview]** 簽並選擇測試描述檔。 產生後，訊息大小會顯示在右上角。

若要限制您的電子郵件，請考慮下列事項：

* 移除多餘或未使用的樣式

* 將部分電子郵件內容移至登陸頁面

* 精簡您的程式碼

請務必在最終傳送前測試任何變更

**SMS長度**

根據預設，SMS 中的字元數量符合 GSM（行動通訊全球系統）標準。使用 GSM 編碼的 SMS 訊息最多只能有 160 個字元，若是以多個部分傳送的訊息，則每個 SMS 的 SMS 訊息最多只能有 153 個字元。

音譯包括當 GSM 標準未考慮到 SMS 的一個字元時，用另一個字元取代該字元。請注意，將個人化欄位插入SMS訊息的內容可能會引入GSM編碼未考慮的字元。 您可以核取對應字母音譯的SMPP頻道設定標籤中的對應方塊，以授權字母音譯 **[!UICONTROL External account]**。
在本節 [中進一步瞭解](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

**提示**:

* 若要保留SMS訊息中所有字元的原樣，請勿變更正確的名稱，例如，請勿啟用音譯。

* 不過，如果您的SMS訊息包含許多未經GSM標準考量的字元，則可讓音譯功能限制傳送訊息的成本。

在本節 [中進一步瞭解](../../delivery/using/sms-channel.md#about-character-transliteration)。

### 處理格式設定 {#formatting}

若要避免常見的格式錯誤，請檢查下列元素：

* 更正日 **期格式**: Adobe Campaign為JavaScript範本和XSL樣式表提供日期格式功能。 [進一步瞭解](../../delivery/using/formatting.md#date-display)

* 電子郵件中 **授權字元** 的使用： 電子郵件地址的有效字元清單已在「XtkEmail_Characters」選項中定義。 瞭解如何存取本節中 [的促銷活動選項](../../installation/using/configuring-campaign-options.md)。 若要正確處理特殊字元，Adobe Campaign必須以Unicode安裝。

* 電子郵件 **驗證配置**: 請確定電子郵件標題包含DKIM簽名。 DKIM（域密鑰標識的郵件）驗證允許接收電子郵件伺服器驗證消息確實是由其聲稱發送者或實體發送的，以及消息內容是否在最初發送（和DKIM「簽名」）和接收時間之間發生了更改。 此標準通常使用「寄件者」或「寄件者」標題中的網域。 如需詳細資訊，請參閱[本區段](../../delivery/using/technical-recommendations.md#dkim)。

* **互動式電子郵件設計** ，可確保電子郵件能夠針對開啟裝置以最佳方式呈現。

   * 使用互動式電子郵件HTML，而非網頁HTML。

   * 使用預覽模式並傳送校樣，以盡可能多的裝置來測試演算。

   * Adobe Campaign Classic數位內容編輯器(DCE)模組包含一些互動式設計格式範本，適用於行動裝置，可透過 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** >取得 **[!UICONTROL Content templates]**。 請參閱 [本文章](https://theblog.adobe.com/responsive-email-design-101/)。



### 管理影像 {#manage-images}

使用影像時，請遵循以下准則。

* **防止影像封鎖** -有些電子郵件用戶端預設會封鎖影像，而有些使用者會將其設定變更為封鎖影像，以儲存資料使用。 因此，如果不下載影像，則會丟失整個消息。 若要避免此情況：

   * 在內容與影像和文字之間取得平衡。 避免完全以影像為基礎的電子郵件。

   * 如果文字必須包含在影像中，請使用alt和title文字，以確保訊息傳達完畢。 設定替代／標題文字的樣式以改善其外觀。

   * 避免使用背景影像，因為有些電子郵件客戶不支援這些影像。

* **讓影像回應速度** -嘗試讓影像回應速度更快且可調整大小。 請注意，由於建置時間較長，這可能會造成成本影響。

* **使用絕對影像參考** -若要從外部存取，連結至促銷活動的電子郵件和公共資源中使用的影像必須存在於可外部存取的伺服器上。

   * 您可以檢查實例配置是否啟用公共資源管理。 [進一步瞭解](../../installation/using/deploying-an-instance.md#managing-public-resources)

   * 從傳送精靈中，您可以匯入包含影像的HTML頁面，或透過圖示直接使用HTML編輯器插入 **[!UICONTROL Image]** 影像。 [進一步瞭解](../../delivery/using/defining-the-email-content.md#adding-images)

   * 如果未顯示影像，請檢查伺服器上是否有影像。 若要這麼做，請按一下傳送中的「來源」標籤。 在網頁瀏覽器中尋找您的影像並複製並貼上每個影像的URL。 如果未顯示影像，請連絡您的IT管理員或提供傳送內容的協力廠商。

### 預覽您的訊息 {#preview-msg}

Adobe建議預覽您的訊息，以檢查其個人化，以及收件者如何看到您的傳送。

* 在傳送捲軸中，子標 **[!UICONTROL Preview]** 簽可讓您檢視收件者每個內容的轉譯。 個性化欄位和內容的條件元素被所選配置檔案的相應資訊替換。 [進一步瞭解](../../delivery/using/defining-the-email-content.md#message-content)

* 每次預覽期間會執行自動反垃圾郵件檢查。 在子標 **[!UICONTROL Preview]** 簽中，檢查 [SpamAssassin](../../delivery/using/spamassassin.md) spam計分。  按一 **[!UICONTROL More...]** 下以進一步瞭解警告。  在這麼做之前，請確定SpamAssassin已正確安裝並設定在Adobe Campaign應用程式伺服器上。 [進一步瞭解](../../installation/using/configuring-spamassassin.md)

## 定義正確的目標 {#define-the-right-target}

目標人口是關鍵： 仔細建立您的清單、在熱門的電子郵件用戶端和行動裝置上測試您的電子郵件，並確保您的電子郵件清單是最新的（沒有未知或過時的位址）。 您也可以傳送校樣，協助設定完整的驗證週期。

在本節中進一步瞭解目 [標人口族群](../../delivery/using/steps-defining-the-target-population.md)

### 鎖定適當的受眾 {#target-the-right-audience}

當您的內容準備好時，您需要仔細定義將收到訊息的對象。

為了讓傳遞成功，您想要將最相關的個人化內容傳送給適當的收件者。 Adobe Campaign可讓您建立最精確的目標： 您可以根據收件者的年齡、當地語系、他們購買的商品，如果他們點選先前遞送的連結，等等。 有了Adobe Campaign，您也可以定義測試設定檔、控制群組和種子位址，以確定您的目標正確無誤。

### 目標映射 {#target-mappings}

在Campaign Classic中，預設會將傳送範本定位為收 **件者**。 Adobe Campaign會為您的傳送提供其他目標對應，您可以根據需要進行變更。

例如，您可以將描述檔透過社交網路收集到的訪客或訂閱資訊服務的訪客傳送至訪客。

這些映射將在 [本節中顯示](../../delivery/using/selecting-a-target-mapping.md)。

您也可以建立和使用自訂的目標對應。 如需詳細資訊，請參閱[本區段](../../configuration/using/target-mapping.md)。

### 外部收件者 {#external-recipients}

您可以將內容傳送給儲存在外部檔案而非儲存在資料庫中的收件者。 在本節 [中進一步瞭解](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients)。

### 傳送給您的訂閱者 {#send-to-subscribers}

若要傳送訊息給電子報的訂閱者，您可以直接將訂閱者鎖定在對應的資訊服務。 在本節 [中進一步瞭解](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service)。


### 測試收件者和種子地址 {#test-recipients-seed-addresses}

若要測試傳送內容，請在傳送至主要目標之前先使用校樣。

請確定您選取了適當的校樣收件者，因為他們會驗證訊息的表單和內容。 本節將介紹定義校樣收件 [者的步驟](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target)。

種子地址用於定位不符合定義的目標標準的接收者，以便在發送到主目標之前測試傳送。 本節將介紹 [這些內容](../../delivery/using/about-seed-addresses.md)。

### 消除重複地址 {#deduplicate-addresses}

請務必避免使用重複的電子郵件位址，因為這會對您的目標產生影響：

* 分割目標時，可多次傳送相同的訊息。

* 如果收件者在收到訊息後取消訂閱，其重複的描述檔仍會收到未來的訊息。

刪除重複地址可保護您的發送信譽並確保良好的隔離管理。

在此使用 [案例中進一步瞭解](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery)。


### 索引電子郵件地址 {#index-addresses}

要優化應用程式中使用的SQL查詢的效能，可以從資料模式的主元素中聲明索引。

將索引新增至電子郵件地址的步驟會顯示 [在本節中](../../configuration/using/database-mapping.md#indexed-fields)。

## 傳送前先執行所有檢查 {#perform-all-checks}

當訊息準備就緒後，請確定其內容在所有裝置上都正確顯示，且不包含任何錯誤，例如錯誤的個人化或損壞的連結。

在傳送訊息之前，請確定參數和設定與傳送一致。

### 驗證是關鍵 {#validation-is-key}

在傳送傳送內容之前，您必須確保收件者會收到您真正想要傳送的訊息。 為此，您需要驗證訊息內容和傳送參數。

此步驟可讓您偵測可能的錯誤並加以修正，然後再傳送至主要目標。

本節將介紹驗證傳送 [的步驟](../../delivery/using/steps-validating-the-delivery.md)。

### 收件箱呈現 {#inbox-and-email-rendering}

收件匣轉換功能可讓您在主要電子郵件用戶端上預覽訊息、掃描內容和信譽，以及瞭解收件者閱讀訊息的方式。

**提示**:

* 您可以在接收郵件的不同上下文中查看發送的郵件： webmail、訊息服務、行動等。

* 收件匣轉換功能對於識別您的電子郵件促銷活動是否成功超過主要ISP（網際網路服務供應商）和網路郵件服務的篩選至關重要。 此類工具會將電子郵件的預檢副本傳送至測試收件匣網路，讓您瞭解訊息在這些服務間的顯示或呈現方式。 它們也可能包含報表和程式碼修正選項，可協助您快速識別並進行修正，以改善傳遞性。

在本節 [中進一步瞭解](../../delivery/using/inbox-rendering.md)。

### 校對訊息 {#proof-messages}

傳送校樣可讓您檢查選擇退出連結、鏡像頁面和任何其他連結、驗證訊息、確認影像已顯示、偵測可能的錯誤等。 您也可能想要檢查不同裝置上的設計和演算。

在本節 [中進一步瞭解](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

### 設定A/B測試傳送 {#a-b-testing-deliveries}

如果您有數個內容要傳送電子郵件，您可以使用A/B測試來找出哪個版本對目標群體的影響最大。

**提示**:

* 將不同的版本傳送給您的部分收件者

* 選取成功率最高的成功率，並將它傳送至目標的其他部分

在本節 [中進一步瞭解](../../workflow/using/a-b-testing.md)。

### 確定訊息已傳送 {#make-sure-your-message-is-delivered}

最後一個步驟是，將您的機會發揮到最大，並運用Adobe Campaign Classic的強大功能，確保您的訊息確實能傳送給相關的收件者。

**執行驗證程式** -您可以定義完整的驗證程式，包括Adobe Campaign運算子和群組，以驗證目標和訊息內容。 這將確保對促銷活動的各種程式進行完整監控： 鎖定、內容、預算、擷取和傳送證明。 視其權限而定，使用者會收到通知、收到校樣，並可驗證或拒絕訊息。 在本節 [中進一步瞭解](../../campaign/using/marketing-campaign-approval.md#approval-process)。

**使用波** -可以使用波逐漸增加發送的音量。 這樣可避免您的訊息被標示為垃圾訊息，或您想要限制每天的訊息數目。 使用波，您可以將傳送分成數批，而不是同時傳送大量訊息。 在本節 [中進一步瞭解](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves)。

**排定訊息優先順序** -您可以指出優先順序等級，以設定傳送的傳送順序。 若要這麼做：

1. 編輯傳送屬性，並選取標 **[!UICONTROL Delivery]** 簽。

1. 定義從到的按比例分配的優先順序 **[!UICONTROL Very low]** 別 **[!UICONTROL Very high]**。

>[!NOTE]
>
>無法定義從傳送內傳送訊息的順序。

**設定IP相關性** -要更好地控制出站SMTP通信，可以通過定義每個相關性可以使用哪些特定IP地址來管理相關性。 這可讓您限制特定傳送給電腦或輸出地址的電子郵件數。 例如，您可以針對每個國家／地區或子網域使用一個相似性。 然後，您可以依國家／地區建立一種類型學，並將每個相似性連結至對應的類型學。

您可以：

* 在serverConf.xml配置檔案中定義IP相關性。 [進一步瞭解](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* 對於每個IPAffinity元素，請聲明可使用的IP位址。 [進一步瞭解](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* 在您選 [擇的](../../campaign/using/about-campaign-typologies.md) 「類型」中 **[!UICONTROL Managing affinities with IP addresses]** ，使用欄位將傳送連結至管理上述相似性的傳送伺服器(MTA)。 [進一步瞭解](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* 傳送電子郵件後，請檢查標題以確認傳送的IP位址。 您的電子郵件管理員應協助您取得標題資訊。

>[!NOTE]
>
>這些步驟大部分只能由專家使用者執行。

**使用類型** -您可以使用類型學規則根據特定標準排除部分目標。 這樣可確保在遵守公司通訊原則的同時，傳送最符合客戶需求及期望的訊息。例如，您可以篩選未到電子報目標年齡的收件者。 在此範例 [中進一步瞭解](../../campaign/using/filtering-rules.md)。

**避免附件** -附件仍是惡意軟體擴散最常見的媒介之一，尤其是當大量傳送附件時。 加入檔案的安全連結，而非附加檔案。 這可確保額外的安全層，以防止意外的重新分發，並大幅降低因訊息大小或安全性原因，在傳入電子郵件閘道中拒絕訊息的機率。

## 追蹤和監控 {#track-and-monitor}

您按了「傳送」按鈕？ 讓我們看看會發生什麼。 傳送後，Adobe Campaign可讓您追蹤已傳送的訊息，並瞭解收件者對傳送的反應。 這可協助您改善未來的傳送方式，並最佳化您的下一個促銷活動。

### 監控傳送 {#monitoring-deliveries}

若要控制您的促銷活動，您必須確保訊息確實已傳送給收件者。

從「促銷活動傳送」控制面板，您可以檢查已處理的訊息和傳送稽核記錄。
您也可以控制傳送記錄檔中訊息的狀態。 [進一步瞭解](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

如果傳送未傳送，且狀態仍為「待定」，該怎麼辦 **呢**?

* 執行進程正在等待某些資源的可用性。 MTA可能尚未啟動。
檢查您的mta@instance模組是否已在MTA伺服器上啟動，並視需要啟動MTA模組。 [進一步瞭解](../../production/using/administration.md).

* 傳送可能使用傳送例項上未設定的相似性。
提示： 檢查流量管理（IP相似性）的設定。 有關詳細資訊，請參閱控制傳出SMTP通信。

>[!NOTE]
>
>這些步驟只能由專家使用者執行。

### 追蹤 {#tracking-deliveries}

若要深入瞭解收件者的行為，您可以追蹤他們對遞送的反應： 接收、開啟、點按連結、取消訂閱等。 在「促銷活動傳統型」中，此資訊會顯示在傳送所定位之收件者的「追蹤」標籤和傳送的「追蹤」標籤中。 在「促銷活動標準」中，它會顯示在傳送的「追蹤記錄檔」標籤中。

**提示**: 預設會啟用訊息追蹤。 若要設定URL，請在傳送精靈的下方區段中選取「顯示URL」選項。 對於訊息的每個URL，您可以選擇是否啟用追蹤。

如需詳細資訊，請參閱「設 [定追蹤](../../delivery/using/how-to-configure-tracked-links.md) 」區段和 [「追蹤指標](../../reporting/using/delivery-reports.md#tracking-indicators) 」說明。

### 傳送效能 {#delivery-performances}

要測量消息的傳送速度，您可以控制傳送吞吐量。 標準是每小時發送的消息數和消息的大小（以位／秒為單位）。 如需詳細資訊，請參閱「傳送 [總處理能力」](../../reporting/using/global-reports.md#delivery-throughput)。

**提示**:

* 請勿在實例上將交貨保持為失敗狀態，因為這會維護臨時表並影響效能。

* 從資料庫移除不再需要的傳送和非作用中收件者，以維持位址品質。

* 請勿嘗試排程大型傳送。 請注意，在系統上均勻分配負載可能需要5到10分鐘。

## 傳送疑難排解 {#delivery-troubleshooting}

當傳送發生問題時，可執行特定動作：

* [傳遞能力問題](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [影像顯示問題](../../production/using/image-display-issues.md)

* [傳送效能問題](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [臨時檔案問題](../../production/using/temporary-files.md) -僅 *限內部部署客戶*
