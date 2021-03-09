---
solution: Campaign Classic
product: campaign
title: 開始追蹤
description: 進一步瞭解在Adobe Campaign Classic追蹤的一般方針。
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: e52d1963b72593c5dab8ced9e459d25b05044022
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 9%

---


# 開始使用訊息追蹤{#get-started-tracking}

由於其追蹤功能，Adobe Campaign可讓您追蹤傳送的訊息，並檢查收件者的行為：開啟、點按連結、取消訂閱等。

此資訊會擷取至傳送之每個收件者之描述檔的&#x200B;**[!UICONTROL Tracking]**&#x200B;標籤中。 此標籤會顯示清單中選取之收件者所追蹤和點按的所有URL連結。 這是傳送畫面中仍顯示之傳送中追蹤的所有URL的累積。 清單可以設定，通常會包含：點按的URL、點按的日期和時間，以及找到URL的檔案。 如需詳細資訊，請參閱[本章節](../../platform/using/editing-a-profile.md#tracking-tab)。

**傳送控制面板**&#x200B;也是監控傳送以及傳送訊息時最終遇到問題的關鍵。 有關詳細資訊，請參閱[本節](../../delivery/using/delivery-dashboard.md)。

下圖顯示了用戶與各種伺服器之間對話的各個階段。

![](assets/tracking-diagram.png)

## 設定追蹤{#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**操作原則**

在使用追蹤之前，您必須先為您的例項設定它。 [進一步了解](../../installation/using/deploying-an-instance.md#operating-principle)

**追蹤伺服器**

若要設定追蹤，您的例項必須向追蹤伺服器宣告並註冊。 [進一步了解](../../installation/using/deploying-an-instance.md#tracking-server)

**儲存追蹤**

設定追蹤並填入URL後，必須註冊追蹤伺服器。 [進一步了解](../../installation/using/deploying-an-instance.md#saving-tracking)

## 消息跟蹤{#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**追蹤的連結**

您可以追蹤訊息的接收和訊息內容中插入連結的啟動，以便更好地瞭解收件者的行為。 [進一步了解](../../delivery/using/how-to-configure-tracked-links.md)

**URL追蹤**

追蹤選項可透過啟用或停用追蹤的URL來設定。 [進一步了解](../../delivery/using/personalizing-url-tracking.md)

**追蹤連結個人化**

Campaign Classic追蹤功能可讓您在電子郵件中新增可個人化且支援追蹤的連結。 [進一步了解](../../delivery/using/tracking-personalized-links.md)

**追蹤記錄檔**

傳送並啟動追蹤後，追蹤技術工作流程會擷取追蹤資料。 此資料可在您傳送的「追蹤」標籤中找到。 [進一步了解](../../delivery/using/accessing-the-tracking-logs.md)

**測試追蹤**

在傳送您的追蹤訊息之前，您可以先在您的鏡像頁面、電子郵件記錄檔和連結上測試追蹤。 [進一步了解](../../delivery/using/testing-tracking.md)

## 網路應用程式追蹤{#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**追蹤 Web 應用程式**

您也可以使用追蹤標籤來追蹤和測量網頁上的瀏覽。 此功能可用於所有Web應用程式類型，例如表單和線上調查。 [進一步了解](../../web/using/tracking-a-web-application.md)

**Web 應用程式追蹤選擇退出**

選擇退出的網路應用程式追蹤可讓您停止追蹤選擇退出行為追蹤的使用者的網路行為。 您可以包含在Web應用程式或登陸頁面中顯示橫幅的功能，讓使用者可以選擇退出。 [進一步了解](../../web/using/web-application-tracking-opt-out.md)

## 追蹤報表{#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**追蹤統計資料**

此報表提供開啟、點按和交易的統計資料，並可讓您追蹤傳送的行銷影響。 [進一步了解](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL 和點按流**

此報表顯示傳送後所瀏覽的頁面清單。 [進一步了解](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**人員與收件者**

透過此範例，進一步瞭解Adobe Campaign地區的人員／人員與收件者之間的追蹤差異。 [進一步了解](../../reporting/using/person-people-recipients.md)

**追蹤指標**

此報告結合了在收到傳送時追蹤收件者行為的關鍵指標，例如開啟率、點進率和點按流。 [進一步了解](../../reporting/using/delivery-reports.md#tracking-indicators)

**指示器計算**

不同的表格會根據傳送類型提供不同報表中使用的指標清單及其計算公式。 [進一步了解](../../reporting/using/indicator-calculation.md)

## 追蹤疑難排解{#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

下列疑難排解提示將協助您解決在Adobe Campaign Classic使用追蹤時最常發生的問題。 如需更進階的疑難排解，請參閱[本節](../../delivery/using/tracking-troubleshooting.md)。

* 檢查trackinglogd進程是否正在運行

   此過程從IIS/Web伺服器共用記憶體讀取並寫入重定向日誌。

   您可以在例項中選擇「監視」標籤，從首頁存取它。 您也可以對實例執行以下命令：`<user>@<instance>:~$ nlserver pdump`

   如果trackinglogd程式未出現在清單中，請在執行個體上使用下列命令啟動它：`<user>@<instance>:~$ nlserver start trackinglogd`

* 檢查追蹤技術工作流程是否最近已執行。

   您可以在資料夾「管理>生產>技術工作流程」中找到「追蹤技術」工作流程。
