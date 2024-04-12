---
product: campaign
title: 為Android裝置建立推播通知
description: 瞭解如何建立Android推播通知
feature: Push
role: User, Developer, Data Engineer
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# 建立Android通知{#create-notificaations-android}

使用Adobe Campaign在Android裝置上傳送推播通知。 有關傳遞建立的全域概念，請參見 [本節](steps-about-delivery-creation-steps.md).

從建立新傳遞開始。

![](assets/nmac_delivery_1.png)

使用Firebase Cloud Messaging時，您可以選擇兩種型別的訊息：

* **[!UICONTROL Data message]**，由使用者端應用程式處理。
  <br>訊息會直接傳送至行動應用程式，以產生Android通知並顯示至裝置。 資料訊息僅包含您的自訂應用程式變數。

* **[!UICONTROL Notification message]**，會由FCM SDK自動處理。
  <br> FCM會自動代表使用者端應用程式在使用者裝置上顯示訊息。 通知訊息包含預先定義的一組引數和選項，但仍可使用自訂應用程式變數進一步個人化。

如需有關Firebase Cloud Messaging訊息型別的詳細資訊，請參閱 [FCM檔案](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages){target="_blank"}.


## 建立資料訊息 {#creating-data-message}

1. 前往 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. 按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 選取 **[!UICONTROL Deliver on Android (android)]** 在 **[!UICONTROL Delivery template]** 下拉式清單。 新增 **[!UICONTROL Label]** 至您的傳遞。

1. 按一下 **[!UICONTROL To]** 以定義要定位的母體。 根據預設， **[!UICONTROL Subscriber application]** 目標對應已套用。 按一下 **[!UICONTROL Add]** 以選取您的服務。

   ![](assets/nmac_android_7.png)

1. 在 **[!UICONTROL Target type]** 視窗，選取 **[!UICONTROL Subscribers of an Android mobile application]** 並按一下 **[!UICONTROL Next]**.

1. 在 **[!UICONTROL Service]** 下拉式清單，選取您先前建立的服務，然後選取應用程式，再按一下 **[!UICONTROL Finish]**.
此 **[!UICONTROL Application variables]** 會根據設定步驟期間新增的內容自動新增。

   ![](assets/nmac_android_6.png)

1. 選取 **[!UICONTROL data message]** 作為 **[!UICONTROL Message Type]**.

1. 編輯您的豐富型通知。

   ![](assets/nmac_android_5.png)

1. 您可以在先前設定的中新增資訊 **[!UICONTROL Application variables]** 如有需要。 **[!UICONTROL Application variables]** 需要在Android服務中設定，且屬於傳送至行動裝置的訊息裝載的一部分。

1. 按一下 **[!UICONTROL Save]** 並傳送您的傳遞。

在訂閱者的行動Android裝置上接收時，影像和網頁應顯示在推播通知中。

![](assets/nmac_android_4.png)

## 建立通知訊息 {#creating-notification-message}

![](assets/do-not-localize/how-to-video.png) [瞭解如何在影片中建立Android推播通知](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html#additional-resources){target="_blank"}.

1. 前往 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

1. 按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 選取 **[!UICONTROL Deliver on Android (android)]** 在 **[!UICONTROL Delivery template]** 下拉式清單。 新增 **[!UICONTROL Label]** 至您的傳遞。

1. 按一下 **[!UICONTROL To]** 以定義要定位的母體。 根據預設， **[!UICONTROL Subscriber application]** 目標對應已套用。 按一下 **[!UICONTROL Add]** 以選取您的服務。

   ![](assets/nmac_android_7.png)

1. 在 **[!UICONTROL Target type]** 視窗，選取 **[!UICONTROL Subscribers of an Android mobile application]** 並按一下 **[!UICONTROL Next]**.

1. 在 **[!UICONTROL Service]** 下拉式清單，選取您先前建立的服務，然後選取應用程式，再按一下 **[!UICONTROL Finish]**.

   ![](assets/nmac_android_6.png)

1. 選取 **[!UICONTROL notification message]** 作為 **[!UICONTROL Message Type]**.

1. 新增標題並編輯您的訊息。 使用個人化推播通知 **[!UICONTROL Notification options]**：

   * **[!UICONTROL Channel ID]**：設定通知的頻道ID。 在收到具有此管道ID的任何通知之前，應用程式必須建立具有此管道ID的管道。
   * **[!UICONTROL Sound]**：設定裝置收到通知時播放的音效。
   * **[!UICONTROL Color]**：設定通知的圖示顏色。
   * **[!UICONTROL Icon]**：設定要在設定檔裝置上顯示的通知圖示。
   * **[!UICONTROL Tag]**：設定用來取代通知抽屜中現有通知的識別碼。
   * **[!UICONTROL Click action]**：設定與使用者點按您的通知相關聯的動作。

   如需詳細資訊，請參閱 **[!UICONTROL Notification options]** 以及如何填寫這些欄位，請參閱 [FCM檔案](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}.

   ![](assets/nmac_android_8.png)

1. 如果您的應用程式已使用HTTP v1 API通訊協定設定，您可以透過下列方式進一步個人化推播通知 **[!UICONTROL HTTPV1 additional options]**：

   * **[!UICONTROL Ticker]**：設定通知的提示文字。 僅適用於設為Android 5.0 Lollipop的裝置。
   * **[!UICONTROL Image]**：設定要在通知中顯示的影像URL。
   * **[!UICONTROL Notification Count]**：設定直接在應用程式圖示上顯示的新未讀取資訊數量。
   * **[!UICONTROL Sticky]**：設為true或false。 如果設為false，則當使用者按一下通知時，會自動將其關閉。 如果設為true，則即使使用者按一下通知，仍會顯示通知。
   * **[!UICONTROL Notification Priority]**：將通知的優先順序層級設定為預設、最低、低或高。 有關詳細資訊，請參閱 [FCM檔案](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority).
   * **[!UICONTROL Visibility]**：將通知的可見度層級設定為公開、私人或秘密。 有關詳細資訊，請參閱 [FCM檔案](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility).

   如需詳細資訊，請參閱 **[!UICONTROL HTTP v1 additional options]** 以及如何填寫這些欄位，請參閱 [FCM檔案](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}.

   ![](assets/nmac_android_9.png)

1. 您可以在先前設定的中新增資訊 **[!UICONTROL Application variables]** 如有需要。 **[!UICONTROL Application variables]** 需要在Android服務中設定，且屬於傳送至行動裝置的訊息裝載的一部分。

1. 按一下 **[!UICONTROL Save]** 並傳送您的傳遞。

在訂閱者的行動Android裝置上接收時，影像和網頁應顯示在推播通知中。
