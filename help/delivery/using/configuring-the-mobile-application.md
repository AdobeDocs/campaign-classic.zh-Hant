---
product: campaign
title: 在 Adobe Campaign 中設定 iOS 行動應用程式
description: 了解如何為 iOS 設定 行動應用程式
feature: Push
role: User, Developer
level: Intermediate, Experienced
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 3%

---

# 針對 iOS 的設定步驟 {#configuring-the-mobile-application-in-adobe-campaign-ios}

安裝套件後，您可以在Adobe Campaign Classic中定義 iOS 應用程式設置。

關鍵步驟為：

1. [設定 iOS 外部帳戶](#configuring-external-account-ios)
1. [設定 iOS 服務](#configuring-ios-service)
1. [在 Campaign 中整合 iOS 行動應用程式](#creating-ios-app)

接著 [，您可以建立適用於 iOS 裝置的推送通知](create-notifications-ios.md)。

## 設定 iOS 外部帳戶 {#configuring-external-account-ios}

若是 iOS，iOS HTTP/2 連接器會傳送通知至 HTTP/2 APNs。

若要配置此連接器，請執行以下步驟追隨：

1. 轉到 **[!UICONTROL Administration > Platform > External accounts]**。
1. 選取&#x200B;**[!UICONTROL iOS routing]**&#x200B;外部帳戶。
1. 在 **[!UICONTROL Connector]** 標籤 中，使用以下URL填寫 **[!UICONTROL Access URL of the connector]** 字段： ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. 按一下&#x200B;**[!UICONTROL Save]**。

您的 iOS 連接器現已配置完畢。 您可以開始創建服務。

## 設定 iOS 服務 {#configuring-ios-service}

>[!CAUTION]
>
>在與 SDK 進行任何整合之前，應用程式必須已針對推送動作進行配置Adobe Systems。
>
>如果不是這種情況，請参閱 [此頁面](https://developer.apple.com/documentation/usernotifications)。

1. 跳到 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 節點並按下 **[!UICONTROL New]**。

   ![](assets/nmac_service_1.png)

1. 定義 a **[!UICONTROL Label]** 與 **[!UICONTROL Internal name]**。
1. 移至 **[!UICONTROL Type]** 欄位並選擇 **[!UICONTROL Mobile application]**。

   >[!NOTE]
   >
   >默認 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 目標對應連結至收件者表格。 如果要使用其他目標對應，則需要創建一個新目標對應並將其輸入 **[!UICONTROL Target mapping]** 到服務的字段中。 有關創建目標對應的詳細資訊，請參閱 [配置指南](../../configuration/using/about-custom-recipient-table.md)。

   ![](assets/nmac_ios.png)

1. **[!UICONTROL Add]**&#x200B;然後按下按鈕以選擇應用程式類型。

   ![](assets/nmac_service_2.png)

1. 建立您的 iOS 開發和生產應用程式。 如需詳細資訊，請參閱本[區段](configuring-the-mobile-application.md#creating-ios-app)。

## 建立 iOS 行動應用程式 {#creating-ios-app}

創建服務後，在 Campaign 中創建 iOS 應用程式。 請遵循以下步驟：

1. 從新創建的服務中，按兩下 **[!UICONTROL Add]** 按鈕以選擇應用程式類型。

   ![](assets/nmac_service_2.png)

1. 將出現以下視窗。 選擇 **[!UICONTROL Create an iOS application]** 並開始方法是輸入 **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. 必要時，您也可以選擇使用一些 **[!UICONTROL Application variables]** 來豐富推送訊息內容。 這些是完全可自定義的，並且是發送到行動裝置的消息負載的一部分。在下面的示例中，我們添加 **mediaURl** 和 **mediaExt** 以創建豐富的推送通知，然後為應用程式提供要在通知中顯示的圖像。

   ![](assets/nmac_ios_3.png)

1. **[!UICONTROL Subscription parameters]**&#x200B;索引標籤可讓您以&#x200B;**[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**&#x200B;結構描述的副檔名定義對應。

   >[!NOTE]
   >
   >確保不要對應用程式的開發版本（沙盒）和生產版本使用相同的證書。

1. 該 **[!UICONTROL Sounds]** 標籤允許您指定要播放的聲音。 按兩下 **[!UICONTROL Add]** 並填寫 **[!UICONTROL Internal name]** 字段，該字段必須包含嵌入應用程式中的文件的名稱或系統聲音的名稱。

1. 按兩下 **[!UICONTROL Next]** 以開始配置開發應用程式。

1. 請確認在 Adobe Campaign 中以及透過 SDK 在應用程式代碼中定義相同 **[!UICONTROL Integration key]** 值。 <!--For more on this, refer to [this page](integrating-campaign-sdk-into-the-mobile-application.md).--> 此整合金鑰特定于每個應用程式，可讓您將行動應用程式連結到 Adobe Campaign 平台。

   >[!NOTE]
   >
   > 可 **[!UICONTROL Integration key]** 完全自定義字串值，但需要與 SDK 中指定的字串完全相同。

1. 從欄位中選擇一個 **[!UICONTROL Application icon]** 現成的圖示以個人化服務中的行動應用程式。

1. 選取 **[!UICONTROL Authentication mode]**。

   ![](assets/nmac_ios_5.png)

   有兩種模式可用：

   * （推薦）： **[!UICONTROL Token-based authentication]**&#x200B;填寫 APNs 連接設置 **[!UICONTROL Key Id]**， **[!UICONTROL Team Id]** 然後按下 **[!UICONTROL Bundle Id]** 選擇您的 p8 證書 **[!UICONTROL Enter the private key...]**。 有關的詳細資訊 **[!UICONTROL Token-based authentication]**，請參閱 [Apple文件](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}。

   * **[!UICONTROL Certificate-based authentication]**：按兩下 **[!UICONTROL Enter the certificate...]**  然後選擇您的 p12 金鑰並輸入 行動應用程式 開發人員提供的密碼。

   >[!NOTE]
   >
   > Adobe Systems建議為您的 iOS 配置使用 **[!UICONTROL Token-based authentication]** ，因為 P8 身份驗證密鑰更新且更安全。

1. **[!UICONTROL Test the connection]**&#x200B;使用按鈕驗證配置。

1. 按下 **[!UICONTROL Next]** 以開始配置生產應用程式，然後追隨上面詳述的相同步驟。


1. 按一下&#x200B;**[!UICONTROL Finish]**。

您的 iOS 應用程式現在已準備就緒，可以在 Campaign Classic 中使用。
