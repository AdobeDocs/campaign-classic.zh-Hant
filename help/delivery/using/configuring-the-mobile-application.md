---
title: 在Adobe Campaign中設定行動應用程式
seo-title: 在Adobe Campaign中設定行動應用程式
description: 在Adobe Campaign中設定行動應用程式
seo-description: null
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a358da7c499b5ee780563b4aef0eb2f4463186cf

---


# 在Adobe Campaign中設定行動應用程式 {#configuring-the-mobile-application-in-adobe-campaign}

您可以根據銷售線上假日套件的公司，在下方找到設定範例。 他的行動應用程式(Neotrips)有兩種版本可供客戶使用：iOS專用的Neotrips和Neotrips。 若要在Adobe Campaign中設定行動應用程式，您必須：

* 為Neotrips行 **[!UICONTROL Mobile application]** 動應用程式建立類型資訊服務。
* 將應用程式的iOS和Android版本新增至此服務。
* 建立iOS和Android的傳送。

![](assets/nmac_service_diagram.png)

>[!NOTE]
>
>前往服 **[!UICONTROL Subscriptions]** 務的標籤，檢視服務訂閱者清單，即所有已在行動裝置上安裝應用程式並同意接收通知的使用者。

## 使用iOS設定行動應用程式 {#configuring-the-mobile-application-ios}

>[!CAUTION]
>
>在與Adobe Campaign SDK整合之前，應用程式必須已設定為推播動作。
>
>如果不是這樣，請參閱 [本頁](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/)。

### 步驟1:安裝軟體包 {#installing-package-ios}

1. 從Adobe Campaign用戶端主控台 **[!UICONTROL Tools > Advanced > Package import...]** 存取套件匯入精靈。

   ![](assets/package_ios.png)

1. Select **[!UICONTROL Install a standard package]**.

1. 在出現的清單中，勾選 **[!UICONTROL Mobile App Channel]**。

   ![](assets/package_ios_2.png)

1. 按一下 **[!UICONTROL Next]**，然 **[!UICONTROL Start]** 後啟動軟體包安裝。

   安裝軟體包後，進度欄顯示 **100%** ，您可以在安裝日誌中看到以下消息： **[!UICONTROL Installation of packages successful]**。

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 安裝窗口。

### 步驟2:設定iOS外部帳戶 {#configuring-external-account-ios}

對於iOS，有兩個連接器可用：

* iOS二進位連接器會在舊版二進位APNS伺服器上傳送通知。
* iOS HTTP/2連接器會傳送通知給HTTP/2 APNS。

要選擇要使用的連接器，請執行以下步驟：

1. 前往 **[!UICONTROL Administration > Platform > External accounts]**。
1. 選擇外 **[!UICONTROL iOS routing]** 部帳戶。
1. 在標籤 **[!UICONTROL Connector]** 中，填寫欄 **[!UICONTROL Access URL of the connector]** 位：

   對於iOS HTTP2:http://localhost:8080/nms/jsp/iosHTTP2.jsp

   ![](assets/nmac_connectors.png)

   >[!NOTE]
   >
   > 您也可以依https://localhost:8080/nms/jsp/ios.jsp設定，但建議您使用第2版的連接器。

1. 按一下 **[!UICONTROL Save]**.

您的iOS連接器現在已設定。 您可以開始建立服務。

### 步驟3:設定iOS服務 {#configuring-ios-service}

1. 轉到節 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 點並按一下 **[!UICONTROL New]**。

   ![](assets/nmac_service_1.png)

1. 定義 **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]**。
1. 轉至欄位 **[!UICONTROL Type]** 並選取 **[!UICONTROL Mobile application]**。

   >[!NOTE]
   >
   >預設的 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 目標對應會連結至收件者表格。 如果要使用不同的目標映射，則需要建立新的目標映射並在服務的字 **[!UICONTROL Target mapping]** 段中輸入。 有關建立目標映射的詳細資訊，請參 [閱配置指南](../../configuration/using/about-custom-recipient-table.md)。

   ![](assets/nmac_ios.png)

