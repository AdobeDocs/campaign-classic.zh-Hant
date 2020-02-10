---
title: 線路頻道
seo-title: 線路頻道
description: 線路頻道
seo-description: null
page-status-flag: never-activated
uuid: 94b4e044-3f5d-42a6-b249-29f417386156
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
discoiquuid: 1d3cc650-3c79-4a1d-b2bc-e7eb6d59d2f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# 線路頻道{#line-channel}

LINE是免費即時訊息、語音和視訊通話的應用程式，適用於所有智慧型手機(iPhone、Android、Windows Phone、Blackberry、Nokia)和PC。 Adobe Campaign可讓您傳送LINE訊息。

LINE僅適用於內部部署或托管服務安裝。

LINE也可與交易訊息模組結合，以在安裝在消費性行動裝置上的LINE應用程式上傳送即時訊息。 For more on this, refer to this [page](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line).

![](assets/line_message.png)

以下各節提供LINE頻道專屬的資訊。 如需如何建立傳送的全域資訊，請參[閱本節](../../delivery/using/steps-about-delivery-creation-steps.md)。

使用LINE渠道的步驟如下：

1. 建立傳送
1. 配置消息內容
1. 選擇目標人口
1. 傳送訊息
1. 監控傳送（追蹤、隔離、報告等）。

## 設定LINE頻道 {#setting-up-line-channel}

### 建立LINE帳戶和外部帳戶 {#creating-a-line-account-and-an-external-account-}

