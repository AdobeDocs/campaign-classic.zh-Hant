---
solution: Campaign Classic
product: campaign
title: 建立推播通知
description: 瞭解如何建立推播通知
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 4%

---


# 建立通知{#creating-notifications}

本節詳細說明iOS和Android通知傳送的特定元素。 在[本節](../../delivery/using/steps-about-delivery-creation-steps.md)中介紹了建立交付的全局概念。

從建立新傳送開始。

![](assets/nmac_delivery_1.png)

## 在iOS {#sending-notifications-on-ios}上傳送通知

1. 選擇&#x200B;**[!UICONTROL Deliver on iOS]**&#x200B;傳送範本。

   ![](assets/nmac_delivery_ios_1.png)

1. 要定義通知的目標，請按一下&#x200B;**[!UICONTROL To]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Add]**。

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >選擇傳送的目標人口時的詳細過程顯示在[本節](../../delivery/using/steps-defining-the-target-population.md)中。
   >
   >有關個人化欄位的詳細資訊，請參閱[關於個人化](../../delivery/using/about-personalization.md)。
   >
   >有關包含種子清單的詳細資訊，請參閱[關於種子地址](../../delivery/using/about-seed-addresses.md)。

1. 選擇&#x200B;**[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**，選擇與您的行動應用程式相關的服務（在本例中為Neotrips），然後選擇應用程式的iOS版本。

   ![](assets/nmac_delivery_ios_3.png)

1. 選擇通知類型：**[!UICONTROL Alert]**、**[!UICONTROL Badge]**&#x200B;或&#x200B;**[!UICONTROL Alert and badge]**&#x200B;或&#x200B;**[!UICONTROL Silent Push]**。

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >iOS 7提供&#x200B;**無訊息推播**&#x200B;模式。 這可讓「無訊息」通知傳送至行動應用程式。 使用者未得知通知的到達。 它會直接傳輸至應用程式。

1. 在&#x200B;**[!UICONTROL Title]**&#x200B;欄位中，輸入您要在通知中顯示的標題標籤。 它只會出現在通知中心提供的通知清單中。 此欄位可讓您定義iOS通知裝載的&#x200B;**title**&#x200B;參數值。

1. 如果您使用HTTP/2連接器，則可新增子標題（iOS通知裝載的&#x200B;**subtit**&#x200B;參數的值）。 請參閱「在Adobe Campaign中設定行動應用程式」一節。[](../../delivery/using/configuring-the-mobile-application.md)

1. 然後根據所選的通知類型輸入&#x200B;**[!UICONTROL Message]**&#x200B;和&#x200B;**[!UICONTROL Value of the badge]**。

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** 並輸 **[!UICONTROL Alert and badge]** 入通知可讓您修改徽章的值（行動應用程式標誌上方的數字）。若要重新整理徽章，您只需輸入0作為值。 如果欄位空白，徽章值不會變更。

1. 按一下&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;圖示，將表情符號插入您的推播通知。 若要自訂表情符號清單，請參閱[自訂表情符號清單](../../delivery/using/customizing-emoticon-list.md)

1. **[!UICONTROL Action button]**&#x200B;允許您為出現在警報通知中的動作按鈕定義標籤（**action_loc_key**&#x200B;欄位）。 如果您的iOS應用程式管理可本機化的字串(**Localizable.strings**)，請在此欄位中輸入對應的金鑰。 如果您的應用程式不管理可本地化的文字，請輸入您要在動作按鈕上看到的標籤。 如需可本地化字串的詳細資訊，請參閱[Apple檔案](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1)。
1. 在&#x200B;**[!UICONTROL Play a sound]**&#x200B;欄位中，選取收到通知時由行動終端播放的音效。

   >[!NOTE]
   >
   >音效必須包含在應用程式中，並在建立服務時加以定義。 請參閱[設定iOS外部帳戶](../../delivery/using/configuring-the-mobile-application.md#configuring-external-account-ios)。

1. 在&#x200B;**[!UICONTROL Application variables]**&#x200B;欄位中，輸入每個變數的值。 應用程式變數可讓您定義通知行為：例如，您可以設定特定應用程式畫面，以便在使用者啟動通知時顯示。

   >[!NOTE]
   >
   >應用程式變數必須定義在行動應用程式的程式碼中，並在建立服務時輸入。 有關詳情，請參閱：[在Adobe Campaign中設定行動應用程式](../../delivery/using/configuring-the-mobile-application.md)。

1. 設定通知後，按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤以預覽通知。

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >通知樣式（橫幅或警報）未在Adobe Campaign中定義。 這取決於使用者在其iOS設定中選取的組態。 不過，Adobe Campaign可讓您預覽每種類型的通知樣式。 按一下右下方的箭頭，從一種樣式切換至另一種樣式。
   >
   >預覽使用iOS 10的外觀和感覺。

若要傳送證明並傳送最終傳送，請使用與電子郵件傳送相同的程式。

傳送訊息後，您可以監控及追蹤傳送內容。 如需詳細資訊，請參閱下列區段。

* [推播通知隔離](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [監視](../../delivery/using/about-delivery-monitoring.md)
* [瞭解傳送故障](../../delivery/using/understanding-delivery-failures.md)

## 在Android {#sending-notifications-on-android}上傳送通知

1. 從選擇&#x200B;**[!UICONTROL Deliver on Android (android)]**&#x200B;傳送範本開始。

   ![](assets/nmac_delivery_android_1.png)

1. 要定義通知的目標，請按一下&#x200B;**[!UICONTROL To]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Add]**。

   ![](assets/nmac_delivery_android_2.png)

1. 選擇&#x200B;**[!UICONTROL Subscribers of an Android mobile application]**，選擇與您的行動應用程式相關的服務（在本例中為Neotrips），然後選擇應用程式的Android版本。

   ![](assets/nmac_delivery_android_3.png)

1. 然後輸入通知的內容。

   ![](assets/nmac_delivery_android_4.png)

1. 按一下&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;圖示，將表情符號插入您的推播通知。 若要自訂表情符號清單，請參閱[自訂表情符號清單](../../delivery/using/defining-interactive-content.md)

1. 在&#x200B;**[!UICONTROL Application variables]**&#x200B;欄位中，輸入每個變數的值。 應用程式變數可讓您定義通知行為：例如，您可以設定特定應用程式畫面，以便在使用者啟動通知時顯示。

   >[!NOTE]
   >
   >應用程式變數必須定義在行動應用程式的程式碼中，並在建立服務時輸入。 有關詳情，請參閱：[在Adobe Campaign中設定行動應用程式](../../delivery/using/configuring-the-mobile-application.md)。

1. 設定通知後，按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤以預覽通知。

   ![](assets/nmac_intro_1.png)

若要傳送證明並傳送最終傳送，請使用與電子郵件傳送相同的程式。

驗證和傳送傳送時的詳細程式會列於以下各節：

* [驗證傳遞](../../delivery/using/steps-validating-the-delivery.md)
* [傳送傳遞](../../delivery/using/steps-sending-the-delivery.md)

傳送訊息後，您可以監控及追蹤傳送內容。 如需詳細資訊，請參閱下列區段。

* [推播通知隔離](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [監視](../../delivery/using/about-delivery-monitoring.md)
* [瞭解傳送故障](../../delivery/using/understanding-delivery-failures.md)
