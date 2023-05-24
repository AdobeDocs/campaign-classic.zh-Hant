---
product: campaign
title: 關於Adobe Campaign Classic中的傳遞能力
description: 進一步瞭解如何在Adobe Campaign中管理傳遞能力
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 6%

---

# 控制您的訊息內容{#control-message-content}



為了確保您的電子郵件可送達收件者並提高您的電子郵件傳遞率，他們必須遵守許多規則。 否則，某些訊息的內容可能會被偵測為垃圾訊息。 Adobe Campaign提供數種工具，可讓您的內容符合這些規則。

設計訊息內容時，請遵循下列原則：

* [寄件者地址](#sender-address)：地址必須明確識別寄件者。 網域必須由寄件者擁有並註冊。 網域登入不得為私用。
* [個人化](#personalization)：個人化內容及定義每位收件者的傳送時間會增加您開啟訊息的機會。
* 影像和文字：遵循像面文字/影像比例（例如60%文字和40%影像）。
* [取消訂閱連結](#opt-out) 和登陸頁面：取消訂閱連結至為必要。 它必須是可見且有效的，而且表單必須是功能性的。
* 預覽：使用Adobe Campaign提供的工具來檢查並最佳化您的電子郵件內容([收件匣轉譯](#message-responsiveness)， [SpamAssassin](#spamassassin))。

如需在設計內容時最佳化傳遞能力的其他秘訣，請參閱 [Adobe傳遞性最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html).

>[!NOTE]
>
>如需編輯電子郵件內容的詳細資訊，請參閱 [定義電子郵件內容](defining-the-email-content.md) 和 [建置個人化內容](design-and-personalize.md).

## 寄件者地址 {#sender-address}

某些ISP會檢查寄件者地址的有效性(**[!UICONTROL From]**)，然後再接受訊息。 格式錯誤的地址可能導致接收伺服器拒絕該地址。

您必須確定執行個體層級（功能表）提供了正確的地址 **[!UICONTROL Tools > Advanced > Deployment wizard...]**)或在最常用的情況下。

如需詳細資訊，請參閱[此頁面](defining-the-email-content.md)。

## 個人化 {#personalization}

為了改善收件者的體驗並讓他們開啟您的電子郵件，Adobe Campaign可讓您個人化您的訊息。

如需在Adobe Campaign中使用個人化欄位的詳細資訊，請參閱 [本節](personalization-fields.md).

在建立內容時，提供一些最佳化個人化的秘訣 [本節](design-and-personalize.md#optimize-personalization).

## 選擇退出連結和表單 {#opt-out}

依預設，分析訊息時， [型別規則](steps-validating-the-delivery.md#validation-process-with-typologies) 檢查是否包含選擇退出連結，如果缺少則產生警告。 您可以變更此規則，以引發錯誤（而非簡單的警告），並阻止傳送在沒有此連結的情況下傳出。

每次傳送前，您必須先檢查選擇退出連結是否正常運作。 例如，傳送校樣時，請確定連結有效、表單線上上，且驗證這會變更 **[!UICONTROL No longer contact this recipient]** 欄位至 **[!UICONTROL Yes]**. 您應該系統地進行這項檢查，因為輸入連結或變更表單時總是可能發生人為錯誤。

瞭解如何插入選擇退出連結 [在本節中](personalization-blocks.md#personalization-blocks-example).

如果在開始傳遞後偵測到有關取消訂閱的問題，仍可以手動執行取消訂閱（例如使用大量更新功能），適用於按一下選擇退出連結的收件者，即使他們無法確認自己的選擇。

一般而言，請勿透過要求收件者填寫電子郵件地址或名稱等欄位，來妨礙想要選擇退出的收件者。 表單應只有一個驗證按鈕，並且只應對加密的識別碼執行調解。

要求額外確認並不可靠：使用者可能有兩個電子郵件地址被重新導向至相同的方塊(例如：firstname.lastname@club.com和firstname.lastname@internet-club.com)。 如果收件者只能記住第一個地址，並希望透過傳送給另一個地址的訊息取消訂閱，則表單將拒絕此操作，因為加密的識別碼和輸入的電子郵件地址不匹配。

## 收件匣轉譯 {#message-responsiveness}

在傳送訊息之前，您可以檢查訊息在不同裝置上的外觀，以測試訊息回應能力。 這是為了確保以最佳方式顯示在各種Web使用者端、網頁郵件和裝置上。

為了執行此操作，Adobe Campaign 會擷取呈現，並將之用於專用報告中。這可讓您在可接收訊息的不同內容中預覽所傳送的訊息。

如需詳細資訊，請參閱 [收件匣轉譯](inbox-rendering.md).

## SpamAssassin {#spamassassin}

Adobe Campaign可設定為搭配SpamAssassin使用。 這可讓您將電子郵件評分，以判斷郵件在收到時是否面臨被反垃圾郵件工具視為垃圾郵件的風險。

在開始傳送之前， **[!UICONTROL Preview]** 標籤可讓您評估風險。 警告訊息會提供測試結果。

在本節瞭解更多 [區段](spamassassin.md).