1. 然後按一下 **[!UICONTROL Add]** 按鈕以選取應用程式類型。

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

1. 請務必在Adobe **[!UICONTROL Integration key]** Campaign和應用程式程式碼中透過SDK定義相同的內容。 有關詳情，請參閱：將 [Campaign SDK整合至行動應用程式](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)。 此整合金鑰是每個應用程式專屬，可讓您將行動應用程式連結至Adobe Campaign平台。

   >[!NOTE]
   >
   > 可 **[!UICONTROL Integration key]** 完全自訂字串值，但必須與SDK中指定的值完全相同。

1. 從欄位中選取一個現成可用的圖示，以個人化 **[!UICONTROL Application icon]** 您服務中的行動應用程式。

1. 按一下 **[!UICONTROL Enter the certificate...]** 連結，然後選取驗證憑證並輸入行動應用程式開發人員提供的密碼。 您可以按一 **[!UICONTROL Test the connection]** 下以確認它成功。

   >[!NOTE]
   >
   >Apple針對相同行動應用程式的開發與生產版本要求不同的憑證。 您需要在Adobe Campaign中設定兩個不同的應用程式。

   ![](assets/nmac_ios_4.png)

1. 按一 **[!UICONTROL Next]** 下以開始設定生產應用程式，並依照上述步驟進行。

   ![](assets/nmac_ios_5.png)

1. 按一下 **[!UICONTROL Finish]**. 您的iOS應用程式現已可供用於Campaign Classic。

### 步驟4:建立iOS豐富式通知 {#creating-ios-delivery}

有了iOS 10或更新版本，就可產生豐富式通知。 Adobe Campaign可以使用變數來傳送通知，讓裝置顯示豐富式通知。

您現在需要建立新的傳送，並將它連結至您建立的行動應用程式。

1. 前往 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 按一下 **[!UICONTROL New]**.

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

## 使用Android設定行動應用程式 {#configuring-the-mobile-application-android}

### 步驟1:安裝軟體包 {#installing-package-android}

1. 從Adobe Campaign用戶端主控台 **[!UICONTROL Tools > Advanced > Package import...]** 存取套件匯入精靈。

   ![](assets/package_ios.png)

1. Select **[!UICONTROL Install a standard package]**.

1. 在出現的清單中，勾選 **[!UICONTROL Mobile App Channel]**。

   ![](assets/package_ios_2.png)

1. 按一下 **[!UICONTROL Next]**，然 **[!UICONTROL Start]** 後啟動軟體包安裝。

   安裝軟體包後，進度欄顯示 **100%** ，您可以在安裝日誌中看到以下消息： **[!UICONTROL Installation of packages successful]**。

   ![](assets/package_ios_3.png)

1. **[!UICONTROL Close]** 安裝窗口。

### 步驟2:設定Android外部帳戶 {#configuring-external-account-android}

對於Android，有兩個連接器可用：

* V1連接器，允許每個MTA子項連接一個。
* V2連接器允許與FCM伺服器同時連接，以提高吞吐量。

要選擇要使用的連接器，請執行以下步驟：

1. 前往 **[!UICONTROL Administration > Platform > External accounts]**。
1. 選擇外 **[!UICONTROL Android routing]** 部帳戶。
1. 在標籤 **[!UICONTROL Connector]** 中，填寫欄 **[!UICONTROL JavaScript used in the connector]** 位：

   針對Android V2:https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > 您也可以依https://localhost:8080/nms/jsp/androidPushConnector.js設定，但建議您使用第2版的連接器。

   ![](assets/nmac_connectors3.png)

1. 對於Android V2,Adobe Server組態檔(serverConf.xml)中還有一個參數：

   * **maxGCMConnectPerChild**:每個子伺服器啟動的FCM的並行HTTP請求的最大限制（預設為8）。

### 步驟3:設定Android服務 {#configuring-android-service}

1. 轉到節 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 點並按一下 **[!UICONTROL New]**。

   ![](assets/nmac_service_1.png)

