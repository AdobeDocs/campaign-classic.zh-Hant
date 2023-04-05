---
product: campaign
title: 在Adobe Campaign中設定Android行動應用程式
description: 了解如何為Android設定行動應用程式
feature: Push
exl-id: 32c35e61-d0a3-478f-b73b-396e2becf7f9
source-git-commit: 8d635722b8961b3edac9cc98f00f17b86f4ee523
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 4%

---

# 針對 Android 的設定步驟

![](../../assets/v7-only.svg)

安裝套件後，您就可以在Adobe Campaign Classic中定義Android應用程式設定。

>[!NOTE]
>
>若要了解如何為iOS設定應用程式，以及如何為iOS建立傳送內容，請參閱 [節](configuring-the-mobile-application.md).

關鍵步驟為：

1. [設定Android外部帳戶](#configuring-external-account-android)
1. [設定Android服務](#configuring-android-service)
1. [在Campaign中建立行動應用程式](#creating-android-app)
1. [使用其他資料擴充應用程式結構](#extend-subscription-schema)

然後，您就能 [建立Android豐富通知](create-notifications-android.md).

## 設定Android外部帳戶 {#configuring-external-account-android}

Android提供兩個連接器：

* V1連接器，允許每個MTA子項有一個連接。
* 允許與FCM伺服器同時連線以改善吞吐量的V2連接器。

要選擇要使用的連接器，請執行以下步驟：

1. 前往 **[!UICONTROL Administration > Platform > External accounts]**.
1. 選取 **[!UICONTROL Android routing]** 外部帳戶。
1. 在 **[!UICONTROL Connector]** 頁簽，填寫 **[!UICONTROL JavaScript used in the connector]** 欄位：

   若為Android V2:https://localhost:8080/nms/jsp/androidPushConnectorV2.js

   >[!NOTE]
   >
   > 您也可以依照下列https://localhost:8080/nms/jsp/androidPushConnector.js進行設定，但建議您使用第2版連接器。

   ![](assets/nmac_connectors3.png)

1. 若為Android V2,Adobe伺服器設定檔案(serverConf.xml)中另有一個參數可供使用：

   * **maxGCMConnectPerChild**:每個子伺服器啟動的對FCM的並行HTTP請求的最大限制（預設為8）。

## 設定Android服務 {#configuring-android-service}

![](assets/do-not-localize/how-to-video.png) [了解如何在影片中設定Android服務](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/configuring-an-android-service-in-campaign.html?lang=en#configuring-an-android-service-and-creating-an-android-mobile-application-in-campaign)

1. 前往 **[!UICONTROL Profiles and Targets > Services and subscriptions]** 節點，按一下 **[!UICONTROL New]**.

   ![](assets/nmac_service_1.png)

1. 定義 **[!UICONTROL Label]** 和 **[!UICONTROL Internal name]**.
1. 前往 **[!UICONTROL Type]** 欄位和選取 **[!UICONTROL Mobile application]**.

   >[!NOTE]
   >
   >預設 **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 目標對應連結至收件者表格。 如果您想使用不同的目標對應，則需要建立新的目標對應，然後在 **[!UICONTROL Target mapping]** 服務欄位。 如需建立目標對應的詳細資訊，請參閱 [本節](../../configuration/using/about-custom-recipient-table.md).

   ![](assets/nmac_ios.png)

1. 然後按一下 **[!UICONTROL Add]** 按鈕，選擇應用程式類型。

   ![](assets/nmac_service_2.png)

1. 建立Android應用程式。 如需詳細資訊，請參閱[本章節](configuring-the-mobile-application-android.md#creating-android-app)。

## 建立Android行動應用程式 {#creating-android-app}

建立服務後，您現在需要建立Android應用程式：

1. 在新建立的服務中，按一下 **[!UICONTROL Add]** 按鈕，選擇應用程式類型。

   ![](assets/nmac_service_2.png)

1. 選擇 **[!UICONTROL Create an Android application]** 並輸入 **[!UICONTROL Label]**.

   ![](assets/nmac_android.png)

1. 確保相同 **[!UICONTROL Integration key]** 是在Adobe Campaign中定義，並透過SDK在應用程式程式碼中定義。 如需詳細資訊，請參閱[本章節](integrating-campaign-sdk-into-the-mobile-application.md)。

   >[!NOTE]
   >
   > 此 **[!UICONTROL Integration key]** 可以使用字串值完全自訂，但必須與SDK中指定的值完全相同。

1. 選取 **[!UICONTROL API version]**:HTTP v1或HTTP（舊版）。 這些設定在 [本節](#select-api-version)

1. 填入 **[!UICONTROL Firebase Cloud Messaging the Android connection settings]** 欄位。

1. 按一下 **[!UICONTROL Finish]**，之後 **[!UICONTROL Save]**。您的Android應用程式現在已準備好用於Campaign Classic。

依預設，Adobe Campaign會在 **[!UICONTROL User identifier]** (@userKey) **[!UICONTROL Subscriber applications (nms:appSubscriptionRcp)]** 表格。 此金鑰可讓您將訂閱連結至收件者。 若要收集其他資料（例如複雜的調解金鑰），您必須套用下列設定：

### 選取API版本{#select-api-version}

建立服務和新的行動應用程式後，您需要根據所選的API版本來設定行動應用程式。

* **HTTP v1** 設定詳細於 [本節](configuring-the-mobile-application-android.md#android-service-httpv1).
* **HTTP（舊版）** 設定詳細於 [本節](configuring-the-mobile-application-android.md#android-service-http).

#### 設定HTTP v1 API{#android-service-httpv1}

若要設定HTTP v1 API版本，請遵循下列步驟：

1. 在 **[!UICONTROL Mobile application creation wizard]** 窗口，選擇 **[!UICONTROL HTTPV1]** 在 **[!UICONTROL API version]** 下拉式清單。

1. 按一下 **[!UICONTROL Load project json file to extract project details...]** 直接載入JSON索引鍵檔案。 如需如何擷取JSON檔案的詳細資訊，請參閱 [本頁](https://firebase.google.com/docs/admin/setup#initialize-sdk).

   您也可以手動輸入下列詳細資訊：
   * **[!UICONTROL Project Id]**
   * **[!UICONTROL Private Key]**
   * **[!UICONTROL Client Email]**

   ![](assets/nmac_android_10.png)

1. 按一下 **[!UICONTROL Test the connection]** 以檢查您的設定是否正確，以及行銷伺服器是否可存取FCM。

   >[!CAUTION]
   >
   >若為中間來源部署， **[!UICONTROL Test connection]** 按鈕不會檢查MID伺服器是否可存取FCM伺服器。

   ![](assets/nmac_android_11.png)

1. 作為選項，您可以使用一些 **[!UICONTROL Application variables]** 如有需要。 這些功能可完全自訂，且是傳送至行動裝置之訊息裝載的一部分。

1. 按一下 **[!UICONTROL Finish]**，之後 **[!UICONTROL Save]**。您的Android應用程式現在已準備好用於Campaign Classic。

以下是FCM裝載名稱，以進一步個人化您的推播通知：

| 訊息類型 | 可設定的訊息元素（FCM裝載名稱） | 可設定選項（FCM裝載名稱） |
|:-:|:-:|:-:|
| 資料訊息 | N/A | validate_only |
| 通知訊息 | title, body, android_channelid，圖示， sound, tag, color, click_action，影像， ticker，黏著， visibility, notification_priority, notification_count <br> | validate_only |

<br>
<br>

#### 設定HTTP（舊版）API{#android-service-http}

若要設定HTTP（舊版）API版本，請遵循下列步驟：

1. 在 **[!UICONTROL Mobile application creation wizard]** 窗口，選擇 **[!UICONTROL HTTP (legacy)]** 在 **[!UICONTROL API version]** 下拉式清單。

1. 輸入 **[!UICONTROL Project key]** 由行動應用程式開發人員提供。

1. 作為選項，您可以使用一些 **[!UICONTROL Application variables]** 如有需要。 這些功能可完全自訂，且是傳送至行動裝置之訊息裝載的一部分。

   在下列範例中，我們新增 **標題**, **imageURL** 和 **iconURL** 若要建立豐富推送通知，然後為應用程式提供要在通知內顯示的影像、標題和圖示。

   ![](assets/nmac_android_2.png)

1. 按一下 **[!UICONTROL Finish]**，之後 **[!UICONTROL Save]**。您的Android應用程式現在已準備好用於Campaign Classic。

以下是FCM裝載名稱，以進一步個人化您的推播通知：

| 訊息類型 | 可設定的訊息元素（FCM裝載名稱） | 可設定選項（FCM裝載名稱） |
|:-:|:-:|:-:|
| 資料訊息 | N/A | dryRun |
| 通知訊息 | title, body, android_channel_id，圖示， sound, tag, color, click_action <br> | dryRun |

<br>

## 擴充appsubscriptionRcp架構 {#extend-subscription-schema}

![](assets/do-not-localize/how-to-video.png) [了解如何在影片中擴充appsubscriptionRcp架構](https://experienceleague.adobe.com/docs/campaign-classic-learn/getting-started-with-push-notifications-for-android/extending-the-app-subscription-schema.html?lang=en#extending-the-app-subscription-schema-to-personalize-push-notifications)

您需要將 **appsubscriptionRcp** 以定義新的其他欄位，以從應用程式儲存Campaign資料庫中的參數。 例如，這些欄位將用於個人化。 操作步驟：

1. 建立的擴充功能 **[!UICONTROL Subscriber applications (nms:appsubscriptionRcp)]** 結構和定義新欄位。 進一步了解中的綱要擴充功能 [本頁](../../configuration/using/about-schema-edition.md)

1. 在 **[!UICONTROL Subscription parameters]** 標籤。

   >[!CAUTION]
   >
   >請確定 **[!UICONTROL Subscription parameters]** 標籤與行動應用程式程式碼中的標籤相同。 請參閱[本節](integrating-campaign-sdk-into-the-mobile-application.md)。
