---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign中設定iOS行動應用程式
description: 瞭解如何針對iOS設定行動應用程式
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 7%

---


# 針對 iOS 的配置步驟 {#configuring-the-mobile-application-in-adobe-campaign-ios}

在安裝套件後，您就可以在Adobe Campaign Classic中定義您的iOS應用程式設定。

>[!NOTE]
>
>若要瞭解如何設定Android適用的應用程式，以及如何建立Android適用的傳送，請參閱此 [節](../../delivery/using/configuring-the-mobile-application-android.md)。

## 設定iOS外部帳戶 {#configuring-external-account-ios}

對於iOS,iOS HTTP/2連接器會傳送通知給HTTP/2 APN。

要配置此連接器，請執行以下步驟：

1. 前往 **[!UICONTROL Administration > Platform > External accounts]**。
1. Select the **[!UICONTROL iOS routing]** external account.
1. 在標籤 **[!UICONTROL Connector]** 中，以下列URL填 **[!UICONTROL Access URL of the connector]** 寫欄位： ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   >[!NOTE]
   >
   > 自 Campaign 第 20.3 發行版本開始，已棄用舊的 iOS 二進位連接器。如果您使用此連接器，則需要據此調整實施。[進一步瞭解](https://helpx.adobe.com/tw/campaign/kb/migrate-to-apns-http2.html)

   ![](assets/nmac_connectors.png)

1. 按一下 **[!UICONTROL Save]**。

您的iOS連接器現在已設定。 您可以開始建立服務。

## 設定iOS服務 {#configuring-ios-service}

>[!CAUTION]
>
>在與Adobe Campaign SDK整合之前，應用程式必須已設定為推播動作。
>
>如果不是這樣，請參閱 [本頁](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/)。

1. 轉到節 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 點並按一下 **[!UICONTROL New]**。

   ![](assets/nmac_service_1.png)

1. Define a **[!UICONTROL Label]** and an **[!UICONTROL Internal name]**.
1. 轉至欄位 **[!UICONTROL Type]** 並選取 **[!UICONTROL Mobile application]**。

   >[!NOTE]
   >
   >預設的 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 目標對應會連結至收件者表格。 如果要使用不同的目標映射，則需要建立新的目標映射並在服務的字 **[!UICONTROL Target mapping]** 段中輸入。 有關建立目標映射的詳細資訊，請參 [閱配置指南](../../configuration/using/about-custom-recipient-table.md)。

   ![](assets/nmac_ios.png)

1. 然後按一下 **[!UICONTROL Add]** 按鈕以選取應用程式類型。

   ![](assets/nmac_service_2.png)

1. 建立您的iOS開發與生產應用程式。 如需詳細資訊，請參閱本[區段](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app)。

## 建立iOS行動應用程式 {#creating-ios-app}

建立服務後，您現在需要建立您的iOS應用程式：

1. 從您新建立的服務中，按一下 **[!UICONTROL Add]** 按鈕以選擇應用程式類型。

   ![](assets/nmac_service_2.png)

1. 出現以下窗口。 選 **[!UICONTROL Create an iOS application]** 擇，然後輸入 **[!UICONTROL Label]**。

   ![](assets/nmac_ios_2.png)

1. 您也可以視需要，以一些內容豐富推播 **[!UICONTROL Application variables]** 訊息內容。 這些功能可完全自訂，而且是傳送至行動裝置的訊息裝載的一部分。
在下列範例中，我們新增 **mediaURl** 和 **mediaExt** ，以建立豐富式推播通知，然後將影像提供給應用程式以顯示在通知中。

   ![](assets/nmac_ios_3.png)

1. 該選 **[!UICONTROL Subscription parameters]** 項卡允許您定義具有方案副檔名的映 **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 射。

   >[!NOTE]
   >
   >請確定您的開發版本（沙盒）和應用程式的生產版本不使用相同的憑證。

1. 此標 **[!UICONTROL Sounds]** 簽可讓您指定要播放的音效。 按一 **[!UICONTROL Add]** 下並填 **[!UICONTROL Internal name]** 寫欄位，欄位中必須包含應用程式中內嵌檔案的名稱或系統音效的名稱。

1. 按一 **[!UICONTROL Next]** 下以開始設定開發應用程式。

1. 請務必在Adobe **[!UICONTROL Integration key]** Campaign和應用程式程式碼中透過SDK定義相同的內容。 有關詳情，請參閱： [將Campaign SDK整合至行動應用程式](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)。 此整合金鑰是每個應用程式專屬，可讓您將行動應用程式連結至Adobe Campaign平台。

   >[!NOTE]
   >
   > 可 **[!UICONTROL Integration key]** 完全自訂字串值，但必須與SDK中指定的值完全相同。

1. 從欄位中選取一個現成可用的圖示，以個人化 **[!UICONTROL Application icon]** 您服務中的行動應用程式。

1. 選取 **[!UICONTROL Authentication mode]**。請注意，您稍後隨時都可以在行動應用程式的標籤 **[!UICONTROL Certificate]** 中變更驗證模式。
   * **[!UICONTROL Certificate-based authentication]**:按一 **[!UICONTROL Enter the certificate...]** 下，然後選取您的p12金鑰，並輸入行動應用程式開發人員提供的密碼。
   * **[!UICONTROL Token-based authentication]**:填寫連線設定 **[!UICONTROL Key ID]**, **[!UICONTROL Team ID]** 然 **[!UICONTROL Bundle ID]** 後按一下選取p8憑證 **[!UICONTROL Enter the private key]**。 For more on **[!UICONTROL Token-based authentication]**, refer to [Apple documentation](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns).

   >[!NOTE]
   >
   > Adobe建議您針 **[!UICONTROL Token-based authentication]** 對iOS設定使用，因為此驗證模式的安全性更高，且不會系結至憑證過期。

   ![](assets/nmac_ios_4.png)

1. 您可以按一 **[!UICONTROL Test the connection]** 下以確認它成功。

1. 按一 **[!UICONTROL Next]** 下以開始設定生產應用程式，並依照上述步驟進行。

   ![](assets/nmac_ios_5.png)

1. 按一下 **[!UICONTROL Finish]**。

您的iOS應用程式現已可供用於Campaign Classic。

## 建立iOS豐富式通知 {#creating-ios-delivery}

有了iOS 10或更新版本，就可產生豐富式通知。 Adobe Campaign可以使用變數來傳送通知，讓裝置顯示豐富式通知。

您現在需要建立新的傳送，並將它連結至您建立的行動應用程式。

1. 前往 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 按一下 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 在下 **[!UICONTROL Deliver on iOS (ios)]** 拉式清 **[!UICONTROL Delivery template]** 單中選取。 新增至 **[!UICONTROL Label]** 您的傳送。

1. 按一 **[!UICONTROL To]** 下以定義要定位的人口。 預設會套用 **[!UICONTROL Subscriber application]** 目標對應。 按一 **[!UICONTROL Add]** 下以選取我們先前建立的服務。

   ![](assets/nmac_ios_9.png)

1. 在窗口 **[!UICONTROL Target type]** 中，選擇並 **[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]** 按一下 **[!UICONTROL Next]**。

1. 在下拉 **[!UICONTROL Service]** 式清單中，選取您先前建立的服務，然後選取您要定位的應用程式，然後按一下 **[!UICONTROL Finish]**。
根 **[!UICONTROL Application variables]** 據在配置步驟中添加的內容自動添加。

   ![](assets/nmac_ios_6.png)

1. 編輯您的豐富式通知。

   ![](assets/nmac_ios_7.png)

1. 核取編輯 **[!UICONTROL Mutable content]** 通知視窗中的方塊，讓行動應用程式下載媒體內容。

1. 按一 **[!UICONTROL Save]** 下並傳送您的傳送。

當在用戶的行動iOS裝置上收到影像和網頁時，應該會顯示在推播通知中。

![](assets/nmac_ios_8.png)
