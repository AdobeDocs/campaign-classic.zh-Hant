---
product: campaign
title: 為Android裝置建立推播通知
description: 瞭解如何建立Android的推播通知
feature: Push
role: User, Developer, Data Engineer
exl-id: 13ccc5d6-4355-42ba-80dc-30a45d3b69a4
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# 建立Android通知{#create-notificaations-android}

使用Adobe Campaign在Android裝置上傳送推播通知。 在[本節](steps-about-delivery-creation-steps.md)中介紹了傳遞建立的全域概念。

從建立新傳遞開始。

![](assets/nmac_delivery_1.png)

使用Firebase Cloud Messaging時，您可以選擇兩種型別的訊息：

* **[!UICONTROL Data message]**，由使用者端應用程式處理。
  <br>訊息會直接傳送至行動應用程式，該應用程式將會產生並向裝置顯示Android通知。 資料訊息僅包含您的自訂應用程式變數。

* **[!UICONTROL Notification message]**，由FCM SDK自動處理。
  <br> FCM會自動代表使用者端應用程式在使用者裝置上顯示訊息。 通知訊息包含預先定義的一組引數和選項，但仍可使用自訂應用程式變數進一步個人化。

如需Firebase Cloud Messaging訊息型別的詳細資訊，請參閱[FCM檔案](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages){target="_blank"}。


## 建立資料訊息 {#creating-data-message}

1. 前往&#x200B;**[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 在&#x200B;**[!UICONTROL Delivery template]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Deliver on Android (android)]**。 新增&#x200B;**[!UICONTROL Label]**&#x200B;至您的傳遞。

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;以定義目標母體。 依預設，會套用&#x200B;**[!UICONTROL Subscriber application]**&#x200B;目標對應。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以選取您的服務。

   ![](assets/nmac_android_7.png)

1. 在&#x200B;**[!UICONTROL Target type]**&#x200B;視窗中，選取&#x200B;**[!UICONTROL Subscribers of an Android mobile application]**&#x200B;並按一下&#x200B;**[!UICONTROL Next]**。

1. 在&#x200B;**[!UICONTROL Service]**&#x200B;下拉式清單中，選取您先前建立的服務，然後選取應用程式，再按一下&#x200B;**[!UICONTROL Finish]**。
**[!UICONTROL Application variables]**&#x200B;會根據組態步驟中新增的內容自動新增。

   ![](assets/nmac_android_6.png)

1. 選取&#x200B;**[!UICONTROL data message]**&#x200B;作為&#x200B;**[!UICONTROL Message Type]**。

1. 編輯您的豐富型通知。

   ![](assets/nmac_android_5.png)

1. 如有需要，您可以在先前設定的&#x200B;**[!UICONTROL Application variables]**&#x200B;中新增資訊。 **[!UICONTROL Application variables]**&#x200B;需要在Android服務中設定，並且是傳送至行動裝置的訊息裝載的一部分。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;並傳送您的傳遞。

在訂閱者的Android行動裝置上接收時，影像和網頁應顯示在推播通知中。

![](assets/nmac_android_4.png)

## 建立通知訊息 {#creating-notification-message}

![](assets/do-not-localize/how-to-video.png) [瞭解如何在影片中建立Android推播通知](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html#additional-resources){target="_blank"}。

1. 前往&#x200B;**[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 在&#x200B;**[!UICONTROL Delivery template]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Deliver on Android (android)]**。 新增&#x200B;**[!UICONTROL Label]**&#x200B;至您的傳遞。

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;以定義目標母體。 依預設，會套用&#x200B;**[!UICONTROL Subscriber application]**&#x200B;目標對應。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以選取您的服務。

   ![](assets/nmac_android_7.png)

1. 在&#x200B;**[!UICONTROL Target type]**&#x200B;視窗中，選取&#x200B;**[!UICONTROL Subscribers of an Android mobile application]**&#x200B;並按一下&#x200B;**[!UICONTROL Next]**。

1. 在&#x200B;**[!UICONTROL Service]**&#x200B;下拉式清單中，選取您先前建立的服務，然後選取應用程式，再按一下&#x200B;**[!UICONTROL Finish]**。

   ![](assets/nmac_android_6.png)

1. 選取&#x200B;**[!UICONTROL notification message]**&#x200B;作為&#x200B;**[!UICONTROL Message Type]**。

1. 新增標題並編輯您的訊息。 使用&#x200B;**[!UICONTROL Notification options]**&#x200B;個人化您的推播通知：

   * **[!UICONTROL Channel ID]**：設定通知的頻道識別碼。 在收到具有此管道ID的任何通知之前，應用程式必須建立具有此管道ID的管道。
   * **[!UICONTROL Sound]**：設定裝置收到通知時播放的聲音。
   * **[!UICONTROL Color]**：設定通知的圖示色彩。
   * **[!UICONTROL Icon]**：將通知的圖示設定為在設定檔的裝置上顯示。
   * **[!UICONTROL Tag]**：設定用來取代通知抽屜中現有通知的識別碼。
   * **[!UICONTROL Click action]**：設定與使用者按一下您的通知相關聯的動作。

   有關&#x200B;**[!UICONTROL Notification options]**&#x200B;以及如何填寫這些欄位的詳細資訊，請參閱[FCM檔案](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}。

   ![](assets/nmac_android_8.png)

1. 如果您的應用程式設定了HTTP v1 API通訊協定，您可以使用下列&#x200B;**[!UICONTROL HTTPV1 additional options]**&#x200B;進一步個人化您的推播通知：

   * **[!UICONTROL Ticker]**：設定通知的提示字元。 僅適用於設為Android 5.0 Lollipop的裝置。
   * **[!UICONTROL Image]**：設定要在通知中顯示的影像URL。
   * **[!UICONTROL Notification Count]**：將新的未讀取資訊的數目設定為直接顯示在應用程式圖示上。
   * **[!UICONTROL Sticky]**：設為True或False。 如果設為false，則當使用者按一下通知時，會自動將其關閉。 如果設為true，則即使使用者按一下通知，仍會顯示通知。
   * **[!UICONTROL Notification Priority]**：將通知的優先順序等級設定為預設、最低、低或高。 如需詳細資訊，請參閱[FCM檔案](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority)。
   * **[!UICONTROL Visibility]**：將通知的可見度等級設定為公開、私人或機密。 如需詳細資訊，請參閱[FCM檔案](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility)。

   有關&#x200B;**[!UICONTROL HTTP v1 additional options]**&#x200B;以及如何填寫這些欄位的詳細資訊，請參閱[FCM檔案](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification){target="_blank"}。

   ![](assets/nmac_android_9.png)

1. 如有需要，您可以在先前設定的&#x200B;**[!UICONTROL Application variables]**&#x200B;中新增資訊。 **[!UICONTROL Application variables]**&#x200B;需要在Android服務中設定，並且是傳送至行動裝置的訊息裝載的一部分。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;並傳送您的傳遞。

在訂閱者的Android行動裝置上接收時，影像和網頁應顯示在推播通知中。
