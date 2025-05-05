---
product: campaign
title: 關於Adobe Campaign Classic中的傳遞能力
description: 進一步瞭解如何在Adobe Campaign中管理傳遞能力
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Deliverability
role: User
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: aa78a51ebea49f98ef7edad7e87a99a680f02b69
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 6%

---

# 控制您的訊息內容{#control-message-content}

為確保您的電子郵件能送達收件者並提高電子郵件傳遞率，他們必須遵守許多規則。 否則，某些訊息的內容可能會偵測為垃圾訊息。 Adobe Campaign提供數種工具，可讓您的內容符合這些規則。

設計訊息內容時，請遵循下列原則：

* [寄件者地址](#sender-address)：此地址必須明確識別寄件者。 網域必須由寄件者擁有並註冊給寄件者。 網域登入不可為私用。
* [Personalization](#personalization)：個人化內容並定義每位收件者的傳送時間，會增加您開啟郵件的機會。
* 影像和文字：遵循像面文字/影像比例（例如60%文字和40%影像）。
* [取消訂閱連結](#opt-out)和登陸頁面：取消訂閱連結是必要的。 它必須可見且有效，而且表單必須有效。
* 預覽：使用Adobe Campaign提供的工具來檢查並最佳化您的電子郵件內容（[收件匣轉譯](#message-responsiveness)，[SpamAssassin](#spamassassin)）。

如需在設計內容時最佳化傳遞能力的其他秘訣，請參閱[Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html?lang=zh-Hant)。

>[!NOTE]
>
>如需編輯電子郵件內容的詳細資訊，請參閱[定義電子郵件內容](defining-the-email-content.md)。

## 寄件者地址 {#sender-address}

某些ISP在接受訊息之前會檢查寄件者地址(**[!UICONTROL From]**)的有效性。 格式錯誤的位址可能會導致接收伺服器拒絕該位址。

您必須確定在執行個體層級（功能表&#x200B;**[!UICONTROL Tools > Advanced > deployment wizard...]**）或最常使用的案例中指定了正確的地址。

如需詳細資訊，請參閱[此頁面](defining-the-email-content.md)。

## 個人化 {#personalization}

為了改善收件者的體驗並讓他們開啟您的電子郵件，Adobe Campaign可讓您個人化您的訊息。

如需在Adobe Campaign中使用個人化欄位的詳細資訊，請參閱[本節](personalization-fields.md)。

## 選擇退出連結和表單 {#opt-out}

依預設，分析訊息時，[型別規則](steps-validating-the-delivery.md#validation-process-with-typologies)會檢查是否包含選擇退出連結，如果缺少該連結，則會產生警告。 您可以變更此規則，以引發錯誤（而非簡單的警告），並阻止傳送在沒有此連結的情況下傳出。

每次傳送前，您必須先檢查選擇退出連結是否正常運作。 例如，傳送校樣時，請確定連結有效、表單線上上，且驗證後會將&#x200B;**[!UICONTROL No longer contact this recipient]**&#x200B;欄位的值變更為&#x200B;**[!UICONTROL Yes]**。 您應該系統地進行此檢查，因為輸入連結或變更表單時總是可能發生人為錯誤。

瞭解如何在本節[&#128279;](personalization-blocks.md#personalization-blocks-example)中插入選擇退出連結。

如果在開始傳遞後偵測到有關取消訂閱的問題，則仍可以為按一下選擇退出連結的收件者手動執行取消訂閱（例如使用大量更新函式），即使他們無法確認自己的選擇。

一般而言，請勿透過要求收件者填寫電子郵件地址或名稱等欄位，來妨礙想要選擇退出的收件者。 表單應只有一個驗證按鈕，並且只應對加密的識別碼執行調解。

要求額外確認並不可靠：使用者可能有兩個電子郵件地址會重新導向至同一個方塊(例如：firstname.lastname@club.com和firstname.lastname@internet-club.com)。 如果收件者僅能記住第一個地址，並想要透過傳送給另一個地址的訊息取消訂閱，則表單將拒絕此操作，因為加密的識別碼和輸入的電子郵件地址不相符。

## 收件匣轉譯 {#message-responsiveness}

在傳送訊息之前，您可以檢查訊息在不同裝置上的外觀，以測試訊息回應能力。 這是為了確保以最佳方式顯示在各種Web使用者端、網頁郵件與裝置上。

為了執行此操作，Adobe Campaign 會擷取呈現，並將之用於專用報告中。這可讓您在可接收訊息的不同內容中預覽所傳送的訊息。

如需詳細資訊，請參閱[收件匣轉譯](inbox-rendering.md)。

## SpamAssassin {#spamassassin}

Adobe Campaign可設定為搭配SpamAssassin使用。 這使得對電子郵件進行評分成為可能，以確定郵件在接收時被反垃圾郵件工具視為垃圾郵件的風險是否存在。

在開始傳遞之前，**[!UICONTROL Preview]**&#x200B;索引標籤可讓您評估風險。 警告訊息會提供測試的結果。

在此[節](spamassassin.md)中瞭解更多。
