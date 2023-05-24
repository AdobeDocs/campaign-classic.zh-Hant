---
product: campaign
title: 開始使用追蹤
description: 進一步瞭解Adobe Campaign中追蹤的一般准則
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring, Email
exl-id: 43779505-9917-4e99-af25-b00a9d29a645
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 10%

---

# 開始使用訊息追蹤 {#get-started-tracking}



藉由Adobe Campaign的追蹤功能，您可以追蹤傳送的訊息並檢查收件者的行為：開啟、點按連結、取消訂閱等。

此資訊擷取於 **[!UICONTROL Tracking]** 每個傳遞收件者之設定檔的索引標籤。 此標籤會顯示從清單中選取的收件者所追蹤和點選的所有URL連結。 這是在傳送中追蹤的所有URL的累積，這些URL仍存在於傳送畫面中。 清單可以設定，通常會包含：點按的URL、點按的日期和時間，以及找到URL的檔案。 如需詳細資訊，請參閱[本章節](../../platform/using/editing-a-profile.md#tracking-tab)。

此 **傳遞儀表板** 也是監控傳送訊息期間所遇到之傳送和最終問題的關鍵。 如需詳細資訊，請參閱 [本節](delivery-dashboard.md).

下圖顯示使用者與各種伺服器之間的對話階段。

![](assets/tracking-diagram.png)

## 設定追蹤 {#configure-tracking}

<img src="assets/do-not-localize/icon-configure.svg" width="60px">

**操作原則**

在使用追蹤之前，您必須先為例項設定追蹤。 [了解更多](../../installation/using/deploying-an-instance.md#operating-principle)

**追蹤伺服器**

若要設定追蹤，您必須向追蹤伺服器宣告及註冊執行個體。 [了解更多](../../installation/using/deploying-an-instance.md#tracking-server)

**儲存追蹤**

設定追蹤並填入您的URL後，必須註冊追蹤伺服器。 [了解更多](../../installation/using/deploying-an-instance.md#saving-tracking)

## 訊息追蹤 {#message-tracking}

<img src="assets/do-not-localize/icon-message-tracking.svg" width="60px">

**追蹤的連結**

您可以追蹤訊息是否收到，以及郵件內容中所插入連結的啟用情況，以便更清楚瞭解收件者的行為。 [了解更多](how-to-configure-tracked-links.md)

**URL追蹤**

追蹤選項可透過啟用或停用追蹤的URL來設定。 [了解更多](personalizing-url-tracking.md)

**追蹤的連結個人化**

Campaign Classic追蹤功能可讓您在電子郵件中新增可個人化且支援追蹤的連結。 [了解更多](tracking-personalized-links.md)

**追蹤記錄**

在傳送傳遞並啟用追蹤後，「追蹤」技術工作流程會擷取追蹤資料。 此資料可在傳遞的「追蹤」標籤中找到。 [了解更多](accessing-the-tracking-logs.md)

**測試追蹤**

在使用追蹤傳送訊息之前，您可以在映象頁面、電子郵件記錄檔和連結上測試追蹤。 [了解更多](testing-tracking.md)

## 網路應用程式追蹤 {#web-application-tracking}

<img src="assets/do-not-localize/icon-web-app.svg" width="60px">

**追蹤 Web 應用程式**

您也可以追蹤和測量具有追蹤標籤的網頁應用程式頁面上的造訪次數。 此功能可用於所有Web應用程式型別，例如表單和登入頁面。 [了解更多](../../web/using/tracking-a-web-application.md)

**網站應用程式追蹤選擇退出**

選擇退出網站應用程式追蹤可讓您停止追蹤選擇退出行為追蹤之一般使用者的網站行為。 您可以在網頁應用程式或登入頁面中加入顯示橫幅的功能，讓使用者選擇退出。 [了解更多](../../web/using/web-application-tracking-opt-out.md)

## 追蹤報表 {#tracking-reports}

<img src="assets/do-not-localize/icon_monitor.svg" width="60px">

**追蹤統計資料**

此報表提供有關開啟、點按和交易的統計資料，並讓您追蹤傳送對行銷的影響。 [了解更多](../../reporting/using/delivery-reports.md#tracking-statistics)

**URL 和點按流**

此報表顯示傳送後瀏覽的頁面清單。 [了解更多](../../reporting/using/delivery-reports.md#urls-and-click-streams)

**人員與收件者**

透過此範例，更能瞭解Adobe Campaign中個人/人員與收件者之間的追蹤差異。 [了解更多](../../reporting/using/person-people-recipients.md)

**追蹤指標**

此報表結合關鍵指標，用於追蹤收件者在收到傳遞時的行為，例如開啟、點進率和點進資料流。 [了解更多](../../reporting/using/delivery-reports.md#tracking-indicators)

**指示器計算**

不同的表格會根據傳遞型別，提供不同報告中使用的指標清單及其計算公式。 [了解更多](../../reporting/using/indicator-calculation.md)

## 追蹤疑難排解 {#tracking-troubleshooting}

<img src="assets/do-not-localize/icon-troubleshooting.svg" width="60px">

下列疑難排解提示可協助您解決在Adobe Campaign Classic中使用追蹤時最常見的問題。 如需更進階的疑難排解，請參閱 [本節](tracking-troubleshooting.md).

* 檢查trackinglogd程式是否正在執行

   此程式會從IIS/Web伺服器共用記憶體讀取並寫入重新導向記錄。

   您可以選取執行個體中的「監督」頁簽，從「首頁」存取它。 您也可以在執行個體上執行下列命令： `<user>@<instance>:~$ nlserver pdump`

   如果trackinglogd處理序未出現在清單中，請在執行個體上使用下列命令來啟動它： `<user>@<instance>:~$ nlserver start trackinglogd`

* 檢查追蹤技術工作流程最近是否一直在執行。

   您可以在資料夾管理>生產>技術工作流程中找到追蹤技術工作流程。
