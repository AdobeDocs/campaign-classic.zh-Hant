---
title: 跨通道傳遞
seo-title: 跨通道傳遞
description: 跨通道傳遞
seo-description: null
page-status-flag: never-activated
uuid: 191ff39e-f739-48b3-8865-ad1b641b7499
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 8dda45b4-4b5d-4b4e-a8b4-45d9bc49aaf3
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 8%

---


# 跨通道傳遞{#cross-channel-deliveries}

跨通道傳送可在促銷活動工作流程活 **[!UICONTROL Deliveries]** 動的標籤中使用。

它們可讓您建立特定通路的傳送。 您可以指定您要傳送的範本及其內容，其方式與傳統傳送精靈相同。

可用的各種渠道包括：

* [電子郵件](../../delivery/using/about-email-channel.md)
* [直接郵件](../../delivery/using/about-direct-mail-channel.md)
* [行動裝置](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md)
* [Facebook](../../social/using/publishing-on-facebook.md)
* [iOS](../../delivery/using/creating-notifications.md#sending-notifications-on-ios)
* [Android](../../delivery/using/creating-notifications.md#sending-notifications-on-android)

您可以使用不同的定位活動，在工作流程的上游指定傳送目標。

例如，我們將在此建立工作流程，以傳送電子郵件或SMS給推播通知訂閱者，然後在一週後傳送推播通知。 操作步驟：

1. 建立促銷活動.
1. 在促銷 **[!UICONTROL Targeting and workflows]** 活動的標籤中，新增至 **[!UICONTROL Query]** 您的工作流程。
1. 設定您的查詢。 例如，我們在此處選取訂閱推播通知的收件者作為目標維度。

   >[!NOTE]
   >
   >對於推播通知，請記得使用訂閱者應 **用程式** 目標維度。

   ![](assets/cross_channel_delivery_1.png)

1. 新增篩選條件至查詢。 在這種情況下，我們將選擇具有行動電話號碼或電子郵件地址的收件者。

   ![](assets/cross_channel_delivery_2.png)

1. 將活動 **[!UICONTROL Split]** 新增至您的工作流程，以劃分具有行動電話號碼的收件者和具有電子郵件地址的收件者。
1. 在標籤 **[!UICONTROL Delivery]** 中，選擇每個目標的傳送。

   在工作流程中按兩下傳送活動，以傳統傳送精靈的相同方式建立傳送。 如需關於此項目的詳細資訊，請參閱此[頁面](../../delivery/using/about-email-channel.md)。

   ![](assets/cross_channel_delivery_3.png)

1. 新增並設定活 **[!UICONTROL Wait]** 動，讓收件者一次不會收到太多傳送。
1. 新增活 **[!UICONTROL Split]** 動以劃分iOS或Android行動應用程式的訂閱者。

   為每個作業系統選擇服務。 For more on service creation, refer to this [page](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. 針對每個作業系統選擇並設定行動應用程式傳送。

   ![](assets/cross_channel_delivery_5.png)
