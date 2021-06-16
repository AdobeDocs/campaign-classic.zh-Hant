---
product: campaign
title: 為Android裝置建立推播通知
description: 了解如何為Android建立推播通知
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: fb2f1769aadbc128d76f343a5fa58ee4e3bda72a
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 1%

---

# 建立Android{#create-notificaations-android}的通知

使用Adobe Campaign在Android裝置上傳送推播通知。 傳遞建立的全域概念在[此小節](../../delivery/using/steps-about-delivery-creation-steps.md)中介紹。

首先，建立新的傳送。

![](assets/nmac_delivery_1.png)

使用Firebase雲端訊息，您可以在兩種訊息類型之間進行選擇：

* **[!UICONTROL Data message]**，由用戶端應用程式處理。
   <br>訊息會直接傳送至行動應用程式，行動應用程式會產生並顯示Android通知給裝置。資料訊息僅包含您的自訂應用程式變數。

* **[!UICONTROL Notification message]**，由FCM SDK自動處理。
   <br> FCM會代表用戶端應用程式在您的使用者裝置上自動顯示訊息。通知訊息包含一組預先定義的參數和選項，但仍可透過自訂應用程式變數進一步個人化。

如需Firebase雲端訊息類型的詳細資訊，請參閱[FCM檔案](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages)。

## 建立資料消息{#creating-data-message}

1. 前往&#x200B;**[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 按一下 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 在&#x200B;**[!UICONTROL Delivery template]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Deliver on Android (android)]**。 將&#x200B;**[!UICONTROL Label]**&#x200B;新增至您的傳送。

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;以定義要定位的母體。 預設會套用&#x200B;**[!UICONTROL Subscriber application]**&#x200B;目標對應。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以選擇您的服務。

   ![](assets/nmac_android_7.png)

1. 在&#x200B;**[!UICONTROL Target type]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Subscribers of an Android mobile application]**&#x200B;並按一下&#x200B;**[!UICONTROL Next]**。

1. 在&#x200B;**[!UICONTROL Service]**&#x200B;下拉式清單中，依序選取您先前建立的服務和應用程式，然後按一下&#x200B;**[!UICONTROL Finish]**。
系統會根據設定步驟期間新增的內容自動新增**[!UICONTROL Application variables]**。

   ![](assets/nmac_android_6.png)

1. 選擇&#x200B;**[!UICONTROL data message]**&#x200B;作為&#x200B;**[!UICONTROL Message Type]**。

1. 編輯豐富通知。

   ![](assets/nmac_android_5.png)

1. 如有需要，您可以在先前設定的&#x200B;**[!UICONTROL Application variables]**&#x200B;中新增資訊。 **[!UICONTROL Application variables]** 需要在Android服務中設定，且是傳送至行動裝置之訊息裝載的一部分。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;並傳送您的傳遞。

在訂閱者的行動Android裝置上收到影像和網頁時，應顯示在推播通知中。

![](assets/nmac_android_4.png)

## 建立通知消息{#creating-notification-message}

>[!NOTE]
>
>通知訊息的其他選項僅可搭配HTTP v1 API設定使用。 如需詳細資訊，請參閱本[區段](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1)。

![](assets/do-not-localize/how-to-video.png) [了解如何在影片中建立Android推播通知](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=en#additional-resources)

1. 前往&#x200B;**[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 按一下 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 在&#x200B;**[!UICONTROL Delivery template]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Deliver on Android (android)]**。 將&#x200B;**[!UICONTROL Label]**&#x200B;新增至您的傳送。

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;以定義要定位的母體。 預設會套用&#x200B;**[!UICONTROL Subscriber application]**&#x200B;目標對應。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以選擇您的服務。

   ![](assets/nmac_android_7.png)

1. 在&#x200B;**[!UICONTROL Target type]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Subscribers of an Android mobile application]**&#x200B;並按一下&#x200B;**[!UICONTROL Next]**。

1. 在&#x200B;**[!UICONTROL Service]**&#x200B;下拉式清單中，依序選取您先前建立的服務和應用程式，然後按一下&#x200B;**[!UICONTROL Finish]**。

   ![](assets/nmac_android_6.png)

1. 選擇&#x200B;**[!UICONTROL notification message]**&#x200B;作為&#x200B;**[!UICONTROL Message Type]**。

1. 新增標題並編輯訊息。 使用&#x200B;**[!UICONTROL Notification options]**&#x200B;個人化您的推播通知：

   * **[!UICONTROL Channel ID]**:設定通知的通道ID。收到具有此通道ID的任何通知之前，應用程式必須先使用此通道ID建立通道。
   * **[!UICONTROL Sound]**:設定在裝置收到通知時播放音效。
   * **[!UICONTROL Color]**:設定通知的圖示顏色。
   * **[!UICONTROL Icon]**:設定通知的圖示，以在您的設定檔裝置上顯示。
   * **[!UICONTROL Tag]**:設定用來取代通知抽屜中現有通知的識別碼。
   * **[!UICONTROL Click action]**:設定與使用者點按您的通知相關聯的動作。

   有關&#x200B;**[!UICONTROL Notification options]**&#x200B;以及如何填寫這些欄位的詳細資訊，請參閱[FCM檔案](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification)。

   ![](assets/nmac_android_8.png)

1. 如果您的應用程式已使用HTTP v1 API通訊協定進行設定，您可以使用下列&#x200B;**[!UICONTROL HTTPV1 additional options]**&#x200B;進一步個人化您的推播通知：

   * **[!UICONTROL Ticker]**:設定通知的代號文字。僅適用於設為Android 5.0 Lollipop的裝置。
   * **[!UICONTROL Image]**:設定要在通知中顯示的影像URL。
   * **[!UICONTROL Notification Count]**:設定要直接顯示在應用程式圖示上的新未讀資訊數。
   * **[!UICONTROL Sticky]**:設為true或false。若設為false，則當使用者按一下通知時，系統會自動將其關閉。 若設為true，即使使用者點按通知，仍會顯示通知。
   * **[!UICONTROL Notification Priority]**:將通知的優先順序設定為預設、最小、低或高。如需詳細資訊，請參閱[FCM檔案](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority)。
   * **[!UICONTROL Visibility]**:將通知的可見度層級設為公開、私人或機密。如需詳細資訊，請參閱[FCM檔案](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility)。

   有關&#x200B;**[!UICONTROL HTTP v1 additional options]**&#x200B;以及如何填寫這些欄位的詳細資訊，請參閱[FCM檔案](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification)。

   ![](assets/nmac_android_9.png)

1. 如有需要，您可以在先前設定的&#x200B;**[!UICONTROL Application variables]**&#x200B;中新增資訊。 **[!UICONTROL Application variables]** 需要在Android服務中設定，且是傳送至行動裝置之訊息裝載的一部分。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;並傳送您的傳遞。

在訂閱者的行動Android裝置上收到影像和網頁時，應顯示在推播通知中。
