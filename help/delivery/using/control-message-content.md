---
solution: Campaign Classic
product: campaign
title: 論Adobe Campaign Classic的傳遞能力
description: 進一步瞭解如何管理Adobe Campaign Classic的傳遞能力。
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: d6a581ae86e50c17ac20fe54baf305b864e11790
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 4%

---


# 控制您的消息內容{#control-message-content}

為了確保您的電子郵件送達您的收件人並改善電子郵件的傳遞率，他們必須遵守許多規則。 否則，某些消息的內容可能被檢測為垃圾郵件。 Adobe Campaign提供數種工具，讓您的內容符合這些規則。

在設計您的訊息內容時，請遵循下列原則：

* [發件人地址](#sender-address):地址必須明確識別發件人。網域必須由傳送者擁有並註冊。 域註冊不得私有化。
* [個人化](#personalization):個人化內容並定義每位收件者的傳送時間，會增加您的訊息開啟的機率。
* 影像和文字：尊重適當的文字／影像比例（例如60%的文字和40%的影像）。
* [取消訂](#opt-out) 閱連結和登陸頁面：取消訂閱連結是必備的。它必須可見且有效，而且表單必須正常運作。
* 預覽：使用Adobe Campaign提供的工具檢查並最佳化您的電子郵件內容（[收件箱轉換](#message-responsiveness)、[SpamAssassin](#spamassassin)）。

如需在設計內容時最佳化傳送能力的其他秘訣，請參閱[Adobe傳送能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html)。

>[!NOTE]
>
>如需編輯電子郵件內容的詳細資訊，請參閱[定義電子郵件內容](../../delivery/using/defining-the-email-content.md)和[建立個人化內容](../../delivery/using/design-and-personalize.md)。

## 發件人地址{#sender-address}

某些ISP在接受消息之前檢查發件人地址(**[!UICONTROL From]**)的有效性。 錯誤形成的地址可能導致接收伺服器拒絕。

您必須確保在實例級別（菜單&#x200B;**[!UICONTROL Tools > Advanced > Deployment wizard...]**）或最常用的情況下提供正確的地址。

有關詳細資訊，請參閱[定義發送者](../../delivery/using/defining-the-email-content.md)。

## 個人化{#personalization}

為了改善收件者的體驗，並讓他們開啟您的電子郵件，Adobe Campaign讓您個人化您的訊息。

有關在Adobe Campaign使用個人化欄位的詳細資訊，請參閱[本節](../../delivery/using/personalization-fields.md)。

建立內容時最佳化個人化的一些秘訣會顯示在[本節](../../delivery/using/design-and-personalize.md#optimize-personalization)中。

## 退出連結並表單{#opt-out}

依預設，在分析訊息時，[排版規則](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)會檢查是否已包含選擇退出連結，並在遺失時產生警告。 您可以變更此規則，以產生錯誤而非簡單警告，並停止傳送離開此連結。

您必須在每次傳送前檢查退出連結是否正常運作。 例如，傳送校樣時，請確定連結有效、表單是線上，且驗證此表格會將&#x200B;**[!UICONTROL No longer contact this recipient]**&#x200B;欄位的值變更為&#x200B;**[!UICONTROL Yes]**。 您應該系統性地進行此檢查，因為在進入連結或更改表單時，總是可能出現人為錯誤。

瞭解如何在本節](../../delivery/using/personalization-blocks.md#personalization-blocks-example)中插入退出連結[。

如果在傳送開始後偵測到有關取消訂閱的問題，則仍可以手動（例如使用大量更新功能）對點按選擇退出連結的收件者執行取消訂閱，即使他們無法確認其選擇。

一般而言，請勿嘗試透過要求收件者填寫電子郵件地址或姓名等欄位，來妨礙想要退出的收件者。 表單應僅包含一個驗證按鈕，且僅應對加密的識別碼執行協調。

要求額外確認是不可靠的：使用者可能有兩個電子郵件地址被重新導向至相同方塊(例如：firstname.lastname@club.com和firstname.lastname@internet-club.com)。 如果收件者只能記住第一個位址，並希望透過傳送給另一個位址的訊息取消訂閱，表單將會拒絕訂閱，因為加密的識別碼與輸入的電子郵件地址不符。

## 收件匣轉譯 {#message-responsiveness}

在傳送訊息之前，您可以檢查訊息在不同裝置上的外觀，以測試訊息回應速度。 這是為了確保它以最佳方式顯示在各種Web用戶端、Web郵件和裝置上。

為了執行此操作，Adobe Campaign 會擷取呈現，並將之用於專用報告中。這可讓您在可接收訊息的不同內容中預覽所傳送的訊息。

有關詳細資訊，請參閱[收件箱轉換](../../delivery/using/inbox-rendering.md)。

## SpamAssassin {#spamassassin}

Adobe Campaign可以配置為與SpamAssassin搭配使用。 這樣，可以對電子郵件進行分數，以確定郵件是否存在被接收時使用的反垃圾郵件工具視為垃圾郵件的風險。

在開始傳送之前，**[!UICONTROL Preview]**&#x200B;標籤可讓您評估風險。 警告訊息會顯示測試結果。

請參閱[一節](../../delivery/using/spamassassin.md)瞭解更多資訊。