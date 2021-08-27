---
product: campaign
title: 跨頻道傳遞
description: 進一步了解跨通道傳遞
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 8%

---

# 跨頻道傳遞{#cross-channel-deliveries}

![](../../assets/common.svg)

跨通道傳送可在促銷活動工作流程活動的&#x200B;**[!UICONTROL Deliveries]**&#x200B;標籤中使用。

可用的各種管道包括：

* [電子郵件](../../delivery/using/about-email-channel.md)
* [直接郵件](../../delivery/using/about-direct-mail-channel.md)
* [行動裝置](../../delivery/using/sms-channel.md)
* [Twitter](../../social/using/publishing-on-twitter.md) (僅限Campaign Classicv7)
* [Facebook](../../social/using/publishing-on-facebook.md) (僅限Campaign Classicv7)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

選取您要作為傳送基礎的範本，並定義其內容。

您可以使用不同的定位活動，為工作流程上游的傳送指定目標。

在以下範例中，我們將建立工作流程，在一週後傳送電子郵件或簡訊給推播通知訂閱者，然後傳送推播通知。 操作步驟：

1. 建立促銷活動.
1. 在促銷活動的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;標籤中，將&#x200B;**[!UICONTROL Query]**&#x200B;新增至工作流程。
1. 設定查詢。 例如，在此處，我們選取訂閱推播通知的收件者作為目標維度。

   >[!NOTE]
   >
   >對於推播通知，請使用&#x200B;**訂閱者應用程式**&#x200B;目標維度。

   ![](assets/cross_channel_delivery_1.png)

1. 將篩選條件新增至查詢。 在此情況下，我們將選取具有行動電話號碼或電子郵件地址的收件者。

   ![](assets/cross_channel_delivery_2.png)

1. 將&#x200B;**[!UICONTROL Split]**&#x200B;活動新增至您的工作流程，以劃分具有行動號碼的收件者和具有電子郵件地址的收件者。
1. 在&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤中，選取每個目標的傳送。

   在工作流程中按兩下傳送活動，以傳統傳送精靈的相同方式建立您的傳送。 如需關於此項目的詳細資訊，請參閱此[頁面](../../delivery/using/about-email-channel.md)。

   ![](assets/cross_channel_delivery_3.png)

1. 新增並設定&#x200B;**[!UICONTROL Wait]**&#x200B;活動，讓收件者不會一次收到太多傳送。
1. 新增&#x200B;**[!UICONTROL Split]**&#x200B;活動，以劃分iOS或Android行動應用程式的訂閱者。

   為每個作業系統選擇服務。 有關服務建立的詳細資訊，請參閱此[page](../../delivery/using/configuring-the-mobile-application.md)。

   ![](assets/cross_channel_delivery_4.png)

1. 為每個作業系統選取並設定行動應用程式傳送。

   ![](assets/cross_channel_delivery_5.png)
