---
product: campaign
title: 建置個人化內容
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 6%

---

# 建置個人化內容 {#build-personalized-content}

![](../../assets/common.svg)

在設計訊息內容時，請嘗試避免可能妨礙您執行傳送的常見問題。 大多數情況下，可能的錯誤都與[personalization](about-personalization.md)、[formatting](defining-the-email-content.md#message-content)和[images](defining-the-email-content.md#adding-images)有關。

## 最佳化個人化 {#optimize-personalization}

為避免執行傳遞作業無法解決的常見問題，並改善收件者的使用體驗，Adobe Campaign可讓您個人化訊息。

您可以使用儲存在Adobe Campaign資料庫中的收件者資料，或透過追蹤、登錄頁面、訂閱等方式收集。
個人化基本介紹在[此區段](personalization-fields.md)中。

請確定您的訊息內容已正確設計，以避免任何與個人化一般相關的錯誤。

**提示**:在來自協力廠商提供之外部檔案的個人化欄位中，外部HTML內容可能會錯誤。若要避免此情況，請檢查語法、使用標籤、字元等。 例如，Adobe Campaign個人化標籤一律具有下列格式：&lt;%=table.field%>。 如需詳細資訊，請參閱[本節](about-personalization.md)。

在個人化區塊中錯誤使用參數可能是問題。 例如，JavaScript中的變數使用方式如下：

    &lt;>var brand = &quot;xxx&quot;
    
    %>

    
    
有關個人化區塊的詳細資訊，請參閱[此區段](personalization-blocks.md)。

您可以在工作流程中準備個人化資料，以改善傳遞準備分析。 如果個人化資料來自透過同盟資料存取(FDA)的外部表格，則應特別使用此功能。 此[此部分](personalization-fields.md#optimizing-personalization)中介紹了此選項

## 建立最佳化內容 {#optimize-content}

建置電子郵件時，請牢記下列一般最佳實務。

* 保持設計簡單

* 請牢記行動使用者

* 避免完全以影像為基礎的電子郵件

* 使用電子郵件安全字型

* 為特殊字元編碼

### 主旨行

在[主旨行](defining-the-email-content.md#message-content)上工作以改善開放率：

* 避開過長的科目。 最多使用50個字元

* 請避免重複使用「free」或「offer」等可視為垃圾訊息的單字

* 避免大寫字母和特殊字元，如「！」、「£」、「€」、「$」

### 鏡像頁面

一律包含鏡像頁面連結。 偏好位置是電子郵件的頂端。 [深入瞭解](sending-messages.md#generating-the-mirror-page)

### 取消訂閱連結

取消訂閱連結至關重要。 表單必須可見且有效，且必須可運作。 依預設，分析訊息時，[類型規則](steps-validating-the-delivery.md#validation-process-with-typologies)會檢查是否已包含選擇退出連結，並在遺失時產生警告。

**提示**:因為一律可能發生人為錯誤，請在每次傳送前檢查選擇退出連結是否正常運作。例如，傳送校樣時，請確定連結有效、表單已上線，且「不再與此收件者聯絡」欄位已變更為「是」。

了解如何在此小節](personalization-blocks.md#personalization-blocks-example)插入選擇退出連結[。

### 電子郵件大小

為避免效能或傳遞能力問題，建議的電子郵件大小上限為&#x200B;**35KB**。 若要檢查訊息大小，請前往&#x200B;**[!UICONTROL Preview]**&#x200B;標籤並選擇測試設定檔。 產生後，訊息大小會顯示在右上角。

若要限制電子郵件，請考慮下列事項：

* 移除冗餘或未使用的樣式

* 將部分電子郵件內容移至登錄頁面

* 縮小程式碼

請務必在最終傳送前測試任何變更

### SMS長度

根據預設，SMS 中的字元數量符合 GSM（行動通訊全球系統）標準。使用 GSM 編碼的 SMS 訊息最多只能有 160 個字元，若是以多個部分傳送的訊息，則每個 SMS 的 SMS 訊息最多只能有 153 個字元。

音譯包括當 GSM 標準未考慮到 SMS 的一個字元時，用另一個字元取代該字元。請注意，將個人化欄位插入SMS訊息的內容，可能會引入GSM編碼未考慮的字元。 您可以核取對應&#x200B;**[!UICONTROL External account]**之SMPP通道設定標籤中的對應方塊，以授權字母音譯。
了解更多[，請參閱本節](sms-set-up.md#creating-an-smpp-external-account)。

**提示**:

* 若要保留SMS訊息中的所有字元原樣，請勿變更正確名稱（例如），請勿啟用音譯。

* 不過，如果您的SMS訊息包含許多GSM標準未考慮的字元，請啟用音譯以限制傳送訊息的成本。

了解更多[，請參閱本節](sms-set-up.md#about-character-transliteration)。

## 處理格式設定 {#formatting}

若要避免常見的格式錯誤，請檢查下列元素：

* 更正&#x200B;**日期格式**:Adobe Campaign為JavaScript模板和XSL樣式表提供日期格式功能。 [深入瞭解](formatting.md#date-display)

* 電子郵件中&#x200B;**授權字元**&#x200B;的用法：電子郵件地址的有效字元清單在「XtkEmail_Characters」選項中定義。 了解如何存取本小節](../../installation/using/configuring-campaign-options.md)中的Campaign選項[。 若要正確處理特殊字元，必須以Unicode安裝Adobe Campaign。

* **電子郵件驗證**&#x200B;的配置：請確定電子郵件標題包含DKIM簽名。 DKIM（域密鑰已識別郵件）驗證允許接收電子郵件伺服器驗證郵件確實是由其聲稱由其發送的個人或實體發送的，以及郵件內容在最初發送時（和DKIM「簽名」）和接收時間之間是否發生了更改。 此標準通常使用寄件者或寄件者標題中的網域。 有關詳細資訊，請參閱[Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

### 回應式電子郵件設計

回應式設計可確保電子郵件在其開啟的裝置上以最佳方式呈現。

* 使用回應式電子郵件HTML而非網頁HTML

* 使用預覽模式並傳送校樣，盡可能在裝置上測試轉譯作業

* Adobe Campaign Classic數位內容編輯器(DCE)模組包含一些響應式設計格式化模板，可通過&#x200B;**[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**&#x200B;為移動設備提供。 了解更多[，請參閱本文](https://theblog.adobe.com/responsive-email-design-101/)

## 管理影像 {#manage-images}

使用影像時，請遵循下列准則。

### 防止影像阻塞

有些電子郵件用戶端預設會封鎖影像，有些使用者會變更其設定以封鎖影像，以便儲存資料使用情況。 因此，如果未下載影像，則會丟失整個消息。 若要避免此情況：

* 平衡內容與影像和文字。 避免完全以影像為基礎的電子郵件。

* 如果影像中必須包含文字，請使用alt和title文字，確保訊息傳達完畢。 設定替代/標題文字的樣式以改善其外觀。

* 避免使用某些電子郵件用戶端不支援的背景影像。

### 讓影像回應式

嘗試讓影像具有回應性和可調整大小。 請注意，這可能會造成成本影響，因為建置所需時間較長。

### 使用絕對影像參照

若要從外部存取，連結至促銷活動的電子郵件和公共資源中使用的影像必須存在於可外部存取的伺服器上。

* 您可以檢查實例配置是否啟用公共資源管理。 [深入瞭解](../../installation/using/deploying-an-instance.md#managing-public-resources)

* 從傳送精靈，您可以透過&#x200B;**[!UICONTROL Image]**&#x200B;圖示，使用HTML編輯器匯入包含影像的HTML頁面或直接插入影像。 [深入瞭解](defining-the-email-content.md#adding-images)

* 如果未顯示影像，請檢查伺服器上是否有影像。 若要這麼做，請按一下傳送中的「來源」標籤。 尋找您的影像，並在網頁瀏覽器中複製並貼上每個影像的URL。 如果未顯示影像，請連絡您的IT管理員或提供您傳送內容的協力廠商。

## 預覽訊息 {#preview-msg}

Adobe建議預覽您的訊息，以檢查其個人化以及收件者如何看到您的傳遞。

* 在傳遞精靈中，**[!UICONTROL Preview]**&#x200B;子標籤可讓您檢視收件者的每個內容呈現。 個人化欄位和內容的條件元素會取代為所選設定檔的對應資訊。 [深入瞭解](defining-the-email-content.md#message-content)

* 每次預覽時都會執行自動反垃圾郵件檢查。 在&#x200B;**[!UICONTROL Preview]**&#x200B;子標籤中，檢查[SpamAssassin](spamassassin.md)垃圾郵件分數。  按一下&#x200B;**[!UICONTROL More...]**&#x200B;以了解更多警告。  在執行此動作之前，請確定Adobe Campaign應用程式伺服器上已正確安裝及設定SpamAssassin。 [深入瞭解](../../installation/using/configuring-spamassassin.md)
