---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign中設定Android行動應用程式
description: 瞭解如何設定Android適用的行動應用程式
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1d7d48f52f69e4902eafa6806c2cd9170c21fe5a
workflow-type: tm+mt
source-wordcount: '1648'
ht-degree: 2%

---


# 針對 Android 的配置步驟

在安裝套件後，您就可以在Adobe Campaign Classic中定義您的Android應用程式設定。

>[!NOTE]
>
>若要瞭解如何為iOS設定應用程式，以及如何建立iOS的傳送，請參閱此[章節](../../delivery/using/configuring-the-mobile-application.md)。

主要步驟為：

1. [設定Android外部帳戶](#configuring-external-account-android)
1. [設定Android服務](#configuring-android-service)
1. [在Campaign中建立行動應用程式](#creating-android-app)
1. [使用其他資料擴充應用程式架構](#extend-subscription-schema)

然後，您就可以[建立Android豐富式通知](#creating-android-delivery)。

## 設定Android外部帳戶{#configuring-external-account-android}

對於Android，有兩個連接器可用：

* V1連接器，允許每個MTA子項連接一個。
* V2連接器允許與FCM伺服器同時連接，以提高吞吐量。

要選擇要使用的連接器，請執行以下步驟：

1. 前往&#x200B;**[!UICONTROL Administration > Platform > External accounts]**。
1. 選擇&#x200B;**[!UICONTROL Android routing]**&#x200B;外部帳戶。
1. 在&#x200B;**[!UICONTROL Connector]**&#x200B;標籤中，填入&#x200B;**[!UICONTROL JavaScript used in the connector]**&#x200B;欄位：

   針對Android V2:https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > 您也可以依https://localhost:8080/nms/jsp/androidPushConnector.js設定，但建議您使用第2版的連接器。

   ![](assets/nmac_connectors3.png)

1. 對於Android V2,Adobe Server組態檔(serverConf.xml)中還有一個參數：

   * **maxGCMConnectPerChild**:每個子伺服器啟動的對FCM的並行HTTP請求的最大限制（預設為8）。

## 設定Android服務{#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [瞭解如何在視訊中設定Android服務](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

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

1. 建立您的Android應用程式。 如需詳細資訊，請參閱本[區段](../../delivery/using/configuring-the-mobile-application-android.md#creating-android-app)。

## 建立Android行動應用程式{#creating-android-app}

在建立服務後，您現在需要建立Android應用程式：

1. 在新建立的服務中，按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以選擇應用程式類型。

   ![](assets/nmac_service_2.png)

1. 選擇&#x200B;**[!UICONTROL Create an Android application]**&#x200B;並輸入&#x200B;**[!UICONTROL Label]**。

   ![](assets/nmac_android.png)

1. 請確定Adobe Campaign和應用程式碼中已透過SDK定義相同的&#x200B;**[!UICONTROL Integration key]**。 有關詳情，請參閱：[將Campaign SDK整合至行動應用程式](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)。

   >[!NOTE]
   >
   > **[!UICONTROL Integration key]**&#x200B;可完全自訂字串值，但必須與SDK中指定的值完全相同。

1. 選擇&#x200B;**[!UICONTROL API version]**:HTTP v1或HTTP（舊版）。 這些配置在[本節](#select-api-version)中有詳細說明

1. 填寫&#x200B;**[!UICONTROL Firebase Cloud Messaging the Android connection settings]**&#x200B;欄位。

1. 按一下 **[!UICONTROL Finish]**，之後 **[!UICONTROL Save]**。您的Android應用程式現在已可供用於Campaign Classic。

依預設，Adobe Campaign會在&#x200B;**[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]**&#x200B;表格的&#x200B;**[!UICONTROL User identifier]**(@userKey)欄位中儲存索引鍵。 此金鑰可讓您將訂閱連結至收件者。 要收集其他資料（如複雜的協調密鑰），需要應用以下配置：

### 選擇API版本{#select-api-version}

在建立服務和新的行動應用程式後，您需要根據所選的API版本來設定行動應用程式。

* **HTTP v1配** 置在本節中有詳細 [說明](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1)。
* **HTTP（舊版）** 設定在本節中詳 [細說明](../../delivery/using/configuring-the-mobile-application-android.md#android-service-http)。

#### 配置HTTP v1 API{#android-service-httpv1}

若要設定HTTP v1 API版本，請遵循下列步驟：

1. 在&#x200B;**[!UICONTROL Mobile application creation wizard]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL API version]**&#x200B;下拉式清單中的&#x200B;**[!UICONTROL HTTPV1]**。

1. 按一下&#x200B;**[!UICONTROL Load project json file to extract projet details...]**&#x200B;可直接載入您的JSON金鑰檔案。 如需如何擷取JSON檔案的詳細資訊，請參閱此[page](https://firebase.google.com/docs/admin/setup#initialize-sdk)頁面。

   您也可以人工輸入下列詳細資訊：
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. 按一下&#x200B;**[!UICONTROL Test the connection]**&#x200B;以檢查您的設定是否正確，以及行銷伺服器是否可存取FCM。

   >[!CAUTION]
   >
   >對於Mid-Sourcing部署，**[!UICONTROL Test connection]**&#x200B;按鈕將不檢查MID伺服器是否可以訪問FCM伺服器。

   ![](assets/nmac_android_11.png)

1. 您也可以視需要使用某些&#x200B;**[!UICONTROL Application variables]**&#x200B;來豐富推播訊息內容。 這些功能可完全自訂，而且是傳送至行動裝置的訊息裝載的一部分。

1. 按一下 **[!UICONTROL Finish]**，之後 **[!UICONTROL Save]**。您的Android應用程式現在已可供用於Campaign Classic。

以下是FCM裝載名稱，可進一步個人化您的推播通知：

| 消息類型 | 可配置消息元素（FCM有效負載名稱） | 可配置選項（FCM有效負載名稱） |
|:-:|:-:|:-:|
| 資料消息 | N/A | validate_only |
| 通知消息 | title, body, android_channel ID, icon, sound, tag, color, click_action，影像， ticker, sticky, visibility, notification_priority, notification_count <br> | validate_only |

<br>
<br>

#### 設定HTTP（舊版）API{#android-service-http}

若要設定HTTP（舊版）API版本，請遵循下列步驟：

1. 在&#x200B;**[!UICONTROL Mobile application creation wizard]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL API version]**&#x200B;下拉式清單中的&#x200B;**[!UICONTROL HTTP (legacy)]**。

1. 輸入由行動應用程式開發人員提供的&#x200B;**[!UICONTROL Project key]**。

1. 您也可以視需要使用某些&#x200B;**[!UICONTROL Application variables]**&#x200B;來豐富推播訊息內容。 這些功能可完全自訂，而且是傳送至行動裝置的訊息裝載的一部分。

   在下列範例中，我們新增&#x200B;**title**、**imageURL**&#x200B;和&#x200B;**iconURL**&#x200B;來建立豐富式推播通知，然後為應用程式提供影像、標題和圖示以顯示在通知中。

   ![](assets/nmac_android_2.png)

1. 按一下 **[!UICONTROL Finish]**，之後 **[!UICONTROL Save]**。您的Android應用程式現在已可供用於Campaign Classic。

以下是FCM裝載名稱，可進一步個人化您的推播通知：

| 消息類型 | 可配置消息元素（FCM有效負載名稱） | 可配置選項（FCM有效負載名稱） |
|:-:|:-:|:-:|
| 資料消息 | 不適用 | dryRun |
| 通知消息 | title, body, android_channel_id, icon, sound, tag, color, click_action <br> | dryRun |

<br>

## 擴充appsubscriptionRcp結構{#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [瞭解如何在視訊中擴充appsubscriptionRcp架構](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

您需要擴充&#x200B;**appsubscriptionRcp**，以定義新的其他欄位，將應用程式的參數儲存在Campaign資料庫中。 例如，這些欄位將用於個人化。 操作步驟：

1. 建立&#x200B;**[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]**&#x200B;方案的副檔名並定義新欄位。 進一步瞭解[本頁](../../configuration/using/about-schema-edition.md)中的架構擴充功能

1. 在&#x200B;**[!UICONTROL Subscription parameters]**&#x200B;標籤中定義映射。

   >[!CAUTION]
   >
   >請確定&#x200B;**[!UICONTROL Subscription parameters]**&#x200B;標籤中的組態名稱與行動應用程式碼中的組態名稱相同。 請參閱「將Campaign SDK整合至行動應用程式](../../delivery/using/integrating-campaign-sdk-into-the-mobile-application.md)」一節。[

## 建立Android豐富式通知{#creating-android-delivery}

有了Firebase Cloud Messaging，您可以選擇兩種訊息類型：

* **[!UICONTROL Data message]**，由用戶端應用程式處理。
   <br>訊息會直接傳送至行動應用程式，而行動應用程式會產生並顯示Android通知至裝置。資料訊息只包含您的自訂應用程式變數。

* **[!UICONTROL Notification message]**，由FCM SDK自動處理。
   <br> FCM會代表用戶端應用程式在您的使用者裝置上自動顯示訊息。通知訊息包含一組預先定義的參數和選項，但仍可使用自訂的應用程式變數進一步個人化。

有關Firebase Cloud消息類型的詳細資訊，請參閱[FCM文檔](https://firebase.google.com/docs/cloud-messaging/concept-options#notifications_and_data_messages)。

### 建立資料消息{#creating-data-message}

1. 前往&#x200B;**[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 按一下 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 在&#x200B;**[!UICONTROL Delivery template]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Deliver on Android (android)]**。 將&#x200B;**[!UICONTROL Label]**&#x200B;新增至您的傳送。

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;定義要定位的人口。 預設情況下，將應用&#x200B;**[!UICONTROL Subscriber application]**&#x200B;目標映射。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;選擇服務。

   ![](assets/nmac_android_7.png)

1. 在&#x200B;**[!UICONTROL Target type]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Subscribers of an Android mobile application]**&#x200B;並按一下&#x200B;**[!UICONTROL Next]**。

1. 在&#x200B;**[!UICONTROL Service]**&#x200B;下拉式清單中，選取您先前建立的服務，然後選擇應用程式，然後按一下&#x200B;**[!UICONTROL Finish]**。
根據在配置步驟中添加的內容，會自動添加**[!UICONTROL Application variables]**。

   ![](assets/nmac_android_6.png)

1. 選擇&#x200B;**[!UICONTROL data message]**&#x200B;作為&#x200B;**[!UICONTROL Message Type]**。

1. 編輯您的豐富式通知。

   ![](assets/nmac_android_5.png)

1. 如有需要，您可以在先前設定的&#x200B;**[!UICONTROL Application variables]**&#x200B;中新增資訊。 **[!UICONTROL Application variables]** 必須在Android服務中設定，且是傳送至行動裝置之訊息裝載的一部分。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;並傳送傳送。

當在訂閱者的行動Android裝置上收到影像和網頁時，應該會顯示在推播通知中。

![](assets/nmac_android_4.png)

### 建立通知消息{#creating-notification-message}

>[!NOTE]
>
>通知訊息的其他選項僅適用於HTTP v1 API設定。 如需詳細資訊，請參閱本[區段](../../delivery/using/configuring-the-mobile-application-android.md#android-service-httpv1)。

![](assets/do-not-localize/how-to-video.png) [瞭解如何在視訊中建立Android推播通知](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-and-sending-push-notifications.html?lang=en#additional-resources)

1. 前往&#x200B;**[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**。

1. 按一下 **[!UICONTROL New]**。

   ![](assets/nmac_android_3.png)

1. 在&#x200B;**[!UICONTROL Delivery template]**&#x200B;下拉式清單中選取&#x200B;**[!UICONTROL Deliver on Android (android)]**。 將&#x200B;**[!UICONTROL Label]**&#x200B;新增至您的傳送。

1. 按一下&#x200B;**[!UICONTROL To]**&#x200B;定義要定位的人口。 預設情況下，將應用&#x200B;**[!UICONTROL Subscriber application]**&#x200B;目標映射。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;選擇服務。

   ![](assets/nmac_android_7.png)

1. 在&#x200B;**[!UICONTROL Target type]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Subscribers of an Android mobile application]**&#x200B;並按一下&#x200B;**[!UICONTROL Next]**。

1. 在&#x200B;**[!UICONTROL Service]**&#x200B;下拉式清單中，選取您先前建立的服務，然後選擇應用程式，然後按一下&#x200B;**[!UICONTROL Finish]**。

   ![](assets/nmac_android_6.png)

1. 選擇&#x200B;**[!UICONTROL notification message]**&#x200B;作為&#x200B;**[!UICONTROL Message Type]**。

1. 新增標題並編輯您的訊息。 使用&#x200B;**[!UICONTROL Notification options]**&#x200B;個人化您的推播通知：

   * **[!UICONTROL Channel ID]**:設定通知的頻道ID。應用程式必須先使用此頻道ID建立頻道，才能收到任何具有此頻道ID的通知。
   * **[!UICONTROL Sound]**:將音效設定為在裝置收到您的通知時播放。
   * **[!UICONTROL Color]**:設定通知的圖示顏色。
   * **[!UICONTROL Icon]**:將通知的圖示設定為顯示在描述檔裝置上。
   * **[!UICONTROL Tag]**:設定用來取代通知抽屜中現有通知的識別碼。
   * **[!UICONTROL Click action]**:設定與使用者相關的動作，按一下您的通知。

   有關&#x200B;**[!UICONTROL Notification options]**&#x200B;以及如何填寫這些欄位的詳細資訊，請參閱[FCM文檔](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification)。

   ![](assets/nmac_android_8.png)

1. 如果您的應用程式已設定HTTP v1 API通訊協定，您可以使用下列&#x200B;**[!UICONTROL HTTPV1 additional options]**&#x200B;進一步個人化您的推播通知：

   * **[!UICONTROL Ticker]**:設定通知的提示文字。僅適用於設為Android 5.0 Lollipop的裝置。
   * **[!UICONTROL Image]**:將影像的URL設定為顯示在通知中。
   * **[!UICONTROL Notification Count]**:設定要直接顯示在應用程式圖示上的新未讀取資訊數目。
   * **[!UICONTROL Sticky]**:設為true或false。如果設為false，則當使用者按一下通知時，通知會自動關閉。 如果設為true，即使使用者按一下通知，通知仍會顯示。
   * **[!UICONTROL Notification Priority]**:將通知的優先順序層級設定為預設、最小、低或高。有關詳細資訊，請參閱[FCM文檔](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#NotificationPriority)。
   * **[!UICONTROL Visibility]**:將通知的可見度等級設為公開、私人或機密。有關詳細資訊，請參閱[FCM文檔](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#visibility)。

   有關&#x200B;**[!UICONTROL HTTP v1 additional options]**&#x200B;以及如何填寫這些欄位的詳細資訊，請參閱[FCM文檔](https://firebase.google.com/docs/reference/fcm/rest/v1/projects.messages#androidnotification)。

   ![](assets/nmac_android_9.png)

1. 如有需要，您可以在先前設定的&#x200B;**[!UICONTROL Application variables]**&#x200B;中新增資訊。 **[!UICONTROL Application variables]** 必須在Android服務中設定，且是傳送至行動裝置之訊息裝載的一部分。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;並傳送傳送。

當在訂閱者的行動Android裝置上收到影像和網頁時，應該會顯示在推播通知中。
