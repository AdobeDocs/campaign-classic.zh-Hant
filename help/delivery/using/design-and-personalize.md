---
product: campaign
title: 建置個人化內容
audience: delivery
feature: Email Design
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 6%

---

# 建置個人化內容 {#build-personalized-content}

![](../../assets/common.svg)

設計郵件內容時，請盡量避免可能阻止您執行傳遞的常見問題。 大多數時候，可能的錯誤都與 [個性化](about-personalization.md)。 [格式](defining-the-email-content.md#message-content) 和 [影像](defining-the-email-content.md#adding-images)。

## 優化個性化 {#optimize-personalization}

為避免可能阻止您執行傳遞並改善收件人體驗的常見問題，Adobe Campaign允許您個性化您的郵件。

您可以使用儲存在Adobe Campaign資料庫中的收件人資料，或通過跟蹤、登錄頁、訂閱等方式收集。
在中介紹個性化基礎 [此部分](personalization-fields.md)。

確保您的郵件內容設計正確，以避免任何與個性化設定通常相關的錯誤。

**提示**:在來自第三方供應商提供的外部檔案的個性化欄位中，外部HTML內容可能錯誤。 要避免這種情況，請檢查語法、使用標籤、字元等。 例如，Adobe Campaign個性化標籤始終具有以下格式：&lt;%=table.field%>。 如需詳細資訊，請參閱[本節](about-personalization.md)。

在個性化塊中不正確使用參數可能是一個問題。 例如，JavaScript中的變數應按如下方式使用：

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

有關個性化塊的詳細資訊，請參閱 [此部分](personalization-blocks.md)。

您可以在工作流中準備個性化資料以改進交付準備分析。 如果個性化資料通過聯合資料存取(FDA)從外部表中來，則應特別使用。 此選項在此中介紹 [此部分](personalization-fields.md#optimizing-personalization)

## 構建優化內容 {#optimize-content}

在生成電子郵件時，請牢記以下一般最佳做法。

* 保持設計簡單

* 記住移動用戶

* 避免完全基於影像的電子郵件

* 使用電子郵件安全字型

* 編碼特殊字元

### 主題行

工作 [主題行](defining-the-email-content.md#message-content) 要提高開放率：

* 避免過長的主題。 最多使用50個字元

* 避免重複使用諸如「免費」或「優惠」等可視為垃圾郵件的詞

* 避免大寫字母和特殊字元，如&quot;!&quot;、&quot;£&quot;、&quot;€&quot;、&quot;$&quot;

### 「鏡像」頁

始終包括鏡像頁面連結。 首選位置是電子郵件的頂部。 [了解更多](sending-messages.md#generating-the-mirror-page)

### 取消訂閱連結

取消訂閱連結至關重要。 它必須可見且有效，並且表單必須有效。 預設情況下，分析消息時， [類型規則](steps-validating-the-delivery.md#validation-process-with-typologies) 檢查是否包括了opt-out連結，如果缺少，則生成警告。

**提示**:由於人為錯誤總是可能發生，因此在每次發送之前，請檢查「opt-out（選擇退出）」連結是否工作正常。 例如，在發送證明時，請確保連結有效，表單聯機，並且「不再聯繫此收件人」欄位更改為「是」。

瞭解如何插入選擇退出連結 [此部分](personalization-blocks.md#personalization-blocks-example)。

### 電子郵件大小

為避免效能或可交付性問題，建議的電子郵件最大大小約為 **35KB**。 要檢查郵件大小，請轉到 **[!UICONTROL Preview]** 的子菜單。 生成後，消息大小將顯示在右上角。

要限制電子郵件，請考慮以下事項：

* 刪除冗餘或未使用的樣式

* 將一些電子郵件內容移動到登錄頁

* 精簡代碼

確保在最終發送之前test任何更改

### SMS長度

根據預設，SMS 中的字元數量符合 GSM（行動通訊全球系統）標準。使用 GSM 編碼的 SMS 訊息最多只能有 160 個字元，若是以多個部分傳送的訊息，則每個 SMS 的 SMS 訊息最多只能有 153 個字元。

音譯包括當 GSM 標準未考慮到 SMS 的一個字元時，用另一個字元取代該字元。請注意，將個性化欄位插入SMS消息的內容可能會引入GSM編碼未考慮的字元。 您可以通過選中相應的SMPP通道設定頁籤中的相應框來授權字元音譯 **[!UICONTROL External account]**。
瞭解更多資訊 [此部分](sms-set-up.md#creating-an-smpp-external-account)。

**提示**:

* 要保留SMS消息中的所有字元，例如，要不更改正確的名稱，請不要啟用音譯。

* 但是，如果您的SMS消息包含許多GSM標準未考慮的字元，則啟用音譯功能可限制發送消息的成本。

瞭解更多資訊 [此部分](sms-set-up.md#about-character-transliteration)。

## 處理格式 {#formatting}

要避免常見格式錯誤，請檢查以下元素：

* 正確 **日期格式**:Adobe Campaign為JavaScript模板和XSL樣式表提供日期格式函式。 [了解更多](formatting.md#date-display)

* 使用 **授權字元** 在電子郵件中：電子郵件地址的有效字元清單在「XtkEmail_Characters」選項中定義。 瞭解如何訪問市場活動選項 [此部分](../../installation/using/configuring-campaign-options.md)。 要正確處理特殊字元，需要以Unicode安裝Adobe Campaign。

* 配置 **電子郵件身份驗證**:確保電子郵件頭包含DKIM簽名。 DKIM（域密鑰標識郵件）驗證允許接收電子郵件伺服器驗證消息確實是由其聲稱其已發送的個人或實體發送的，以及消息內容是否在最初發送（和DKIM「簽名」）和接收時間之間發生了更改。 此標準通常使用「發件人」或「發件人」標題中的域。 有關詳細資訊，請參閱 [Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

### 響應性電子郵件設計

響應性設計確保電子郵件對開啟該電子郵件的設備進行最佳呈現。

* 使用響應性電子郵件HTML，而不是WebHTML

* 使用預覽模式併發送校樣以在盡可能多的設備上test渲染

* Adobe Campaign Classic數字內容編輯器(DCE)模組包括一些響應性設計格式模板，可通過 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**。 瞭解更多資訊 [本文](https://theblog.adobe.com/responsive-email-design-101/)

## 管理映像 {#manage-images}

使用影像時，請遵循以下指導原則。

### 防止影像阻塞

預設情況下，某些電子郵件客戶端會阻止影像，而一些用戶會更改其設定以阻止影像以保存資料使用情況。 因此，如果不下載影像，則整個消息可能丟失。 為避免這種情況：

* 將內容與影像和文本平衡。 避免完全基於影像的電子郵件。

* 如果文本必須包含在影像中，請使用Alt和標題文本來確保您的消息傳遞。 設定替換/標題文本的樣式以改進其外觀。

* 避免使用背景影像，因為某些電子郵件客戶端不支援這些影像。

### 使影像響應

嘗試使影像響應並可調整大小。 請注意，這可能會帶來成本影響，因為需要較長的構建時間。

### 使用絕對影像參照

要從外部訪問，與市場活動連結的電子郵件和公共資源中使用的影像必須存在於外部可訪問的伺服器上。

* 您可以檢查實例配置是否啟用公共資源管理。 [了解更多](../../installation/using/deploying-an-instance.md#managing-public-resources)

* 從傳遞嚮導中，您可以導入包含影像的HTML頁，或直接使用HTML編輯器通過 **[!UICONTROL Image]** 表徵圖 [了解更多](defining-the-email-content.md#adding-images)

* 如果未顯示影像，請檢查該影像是否在伺服器上可用。 要執行此操作，請按一下交貨中的「源」頁籤。 在Web瀏覽器中查找影像並複製貼上每個影像的URL。 如果未顯示影像，請與IT管理員或提供交付內容的第三方供應商聯繫。

## 預覽您的郵件 {#preview-msg}

Adobe建議預覽您的郵件以檢查其個性化以及您的收件人將如何查看您的遞送。

* 在傳遞嚮導中， **[!UICONTROL Preview]** 子頁籤用於查看收件人的每個內容的呈現。 將個性化欄位和內容的條件元素替換為所選簡檔的相應資訊。 [了解更多](defining-the-email-content.md#message-content)

* 在每次預覽期間執行自動反垃圾郵件檢查。 在 **[!UICONTROL Preview]** 頁籤，選中 [垃圾郵件刺客](spamassassin.md) 垃圾郵件評分。  按一下 **[!UICONTROL More...]** 來瞭解有關警告的更多資訊。  在執行此操作之前，請確保在Adobe Campaign應用程式伺服器上正確安裝和配置了SpamAssassin。 [了解更多](../../installation/using/configuring-spamassassin.md)
