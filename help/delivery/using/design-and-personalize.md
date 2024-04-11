---
product: campaign
title: 建置個人化內容
description: 瞭解如何在Adobe Campaign傳遞中建立個人化內容
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Email Design, Personalization
role: User
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1293'
ht-degree: 4%

---

# 建置個人化內容 {#build-personalized-content}

在設計訊息內容時，請儘量避免可能會使您無法執行傳送的常見問題。 大多數時候，可能的錯誤是與 [個人化](about-personalization.md)， [格式化](defining-the-email-content.md#message-content) 和 [影像](defining-the-email-content.md#adding-images).

## 最佳化個人化 {#optimize-personalization}

為避免阻止您執行傳送的常見問題並改善收件者體驗，Adobe Campaign可讓您個人化您的訊息。

您可以使用儲存在Adobe Campaign資料庫中的收件者資料，或是透過追蹤、登陸頁面、訂閱等收集的資料。
中的個人化基本介紹 [本節](personalization-fields.md).

請確定您的訊息內容經過適當設計，以避免發生任何錯誤，這些錯誤通常與個人化有關。

**提示**：在來自協力廠商提供之外部檔案的個人化欄位中，外部HTML內容可能會錯誤。 要避免此問題，請檢查語法、標籤的使用和字元等。 例如，Adobe Campaign個人化標籤的格式一律如下： &lt;%=table.field%>。 如需詳細資訊，請參閱[本節](about-personalization.md)。

個人化區塊中引數的使用不正確可能是個問題。 例如，JavaScript中的變數使用方式如下：

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

如需個人化區塊的詳細資訊，請參閱 [本節](personalization-blocks.md).

您可以在工作流程中準備個人化資料，以改善傳送準備分析。 如果個人化資料來自透過同盟資料存取(FDA)的外部表格，則應特別使用此專案。 此選項的說明如下 [本節](personalization-fields.md#optimizing-personalization)

## 建置最佳化內容 {#optimize-content}

建立電子郵件時，請記住以下一般最佳實務。

* 讓設計保持簡單

* 將行動使用者牢記在心

* 避免完全以影像為基礎的電子郵件

* 使用電子郵件安全字型

* 編碼特殊字元

### 主旨列

處理 [主旨列](defining-the-email-content.md#message-content) 若要改善開啟率：

* 避免主題過長。 最多使用50個字元

* 避免使用重複性的字詞，例如「free」或「offer」，這些字詞可能會被視為垃圾訊息

* 避免使用大寫字母和「！」、「£」、「€」、「$」等特殊字元

### 鏡像頁面

一律包含映象頁面連結。 偏好位置是電子郵件的頂端。 [了解更多](sending-messages.md#generating-the-mirror-page)

### 取消訂閱連結

取消訂閱連結至關重要。 它必須可見且有效，而且表單必須有效。 依預設，分析訊息時， [型別規則](steps-validating-the-delivery.md#validation-process-with-typologies) 檢查是否包含退出連結，如果缺少該連結，則會產生警告。

**秘訣**：由於永遠可能發生人為錯誤，請在每次傳送前檢查選擇退出連結是否正確運作。 例如，傳送校樣時，請確定連結有效、表單線上上，且「不再聯絡此收件者」欄位已變更為「是」。

瞭解如何插入選擇退出連結 [在本節中](personalization-blocks.md#personalization-blocks-example).

### 電子郵件大小

為避免效能或傳遞能力問題，建議的最大電子郵件大小約為 **35KB**. 若要檢查郵件大小，請移至 **[!UICONTROL Preview]** 標籤並選擇測試設定檔。 產生後，訊息大小將顯示在右上角。

若要將您的電子郵件保持在限制以下，請考慮以下事項：

* 移除多餘或未使用的樣式

* 將部分電子郵件內容移至登陸頁面

* 將程式碼縮制

請務必在最終傳送前測試任何變更

### 簡訊長度

根據預設，SMS中的字元數量符合GSM（行動通訊全球系統）標準。 使用 GSM 編碼的簡訊訊息最多只能有 160 個字元，若是以多個部分傳送的訊息，則每個簡訊的簡訊訊息最多只能有 153 個字元。

音譯包括當GSM標準未考慮到SMS的一個字元時，用另一個字元取代該字元。 請注意，將個人化欄位插入您的SMS訊息內容，可能會引入GSM編碼未考慮的字元。 您可以核取對應方塊的SMPP管道設定索引標籤中的對應方塊，以授權字母音譯 **[!UICONTROL External account]**.
瞭解更多 [在本節中](sms-set-up.md#creating-an-smpp-external-account).

**提示**：

* 若要保留SMS訊息中的所有字元原樣，例如不要變更正確名稱，請勿啟用音譯。

* 不過，如果您的SMS訊息包含許多GSM標準未考慮的字元，請啟用音譯以限制傳送訊息的成本。

瞭解更多 [在本節中](sms-set-up.md#about-character-transliteration).

## 處理格式設定 {#formatting}

若要避免常見的格式錯誤，請核取下列元素：

* 正確 **日期格式**：Adobe Campaign提供JavaScript範本和XSL樣式表的日期格式功能。 [了解更多](formatting.md#date-display)

* 使用方式 **授權字元** 在電子郵件中：電子郵件地址的有效字元清單在「XtkEmail_Characters」選項中定義。 瞭解如何存取Campaign選項 [在本節中](../../installation/using/configuring-campaign-options.md). 若要正確處理特殊字元，Adobe Campaign必須安裝在Unicode中。

* 的設定 **電子郵件驗證**：請確定電子郵件標頭包含DKIM簽章。 DKIM （網域金鑰識別郵件）驗證可讓接收電子郵件伺服器驗證訊息是否確實是由其聲稱傳送訊息的個人或實體所傳送，以及訊息內容在最初傳送時間（和DKIM「簽署」）與接收時間之間是否有變更。 此標準通常使用寄件者或寄件者標題中的網域。 有關詳細資訊，請參閱 [Adobe傳遞性最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### 回應式電子郵件設計

回應式設計可確保電子郵件以最佳方式呈現開啟所在裝置的內容。

* 使用回應式電子郵件HTML，而不是網頁HTML

* 使用預覽模式和傳送校樣，以測試儘可能多的裝置上的轉譯

* Adobe Campaign Classic數位內容編輯器(DCE)模組包含一些回應式設計格式化行動範本，可透過以下方式取得： **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. 瞭解更多 [本文章](https://theblog.adobe.com/responsive-email-design-101/)

## 管理影像 {#manage-images}

使用影像時，請遵循下列准則。

### 避免影像封鎖

有些電子郵件使用者端依預設會封鎖影像，有些使用者則變更其設定以封鎖影像，以儲存資料使用量。 因此，如果未下載影像，可能會遺失整個訊息。 若要避免此情況：

* 平衡您的內容與影像與文字。 避免使用完全以影像為基礎的電子郵件。

* 如果文字必須包含在影像中，請使用替代文字和標題文字來確認訊息是否傳入。 設定替代/標題文字的樣式，以改善其外觀。

* 避免使用背景影像，因為有些電子郵件使用者端不支援這些影像。

### 讓影像回應

嘗試讓影像回應靈敏且可調整大小。 請注意，這可能會造成成本影響，因為建置時間較長。

### 使用絕對影像參照

若要從外部存取，連結至行銷活動的電子郵件和公共資源中所使用的影像，必須存在於外部可存取的伺服器上。

* 您可以檢查執行處理組態是否可啟用公用資源管理。 [了解更多](../../installation/using/deploying-an-instance.md#managing-public-resources)

* 從傳遞精靈中，您可以匯入包含影像的HTML頁面，或直接使用HTML編輯器透過插入影像 **[!UICONTROL Image]** 圖示。 [了解更多](defining-the-email-content.md#adding-images)

* 如果未顯示影像，請檢查伺服器上是否有這些影像。 若要這麼做，請按一下傳送中的「來源」標籤。 尋找您的影像，並在網頁瀏覽器中複製並貼上每個影像的URL。 如果未顯示影像，請聯絡您的IT管理員或提供傳送內容的協力廠商廠商。

## 預覽您的訊息 {#preview-msg}

Adobe建議預覽您的訊息，以檢查其個人化傾向以及收件者看到您傳遞內容的方式。

* 在傳遞精靈中， **[!UICONTROL Preview]** 子索引標籤可讓您檢視每個收件者的內容轉譯。 個人化欄位和內容的條件元素會取代為所選設定檔的對應資訊。 [了解更多](defining-the-email-content.md#message-content)

* 每次預覽期間都會執行自動反垃圾郵件檢查。 在 **[!UICONTROL Preview]** 子標籤，核取 [SpamAssassin](spamassassin.md) 垃圾郵件評分。  按一下 **[!UICONTROL More...]** 以進一步瞭解警告。  在執行此操作之前，請確定Adobe Campaign應用程式伺服器上已正確安裝和設定SpamAssassin。 [了解更多](../../installation/using/configuring-spamassassin.md)
