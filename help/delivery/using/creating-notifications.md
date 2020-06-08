---
title: 建立通知
seo-title: 建立通知
description: 建立通知
seo-description: null
page-status-flag: never-activated
uuid: fb1862df-e616-4147-a642-dc867bc983b5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 345af5c2-c852-4086-8ed0-ff3e7e402e04
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5847107a459bf47f34e4994c3521266bb174d8cb
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---


# 建立通知{#creating-notifications}

本節詳細說明iOS和Android通知傳送的特定元素。 本節將介紹有關建立交付的全 [局概念](../../delivery/using/steps-about-delivery-creation-steps.md)。

從建立新傳送開始。

![](assets/nmac_delivery_1.png)

## 在iOS上傳送通知 {#sending-notifications-on-ios}

1. 選擇傳 **[!UICONTROL Deliver on iOS]** 送範本。

   ![](assets/nmac_delivery_ios_1.png)

1. 若要定義通知的目標，請按一下連 **[!UICONTROL To]** 結，然後按一下 **[!UICONTROL Add]**。

   ![](assets/nmac_delivery_ios_2.png)

   >[!NOTE]
   >
   >本節將介紹在選擇交貨的目標人口時的詳細 [流程](../../delivery/using/steps-defining-the-target-population.md)。
   >
   >有關個人化欄位使用的詳細資訊，請參閱關於個 [人化](../../delivery/using/about-personalization.md)。
   >
   >有關包含種子清單的詳細資訊，請參閱關於 [種子地址](../../delivery/using/about-seed-addresses.md)。

1. 選 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**&#x200B;取與您的行動應用程式相關的服務（在本例中為Neotrips），然後選取應用程式的iOS版本。

   ![](assets/nmac_delivery_ios_3.png)

1. 選擇通知類型： **[!UICONTROL Alert]**、 **[!UICONTROL Badge]**&#x200B;或 **[!UICONTROL Alert and badge]** 或 **[!UICONTROL Silent Push]**。

   ![](assets/nmac_delivery_ios_4.png)

   >[!NOTE]
   >
   >iOS **7提供** 「無訊息推播」模式。 這可讓「無訊息」通知傳送至行動應用程式。 使用者未得知通知的到達。 它會直接傳輸至應用程式。

1. 在字 **[!UICONTROL Title]** 段中，輸入要顯示在通知中的標題標籤。 它只會出現在通知中心提供的通知清單中。 此欄位可讓您定義iOS通知裝載 **的** title參數值。

1. 如果您使用HTTP/2連接器，則可新增子標題(iOS通知裝載的 **子標題** 參數值)。 請參閱「在 [Adobe Campaign中設定行動應用程式](../../delivery/using/configuring-the-mobile-application.md) 」一節。

1. 然後，根據選 **[!UICONTROL Message]** 擇的通 **[!UICONTROL Value of the badge]** 知類型輸入和。

   ![](assets/nmac_delivery_ios_5.png)

   >[!NOTE]
   >
   >**[!UICONTROL Badge]** 並輸 **[!UICONTROL Alert and badge]** 入通知可讓您修改徽章的值（行動應用程式標誌上方的數字）。 若要重新整理徽章，您只需輸入0作為值。 如果欄位空白，徽章值不會變更。

1. 按一下圖 **[!UICONTROL Insert emoticon]** 示，將表情符號插入您的推播通知。 若要自訂表情符號清單，請參閱自 [訂表情符號清單](../../delivery/using/defining-interactive-content.md)

