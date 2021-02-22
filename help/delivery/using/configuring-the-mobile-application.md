---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign中設定iOS行動應用程式
description: 瞭解如何針對iOS設定行動應用程式
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 22f44f5723ab35e95caa438583fe06314c763ba1
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 4%

---


# 針對 iOS 的配置步驟 {#configuring-the-mobile-application-in-adobe-campaign-ios}

在安裝套件後，您就可以在Adobe Campaign Classic中定義您的iOS應用程式設定。

>[!NOTE]
>
>若要瞭解如何設定Android應用程式以及如何建立Android的傳送，請參閱此[章節](../../delivery/using/configuring-the-mobile-application-android.md)。

## 設定iOS外部帳戶{#configuring-external-account-ios}

對於iOS,iOS HTTP/2連接器會傳送通知給HTTP/2 APN。

要配置此連接器，請執行以下步驟：

1. 前往&#x200B;**[!UICONTROL Administration > Platform > External accounts]**。
1. 選擇&#x200B;**[!UICONTROL iOS routing]**&#x200B;外部帳戶。
1. 在&#x200B;**[!UICONTROL Connector]**&#x200B;標籤中，以下列URL填入&#x200B;**[!UICONTROL Access URL of the connector]**&#x200B;欄位：```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. 按一下 **[!UICONTROL Save]**。

您的iOS連接器現在已設定。 您可以開始建立服務。

## 配置iOS服務{#configuring-ios-service}

>[!CAUTION]
>
>在與Adobe Campaign SDK整合之前，應用程式必須已設定為推播動作。
>
>如果不是這樣，請參閱[本頁](https://developer.apple.com/documentation/usernotifications)。

1. 轉到&#x200B;**[!UICONTROL Profiles and Targets > Services and subscriptions]**&#x200B;節點，然後按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/nmac_service_1.png)

1. 定義&#x200B;**[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal name]**。
1. 轉至&#x200B;**[!UICONTROL Type]**&#x200B;欄位並選取&#x200B;**[!UICONTROL Mobile application]**。

   >[!NOTE]
   >
   >預設的&#x200B;**[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**&#x200B;目標對應會連結至收件者表格。 如果要使用不同的目標映射，則需要建立新的目標映射，並在服務的&#x200B;**[!UICONTROL Target mapping]**&#x200B;欄位中輸入該映射。 有關建立目標映射的詳細資訊，請參閱[配置指南](../../configuration/using/about-custom-recipient-table.md)。

   ![](assets/nmac_ios.png)

1. 然後，按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以選擇應用程式類型。

   ![](assets/nmac_service_2.png)

1. 建立您的iOS開發與生產應用程式。 如需詳細資訊，請參閱本[區段](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app)。

## 建立iOS行動應用程式{#creating-ios-app}

建立服務後，您現在需要建立您的iOS應用程式：

1. 在新建立的服務中，按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以選擇應用程式類型。

   ![](assets/nmac_service_2.png)

1. 出現以下窗口。 選擇&#x200B;**[!UICONTROL Create an iOS application]**&#x200B;並輸入&#x200B;**[!UICONTROL Label]**&#x200B;開始。

   ![](assets/nmac_ios_2.png)

1. 您也可以視需要使用某些&#x200B;**[!UICONTROL Application variables]**來豐富推播訊息內容。 這些功能可完全自訂，而且是傳送至行動裝置的訊息裝載的一部分。
在下列範例中，我們新增**mediaURl**&#x200B;和&#x200B;**mediaExt**&#x200B;以建立豐富式推播通知，然後將影像提供給應用程式以顯示在通知中。

   ![](assets/nmac_ios_3.png)

1. 使用&#x200B;**[!UICONTROL Subscription parameters]**&#x200B;頁籤可以定義具有&#x200B;**[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**&#x200B;方案副檔名的映射。

   >[!NOTE]
   >
   >請確定您的開發版本（沙盒）和應用程式的生產版本不使用相同的憑證。

1. **[!UICONTROL Sounds]**&#x200B;標籤可讓您指定要播放的音效。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;並填寫&#x200B;**[!UICONTROL Internal name]**&#x200B;欄位，該欄位必須包含應用程式中嵌入的檔案的名稱或系統聲音的名稱。

1. 按一下&#x200B;**[!UICONTROL Next]**&#x200B;開始設定開發應用程式。

1. 請確定Adobe Campaign和應用程式碼中已透過SDK定義相同的&#x200B;**[!UICONTROL Integration key]**。 有關詳情，請參閱：[將Campaign SDK整合至行動應用程式](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)。 此整合金鑰是每個應用程式專屬，可讓您將行動應用程式連結至Adobe Campaign平台。

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]**&#x200B;可完全自訂字串值，但必須與SDK中指定的值完全相同。

