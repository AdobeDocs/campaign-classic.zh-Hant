---
product: campaign
title: 在Adobe Campaign中設定iOS行動應用程式
description: 瞭解如何設定iOS的行動應用程式
feature: Push
role: User, Developer
exl-id: 67eee1c5-a918-46b9-875d-7c3c71c00635
source-git-commit: 81b47231b027a189bc8b9029b7d48939734d08ed
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 3%

---

# 針對 iOS 的設定步驟 {#configuring-the-mobile-application-in-adobe-campaign-ios}

安裝套件後，您可以在Adobe Campaign Classic中定義iOS應用程式設定。

主要步驟為：

1. [設定iOS外部帳戶](#configuring-external-account-ios)
1. [設定iOS服務](#configuring-ios-service)
1. [在Campaign中整合iOS行動應用程式](#creating-ios-app)

然後，您就可以[建立iOS裝置的推播通知](create-notifications-ios.md)。

## 設定iOS外部帳戶 {#configuring-external-account-ios}

對於iOS，iOS HTTP/2聯結器會傳送通知至HTTP/2 APN。

若要設定此聯結器，請遵循下列步驟：

1. 移至&#x200B;**[!UICONTROL Administration > Platform > External accounts]**。
1. 選取&#x200B;**[!UICONTROL iOS routing]**&#x200B;外部帳戶。
1. 在&#x200B;**[!UICONTROL Connector]**&#x200B;索引標籤中，使用下列URL填入&#x200B;**[!UICONTROL Access URL of the connector]**&#x200B;欄位： ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. 按一下&#x200B;**[!UICONTROL Save]**。

您的iOS聯結器現已設定完成。 您可以開始建立服務。

## 設定iOS服務 {#configuring-ios-service}

>[!CAUTION]
>
>在將應用程式與Adobe SDK進行任何整合之前，必須先設定推送動作。
>
>如果不是這種情況，請參考[此頁面](https://developer.apple.com/documentation/usernotifications)。

1. 前往&#x200B;**[!UICONTROL Profiles and Targets > Services and subscriptions]**&#x200B;節點並按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/nmac_service_1.png)

1. 定義&#x200B;**[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Internal name]**。
1. 移至&#x200B;**[!UICONTROL Type]**&#x200B;欄位並選取&#x200B;**[!UICONTROL Mobile application]**。

   >[!NOTE]
   >
   >預設&#x200B;**[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**&#x200B;目標對應已連結至收件者表格。 如果您想使用不同的目標對應，則需要建立新的目標對應，並在服務的&#x200B;**[!UICONTROL Target mapping]**&#x200B;欄位中輸入它。 如需建立目標對應的詳細資訊，請參閱[組態指南](../../configuration/using/about-custom-recipient-table.md)。

   ![](assets/nmac_ios.png)

1. 然後按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以選取應用程式型別。

   ![](assets/nmac_service_2.png)

1. 建立您的iOS開發和生產應用程式。 如需詳細資訊，請參閱本[區段](configuring-the-mobile-application.md#creating-ios-app)。

## 建立iOS行動應用程式 {#creating-ios-app}

建立服務後，請在Campaign中建立iOS應用程式。 請遵循以下步驟：

1. 從您新建立的服務中，按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以選取應用程式型別。

   ![](assets/nmac_service_2.png)

1. 下列視窗會出現。 選取&#x200B;**[!UICONTROL Create an iOS application]**&#x200B;並輸入&#x200B;**[!UICONTROL Label]**&#x200B;以開始。

   ![](assets/nmac_ios_2.png)

1. 您可以視需要以約&#x200B;**[!UICONTROL Application variables]**擴充推送訊息內容，作為選項。 這些都是可完全自訂的專案，而且是傳送至行動裝置的訊息裝載的一部分。
在下列範例中，我們新增**mediaURl**&#x200B;和&#x200B;**mediaExt**&#x200B;來建立豐富推送通知，然後提供應用程式要在通知內顯示的影像。

   ![](assets/nmac_ios_3.png)

1. **[!UICONTROL Subscription parameters]**&#x200B;索引標籤可讓您以&#x200B;**[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**&#x200B;結構描述的副檔名定義對應。

   >[!NOTE]
   >
   >請務必不要在應用程式的開發版本（沙箱）和生產版本中使用相同的憑證。

1. **[!UICONTROL Sounds]**&#x200B;索引標籤可讓您指定要播放的聲音。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;並填入&#x200B;**[!UICONTROL Internal name]**&#x200B;欄位，欄位必須包含內嵌於應用程式中的檔案名稱或系統聲音名稱。

1. 按一下&#x200B;**[!UICONTROL Next]**&#x200B;開始設定開發應用程式。

1. 確定透過SDK在Adobe Campaign和應用程式程式碼中定義了相同的&#x200B;**[!UICONTROL Integration key]**。 <!--For more on this, refer to [this page](integrating-campaign-sdk-into-the-mobile-application.md).-->此整合金鑰是每個應用程式專屬的金鑰，可讓您將行動應用程式連結至Adobe Campaign平台。

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]**&#x200B;可使用字串值完全自訂，但必須與SDK中指定的完全相同。

1. 從&#x200B;**[!UICONTROL Application icon]**&#x200B;欄位選取其中一個現成的圖示，以個人化您服務中的行動應用程式。

1. 選取 **[!UICONTROL Authentication mode]**。

   ![](assets/nmac_ios_5.png)

   提供兩種模式：

   * （建議） **[!UICONTROL Token-based authentication]**：填入APNs連線設定&#x200B;**[!UICONTROL Key Id]**、**[!UICONTROL Team Id]**&#x200B;和&#x200B;**[!UICONTROL Bundle Id]**，然後按一下&#x200B;**[!UICONTROL Enter the private key...]**&#x200B;以選取您的p8憑證。 如需&#x200B;**[!UICONTROL Token-based authentication]**&#x200B;的詳細資訊，請參閱[Apple檔案](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}。

   * **[!UICONTROL Certificate-based authentication]**：按一下&#x200B;**[!UICONTROL Enter the certificate...]**，然後選取您的p12金鑰並輸入行動應用程式開發人員提供的密碼。

   >[!NOTE]
   >
   > Adobe建議將&#x200B;**[!UICONTROL Token-based authentication]**&#x200B;用於iOS設定，因為P8驗證金鑰較新且較安全。

1. 使用&#x200B;**[!UICONTROL Test the connection]**&#x200B;按鈕驗證您的設定。

1. 按一下&#x200B;**[!UICONTROL Next]**&#x200B;開始設定生產應用程式，並依照上述步驟執行。


1. 按一下&#x200B;**[!UICONTROL Finish]**。

您的iOS應用程式現在已準備好用於Campaign Classic。
