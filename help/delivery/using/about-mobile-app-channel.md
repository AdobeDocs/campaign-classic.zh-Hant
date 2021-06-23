---
product: campaign
title: 關於Adobe Campaign Classic中的行動應用程式頻道
description: 本節提供Adobe Campaign Classic中行動應用程式通道的特定一般資訊。
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 1%

---

# 開始使用行動應用程式頻道{#about-mobile-app-channel}

**行動應用程式頻道**&#x200B;可讓您使用Adobe Campaign平台，透過應用程式將個人化推播通知傳送至iOS和Android終端機。

>[!CAUTION]
>
>本檔案詳細說明將行動應用程式與Adobe Campaign平台整合的程式。 它不提供如何建立行動應用程式，或如何設定以管理通知的資訊。 如果您想要進一步了解，請參閱官方的Apple [檔案](https://developer.apple.com/)和Android [檔案](https://developer.android.com/index.html)。

有兩個可用的傳送通道：

* iOS通道，可讓您傳送通知至Apple行動裝置。

   ![](assets/nmac_intro_2.png)

* Android通道，可讓您傳送資料訊息至Android行動裝置。

   ![](assets/nmac_intro_1.png)

與這兩個管道對應，促銷活動工作流程中有兩個傳送活動：

![](assets/nmac_intro_3.png)


>[!NOTE]
>
>交易式訊息也提供兩個交易式訊息範本。

當使用者啟動通知以顯示符合應用程式內容的畫面時，您可以定義應用程式行為。 例如：

* 系統會傳送通知給客戶，通知客戶其包裹已從倉庫退出。 啟動通知會開啟一個頁面，其中包含與傳送相關的資訊。
* 使用者已將項目新增至購物車，但未完成購買便離開應用程式。 系統會傳送通知，告知對方購物車已遭放棄。 當使用者啟動通知時，項目會顯示在畫面上。

>[!CAUTION]
>
>* 您必須確定傳送至行動應用程式的通知符合Apple（Apple推播通知服務）和Google（Firebase雲端訊息）所指定的必要條件。
>* 警告：在某些國家/地區，法律要求您將收集到的資料類型行動應用程式及其處理用途通知使用者。 你必須檢查立法。


**[!UICONTROL NMAC opt-out management]**(mobileAppOptOutMgt)工作流程會更新行動裝置上的通知取消訂閱。 有關此工作流的詳細資訊，請參閱[技術工作流清單](../../workflow/using/about-technical-workflows.md)。

Adobe Campaign與HTTP/2 APN相容。 有關配置步驟的詳細資訊，請參閱[此部分](configuring-the-mobile-application.md)部分。

如需如何建立傳送的全域資訊，請參閱[此區段](steps-about-delivery-creation-steps.md)。

## 資料路徑 {#data-path}

下列結構詳細說明讓行動應用程式與Adobe Campaign交換資料的步驟。 此過程涉及三個實體：

* 行動應用程式
* 通知服務：適用於Apple的APN（Apple推播通知服務）和適用於Android的FCM（Firebase雲端訊息）
* Adobe Campaign

通知程式的三個主要步驟為：在Adobe Campaign中註冊應用程式（訂閱收集）、傳送和追蹤。

### 步驟1:訂閱集合 {#step-1--subscription-collection}

行動應用程式由使用者從App Store或Google Play下載。 此應用程式包含連線設定（Android適用的iOS憑證和專案金鑰）和整合金鑰。 首次開啟應用程式時（視設定而定），可要求使用者輸入註冊資訊(@userKey:電子郵件或帳號)。 同時，應用程式會向通知服務提問以收集通知ID（推播ID）。 所有這些資訊（連線設定、整合金鑰、通知識別碼、userKey）都會傳送至Adobe Campaign。

![](assets/nmac_register_view.png)

### 步驟2:傳送 {#step-2--delivery}

行銷人員鎖定應用程式訂閱者。 傳送程式會將連線設定傳送至通知服務（iOS憑證和Android專案金鑰）、通知ID（推播ID）和通知內容。 通知服務向目標終端發送通知。

下列資訊適用於Adobe Campaign:

* 僅限Android:已顯示通知的裝置數（曝光數）
* Android和iOS:通知的點按次數

![](assets/nmac_delivery_view.png)

Adobe Campaign伺服器必須能夠連絡iOS HTTP/2連接器443埠上的APN伺服器。

若要檢查其是否正常運作，請使用下列命令：

* 針對測試：

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* 在生產中：

   ```
   telnet gateway.push.apple.com
   ```

使用iOS HTTP/2連接器，MTA、Web伺服器和工作流伺服器必須能夠聯繫埠443上的APN。
