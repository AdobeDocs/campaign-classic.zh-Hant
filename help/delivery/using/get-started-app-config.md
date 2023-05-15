---
product: campaign
title: 在Adobe Campaign中設定行動應用程式
description: 了解如何從行動應用程式設定開始
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Push
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: e011333411af79b985166a4e73592a1860749cf1
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 10%

---

# 開始使用應用程式設定



您可以在本節中找到以銷售線上假日套件的公司為基礎的設定範例。 其行動應用程式(Neotrips)提供兩種版本供其客戶使用：Android的Neotrips和iOS的Neotrips。

若要在Adobe Campaign中傳送推播通知，您必須：

* 建立 **[!UICONTROL Mobile application]** 為Neotrips行動應用程式輸入資訊服務。 請參閱 [本節為iOS](configuring-the-mobile-application.md#configuring-ios-service). 和 [Android適用的本節](configuring-the-mobile-application-android.md#configuring-android-service).
* 將應用程式的iOS和Android版本新增至此服務。
* 建立傳送 [iOS](create-notifications-ios.md) 和 [Android](create-notifications-android.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>前往 **[!UICONTROL Subscriptions]** 頁簽，查看服務的訂閱者清單，即所有在行動裝置上安裝了應用程式並同意接收通知的人員。

## 安裝套件 {#installing-package-ios}

[!BADGE 內部部署與混合]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"}

![](assets/do-not-localize/how-to-video.png) [了解如何在影片中安裝行動應用程式套件](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

身為混合/托管客戶，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 團隊來存取Campaign中的推播通知通道。

身為內部部署客戶，您需要安裝內建套件。

>[!CAUTION]
>
>進一步了解Campaign內建套件、最佳實務和建議，位於 [本頁](../../installation/using/installing-campaign-standard-packages.md).

安裝步驟為：

1. 從訪問包導入嚮導 **[!UICONTROL Tools > Advanced > Import package]** 在Adobe Campaign用戶端主控台中。

   ![](assets/package_ios.png)

1. 選取 **[!UICONTROL Install a standard package]**。

1. 在顯示的清單中，核取 **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. 按一下 **[!UICONTROL Next]**，然後 **[!UICONTROL Start]** 以啟動軟體包安裝。

   安裝軟體包後，進度欄將顯示 **100%** 而且，您會在安裝記錄中看到下列訊息： **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 安裝窗口。

完成此步驟後，您就可以設定Android和iOS應用程式。
請參閱以下章節：

* [針對 iOS 的設定步驟](configuring-the-mobile-application.md)

* [針對 Android 的設定步驟](configuring-the-mobile-application-android.md)
