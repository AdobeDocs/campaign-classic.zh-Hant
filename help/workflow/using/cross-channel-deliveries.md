---
product: campaign
title: 跨頻道傳遞
description: 進一步瞭解跨頻道傳遞
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows, Channels Activity
exl-id: 3bb468e2-7bcf-456f-8d8f-1c4e608e2b25
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 10%

---

# 跨頻道傳遞{#cross-channel-deliveries}



跨頻道傳遞適用於 **[!UICONTROL Deliveries]** 行銷活動工作流程活動的標籤。

可用的各種管道包括：

* [電子郵件](../../delivery/using/about-email-channel.md)
* [直接郵件](../../delivery/using/about-direct-mail-channel.md)
* [行動裝置](../../delivery/using/sms-channel.md)
* [X (先前稱為Twitter)](../../social/using/about-social-marketing.md)
* [iOS](../../delivery/using/create-notifications-ios.md)
* [Android](../../delivery/using/create-notifications-android.md)

選取傳遞所依據的範本，並定義其內容。

您可以使用不同的目標定位活動，在工作流程上游指定傳送的目標。

在以下範例中，我們將建立工作流程以傳送電子郵件或簡訊給推播通知的訂閱者，然後在一週後傳送推播通知。 操作步驟：

1. 建立促銷活動.
1. 在 **[!UICONTROL Targeting and workflows]** 索引標籤中，新增 **[!UICONTROL Query]** 至您的工作流程。
1. 設定您的查詢。 例如，我們在這裡選取訂閱了推播通知的收件者作為目標維度。

   >[!NOTE]
   >
   >對於推播通知，請使用 **訂閱者應用程式** 目標維度。

   ![](assets/cross_channel_delivery_1.png)

1. 將篩選條件新增至查詢。 在此情況下，我們將選取擁有行動電話號碼或電子郵件地址的收件者。

   ![](assets/cross_channel_delivery_2.png)

1. 新增 **[!UICONTROL Split]** 活動至您的工作流程，以劃分擁有行動電話號碼的收件者和擁有電子郵件地址的收件者。
1. 在 **[!UICONTROL Delivery]** 索引標籤中，選取每個目標的傳送。

   按兩下工作流程中的傳送活動，以傳統傳送精靈的相同方式建立您的傳送。 如需關於此項目的詳細資訊，請參閱此[頁面](../../delivery/using/about-email-channel.md)。

   ![](assets/cross_channel_delivery_3.png)

1. 新增並設定 **[!UICONTROL Wait]** 活動，讓收件者無法一次收到太多傳遞。
1. 新增 **[!UICONTROL Split]** 劃分iOS或Android行動應用程式訂閱者的活動。

   選取每個作業系統的服務。 有關建立服務的詳細資訊，請參閱本節 [頁面](../../delivery/using/configuring-the-mobile-application.md).

   ![](assets/cross_channel_delivery_4.png)

1. 選取並設定每個作業系統的行動應用程式傳送。

   ![](assets/cross_channel_delivery_5.png)
