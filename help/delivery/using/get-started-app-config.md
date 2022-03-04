---
product: campaign
title: '在Adobe Campaign配置移動應用程式 '
description: 瞭解如何從移動應用程式配置開始
feature: Push
exl-id: 95bc07cc-8837-4511-81bc-05fad28191c9
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 7%

---

# 開始使用應用程式設定

在本節中，您可以根據銷售線上假日套餐的公司找到配置示例。 其移動應用(Neotrips)以兩種版本提供給客戶：Android的Neotrips和iOS的Neotrips。

要在Adobe Campaign發送推送通知，您需要：

* 建立 **[!UICONTROL Mobile application]** 為Neotrips移動應用程式鍵入資訊服務。 請參閱 [本節為iOS](configuring-the-mobile-application.md#configuring-ios-service)。 和 [本節針對Android](configuring-the-mobile-application-android.md#configuring-android-service)。
* 將應用程式的iOS和Android版本添加到此服務。
* 建立交貨 [iOS](create-notifications-ios.md) 和 [安卓](create-notifications-android.md)。

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>轉到 **[!UICONTROL Subscriptions]** 頁籤，查看服務的訂閱者清單，即在其移動設備上安裝了應用程式並同意接收通知的所有用戶。

## 安裝軟體包 {#installing-package-ios}

![](assets/do-not-localize/how-to-video.png) [瞭解如何在視頻中安裝移動應用程式套件](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/sending-messages/push-channel/installing-the-mobile-app-channel.html?lang=en#sending-messages)

作為混合/托管客戶，請聯繫 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 團隊，以訪問「市場活動」中的推送通知渠道。

作為內部客戶，您需要安裝內置軟體包。

>[!CAUTION]
>
>瞭解有關中活動內置的產品包、最佳做法和建議的更多資訊 [此頁](../../installation/using/installing-campaign-standard-packages.md)。

安裝步驟包括：

1. 從訪問包導入嚮導 **[!UICONTROL Tools > Advanced > Import package]** 在Adobe Campaign客戶端控制台中。

   ![](assets/package_ios.png)

1. 選取 **[!UICONTROL Install a standard package]**。

1. 在顯示的清單中，選中 **[!UICONTROL Mobile App Channel]**。

   ![](assets/package_ios_2.png)

1. 按一下 **[!UICONTROL Next]**，則 **[!UICONTROL Start]** 啟動軟體包安裝。

   安裝軟體包後，進度欄將顯示 **100%** 您可以在安裝日誌中看到以下消息： **[!UICONTROL Installation of packages successful]**。

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 安裝窗口。

完成此步驟後，您可以配置Android和iOS應用。
請參閱以下各節：

* [針對 iOS 的設定步驟](configuring-the-mobile-application.md)

* [針對 Android 的設定步驟](configuring-the-mobile-application-android.md)