1. 定義 **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]**。
1. 轉至欄位 **[!UICONTROL Type]** 並選取 **[!UICONTROL Mobile application]**。

   >[!NOTE]
   >
   >預設的 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 目標對應會連結至收件者表格。 如果要使用不同的目標映射，則需要建立新的目標映射並在服務的字 **[!UICONTROL Target mapping]** 段中輸入。 有關建立目標映射的詳細資訊，請參 [閱配置指南](../../configuration/using/about-custom-recipient-table.md)。

   ![](assets/nmac_ios.png)

1. 然後按一下 **[!UICONTROL Add]** 按鈕以選取應用程式類型。

   ![](assets/nmac_service_2.png)

1. Select **[!UICONTROL Create an Android application]**.

   ![](assets/nmac_android.png)

1. 輸入 **[!UICONTROL Label]**。

1. 請務必在Adobe **[!UICONTROL Integration key]** Campaign和應用程式程式碼中透過SDK定義相同的內容。 有關詳情，請參閱：將 [Campaign SDK整合至行動應用程式](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)。

   >[!NOTE]
   >
   > 可 **[!UICONTROL Integration key]** 完全自訂字串值，但必須與SDK中指定的值完全相同。

1. 從欄位中選取一個現成可用的圖示，以個人化 **[!UICONTROL Application icon]** 您服務中的行動應用程式。

1. 輸入應用程式的連接設定：輸入由行動應用程式開發人員提供的專案金鑰。

1. 您也可以視需要，以一些內容豐富推播 **[!UICONTROL Application variables]** 訊息內容。 這些功能可完全自訂，而且是傳送至行動裝置的訊息裝載的一部分。

   在下列範例中，我們新增 **title**、 **imageURL** 和iconURL **** ，以建立豐富式推播通知，然後為應用程式提供影像、標題和圖示，以便在通知中顯示。

   ![](assets/nmac_android_2.png)

1. 按一 **[!UICONTROL Finish]** 下 **[!UICONTROL Save]**。 您的Android應用程式現在已可供用於Campaign Classic。

依預設，Adobe Campaign會在表格的(@userKey) **[!UICONTROL User identifier]** 欄位中儲存金鑰 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 。 此金鑰可讓您將訂閱連結至收件者。 要收集其他資料（如複雜的協調密鑰），需要應用以下配置：

1. 建立方案的擴 **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 展名並定義新欄位。
1. 在標籤中定義映 **[!UICONTROL Subscription parameters]** 射。
   >[!CAUTION]
   >
   >請確定標籤中的設 **[!UICONTROL Subscription parameters]** 定名稱與行動應用程式程式碼中的設定名稱相同。 請參閱「將 [Campaign SDK整合至行動應用程式」區](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md) 段。

### 步驟4:建立Android豐富式通知 {#creating-android-delivery}

您現在需要建立新的傳送，並將它連結至您建立的行動應用程式。

1. 前往 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 按一下 **[!UICONTROL New]**.

   ![](assets/nmac_android_3.png)

1. 在下 **[!UICONTROL Deliver on Android (android)]** 拉式清 **[!UICONTROL Delivery template]** 單中選取。 新增至 **[!UICONTROL Label]** 您的傳送。

1. 按一 **[!UICONTROL To]** 下以定義要定位的人口。 預設會套用 **[!UICONTROL Subscriber application]** 目標對應。 按一 **[!UICONTROL Add]** 下以選取我們先前建立的服務。

   ![](assets/nmac_android_7.png)

1. 在視窗中， **[!UICONTROL Target type]** 選取Android行動應用程式的訂閱者，然後按一下 **[!UICONTROL Next]**。

1. 在下拉 **[!UICONTROL Service]** 式清單中，選取您先前建立的服務，然後選擇應用程式，然後按一下 **[!UICONTROL Finish]**。
根 **[!UICONTROL Application variables]** 據在配置步驟中添加的內容自動添加。

   ![](assets/nmac_android_6.png)

1. 編輯您的豐富式通知。

   ![](assets/nmac_android_5.png)

1. 按一 **[!UICONTROL Save]** 下並傳送您的傳送。

當在訂閱者的行動Android裝置上收到影像和網頁時，應該會顯示在推播通知中。

![](assets/nmac_android_4.png)
