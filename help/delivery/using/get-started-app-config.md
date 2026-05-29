---
product: campaign
title: 在Adobe Campaign中設定行動應用程式
description: 瞭解如何開始使用行動應用程式設定
feature: Push
role: User, Developer
level: Intermediate, Experienced
hide: true
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
TQID: https://experienceleague.adobe.com/cJ0deoAKq2ac-04v87YFRvwx-mqhrHyzQYxGmkvgKiY
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 330
ht-degree: 13%

---

# 開始使用應用程式設定



您可以在本節中找到銷售線上假日套件的公司設定範例。 其行動應用程式(Neotrips)提供兩個版本供客戶使用：Android的Neotrips和iOS的Neotrips。

若要在Adobe Campaign中傳送推播通知，您需要：

* 為Neotrips行動應用程式建立&#x200B;**[!UICONTROL Mobile application]**&#x200B;型別資訊服務。 請參閱iOS[&#128279;](configuring-the-mobile-application.md#configuring-ios-service)的本節。 和[Android](configuring-the-mobile-application-android.md#configuring-android-service)的此區段。
* 將應用程式的iOS和Android版本新增至此服務。
* 建立[iOS](create-notifications-ios.md)和[Android](create-notifications-android.md)的傳遞。

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>移至服務的&#x200B;**[!UICONTROL Subscriptions]**&#x200B;標籤，以檢視服務的訂閱者清單，亦即已在行動裝置上安裝應用程式並同意接收通知的所有人員。

## 安裝套件 {#installing-package-ios}

[!BADGE 內部部署與混合式]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"}

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

完成此步驟後，您就可以設定您的Android和iOS應用程式。
請參閱下列章節：

* [針對 iOS 的設定步驟](configuring-the-mobile-application.md)

* [針對 Android 的設定步驟](configuring-the-mobile-application-android.md)
