---
product: campaign
title: '在 Adobe Campaign 設定行動應用程式 '
description: 了解如何從行動應用程式設定開始
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 10%

---

# 開始使用應用程式設定

您可以在本節中找到以銷售線上假日套件的公司為基礎的設定範例。 他的移動應用程式(Neotrips)提供兩種版本給客戶：Android版Neotrips與iOS版Neotrips。

若要在Adobe Campaign中傳送推播通知，您必須：

* 為Neotrips行動應用程式建立&#x200B;**[!UICONTROL Mobile application]**&#x200B;類型資訊服務。 有關iOS](configuring-the-mobile-application.md#configuring-ios-service)，請參閱[此部分。 和[適用於Android](configuring-the-mobile-application-android.md#configuring-android-service)的此區段。
* 將應用程式的iOS和Android版本新增至此服務。
* 為[iOS](create-notifications-ios.md)和[Android](create-notifications-android.md)建立傳送。

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>前往服務的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;標籤以檢視服務的訂閱者清單，亦即所有在行動裝置上安裝了應用程式並同意接收通知的使用者。

## 安裝套件 {#installing-package-ios}

![](assets/do-not-localize/how-to-video.png) [了解如何在影片中安裝行動應用程式套件](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

身為混合/托管客戶，請連絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)團隊，以存取Campaign中的推播通知通道。

身為內部部署客戶，您需要安裝內建套件。

>[!CAUTION]
>
>在[本頁面](../../installation/using/installing-campaign-standard-packages.md)中深入了解Campaign內建套件、最佳實務和建議。

安裝步驟為：

1. 從Adobe Campaign用戶端主控台的&#x200B;**[!UICONTROL Tools > Advanced > Package import...]**&#x200B;存取套件匯入精靈。

   ![](assets/package_ios.png)

1. 選取 **[!UICONTROL Install a standard package]**。

1. 在顯示的清單中，檢查&#x200B;**[!UICONTROL Mobile App Channel]**。

   ![](assets/package_ios_2.png)

1. 按一下&#x200B;**[!UICONTROL Next]**，然後按一下&#x200B;**[!UICONTROL Start]**&#x200B;以啟動軟體包安裝。

   安裝軟體包後，進度欄顯示&#x200B;**100%**，您可以在安裝日誌中看到以下消息：**[!UICONTROL Installation of packages successful]**。

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 安裝窗口。

完成此步驟後，您就可以設定Android和iOS應用程式。
請參閱以下章節：

* [針對 iOS 的設定步驟](configuring-the-mobile-application.md)

* [針對 Android 的設定步驟](configuring-the-mobile-application-android.md)
