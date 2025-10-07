---
product: campaign
title: 開始使用行動應用程式頻道
description: 開始使用Adobe Campaign中的行動應用程式頻道
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: 89e350c727fb9379d28916f79d9749f22fd4974f
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---

# 開始使用行動應用程式頻道{#about-mobile-app-channel}

透過Adobe Campaign建立推播通知傳遞，以傳送個人化訊息給您的行動應用程式使用者。

推播通知可讓您即時與iOS和Android上的使用者互動。 不論是傳送更新、公告或促銷活動，您都可以控制內容、時間及目標。 在[Adobe Campaign v8檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/send/emails/email){target=_blank}中瞭解如何設定及使用推播頻道、管理訂閱、與APN和FCM整合，以及個人化訊息。

做為Campaign v8促銷活動的一部分，Campaign Classic檔案已重新整理。 現在僅可在Campaign v8檔案集中使用常見功能。

>[!BEGINTABS]

>[!TAB 推播通道檔案]

若要進一步瞭解推播通知頻道，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=zh-Hant){target=_blank}。

[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=zh-Hant){target=_blank}


>[!TAB 推播傳遞建立]

在Campaign v8檔案中瞭解與推播傳送建立相關的關鍵步驟：

* [建立推播通知](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=zh-Hant#push-create){target="_blank"}：瞭解建立推播傳遞所需的不同步驟。
* [傳送及監視推播通知](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=zh-Hant#push-test){target="_blank"}：瞭解如何驗證、傳送及追蹤您的傳遞。
* [設計Android豐富推送傳送](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-android.html?lang=zh-Hant){target="_blank"}：瞭解如何建立和設定Android裝置的豐富推送通知。
* [設計iOS豐富推送傳送](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/rich-push/rich-push-ios.html?lang=zh-Hant){target="_blank"}：瞭解如何在Adobe Campaign v8中為iOS裝置設計和設定豐富推送通知。


>[!TAB 推播引數]

請參閱這些頁面，以在Campaign v8檔案中瞭解推播引數：

* [設定先決條件](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=zh-Hant#before-starting){target="_blank"}：瞭解如何設定許可權及設定您的應用程式。
* [設定launch屬性](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=zh-Hant#launch-property){target="_blank"}：瞭解如何在Adobe Experience Platform資料收集中設定行動標籤屬性以啟用推播通知。
* [設定推送服務行動服務](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=zh-Hant#push-service){target="_blank"}：在Adobe中設定iOS和Android推送服務，為您的行動應用程式使用者啟用目標式推送通知。
* [在行動屬性中設定擴充功能](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=zh-Hant#configure-extension){target="_blank"}：將Campaign擴充功能整合至行動屬性，以啟用推播通知並有效管理使用者互動。

>[!ENDTABS]


以下是Campaign Classic的專屬資訊。

+++ **封裝安裝**

![](assets/do-not-localize/how-to-video.png) [瞭解如何在影片中安裝行動應用程式套件](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=zh-Hant#sending-messages)

身為混合/託管客戶，請聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)團隊以存取Campaign中的推播通知頻道。

身為內部部署客戶，您必須安裝內建套件。

>[!CAUTION]
>
>在[此頁面](../../installation/using/installing-campaign-standard-packages.md)中進一步瞭解Campaign內建套件、最佳實務和建議。

安裝步驟如下：

1. 從Adobe Campaign使用者端主控台的&#x200B;**[!UICONTROL Tools > Advanced > Import package]**&#x200B;存取套件匯入小幫手。

   ![](assets/package_ios.png)

1. 選取 **[!UICONTROL Install a standard package]**。

1. 在出現的清單中，核取&#x200B;**[!UICONTROL Mobile App Channel]**。

   ![](assets/package_ios_2.png)

1. 按一下&#x200B;**[!UICONTROL Next]**，然後按一下&#x200B;**[!UICONTROL Start]**&#x200B;以開始安裝封裝。

   安裝套件後，進度列會顯示&#x200B;**100%**，您可以在安裝記錄檔中看到下列訊息： **[!UICONTROL Installation of packages successful]**。

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]**&#x200B;安裝視窗。

完成此步驟後，您就可以設定您的Android和iOS應用程式。 請參閱Campaign v8 [檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push.html?lang=zh-Hant){target="_blank"}。

+++

+++ **疑難排解**

如果您的行動裝置已連線至Wi-Fi，但您未收到通知，請檢查防火牆是否未封鎖FCM/APNs連線埠。

**Android**：行動裝置已連線到連線埠5228到5230上的FCM伺服器。 因此，您必須設定防火牆，使其可授權與FCM的連線。 要開啟的連線埠為：5228 （最常使用）、5229和5230。

**iOS**：

HTTP/2聯結器：您必須允許與下列伺服器之間的通訊：

* api.push.apple.com：連線埠443
* api.development.push.apple.com：連線埠443

>[!NOTE]
>
>如需這兩個聯結器的詳細資訊，請參閱Campaign v8 [檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html?lang=zh-Hant){target="_blank"}。

+++