>[!NOTE]
>
>在建立LINE帳戶和外部帳戶之前，您必須先將LINE套件安裝在實例上。 有關此問題的詳細資訊，請參 [閱《安裝指南](../../installation/using/installing-campaign-standard-packages.md#line-package) 》中的「LINE」一節。

您必須先建立LINE帳戶，才能將其連結至Adobe Campaign。 然後，您可以傳送LINE訊息給已在行動應用程式中新增您LINE帳戶的使用者。 外部帳戶和LINE帳戶只能由平台的功能管理員管理。

要建立和配置LINE帳戶，請參 [閱https://developers.line.me/](https://developers.line.me/)。

要建立和配置LINE服務，請參閱管 [理訂閱](../../delivery/using/managing-subscriptions.md)。

![](assets/line_service.png)

最後，若要在Adobe Campaign上建立外部帳戶：

1. 在「管 **理** >平台 **」樹結構中，按一下** 「外部帳戶 **** 」頁籤。
1. 然後按一下「 **新** 」圖示。

   ![](assets/line_config.png)

1. 填寫「標 **簽** 」和「 **內部名稱** 」欄位。
1. 在欄位 **[!UICONTROL Type]** 中，選擇路由，在「渠道」字 **段中** ，選擇LINE。
1. 按一下 **[!UICONTROL Save]** 建立LINE外部帳戶。
1. 然後 **LINE** personalization欄位會出現在「一般」圖示 **下方** ，請填寫下列欄位：

   ![](assets/line_config_2.png)

   * **渠道別名**:是透過您的「 >標籤」中的「行」 **[!UICONTROL Channels]** 帳戶 **[!UICONTROL Technical configuration]** 提供。
   * **頻道ID**:是透過「渠道」>「基本資訊」面板 **標籤中的****LINE帳戶提供** 。
   * **通道密鑰**:是透過「渠道」>「基本資訊」面板 **標籤中的****LINE帳戶提供** 。
   * **存取Token**:是透過您在開發人員入口網站中的LINE帳戶，或按一下按鈕提 **[!UICONTROL Get access token]** 供。
   * **存取Token到期日**:可讓您指定存取Token的到期日。
   * **LINE訂閱服務**:允許您指定用戶將訂閱的服務。

>[!NOTE]
>
>您必須確認和工 **[!UICONTROL LINE access token update (updateLineAccessToken)]** 作 **[!UICONTROL Delete blocked LINE users (deleteBlockedLineUsers)]** 流程已啟動。 在瀏覽器中，單 **[!UICONTROL Administration > Production > Technical workflows > LINE workflows]** 擊以檢查工作流的狀態。

## 建立傳送 {#creating-the-delivery}

要建立 **LINE** 交貨，您必須遵循以下步驟：

>[!NOTE]
>
>本節將介紹有關建立交付的全 [局概念](../../delivery/using/steps-about-delivery-creation-steps.md)。

1. 從標籤中 **[!UICONTROL Campaigns]** 選擇，然 **[!UICONTROL Deliveries]** 後按一下該 **[!UICONTROL Create]** 按鈕。
1. 在出現的視窗中，選取傳送 **[!UICONTROL LINE V2 delivery]** 範本。

   ![](assets/line_message_01.png)

1. 使用標籤、程式碼和說明來識別您的傳送。 如需詳細資訊，請參閱[本小節](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery)。
1. 按一 **[!UICONTROL Continue]** 下以建立傳送。

## 定義內容 {#defining-the-content}

要定義LINE傳送的內容，首先必須向傳送添加消息類型。 每個LINE傳送最多可包含5條消息。

您可以選擇兩種消息類型：

* 文字訊息
* 影像和連結

### 設定文字訊息傳送 {#configuring-a-text-message-delivery}

文 **字訊息** LINE傳送是以文字形式傳送給收件者的訊息。

![](assets/line_message_02.png)

此類型訊息的設定類似於電子郵件中 **的文** 字設定。 For more information, refer to this [page](../../delivery/using/defining-the-email-content.md#message-content).

### 設定影像和連結傳送 {#configuring-an-image-and-link-delivery}

影 **像和連結** LINE傳送是以影像形式傳送給收件者的訊息，可能包含一或多個URL。

您可以使用：

* 個 **人化影像**,

   >[!NOTE]
   >
   >您可以使用 **%SIZE%** 變數：此變數可讓您根據收件者行動裝置的螢幕大小，最佳化影像顯示。

   ![](assets/line_message_04.png)

* 影像 **URL**,

   ![](assets/line_message_03.png)

   影像URL可讓您使用不同的影像解析度，以最佳化行動裝置上的傳送可見度。 僅支援相同高度和寬度的影像。

   您可以根據螢幕大小來定義影像：

   * 1040px
   * 700px
   * 460px
   * 300px
   * 240px
   >[!NOTE]
   >
   >每個具有連結的LINE影像都必須使用1040x1040像素大小。

   然後，您必須新增會在收件者行動裝置上彈出的替代文字。

* 和 **[!UICONTROL Links]**。

   ![](assets/line_message_05.png)

   該 **[!UICONTROL Links]** 區段可讓您選擇不同的版面，將影像分割為多個可點選區域。 然後，您可以為每位使用者指派專屬連結。

>[!NOTE]
>
>&lt;%@ include option=&#39;NmsServer_URL&#39; %>/webApp/APP3?id=&lt;%=escapeUrl(cryptString(visitor.id))%>語法可讓您在LINE訊息中包含網頁應用程式的連結。

### 建議 {#recommendations}

* 當您第一次將LINE傳送傳送給新的收件者時，必須將有關使用條款和同意的正式LINE訊息新增至傳送。 官方訊息可從下列連結取得： [https://terms.line.me/OA_privacy/](https://terms.line.me/OA_privacy/sp?lang=fr)。

## 選擇目標人口 {#selecting-the-target-population}

選擇LINE傳送的收件者類似於定義電子郵件傳送的收件者。 如需詳細資訊，請參閱「 [識別目標人口族群](../../delivery/using/steps-defining-the-target-population.md)」。

定位是對訪客 **執行**。

## 傳送訊息 {#sending-messages}

當您的傳送已建立並正確設定時，您可以將它傳送至先前定義的目標。

傳送LINE傳送類似於傳送電子郵件傳送。 如需傳送傳送的詳細資訊，請參閱傳送 [訊息](../../delivery/using/sending-messages.md)。

## 存取報表 {#accessing-reports}

按一下瀏覽器中的，可查看LINE服務 **[!UICONTROL Profiles and Targets > Services and Subscriptions > LINE]** 的報告。 然後，按一下 **[!UICONTROL Reports]** LINE服務中的表徵圖。

![](assets/line_reports.png)

要查看LINE交貨的報表，請按一下， **[!UICONTROL Campaign Management > Deliveries]** 然後選擇所需的交貨。 追蹤報表會指出點進率。 LINE未考慮開放率。

![](assets/line_reports_01.png)

## 範例：建立和發送個性化的LINE消息 {#example--create-and-send-a-personalized-line-message}

在此範例中，我們將建立並設定文字訊息和包含資料的影像，這些資料會根據收件者個人化。

1. 按一下標籤中的按鈕，創 **[!UICONTROL Create]** 建LINE交 **[!UICONTROL Campaign]** 貨。

   ![](assets/line_usecase.png)

1. 選取傳送 **[!UICONTROL LINE V2 delivery]** 範本，並命名傳送。

   ![](assets/line_usecase_01.png)

1. 在傳送的設定視窗中，選取您的目標人口。

   ![](assets/line_usecase_02.png)

1. 按一 **[!UICONTROL Add]** 下以建立訊息並選取 **[!UICONTROL Message type]**。

   在這裡，我們首先要建立文字訊息。

   ![](assets/line_usecase_03.png)

1. 將游標置於要插入個人化文字的位置，然後按一下下拉式圖示，然後選取 **[!UICONTROL Visitor > First name]**。

   ![](assets/line_usecase_05.png)

1. 請依照相同的程式新增影像，並 **[!UICONTROL Image and links]** 在下拉式清 **[!UICONTROL Message type]** 單中選取。

   新增您的影像URL。

   ![](assets/line_usecase_07.png)

1. 在區段 **[!UICONTROL Links]** 中，選取將影像分割為多個可點選區域的版面。
1. 為影像的每個區域指派URL。

   ![](assets/line_usecase_08.png)

1. 儲存傳送內容，然後按一 **[!UICONTROL Send]** 下以分析並傳送至目標。

   傳送內容會傳送至目標。

   ![](assets/line_usecase_06.png)
