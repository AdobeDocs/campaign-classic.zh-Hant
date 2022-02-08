---
product: campaign
title: 關於Adobe Campaign Classic的可交付性
description: 瞭解有關在Adobe Campaign管理可交付性的更多資訊
feature: Deliverability
exl-id: dcd3a9f9-5fe9-4c28-a4a5-5aed67b036ab
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 5%

---

# 控制您的消息內容{#control-message-content}

![](../../assets/common.svg)

為了確保您的電子郵件到達您的收件人並提高您的電子郵件傳送率，他們必須遵守許多規則。 否則，某些消息的內容可以被檢測為垃圾郵件。 Adobe Campaign為您提供了多種工具，使您的內容符合這些規則。

在設計消息內容時，請遵循以下原則：

* [發件人地址](#sender-address):地址必須明確地標識發件人。 域必須由發件人擁有並註冊。 不能對域註冊進行私有化。
* [個性化](#personalization):個性化內容並定義每個收件人的發送時間會增加您的郵件開啟的機會。
* 影像和文本：尊重適當的文本/影像比率（例如60%的文本和40%的影像）。
* [取消訂閱連結](#opt-out) 和登錄頁：取消訂閱連結是必要的。 它必須可見且有效，並且表單必須有效。
* 預覽：使用Adobe Campaign提供的工具檢查和優化您的電子郵件內容([收件箱呈現](#message-responsiveness)。 [垃圾郵件刺客](#spamassassin))。

有關在設計內容時優化可交付性的其他提示，請參見 [Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/content-best-practices-for-optimal-delivery.html)。

>[!NOTE]
>
>有關編輯電子郵件內容的詳細資訊，請參閱 [定義電子郵件內容](defining-the-email-content.md) 和 [構建個性化內容](design-and-personalize.md)。

## 發件人地址 {#sender-address}

某些ISP檢查發送者地址的有效性(**[!UICONTROL From]**)，然後接受消息。 格式錯誤的地址可能導致接收伺服器拒絕它。

您必須確保在實例級別（菜單）提供正確的地址 **[!UICONTROL Tools > Advanced > Deployment wizard...]**)或最常使用的情形。

如需詳細資訊，請參閱[此頁面](defining-the-email-content.md)。

## 個人化 {#personalization}

為了改善收件人的體驗並讓他們開啟您的電子郵件，Adobe Campaign使您能夠個性化您的郵件。

有關在Adobe Campaign使用個性化欄位的詳細資訊，請參見 [此部分](personalization-fields.md)。

在中提供了構建內容時優化個性化的一些提示 [此部分](design-and-personalize.md#optimize-personalization)。

## 選擇退出連結和窗體 {#opt-out}

預設情況下，分析消息時， [類型規則](steps-validating-the-delivery.md#validation-process-with-typologies) 檢查是否包括了opt-out連結，如果缺少，則生成警告。 您可以更改此規則，以便引發錯誤，而不是簡單的警告，並阻止沒有此連結的傳送退出。

每次發送前，必須檢查選擇退出連結是否正常工作。 例如，在發送證明時，請確保連結有效，表單處於聯機狀態，並且驗證此項會更改 **[!UICONTROL No longer contact this recipient]** 欄位 **[!UICONTROL Yes]**。 您應系統地進行此檢查，因為在輸入連結或更改表單時始終可能出現人為錯誤。

瞭解如何插入選擇退出連結 [此部分](personalization-blocks.md#personalization-blocks-example)。

如果在交貨啟動後檢測到與取消訂閱有關的問題，則仍然可以為那些按一下選擇退出連結的收件人手動執行取消訂閱（例如，使用成批更新功能），即使他們無法確認其選擇。

一般來說，不要通過要求收件人填寫電子郵件地址或姓名等欄位來妨礙希望退出的收件人。 表單應僅具有一個驗證按鈕，並且應僅對加密標識符執行協調。

請求其他確認不可靠：用戶可能有兩個重定向到同一框的電子郵件地址(例如：firstname.lastname@club.com和firstname.lastname@internet-club.com)。 如果收件人只能記住第一個地址並希望通過發送到另一個地址的消息取消訂閱，則表單將拒絕此操作，因為加密標識符與輸入的電子郵件地址不匹配。

## 收件匣轉譯 {#message-responsiveness}

在發送郵件之前，您可以通過檢查不同設備上的郵件外觀來test郵件響應。 這是為了確保它以最佳方式顯示在各種Web客戶端、 Web郵件和設備上。

為了執行此操作，Adobe Campaign 會擷取呈現，並將之用於專用報告中。這可讓您在可接收訊息的不同內容中預覽所傳送的訊息。

有關此的詳細資訊，請參閱 [收件箱呈現](inbox-rendering.md)。

## SpamAssassin {#spamassassin}

Adobe Campaign可配置為與SpamAssassin配合使用。 這使得對電子郵件進行評分以確定郵件是否存在被接收時使用的反垃圾郵件工具視為垃圾郵件的風險。

在開始交貨前， **[!UICONTROL Preview]** 頁籤。 警告消息將給出test的結果。

瞭解更多資訊 [節](spamassassin.md)。
