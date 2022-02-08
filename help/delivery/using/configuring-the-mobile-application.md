---
product: campaign
title: 在Adobe Campaign配置iOS移動應用程式
description: 瞭解如何為iOS設定移動應用程式
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 6%

---

# 針對 iOS 的設定步驟 {#configuring-the-mobile-application-in-adobe-campaign-ios}

![](../../assets/common.svg)

安裝包後，您可以在Adobe Campaign Classic定義您的iOS應用設定。

>[!NOTE]
>
>要瞭解如何為Android配置應用以及如何為Android建立交付，請參閱此 [節](configuring-the-mobile-application-android.md)。

關鍵步驟是：

1. [配置iOS外部帳戶](#configuring-external-account-ios)
1. [配置iOS服務](#configuring-ios-service)
1. [將iOS移動應用整合到活動中](#creating-ios-app)

然後你就能 [為iOS設備建立推送通知](create-notifications-ios.md)。


## 配置iOS外部帳戶 {#configuring-external-account-ios}

對於iOS,iOSHTTP/2連接器將通知發送到HTTP/2 APN。

要配置此連接器，請執行以下步驟：

1. 轉到 **[!UICONTROL Administration > Platform > External accounts]**。
1. 選擇 **[!UICONTROL iOS routing]** 外部帳戶。
1. 在 **[!UICONTROL Connector]** 的 **[!UICONTROL Access URL of the connector]** 欄位，其URL如下： ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. 按一下&#x200B;**[!UICONTROL Save]**。

您的iOS連接器已配置。 您可以開始建立服務。

## 配置iOS服務 {#configuring-ios-service}

>[!CAUTION]
>
>在與Adobe CampaignSDK進行任何整合之前，必須已為推送操作配置了應用程式。
>
>如果情況不是這樣，請參閱 [此頁](https://developer.apple.com/documentation/usernotifications)。

1. 轉到 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 按一下 **[!UICONTROL New]**。

   ![](assets/nmac_service_1.png)

1. 定義 **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]**。
1. 轉到 **[!UICONTROL Type]** 選擇 **[!UICONTROL Mobile application]**。

   >[!NOTE]
   >
   >預設 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 目標映射連結到收件人表。 如果要使用其他目標映射，則需要建立新的目標映射，並在 **[!UICONTROL Target mapping]** 服務欄位。 有關建立目標映射的詳細資訊，請參閱 [配置指南](../../configuration/using/about-custom-recipient-table.md)。

   ![](assets/nmac_ios.png)

1. 然後按一下 **[!UICONTROL Add]** 按鈕。

   ![](assets/nmac_service_2.png)

1. 建立您的iOS開發和生產應用程式。 如需詳細資訊，請參閱本[區段](configuring-the-mobile-application.md#creating-ios-app)。

## 建立iOS移動應用 {#creating-ios-app}

在建立服務後，在市場活動中建立您的iOS應用程式。 請遵循以下步驟：

1. 在新建立的服務中，按一下 **[!UICONTROL Add]** 按鈕。

   ![](assets/nmac_service_2.png)

1. 出現以下窗口。 選擇 **[!UICONTROL Create an iOS application]** 從輸入 **[!UICONTROL Label]**。

   ![](assets/nmac_ios_2.png)

1. 作為一個選項，您可以使用一些 **[!UICONTROL Application variables]** 如果需要。 這些是完全可定製的，並且是發送到移動設備的消息負載的一部分。
在以下示例中，我們添加 **媒體URl** 和 **媒體擴展** 建立富推送通知，然後向應用程式提供要在通知中顯示的影像。

   ![](assets/nmac_ios_3.png)

1. 的 **[!UICONTROL Subscription parameters]** 頁籤中，可以使用 **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 架構。

   >[!NOTE]
   >
   >確保對應用程式的開發版本（沙盒）和生產版本不使用相同的證書。

1. 的 **[!UICONTROL Sounds]** 頁籤中，您可以指定要播放的聲音。 按一下 **[!UICONTROL Add]** 填充 **[!UICONTROL Internal name]** 欄位，該欄位必須包含應用程式中嵌入的檔案名稱或系統聲音的名稱。

1. 按一下 **[!UICONTROL Next]** 開始配置開發應用程式。

1. 確保相同 **[!UICONTROL Integration key]** 在Adobe Campaign和應用程式碼中通過SDK定義。 如需詳細資訊，請參閱[此頁面](integrating-campaign-sdk-into-the-mobile-application.md)。此整合密鑰特定於每個應用程式，使您可以將移動應用程式連結到Adobe Campaign平台。

   >[!NOTE]
   >
   > 的 **[!UICONTROL Integration key]** 完全可自定義，但需要與SDK中指定的值完全相同。

1. 從 **[!UICONTROL Application icon]** 欄位來個性化服務中的移動應用程式。

1. 選取 **[!UICONTROL Authentication mode]**。請注意，以後您總可以在 **[!UICONTROL Certificate]** 頁籤。
   * **[!UICONTROL Certificate-based authentication]**:按一下 **[!UICONTROL Enter the certificate...]**  然後選擇p12密鑰並輸入移動應用程式開發人員提供的密碼。
   * **[!UICONTROL Token-based authentication]**:填寫連接設定 **[!UICONTROL Key ID]**。 **[!UICONTROL Team ID]** 和 **[!UICONTROL Bundle ID]** 然後按一下 **[!UICONTROL Enter the private key]**。 更多內容 **[!UICONTROL Token-based authentication]**，請參閱 [Apple文檔](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns)。

   >[!NOTE]
   >
   > Adobe建議使用 **[!UICONTROL Token-based authentication]** 對於您的iOS配置，因為此身份驗證模式更安全，並且不綁定到證書過期。

   ![](assets/nmac_ios_4.png)

1. 您可以按一下 **[!UICONTROL Test the connection]** 來確保成功。

1. 按一下 **[!UICONTROL Next]** 開始配置生產應用程式，並執行與上面詳述的步驟相同。

   ![](assets/nmac_ios_5.png)

1. 按一下&#x200B;**[!UICONTROL Finish]**。

您的iOS應用程式現已準備好用於Campaign Classic。
