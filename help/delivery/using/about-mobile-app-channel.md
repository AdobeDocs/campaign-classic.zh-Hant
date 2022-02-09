---
product: campaign
title: '開始使用行動應用程式頻道 '
description: 開始使用Adobe Campaign Classic的移動應用頻道
feature: Push
exl-id: c3b0406f-f652-42f4-ad0d-23fb719cd1b6
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 2%

---

# 開始使用行動應用程式頻道{#about-mobile-app-channel}

![](../../assets/common.svg)

的 **移動應用頻道** 讓你使用Adobe Campaign平台通過應用向iOS和安卓終端發送個性化推送通知。

>[!CAUTION]
>
>本文檔詳細介紹了將您的移動應用程式與Adobe Campaign平台整合的過程。 它不提供有關如何建立移動應用程式或如何配置它以管理通知的資訊。 如想進一步瞭解，請參閱官方的Apple [文檔](https://developer.apple.com/) 和Android [文檔](https://developer.android.com/index.html)。

有兩個交付渠道：

* 一個iOS頻道，使您能夠向Apple移動設備發送通知。

   ![](assets/nmac_intro_2.png)

* 一種Android通道，使您能夠向Android移動設備發送資料消息。

   ![](assets/nmac_intro_1.png)

與這兩個渠道對應，市場活動工作流中有兩個交付活動：

![](assets/nmac_intro_3.png)


>[!NOTE]
>
>還有兩個事務性消息模板可用於事務性消息傳遞。

您可以為用戶激活通知以顯示與應用程式上下文匹配的螢幕時定義應用程式行為。 例如：

* 客戶會收到通知，告知其包裹已從倉庫退出。 激活通知會開啟一個頁面，其中包含與交貨相關的資訊。
* 用戶已將物料添加到購物車，但未完成購買而離開了應用程式。 將發送通知，告知他們的購物車已被放棄。 激活通知後，該項目將顯示在螢幕上。

>[!CAUTION]
>
>* 您需要確保發送到移動應用程式的通知符合Apple(Apple推送通知服務)和Google（Firebase雲消息）指定的先決條件和條件。
>* 警告：在某些國家/地區，法律要求您將收集到的資料類型移動應用程式及其處理目的告知用戶。 你必須檢查立法。


的 **[!UICONTROL NMAC opt-out management]** (mobileAppOptOutMgt)工作流更新移動設備上的通知取消訂閱。 有關此工作流的詳細資訊，請參閱 [技術工作流清單](../../workflow/using/about-technical-workflows.md)。

Adobe Campaign與HTTP/2 APN相容。 有關配置步驟的詳細資訊，請參閱 [此部分](configuring-the-mobile-application.md) 的子菜單。

有關如何建立交貨的全局資訊，請參閱 [此部分](steps-about-delivery-creation-steps.md)。

## 資料路徑 {#data-path}

以下架構詳細說明了使移動應用程式能夠與Adobe Campaign交換資料的步驟。 此過程涉及三個實體：

* 移動應用
* 通知服務：用於Apple的APN(Apple推送通知服務)和用於Android的FCM（Firebase雲消息）
* Adobe Campaign

通知流程的三個主要步驟是：申請在Adobe Campaign的登記（訂閱收集）、交付和跟蹤。

### 步驟1:訂閱集合 {#step-1--subscription-collection}

用戶從App Store或Google Play下載移動應用。 此應用程式套件含連接設定(Android的iOS證書和項目密鑰)和整合密鑰。 首次開啟應用程式時（視配置而定），可要求用戶輸入註冊資訊(@userKey:電子郵件或實例帳號)。 同時，應用程式詢問通知服務以收集通知ID（推送ID）。 所有這些資訊（連接設定、整合密鑰、通知標識符、用戶密鑰）都發送到Adobe Campaign。

![](assets/nmac_register_view.png)

### 步驟2:交貨 {#step-2--delivery}

營銷人員瞄準應用程式訂閱者。 傳遞過程將連接設定發送到通知服務(Android的iOS證書和項目密鑰)、通知ID（推送ID）和通知內容。 通知服務向目標終端發送通知。

以下資訊可在Adobe Campaign查閱：

* 僅限Android:顯示通知的設備數（印象）
* 安卓和iOS:通知的點擊次數

![](assets/nmac_delivery_view.png)

Adobe Campaign伺服器必須能夠與iOSHTTP/2連接器的443埠上的APNs伺服器聯繫。

要檢查其工作正常，請使用以下命令：

* 對於test:

   ```
   api.development.push.apple.com:443
   ```

* 生產中：

   ```
   api.push.apple.com:443
   ```

使用iOSHTTP/2連接器，MTA和Web伺服器必須能夠與埠443上的APN聯繫。

如果需要通過代理使用iOSHTTP/2連接器，請參閱此 [頁](../../installation/using/file-res-management.md#proxy-connection-configuration)。
