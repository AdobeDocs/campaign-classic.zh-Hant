---
product: campaign
title: 開始使用行動應用程式頻道
description: 開始使用Adobe Campaign中的行動應用程式頻道
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Push
role: User
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: 81b47231b027a189bc8b9029b7d48939734d08ed
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 10%

---

# 開始使用行動應用程式頻道{#about-mobile-app-channel}

**行動應用程式頻道**&#x200B;可讓您使用Adobe Campaign平台，透過應用程式將個人化推播通知傳送至iOS和Android終端。

有兩種傳送通道可供使用：

* 可讓您將通知傳送至Apple行動裝置的iOS頻道。

  ![](assets/nmac_intro_2.png)

* Android通道，可讓您將資料訊息傳送至Android行動裝置。

  ![](assets/nmac_intro_1.png)

  >[!IMPORTANT]
  >
  >Android Firebase Cloud Messaging (FCM) 服務的一些重要變更將於 2024 年發行，並可能影響 Adobe Campaign 實施。Android 推播訊息訂閱服務設定可能需要更新，才能支援此變更。您已經可以檢查並採取行動。 在此[Adobe Campaign v8技術檔案](https://experienceleague.adobe.com/docs/campaign/technotes-ac/tn-new/push-technote.html?lang=zh-Hant){target="_blank"}中進一步瞭解。

對應這兩個管道，行銷活動工作流程中有兩個傳遞活動。 有兩個異動訊息範本也可用於異動訊息。

![](assets/nmac_intro_3.png)


您可以定義當使用者啟動通知以顯示符合應用程式內容的畫面時的應用程式行為。 例如：

* 系統會傳送通知給客戶，通知他們包裹已離開倉儲。 啟用通知會開啟一個頁面，其中包含傳遞相關的資訊。
* 使用者已將專案新增到購物車，但未完成購買就離開了應用程式。 已傳送通知，通知他們已放棄購物車。 當他們啟動通知時，專案會顯示在畫面上。

>[!CAUTION]
>
>* 您必須確保傳送至行動應用程式的通知符合Apple (Apple推播通知服務)和Google （Firebase雲端通訊）所指定的必要條件和條件。
>* 警告：在某些國家，法律要求您通知使用者您收集的資料型別行動應用程式及其處理的目的。 您必須檢查法規。

**[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt)工作流程會更新行動裝置上的通知取消訂閱。 如需此工作流程的詳細資訊，請參閱[技術工作流程清單](../../workflow/using/about-technical-workflows.md)。

Adobe Campaign與HTTP/2 APN相容。 如需設定步驟的詳細資訊，請參閱[本區段](configuring-the-mobile-application.md)區段。

如需如何建立傳遞的全域資訊，請參閱[本節](steps-about-delivery-creation-steps.md)。


## 設定推播通知頻道 {#push-notification-configuration}

若要使用Adobe Campaign傳送推播通知，您必須先設定環境和應用程式。 開始使用Adobe Campaign傳送推播通知之前，您需要確保行動應用程式上和Adobe Experience Platform中的標籤已具備設定和整合。 Adobe Experience Platform Mobile SDK透過Android和iOS相容的SDK，為您的行動裝置提供使用者端整合API。 SDK 設定可透過資料彙集 UI 來管理，提供靈活的設定與可擴充的規則式整合。 在[Adobe Campaign v8檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/send/push/push-settings)中進一步瞭解。


## 資料路徑 {#data-path}

下列結構描述詳細說明可讓行動應用程式與Adobe Campaign交換資料的步驟。 此程式涉及三個實體：

* 行動應用計畫
* 通知服務：適用於Apple的APN (Apple推播通知服務)和適用於Android的FCM (Firebase Cloud Messaging)
* Adobe Campaign

通知程式的三個主要步驟是：在Adobe Campaign中註冊應用程式（訂閱收集）、傳送和追蹤。

### 步驟1：訂閱集合 {#step-1--subscription-collection}

使用者可以從App Store或Google Play下載行動應用程式。 此應用程式包含連線設定(Android的iOS憑證和專案金鑰)和整合金鑰。 第一次開啟應用程式時（視組態而定），系統會要求使用者輸入註冊資訊(例@userKey：電子郵件或帳號)。 同時，應用程式會詢問通知服務是否要收集通知ID （推播ID）。 所有這些資訊（連線設定、整合金鑰、通知識別碼、userKey）都會傳送至Adobe Campaign。

![](assets/nmac_register_view.png)

### 步驟2：傳送 {#step-2--delivery}

行銷人員鎖定應用程式訂閱者。 傳送程式會將連線設定傳送至通知服務(Android的iOS憑證和專案金鑰)、通知ID （推播ID）和通知內容。 通知服務會將通知傳送至目標終端。

Adobe Campaign中有以下資訊：

* 僅限Android：已顯示通知（曝光數）的裝置數
* Android和iOS：通知的點按次數

![](assets/nmac_delivery_view.png)

Adobe Campaign伺服器必須能夠連絡iOS HTTP/2聯結器的443連線埠上的APNs伺服器。

若要檢查它是否正常運作，請使用下列命令：

* 對於測試：

  ```
  api.development.push.apple.com:443
  ```

* 生產中：

  ```
  api.push.apple.com:443
  ```

使用iOS HTTP/2聯結器時，MTA和Web伺服器必須能夠聯絡連線埠443上的APN。

如果您需要透過Proxy使用iOS HTTP/2聯結器，請參閱此[頁面](../../installation/using/file-res-management.md#proxy-connection-configuration)。
