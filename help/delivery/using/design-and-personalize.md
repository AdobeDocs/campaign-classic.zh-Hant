---
title: 建立個人化內容
seo-title: 建立個人化內容
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1269'
ht-degree: 7%

---


# 建立個人化內容 {#build-personalized-content}

在設計訊息內容時，請盡量避免可能導致您無法執行傳送的常見問題。 大部分時候，可能的錯誤都與個人化、格 [式化](../../delivery/using/about-personalization.md)[和影像](../../delivery/using/defining-the-email-content.md#message-content) 有 [關](../../delivery/using/defining-the-email-content.md#adding-images)。

## 最佳化個人化 {#optimize-personalization}

為避免常見問題，避免您無法執行傳送作業，並改善收件者的體驗，Adobe Campaign可讓您個人化您的訊息。

您可以使用儲存在Adobe Campaign資料庫中或透過追蹤、登陸頁面、訂閱等方式收集的收件者資料。
本節將介紹個人化 [基本概念](../../delivery/using/personalization-fields.md)。

請確定您的訊息內容已正確設計，以避免任何通常與個人化相關的錯誤。

**提示**:在來自第三方廠商提供之外部檔案的個人化欄位中，外部HTML內容可能錯誤。 若要避免此情況，請檢查語法、使用標籤、字元等。 例如，Adobe Campaign個人化標籤一律有下清單格：&lt;%=table.field%>。 如需詳細資訊，請參閱[本區段](../../delivery/using/about-personalization.md)。

在個人化區塊中使用參數不正確可能是個問題。 例如，JavaScript中的變數應使用如下：

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

有關個人化區塊的詳細資訊，請參 [閱本節](../../delivery/using/personalization-blocks.md)。

您可以在工作流程中準備個人化資料，以改善傳送準備分析。 如果個人化資料是透過Federated Data Access(FDA)來自外部表格，則應特別使用。 本節將介紹此選 [項](../../delivery/using/personalization-fields.md#optimizing-personalization)

## 建立最佳化內容 {#optimize-content}

在建立電子郵件時，請牢記以下一般最佳實務。

* 讓設計更簡單

* 讓行動使用者注意

* 避免完全以影像為基礎的電子郵件

* 使用電子郵件安全字型

* 編碼特殊字元

### 主旨行

在主題行 [中](../../delivery/using/defining-the-email-content.md#message-content) ，改善開放率：

* 避免主題過長。 最多使用50個字元

* 避免重複使用「免費」或「選件」等可視為垃圾訊息的字詞

* 避免使用大寫字母和特殊字元，例如&quot;!&quot;、&quot;£&quot;、&quot;€&quot;、&quot;$&quot;

### 鏡像頁

一律包含鏡像頁面連結。 首選位置是電子郵件的頂端。 [進一步瞭解](../../delivery/using/sending-messages.md#generating-the-mirror-page)

### 取消訂閱連結

取消訂閱連結是必備的。 它必須可見且有效，而且表單必須正常運作。 依預設，在分析訊息時，排 [版規則會檢查是否已包含選擇退出連結](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) ，並在遺失時產生警告。

**提示**:由於人為錯誤總是可能發生，因此每次傳送前請先檢查退出連結是否正常運作。 例如，傳送證明時，請確定連結有效、表單是線上的，以及「不再與此收件者聯絡」欄位已變更為「是」。

瞭解如何在本節中插入退出 [連結](../../delivery/using/personalization-blocks.md#personalization-blocks-example)。

### 電子郵件大小

為避免效能或傳遞性問題，建議電子郵件的最大大小約為 **35KB**。 若要檢查訊息大小，請前往標 **[!UICONTROL Preview]** 簽並選擇測試描述檔。 產生後，訊息大小會顯示在右上角。

若要限制您的電子郵件，請考慮下列事項：

* 移除多餘或未使用的樣式

* 將部分電子郵件內容移至登陸頁面

* 精簡您的程式碼

請務必在最終傳送前測試任何變更

### SMS長度

根據預設，SMS 中的字元數量符合 GSM（行動通訊全球系統）標準。使用 GSM 編碼的 SMS 訊息最多只能有 160 個字元，若是以多個部分傳送的訊息，則每個 SMS 的 SMS 訊息最多只能有 153 個字元。

音譯包括當 GSM 標準未考慮到 SMS 的一個字元時，用另一個字元取代該字元。請注意，將個人化欄位插入SMS訊息的內容可能會引入GSM編碼未考慮的字元。 您可以核取對應字母音譯的SMPP頻道設定標籤中的對應方塊，以授權字母音譯 **[!UICONTROL External account]**。
在本節 [中進一步瞭解](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)。

**提示**:

* 若要保留SMS訊息中所有字元的原樣，請勿變更正確的名稱，例如，請勿啟用音譯。

* 不過，如果您的SMS訊息包含許多未經GSM標準考量的字元，則可讓音譯功能限制傳送訊息的成本。

在本節 [中進一步瞭解](../../delivery/using/sms-channel.md#about-character-transliteration)。

## 處理格式設定 {#formatting}

若要避免常見的格式錯誤，請檢查下列元素：

* 更正日 **期格式**:Adobe Campaign為JavaScript範本和XSL樣式表提供日期格式功能。 [進一步瞭解](../../delivery/using/formatting.md#date-display)

* 電子郵件中 **授權字元** 的使用：電子郵件地址的有效字元清單已在「XtkEmail_Characters」選項中定義。 瞭解如何存取本節中 [的促銷活動選項](../../installation/using/configuring-campaign-options.md)。 若要正確處理特殊字元，Adobe Campaign必須以Unicode安裝。

* 電子郵件驗 **證的配置**:請確定電子郵件標題包含DKIM簽名。 DKIM（域密鑰標識的郵件）驗證允許接收電子郵件伺服器驗證消息確實是由其聲稱發送者或實體發送的，以及消息內容是否在最初發送（和DKIM「簽名」）和接收時間之間發生了更改。 此標準通常使用「寄件者」或「寄件者」標題中的網域。 如需詳細資訊，請參閱[本章節](../../delivery/using/technical-recommendations.md#dkim)。

### 互動式電子郵件設計

互動式設計可確保電子郵件能夠針對開啟裝置以最佳方式呈現。

* 使用互動式電子郵件HTML，而非網頁HTML

* 使用預覽模式並傳送校樣，以盡可能多的裝置來測試演算效果

* Adobe Campaign Classic數位內容編輯器(DCE)模組包含一些互動式設計格式範本，適用於行動裝置，可透過 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** >取得 **[!UICONTROL Content templates]**。 在本文中 [進一步瞭解](https://theblog.adobe.com/responsive-email-design-101/)

## 管理影像 {#manage-images}

使用影像時，請遵循以下准則。

### 防止影像封鎖

有些電子郵件用戶端依預設會封鎖影像，而有些使用者會變更其設定來封鎖影像，以儲存資料使用情況。 因此，如果不下載影像，則會丟失整個消息。 若要避免此情況：

* 在內容與影像和文字之間取得平衡。 避免完全以影像為基礎的電子郵件。

* 如果文字必須包含在影像中，請使用alt和title文字，以確保訊息傳達完畢。 設定替代／標題文字的樣式以改善其外觀。

* 避免使用背景影像，因為有些電子郵件客戶不支援這些影像。

### 讓影像互動

嘗試讓影像回應速度快且可調整大小。 請注意，由於建置時間較長，這可能會造成成本影響。

### 使用絕對影像參照

若要從外部存取，連結至促銷活動的電子郵件和公共資源中使用的影像必須存在於外部存取的伺服器上。

* 您可以檢查實例配置是否啟用公共資源管理。 [進一步瞭解](../../installation/using/deploying-an-instance.md#managing-public-resources)

* 從傳送精靈中，您可以匯入包含影像的HTML頁面，或透過圖示直接使用HTML編輯器插入 **[!UICONTROL Image]** 影像。 [進一步瞭解](../../delivery/using/defining-the-email-content.md#adding-images)

* 如果未顯示影像，請檢查伺服器上是否有影像。 若要這麼做，請按一下傳送中的「來源」標籤。 在網頁瀏覽器中尋找您的影像並複製並貼上每個影像的URL。 如果未顯示影像，請連絡您的IT管理員或提供傳送內容的協力廠商。

## 預覽您的訊息 {#preview-msg}

Adobe建議預覽您的訊息，以檢查其個人化，以及收件者如何看到您的傳送。

* 在傳送捲軸中，子標 **[!UICONTROL Preview]** 簽可讓您檢視收件者每個內容的轉譯。 個性化欄位和內容的條件元素被所選配置檔案的相應資訊替換。 [進一步瞭解](../../delivery/using/defining-the-email-content.md#message-content)

* 每次預覽期間會執行自動反垃圾郵件檢查。 在子標 **[!UICONTROL Preview]** 簽中，檢查 [SpamAssassin](../../delivery/using/spamassassin.md) spam計分。  按一 **[!UICONTROL More...]** 下以進一步瞭解警告。  在這麼做之前，請確定SpamAssassin已正確安裝並設定在Adobe Campaign應用程式伺服器上。 [進一步瞭解](../../installation/using/configuring-spamassassin.md)
