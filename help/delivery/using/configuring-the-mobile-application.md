---
product: campaign
title: 在Adobe Campaign中設定iOS行動應用程式
description: 了解如何為iOS設定行動應用程式
feature: Push
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: fd19a2f11773e9e4c841f685a3491a763493e572
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 6%

---

# 針對 iOS 的設定步驟 {#configuring-the-mobile-application-in-adobe-campaign-ios}

![](../../assets/common.svg)

安裝套件後，您就可以在Adobe Campaign Classic中定義iOS應用程式設定。

>[!NOTE]
>
>若要了解如何為Android設定您的應用程式，以及如何建立Android的傳送，請參閱以下內容 [節](configuring-the-mobile-application-android.md).

關鍵步驟為：

1. [設定iOS外部帳戶](#configuring-external-account-ios)
1. [設定iOS服務](#configuring-ios-service)
1. [將iOS行動應用程式整合至Campaign](#creating-ios-app)

然後，您就能 [為iOS裝置建立推播通知](create-notifications-ios.md).


## 設定iOS外部帳戶 {#configuring-external-account-ios}

若為iOS,iOS HTTP/2連接器會傳送通知至HTTP/2 APN。

要配置此連接器，請執行以下步驟：

1. 前往 **[!UICONTROL Administration > Platform > External accounts]**.
1. 選取 **[!UICONTROL iOS routing]** 外部帳戶。
1. 在 **[!UICONTROL Connector]** 頁簽，填寫 **[!UICONTROL Access URL of the connector]** 欄位中填入下列URL: ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. 按一下&#x200B;**[!UICONTROL Save]**。

您的iOS連接器現已設定完畢。 您可以開始建立服務。

## 設定iOS服務 {#configuring-ios-service}

>[!CAUTION]
>
>應用程式必須先設定為「推送」動作，才能進行與AdobeSDK的任何整合。
>
>若非如此，請參閱 [本頁](https://developer.apple.com/documentation/usernotifications).

1. 前往 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 節點，按一下 **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. 定義 **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]**.
1. 前往 **[!UICONTROL Type]** 欄位和選取 **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >預設 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 目標對應連結至收件者表格。 如果您想使用不同的目標對應，則需要建立新的目標對應，然後在 **[!UICONTROL Target mapping]** 服務欄位。 如需建立目標對應的詳細資訊，請參閱 [設定指南](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. 然後按一下 **[!UICONTROL Add]** 按鈕，選擇應用程式類型。

   ![](assets/nmac_service_2.png)

1. 建立您的iOS開發與生產應用程式。 如需詳細資訊，請參閱本[區段](configuring-the-mobile-application.md#creating-ios-app)。

## 建立iOS行動應用程式 {#creating-ios-app}

建立服務後，在Campaign中建立iOS應用程式。 請遵循以下步驟：

1. 在新建立的服務中，按一下 **[!UICONTROL Add]** 按鈕，選擇應用程式類型。

   ![](assets/nmac_service_2.png)

1. 出現以下窗口。 選擇 **[!UICONTROL Create an iOS application]** 然後從輸入 **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. 作為選項，您可以使用一些 **[!UICONTROL Application variables]** 如有需要。 這些功能可完全自訂，且是傳送至行動裝置之訊息裝載的一部分。
在下列範例中，我們新增 **mediaURl** 和 **mediaExt** 若要建立豐富推送通知，然後為應用程式提供要在通知內顯示的影像。

   ![](assets/nmac_ios_3.png)

1. 此 **[!UICONTROL Subscription parameters]** 索引標籤可讓您以 **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 綱要。

   >[!NOTE]
   >
   >請確定您的開發版本（沙箱）和應用程式的生產版本不使用相同的憑證。

1. 此 **[!UICONTROL Sounds]** 索引標籤可讓您指定要播放的音效。 按一下 **[!UICONTROL Add]** 填 **[!UICONTROL Internal name]** 欄位，必須包含應用程式中嵌入的檔案的名稱或系統聲音的名稱。

1. 按一下 **[!UICONTROL Next]** 以開始設定開發應用程式。

1. 確保相同 **[!UICONTROL Integration key]** 是在Adobe Campaign中定義，並透過SDK在應用程式程式碼中定義。 如需詳細資訊，請參閱[此頁面](integrating-campaign-sdk-into-the-mobile-application.md)。此整合金鑰是每個應用程式專屬的，可讓您將行動應用程式連結至Adobe Campaign平台。

   >[!NOTE]
   >
   > 此 **[!UICONTROL Integration key]** 可以使用字串值完全自訂，但必須與SDK中指定的值完全相同。

1. 從 **[!UICONTROL Application icon]** 欄位來個人化您服務中的行動應用程式。

1. 選取 **[!UICONTROL Authentication mode]**。請注意，您隨時可以在 **[!UICONTROL Certificate]** 標籤。
   * **[!UICONTROL Certificate-based authentication]**:按一下 **[!UICONTROL Enter the certificate...]**  然後選取您的p12金鑰，並輸入行動應用程式開發人員提供的密碼。
   * **[!UICONTROL Token-based authentication]**:填入連線設定 **[!UICONTROL Key ID]**, **[!UICONTROL Team ID]** 和 **[!UICONTROL Bundle ID]** 然後按一下 **[!UICONTROL Enter the private key]**. 如需詳細資訊 **[!UICONTROL Token-based authentication]**，請參閱 [Apple檔案](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns).

   >[!NOTE]
   >
   > Adobe建議使用 **[!UICONTROL Token-based authentication]** 的iOS設定，因為此驗證模式較安全，且未系結至憑證過期。

   ![](assets/nmac_ios_4.png)

1. 您可以按一下 **[!UICONTROL Test the connection]** 以確保成功。

1. 按一下 **[!UICONTROL Next]** 若要開始設定生產應用程式，請依照上述步驟操作。

   ![](assets/nmac_ios_5.png)

1. 按一下&#x200B;**[!UICONTROL Finish]**。

您的iOS應用程式現在已準備好用於Campaign Classic。
