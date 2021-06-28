---
product: campaign
title: 開始追蹤
description: 進一步了解Adobe Campaign Classic中追蹤的一般准則。
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: ee3d643e4ba607b3d7ca816eabf862b867d1f3f4
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 9%

---

# 開始使用訊息追蹤 {#get-started-tracking}

有了Adobe Campaign的追蹤功能，您便能追蹤傳送的訊息，並檢查收件者的行為：開啟、點按連結、取消訂閱等。

此資訊會在傳送每個收件者之設定檔的&#x200B;**[!UICONTROL Tracking]**&#x200B;標籤中擷取。 此索引標籤會顯示清單中所選收件者所追蹤及點按的所有URL連結。 這是傳遞畫面中仍顯示之傳遞中追蹤的所有URL的累積。 清單可以設定，且通常包含：點按的URL、點按的日期和時間，以及找到URL的檔案。 如需詳細資訊，請參閱[本章節](../../platform/using/editing-a-profile.md#tracking-tab)。

**傳遞控制面板**&#x200B;也是監控傳送及傳送訊息期間最終遇到問題的關鍵。 有關詳細資訊，請參閱[此部分](delivery-dashboard.md)。

下圖顯示使用者與各種伺服器之間對話的階段。

![](assets/tracking-diagram.png)

## 設定追蹤 {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**操作原則**

使用追蹤之前，您必須先為執行個體設定它。 [深入瞭解](../../installation/using/deploying-an-instance.md#operating-principle)

**追蹤伺服器**

若要設定追蹤，您的例項必須向追蹤伺服器宣告及註冊。 [深入瞭解](../../installation/using/deploying-an-instance.md#tracking-server)

**儲存追蹤**

設定追蹤並填入URL後，必須註冊追蹤伺服器。 [深入瞭解](../../installation/using/deploying-an-instance.md#saving-tracking)

## 訊息追蹤 {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**追蹤的連結**

您可以追蹤訊息的接收情況以及郵件內容中插入的連結的啟用情況，以便更清楚了解收件者的行為。 [深入瞭解](how-to-configure-tracked-links.md)

**URL追蹤**

您可以啟用或停用追蹤的URL來設定追蹤選項。 [深入瞭解](personalizing-url-tracking.md)

**追蹤連結個人化**

Campaign Classic追蹤功能可讓您在可個人化且支援追蹤的電子郵件中新增連結。 [深入瞭解](tracking-personalized-links.md)

**追蹤記錄**

追蹤技術工作流程會在傳送並啟動追蹤後擷取追蹤資料。 您可以在傳送的「追蹤」標籤中找到此資料。 [深入瞭解](accessing-the-tracking-logs.md)

**測試追蹤**

在使用追蹤傳送訊息之前，您可以先在鏡像頁面、電子郵件記錄檔和連結上測試追蹤。 [深入瞭解](testing-tracking.md)

## Web應用程式追蹤 {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**追蹤 Web 應用程式**

您也可以使用追蹤標籤來追蹤及測量網頁上的造訪次數。 此功能可用於所有Web應用程式類型，例如表單和登錄頁面。 [深入瞭解](../../web/using/tracking-a-web-application.md)

**網站應用程式追蹤選擇退出**

Web應用程式追蹤選擇退出可讓您停止追蹤選擇退出行為追蹤之使用者的Web行為。 您可以包含將橫幅顯示至網頁應用程式或登陸頁面的功能，讓使用者可以選擇退出。 [深入瞭解](../../web/using/web-application-tracking-opt-out.md)

## 追蹤報表 {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**追蹤統計資料**

此報表提供開啟、點按和交易的統計資料，並可讓您追蹤傳送對行銷的影響。 [深入瞭解](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL 和點按流**

此報表顯示傳送後所造訪的頁面清單。 [深入瞭解](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**人員與收件者**

透過此範例，更清楚了解Adobe Campaign中人員與收件者之間的追蹤差異。 [深入瞭解](../../reporting/using/person-people-recipients.md)

**追蹤指標**

此報表結合了在收到傳遞時追蹤收件者行為的關鍵指標，例如開啟率、點進率和點按資料流。 [深入瞭解](../../reporting/using/delivery-reports.md#tracking-indicators)

**指示器計算**

不同的表格會根據傳送類型，提供不同報表中使用的指標清單及其計算公式。 [深入瞭解](../../reporting/using/indicator-calculation.md)

## 追蹤疑難排解 {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

下列疑難排解提示可協助您解決在Adobe Campaign Classic中使用追蹤時最常發生的問題。 如需更進階的疑難排解，請參閱[此區段](tracking-troubleshooting.md)。

* 檢查trackinglogd程式是否執行中

   此過程從IIS/Web伺服器共用記憶體中讀取並寫入重定向日誌。

   您可以在執行個體中選取「監控」標籤，從首頁存取它。 您也可以在執行個體上執行下列命令：`<user>@<instance>:~$ nlserver pdump`

   如果trackinglogd程式未出現在清單中，請在執行個體上使用下列命令啟動：`<user>@<instance>:~$ nlserver start trackinglogd`

* 檢查「追蹤」技術工作流程是否最近執行。

   您可以在資料夾「管理>生產>技術工作流程」中找到「追蹤」技術工作流程。