1. 從&#x200B;**[!UICONTROL Application icon]**&#x200B;欄位中，選取一個現成可用的圖示，以個人化您服務中的行動應用程式。

1. 選取 **[!UICONTROL Authentication mode]**。請注意，您隨時可以在行動應用程式的&#x200B;**[!UICONTROL Certificate]**&#x200B;標籤中變更驗證模式。
   * **[!UICONTROL Certificate-based authentication]**:按一 **[!UICONTROL Enter the certificate...]**  下，然後選取您的p12金鑰，並輸入行動應用程式開發人員提供的密碼。
   * **[!UICONTROL Token-based authentication]**:填寫連線設定 **[!UICONTROL Key ID]**, **[!UICONTROL Team ID]** 然 **[!UICONTROL Bundle ID]** 後按一下選取p8憑證 **[!UICONTROL Enter the private key]**。有關&#x200B;**[!UICONTROL Token-based authentication]**&#x200B;的更多資訊，請參閱[Apple檔案](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns)。

   >[!NOTE]
   >
   > Adobe建議將&#x200B;**[!UICONTROL Token-based authentication]**&#x200B;用於您的iOS設定，因為此驗證模式更安全，且不會系結至憑證過期。

   ![](assets/nmac_ios_4.png)

1. 您可以按一下&#x200B;**[!UICONTROL Test the connection]**&#x200B;以確定它成功。

1. 按一下&#x200B;**[!UICONTROL Next]**&#x200B;開始設定生產應用程式，並依照上述步驟進行。

   ![](assets/nmac_ios_5.png)

1. 按一下 **[!UICONTROL Finish]**。

您的iOS應用程式現已可供用於Campaign Classic。

## 建立iOS豐富式通知{#creating-ios-delivery}

有了iOS 10或更新版本，就可產生豐富式通知。 Adobe Campaign可以使用變數來傳送通知，讓裝置顯示豐富式通知。

您現在需要建立新的傳送，並將它連結至您建立的行動應用程式。

1. 前往&#x200B;**[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 按一下 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 在&#x200B;**[!UICONTROL Delivery template]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Deliver on iOS (ios)]**。 將&#x200B;**[!UICONTROL Label]**&#x200B;新增至您的傳送。

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;定義要定位的人口。 預設情況下，將應用&#x200B;**[!UICONTROL Subscriber application]**&#x200B;目標映射。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以選擇以前建立的服務。

   ![](assets/nmac_ios_9.png)

1. 在&#x200B;**[!UICONTROL Target type]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Subscribers of an iOS mobile application (iPhone, iPad)]**&#x200B;並按一下&#x200B;**[!UICONTROL Next]**。

1. 在&#x200B;**[!UICONTROL Service]**&#x200B;下拉式清單中，選取您先前建立的服務，然後選取您要定位的應用程式，然後按一下&#x200B;**[!UICONTROL Finish]**。
根據在配置步驟中添加的內容，會自動添加**[!UICONTROL Application variables]**。

   ![](assets/nmac_ios_6.png)

1. 編輯您的豐富式通知。

   ![](assets/nmac_ios_7.png)

1. 勾選編輯通知視窗中的&#x200B;**[!UICONTROL Mutable content]**&#x200B;方塊，讓行動應用程式下載媒體內容。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;並傳送傳送。

當在用戶的行動iOS裝置上收到影像和網頁時，應該會顯示在推播通知中。

![](assets/nmac_ios_8.png)
