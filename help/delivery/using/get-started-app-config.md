---
product: campaign
title: 在Adobe Campaign中設定行動應用程式
description: 瞭解如何開始使用行動應用程式設定
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Push
role: User, Developer
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 8%

---

# 開始使用應用程式設定



您可以在本節中找到銷售線上假日套件的公司設定範例。 其行動應用程式(Neotrips)提供兩個版本供客戶使用：Android的Neotrips和iOS的Neotrips。

若要在Adobe Campaign中傳送推播通知，您需要：

* 建立 **[!UICONTROL Mobile application]** 輸入Neotrips行動應用程式的資訊服務。 請參閱 [適用於iOS的本節](configuring-the-mobile-application.md#configuring-ios-service). 和 [適用於Android的本節](configuring-the-mobile-application-android.md#configuring-android-service).
* 將應用程式的iOS和Android版本新增至此服務。
* 建立傳遞 [iOS](create-notifications-ios.md) 和 [Android](create-notifications-android.md).

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>前往 **[!UICONTROL Subscriptions]** 服務的索引標籤，以檢視服務的訂閱者清單，也就是在行動裝置上安裝應用程式並同意接收通知的所有人員。

## 安裝套件 {#installing-package-ios}

[!BADGE 內部部署和混合]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"}

![](assets/do-not-localize/how-to-video.png) [在影片中瞭解如何安裝行動應用程式套件](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html#sending-messages)

身為混合/託管客戶，請聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 團隊以存取Campaign中的推播通知頻道。

身為內部部署客戶，您必須安裝內建套件。

>[!CAUTION]
>
>進一步瞭解Campaign內建套件，最佳實務和建議 [此頁面](../../installation/using/installing-campaign-standard-packages.md).

安裝步驟如下：

1. 從存取套件匯入精靈 **[!UICONTROL Tools > Advanced > Import package]** 在Adobe Campaign使用者端主控台中。

   ![](assets/package_ios.png)

1. 選取 **[!UICONTROL Install a standard package]**。

1. 在出現的清單中，核取 **[!UICONTROL Mobile App Channel]**.

   ![](assets/package_ios_2.png)

1. 按一下 **[!UICONTROL Next]**，然後 **[!UICONTROL Start]** 以開始安裝封裝。

   安裝套件後，進度列會顯示 **100%** 而且您會在安裝記錄檔中看到下列訊息： **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 安裝視窗。

完成此步驟後，您就可以設定Android和iOS應用程式。
請參閱下列章節：

* [針對 iOS 的設定步驟](configuring-the-mobile-application.md)

* [針對 Android 的設定步驟](configuring-the-mobile-application-android.md)
