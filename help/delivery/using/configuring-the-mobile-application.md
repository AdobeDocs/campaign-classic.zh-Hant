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

然後，您將能夠 [為iOS裝置建立推播通知](create-notifications-ios.md).

## 設定iOS外部帳戶 {#configuring-external-account-ios}

對於iOS，iOS HTTP/2聯結器會傳送通知至HTTP/2 APN。

若要設定此聯結器，請遵循下列步驟：

1. 前往 **[!UICONTROL Administration > Platform > External accounts]**.
1. 選取 **[!UICONTROL iOS routing]** 外部帳戶。
1. 在 **[!UICONTROL Connector]** 標籤，填入 **[!UICONTROL Access URL of the connector]** 具有下列URL的欄位： ```http://localhost:8080/nms/jsp/iosHTTP2.jsp```

   ![](assets/nmac_connectors.png)

1. 按一下&#x200B;**[!UICONTROL Save]**。

您的iOS聯結器現已設定完成。 您可以開始建立服務。

## 設定iOS服務 {#configuring-ios-service}

>[!CAUTION]
>
>在將應用程式與Adobe SDK進行任何整合之前，必須先設定推送動作。
>
>如果不是這種情況，請參閱 [此頁面](https://developer.apple.com/documentation/usernotifications).

1. 前往 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 節點並按一下 **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. 定義 **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]**.
1. 前往 **[!UICONTROL Type]** 欄位並選取 **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >預設 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 目標對應會連結至收件者表格。 如果您想使用不同的目標對應，則需要建立新的目標對應，並在 **[!UICONTROL Target mapping]** 服務的欄位。 有關建立目標對應的詳細資訊，請參閱 [設定指南](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. 然後按一下 **[!UICONTROL Add]** 按鈕以選取應用程式型別。

   ![](assets/nmac_service_2.png)

1. 建立您的iOS開發和生產應用程式。 如需詳細資訊，請參閱本[區段](configuring-the-mobile-application.md#creating-ios-app)。

## 建立iOS行動應用程式 {#creating-ios-app}

建立服務後，請在Campaign中建立iOS應用程式。 請遵循以下步驟：

1. 從您新建立的服務，按一下 **[!UICONTROL Add]** 按鈕以選取應用程式型別。

   ![](assets/nmac_service_2.png)

1. 下列視窗會出現。 選取 **[!UICONTROL Create an iOS application]** 並從輸入 **[!UICONTROL Label]**.

   ![](assets/nmac_ios_2.png)

1. 或者，您也可以選擇擴充推送訊息的內容 **[!UICONTROL Application variables]** 如有需要。 這些都是可完全自訂的專案，而且是傳送至行動裝置的訊息裝載的一部分。
在以下範例中，我們新增 **mediaURl** 和 **mediaExt** 以建立豐富推送通知，然後為應用程式提供要在通知內顯示的影像。

   ![](assets/nmac_ios_3.png)

1. 此 **[!UICONTROL Subscription parameters]** 標籤可讓您定義具有擴充功能的對應， **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 綱要。

   >[!NOTE]
   >
   >請務必不要在應用程式的開發版本（沙箱）和生產版本中使用相同的憑證。

1. 此 **[!UICONTROL Sounds]** 索引標籤可讓您指定要播放的聲音。 按一下 **[!UICONTROL Add]** 並填滿 **[!UICONTROL Internal name]** 欄位，其中必須包含內嵌於應用程式中的檔案名稱或系統聲音名稱。

1. 按一下 **[!UICONTROL Next]** 以開始設定開發應用程式。

1. 確定相同 **[!UICONTROL Integration key]** 是透過SDK在Adobe Campaign和應用程式程式碼中定義的。 <!--For more on this, refer to [this page](integrating-campaign-sdk-into-the-mobile-application.md).--> 此整合金鑰是每個應用程式專屬的金鑰，可讓您將行動應用程式連結至Adobe Campaign平台。

   >[!NOTE]
   >
   > 此 **[!UICONTROL Integration key]** 可使用字串值完全自訂，但需與SDK中指定的值完全相同。

1. 從「 」中選取其中一個現成可用的圖示 **[!UICONTROL Application icon]** 欄位來個人化您服務中的行動應用程式。

1. 選取 **[!UICONTROL Authentication mode]**。

   ![](assets/nmac_ios_5.png)

   提供兩種模式：

   * （建議） **[!UICONTROL Token-based authentication]**：填入APNs連線設定 **[!UICONTROL Key Id]**， **[!UICONTROL Team Id]** 和 **[!UICONTROL Bundle Id]** 然後按一下「 」以選取您的p8憑證 **[!UICONTROL Enter the private key...]**. 有關詳細資訊 **[!UICONTROL Token-based authentication]**，請參閱 [Apple檔案](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_token-based_connection_to_apns){target="_blank"}.

   * **[!UICONTROL Certificate-based authentication]**：按一下 **[!UICONTROL Enter the certificate...]**  接著，選取您的p12金鑰並輸入行動應用程式開發人員提供的密碼。

   >[!NOTE]
   >
   > Adobe建議使用 **[!UICONTROL Token-based authentication]** 用於您的iOS設定，因為P8驗證金鑰更新且更安全。

1. 使用 **[!UICONTROL Test the connection]** 按鈕以驗證您的設定。

1. 按一下 **[!UICONTROL Next]** 以開始設定生產應用程式，並依照上述步驟進行。


1. 按一下&#x200B;**[!UICONTROL Finish]**。

您的iOS應用程式現在已準備好用於Campaign Classic。
