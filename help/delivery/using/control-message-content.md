---
product: campaign
title: 關於Adobe Campaign Classic中的傳遞能力
description: 進一步了解在Adobe Campaign Classic中管理傳遞能力。
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 4%

---

# 控制訊息內容{#control-message-content}

![](../../assets/common.svg)

為了確保您的電子郵件可送達您的收件者，並改善您的電子郵件傳遞率，他們必須遵守許多規則。 否則，某些消息的內容可能被檢測為垃圾郵件。 Adobe Campaign提供數種工具，讓您的內容符合這些規則。

設計訊息內容時，請遵循下列原則：

* [寄件者地址](#sender-address):地址必須明確標識發件人。網域必須屬於寄件者，並註冊給寄件者。 域註冊表不得私有化。
* [個人化](#personalization):個人化內容並定義每位收件者的傳送時間，可增加開啟訊息的機率。
* 影像和文字：請遵循適當的文字/影像比例（例如60%的文字和40%的影像）。
* [取消訂](#opt-out) 閱連結和登錄頁面：取消訂閱連結至關重要。表單必須可見且有效，且必須可運作。
* 預覽：使用Adobe Campaign提供的工具來檢查並最佳化電子郵件內容（[收件匣轉譯](#message-responsiveness)、[SpamAssassin](#spamassassin)）。

如需在設計內容時最佳化傳遞能力的其他秘訣，請參閱[Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html)。

>[!NOTE]
>
>如需編輯電子郵件內容的詳細資訊，請參閱「定義電子郵件內容」](defining-the-email-content.md)和「建立個人化內容」](design-and-personalize.md)。[[

## 寄件者地址 {#sender-address}

某些ISP在接受郵件之前檢查發件人地址(**[!UICONTROL From]**)的有效性。 錯誤形成的地址可能導致接收伺服器拒絕該地址。

您必須確保在執行個體層級（功能表&#x200B;**[!UICONTROL Tools > Advanced > Deployment wizard...]**）或最常使用的情況下提供正確的地址。

有關詳細資訊，請參閱[定義寄件者](defining-the-email-content.md)。

## 個人化 {#personalization}

為了改善收件者的體驗，並讓他們開啟您的電子郵件，Adobe Campaign可讓您個人化您的訊息。

如需在Adobe Campaign中使用個人化欄位的詳細資訊，請參閱[此區段](personalization-fields.md)。

在[此區段](design-and-personalize.md#optimize-personalization)中會顯示建立內容時最佳化個人化的一些秘訣。

## 退出連結和表單 {#opt-out}

依預設，分析訊息時，[類型規則](steps-validating-the-delivery.md#validation-process-with-typologies)會檢查是否已包含選擇退出連結，並在遺失時產生警告。 您可以變更此規則，以引發錯誤（而非簡單警告），並在沒有此連結的情況下停止傳送。

您必須在每次傳送前，檢查選擇退出連結是否正常運作。 例如，傳送校樣時，請確定連結有效、表單已上線且驗證會將&#x200B;**[!UICONTROL No longer contact this recipient]**&#x200B;欄位的值變更為&#x200B;**[!UICONTROL Yes]**。 您應系統地進行此檢查，因為在進入連結或更改表單時，始終可能出現人為錯誤。

了解如何在此小節](personalization-blocks.md#personalization-blocks-example)插入選擇退出連結[。

如果在傳送開始後偵測到有關取消訂閱的問題，則即使收件者無法確認其選擇，仍可手動執行取消訂閱（例如使用大量更新功能）。

一般而言，請勿嘗試讓想要退出的收件者填寫欄位（例如其電子郵件地址或名稱），以此方式來阻礙收件者。 表單應僅包含一個驗證按鈕，且調解應僅對加密識別碼執行。

請求附加確認是不可靠的：使用者可能有兩個電子郵件地址已重新導向至相同的方塊(例如：firstname.lastname@club.com和firstname.lastname@internet-club.com)。 如果收件者只能記住第一個地址，並希望通過發送到另一個地址的郵件取消訂閱，則表單將拒絕此項，因為加密的標識符與輸入的電子郵件地址不匹配。

## 收件匣轉譯 {#message-responsiveness}

在傳送訊息之前，您可以檢查訊息在不同裝置上的外觀，以測試訊息的回應速度。 這是為了確保以最佳方式顯示在各種Web用戶端、網頁郵件和裝置上。

為了執行此操作，Adobe Campaign 會擷取呈現，並將之用於專用報告中。這可讓您在可接收訊息的不同內容中預覽所傳送的訊息。

有關詳細資訊，請參閱[收件箱呈現](inbox-rendering.md)。

## SpamAssassin {#spamassassin}

Adobe Campaign可設定為與SpamAssassin搭配使用。 這樣就可以對電子郵件進行分數，以確定郵件是否存在被接收時使用的反垃圾郵件工具視為垃圾郵件的風險。

開始傳送前， **[!UICONTROL Preview]**&#x200B;標籤可讓您評估風險。 警告訊息會提供測試結果。

了解更多[小節](spamassassin.md)。