1. 可 **[!UICONTROL Action button]** 讓您為出現在警報通知(裝載的&#x200B;**** action_loc_key欄位)上的動作按鈕定義標籤。 如果您的iOS應用程式管理可本地化字串(**Localablized.strings**)，請在此欄位中輸入對應的金鑰。 如果您的應用程式不管理可本地化的文字，請輸入您要在動作按鈕上看到的標籤。 如需可本地化字串的詳細資訊，請參閱 [Apple檔案](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/CreatingtheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH10-SW1) 。
1. 在欄位 **[!UICONTROL Play a sound]** 中，選取收到通知時由行動終端播放的音效。

   >[!NOTE]
   >
   >音效必須包含在應用程式中，並在建立服務時加以定義。 請參閱 [設定iOS外部帳戶](../../delivery/using/configuring-the-mobile-application.md#configuring-external-account-ios)。

1. 在欄位 **[!UICONTROL Application variables]** 中，輸入每個變數的值。 應用程式變數可讓您定義通知行為： 例如，您可以設定特定應用程式畫面，以便在使用者啟動通知時顯示。

   >[!NOTE]
   >
   >應用程式變數必須定義在行動應用程式的程式碼中，並在建立服務時輸入。 有關詳情，請參閱： [在Adobe Campaign中設定行動應用程式](../../delivery/using/configuring-the-mobile-application.md)。

1. 在設定通知後，按一下標 **[!UICONTROL Preview]** 簽以預覽通知。

   ![](assets/nmac_intro_2.png)

   >[!NOTE]
   >
   >通知樣式（橫幅或警報）未在Adobe Campaign中定義。 這取決於使用者在其iOS設定中選取的組態。 不過，Adobe Campaign可讓您預覽每種類型的通知樣式。 按一下右下方的箭頭，從一種樣式切換至另一種樣式。
   >
   >預覽使用iOS 10的外觀和感覺。

若要傳送證明並傳送最終傳送，請使用與電子郵件傳送相同的程式。

傳送訊息後，您可以監控及追蹤傳送內容。 如需更多相關資訊，請參閱以下章節：

* [推播通知隔離](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [監控傳送](../../delivery/using/monitoring-a-delivery.md)
* [瞭解傳送故障](../../delivery/using/understanding-delivery-failures.md)

## 在Android上傳送通知 {#sending-notifications-on-android}

1. 從選取傳送范 **[!UICONTROL Deliver on Android (android)]** 本開始。

   ![](assets/nmac_delivery_android_1.png)

1. 若要定義通知的目標，請按一下連 **[!UICONTROL To]** 結，然後按一下 **[!UICONTROL Add]**。

   ![](assets/nmac_delivery_android_2.png)

1. 選 **[!UICONTROL Subscribers of an Android mobile application]**&#x200B;取、選擇與您行動應用程式相關的服務（在本例中為Neotrips），然後選取應用程式的Android版本。

   ![](assets/nmac_delivery_android_3.png)

1. 然後輸入通知的內容。

   ![](assets/nmac_delivery_android_4.png)

1. 按一下圖 **[!UICONTROL Insert emoticon]** 示，將表情符號插入您的推播通知。 若要自訂表情符號清單，請參閱自 [訂表情符號清單](../../delivery/using/defining-interactive-content.md)

1. 在欄位 **[!UICONTROL Application variables]** 中，輸入每個變數的值。 應用程式變數可讓您定義通知行為： 例如，您可以設定特定應用程式畫面，以便在使用者啟動通知時顯示。

   >[!NOTE]
   >
   >應用程式變數必須定義在行動應用程式的程式碼中，並在建立服務時輸入。 有關詳情，請參閱： [在Adobe Campaign中設定行動應用程式](../../delivery/using/configuring-the-mobile-application.md)。

1. 在設定通知後，按一下標 **[!UICONTROL Preview]** 簽以預覽通知。

   ![](assets/nmac_intro_1.png)

若要傳送證明並傳送最終傳送，請使用與電子郵件傳送相同的程式。

驗證和傳送傳送時的詳細程式會列於以下各節：

* [驗證傳送](../../delivery/using/steps-validating-the-delivery.md)
* [傳送傳送](../../delivery/using/steps-sending-the-delivery.md)

傳送訊息後，您可以監控及追蹤傳送內容。 如需更多相關資訊，請參閱以下章節：

* [推播通知隔離](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)
* [監控傳送](../../delivery/using/monitoring-a-delivery.md)
* [瞭解傳送故障](../../delivery/using/understanding-delivery-failures.md)
