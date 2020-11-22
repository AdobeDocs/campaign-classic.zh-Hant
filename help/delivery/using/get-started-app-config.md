---
solution: Campaign Classic
product: campaign
title: '在 Adobe Campaign 設定行動應用程式 '
description: 瞭解如何從行動應用程式設定開始
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 10%

---


# 開始使用應用程式配置

您可以在本節中找到根據銷售線上假日套件的公司所提供的組態範例。 他的行動應用程式(Neotrips)有兩種版本可供客戶使用：iOS專用的Neotrips和Neotrips。

若要在Adobe Campaign中傳送推播通知，您必須：

* 為Neotrips行 **[!UICONTROL Mobile application]** 動應用程式建立類型資訊服務。 如需iOS, [請參閱本節](../../delivery/using/configuring-the-mobile-application.md#configuring-ios-service)。 和本 [節的Android版](../../delivery/using/configuring-the-mobile-application-android.md#configuring-android-service)。
* 將應用程式的iOS和Android版本新增至此服務。
* 建立iOS和Android的傳送。 [請參見此頁面](../../delivery/using/creating-notifications.md)。

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>前往服 **[!UICONTROL Subscriptions]** 務的標籤，檢視服務訂閱者清單，即所有已在行動裝置上安裝應用程式並同意接收通知的使用者。

## 安裝軟體包 {#installing-package-ios}

身為混合／代管客戶，請聯絡Adobe客戶服務團隊以存取Campaign中的推播通知頻道。

身為內部部署客戶，您需要執行下列安裝步驟：

1. 從Adobe Campaign用戶端主控台 **[!UICONTROL Tools > Advanced > Package import...]** 存取套件匯入精靈。

   ![](assets/package_ios.png)

1. 選取 **[!UICONTROL Install a standard package]**。

1. 在出現的清單中，勾選 **[!UICONTROL Mobile App Channel]**。

   ![](assets/package_ios_2.png)

1. 按一下 **[!UICONTROL Next]**，然 **[!UICONTROL Start]** 後啟動軟體包安裝。

   安裝軟體包後，進度欄顯示 **100%** ，您可以在安裝日誌中看到以下消息： **[!UICONTROL Installation of packages successful]**.

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 安裝窗口。

完成此步驟後，您就可以設定您的Android和iOS應用程式。
請參閱以下章節：

* [針對 iOS 的配置步驟](../../delivery/using/configuring-the-mobile-application.md)

* [針對 Android 的配置步驟](../../delivery/using/configuring-the-mobile-application-android.md)
