---
solution: Campaign Classic
product: campaign
title: 關於Adobe Campaign Classic的行動應用程式頻道
description: 本節提供Adobe Campaign Classic行動應用程式頻道的一般資訊。
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
translation-type: tm+mt
source-git-commit: 9237e11edec4114b2bd0932e6128775f36aad27c
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---


# 開始使用行動應用程式頻道{#about-mobile-app-channel}

**行動應用頻道**&#x200B;可讓您使用Adobe Campaign平台，透過應用程式將個人化推播通知傳送至iOS和Android終端機。

>[!CAUTION]
>
>本檔案詳細說明整合行動應用程式與Adobe Campaign平台的程式。 它不提供如何建立行動應用程式或如何設定它以管理通知的資訊。 如果您想要進一步瞭解此資訊，請參閱官方的Apple [檔案](https://developer.apple.com/)和Android [檔案](https://developer.android.com/index.html)。

提供兩個傳送渠道：

* iOS頻道，可讓您傳送通知至Apple行動裝置。

   ![](assets/nmac_intro_2.png)

* 一種Android頻道，可讓您傳送資料訊息至Android行動裝置。

   ![](assets/nmac_intro_1.png)

與這兩個渠道相對應，促銷活動工作流程中有兩個傳送活動：

![](assets/nmac_intro_3.png)


>[!NOTE]
>
>另外，還提供兩個事務性消息模板用於事務性消息傳遞。

您可以定義應用程式行為，以供使用者啟動通知以顯示符合應用程式內容的畫面。 例如：

* 通知客戶告知其包裹已離開倉庫。 啟動通知會開啟含有傳送相關資訊的頁面。
* 使用者已將項目新增至購物車，但未完成購買就離開應用程式。 系統會傳送通知，告知他們購物車已遭棄用。 當他們啟動通知時，項目會顯示在螢幕上。

>[!CAUTION]
>
>* 您必須確保傳送至行動應用程式的通知符合Apple（Apple推播通知服務）和Google（Firebase Cloud訊息）所指定的必要條件。
>* 警告：在某些國家／地區，法律要求您告知使用者您收集到的資料類型行動應用程式及其處理目的。 你必須檢查法律。


**[!UICONTROL NMAC opt-out management]**(mobileAppOptOutMgt)工作流程會更新行動裝置上取消訂閱的通知。 有關此工作流的詳細資訊，請參閱[技術工作流清單](../../workflow/using/about-technical-workflows.md)。

Adobe Campaign與HTTP/2 APN相容。 有關配置步驟的詳細資訊，請參閱[本節](../../delivery/using/configuring-the-mobile-application.md)一節。

有關如何建立傳送的全局資訊，請參閱[本節](../../delivery/using/steps-about-delivery-creation-steps.md)。

## 資料路徑{#data-path}

下列結構說明讓行動應用程式與Adobe Campaign交換資料的步驟。 此過程涉及三個實體：

* 行動應用程式
* 通知服務：適用於Apple的APN（Apple推播通知服務）和適用於Android的FCM（Firebase Cloud訊息）
* Adobe Campaign

通知程式的三個主要步驟是：在Adobe Campaign註冊（訂閱收集）、交付和追蹤。

### 步驟1:訂閱系列{#step-1--subscription-collection}

行動應用程式是由使用者從App Store或Google Play下載。 此應用程式包含連線設定（iOS憑證和Android專案金鑰）和整合金鑰。 首次開啟應用程式時（視設定而定），系統會要求使用者輸入註冊資訊(@userKey:電子郵件或帳號)。 同時，應用程式會詢問通知服務以收集通知ID（推播ID）。 所有這些資訊（連線設定、整合金鑰、通知識別碼、userKey）都會傳送至Adobe Campaign。

![](assets/nmac_register_view.png)

### 步驟2:傳送{#step-2--delivery}

行銷人員鎖定應用程式訂閱者。 傳送程式會傳送連線設定至通知服務（iOS憑證和Android專案金鑰）、通知ID（推播ID）和通知內容。 通知服務向目標終端發送通知。

在Adobe Campaign，可獲得以下資訊：

* 僅限Android:顯示通知的裝置數（曝光數）
* Android和iOS:通知的點按次數

![](assets/nmac_delivery_view.png)

Adobe Campaign伺服器必須能夠在iOS HTTP/2連接器的443埠上與APNs伺服器聯繫。

若要檢查它是否正常運作，請使用下列命令：

* 針對測試：

   ```
   telnet gateway.sandbox.push.apple.com
   ```

* 生產中：

   ```
   telnet gateway.push.apple.com
   ```

使用iOS HTTP/2連接器，MTA、Web伺服器和工作流伺服器必須能夠與埠443上的APN聯繫。

