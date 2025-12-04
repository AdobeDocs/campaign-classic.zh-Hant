---
product: campaign
title: 開始使用傳遞監視
description: 進一步瞭解Campaign Classic傳遞監視功能
feature: Monitoring, Deliverability
role: User
exl-id: 9ce11da0-e37b-459e-8ec7-d2bddf59bdf7
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 1%

---

# 開始使用傳遞監視 {#about-delivery-monitoring}

>[!IMPORTANT]
>
>此頁面記錄混合式與內部部署的&#x200B;**Campaign Classic v7特定監視功能**。

## 監視功能

### 傳遞監視 {#monitoring-deliveries}

**若是Campaign Classic v7混合/內部部署**，伺服器資源和MTA （郵件傳輸代理程式）設定需要額外的監視。

#### 疑難排解擱置的傳遞 {#pending-deliveries}

如果未傳送傳遞且其狀態仍為&#x200B;**擱置中**，該怎麼辦？

* 執行程式正在等待某些資源的可用性。 MTA可能尚未啟動。
檢查您的mta@instance模組是否已在MTA伺服器上啟動，並視需要啟動MTA模組。 [了解更多](../../production/using/administration.md)。

* 傳遞可能使用傳送執行個體上尚未設定的相似性。
提示：檢查流量管理（IP相似性）的設定。 如需詳細資訊，請參閱控制傳出SMTP流量。

>[!NOTE]
>
>這些步驟只能由內部部署安裝的專家使用者執行。

### 傳遞能力監視 {#deliverability-monitoring}

#### 傳遞套件安裝 {#deliverability-package}

此功能透過Adobe Campaign中的專用套件提供。 若要使用它，必須安裝此套件。 完成後，請重新啟動伺服器以納入考量的套件。

* 針對託管及混合式使用者端，Adobe技術支援和顧問已在您的執行個體上設定&#x200B;**傳遞能力監視**。 如需詳細資訊，請聯絡您的Adobe客戶主管。

* 對於內部部署安裝，您必須透過&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]** > **[!UICONTROL Tools]** > **[!UICONTROL Advanced]**&#x200B;功能表安裝&#x200B;**[!UICONTROL Import package]**&#x200B;套件。 如需詳細資訊，請參閱[安裝Campaign Classic標準套件](../../installation/using/installing-campaign-standard-packages.md)。

#### 傳遞能力工作流程 {#deliverability-workflow}

在Adobe Campaign Classic中，**傳遞能力監視**&#x200B;是由&#x200B;**[!UICONTROL Refresh for deliverability]**&#x200B;工作流程管理。 依預設，它安裝在所有執行個體上，可讓您初始化退回郵件限定規則清單、網域清單和MX清單。 安裝&#x200B;**[!UICONTROL Deliverability monitoring (Email Deliverability)]**&#x200B;封裝後，此工作流程會在夜間執行，以定期更新規則清單，並讓您主動管理平台傳遞能力。

**傳遞套件可讓您存取：**

* [收件匣轉譯報告](inbox-rendering.md)可讓您預覽主要電子郵件使用者端上的郵件，以掃描內容與信譽。
* 訊息品質（收件匣、垃圾郵件）的概觀。

#### 監控工具 {#monitoring-tools}

**對於內部部署安裝**，您可以使用下列監視工具：

* **[!UICONTROL Delivery throughput]**&#x200B;報告提供指定期間內整個平台的輸送量概觀。 如需詳細資訊，請參閱[本節](../../reporting/using/global-reports.md#delivery-throughput)。
* 每次傳送都會產生不同網際網路服務提供者(ISP)的廣播統計報表。 它會顯示一些可能影響您傳送能力的資料品質和信譽量度，包括下列數字：
   * **[!UICONTROL Hard bounces]**&#x200B;表示資料品質。 此數字應小於2%。
   * **[!UICONTROL Soft bounces]**&#x200B;表示信譽。 任何特定ISP的這個數字都不應超過10%。

  如需詳細資訊，請參閱[傳遞統計資料](../../reporting/using/global-reports.md#delivery-statistics)區段。

#### 監視指南 {#monitoring-guidelines}

**對於內部部署安裝**，以下是傳遞能力監視的其他准則：

* 定期檢查整個平台的[傳遞輸送量](../../reporting/using/global-reports.md#delivery-throughput)，以確認其是否與原始設定一致。
* 檢查傳遞範本中的[重試](delivery-failures-quarantine.md#retries-after-a-delivery-temporary-failure)是否已正確設定（重試期間為30分鐘，重試次數超過20次）。
* 定期確認[退信](delivery-failures-quarantine.md#bounce-mail-management)信箱可存取，且帳戶不會過期。
* 檢查可從[傳遞儀表板](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}存取的每個傳遞輸送量，以確保其與傳遞內容的有效性一致（例如，「Flash銷售」應在幾分鐘內傳遞，而非幾天）。
* 使用波段時，請確認每個波段都有足夠的時間完成，才能觸發下一個波段。
* 檢查錯誤數目和新的[隔離](delivery-failures-quarantine.md)是否與其他傳遞一致。
* 仔細查閱[傳遞記錄](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard#delivery-logs-and-history){target="_blank"}以詳細檢查反白顯示的錯誤型別（封鎖清單、DNS問題、反垃圾郵件規則等）。

### 疑難排解 {#delivery-troubleshooting}

在&#x200B;**混合/內部部署**&#x200B;上遇到傳遞問題時，可執行特定動作：

* [傳遞能力問題](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [影像顯示問題](../../production/using/image-display-issues.md)
* [傳遞效能問題](delivery-performance-troubleshooting.md)
* [暫存檔案問題](../../production/using/temporary-files.md) — 僅限&#x200B;*內部部署客戶*

## 監視您的傳遞

下列資源將協助您監視及追蹤Campaign Classic v7的傳遞效能：

### 存取傳遞儀表板

瞭解如何存取傳遞清單，並使用傳遞儀表板來監視您的傳送活動：

* [在Campaign UI中監視傳遞](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} （Campaign v8檔案 — 適用於v7和v8）
* [傳遞狀態](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} （Campaign v8檔案）
* [進階：自訂傳遞記錄](customize-delivery-logs.md) （僅限v7混合/內部部署 — 結構描述延伸）

### 追蹤訊息互動

追蹤開啟、點按次數，以及收件者與您傳送內容的互動：

* [訊息追蹤檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking){target="_blank"} （Campaign v8檔案 — 適用於v7和v8）
* [設定追蹤的連結](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracked-links){target="_blank"} （Campaign v8檔案）
* [存取追蹤記錄](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/analytics/tracking/tracking-logs){target="_blank"} （Campaign v8檔案）

### 最佳化傳遞效能

傳遞效能問題的最佳實務及疑難排解：

* [傳遞最佳實務](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} （Campaign v8檔案 — 適用於v7和v8）
* [傳遞效能與疑難排解](delivery-performance-troubleshooting.md) （v7混合/內部部署特定設定）

### 瞭解失敗和隔離

管理傳送失敗、退回郵件和隔離地址：

* [瞭解傳送失敗](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} （Campaign v8檔案 — v7和v8的全面指南）
* [隔離管理](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} （Campaign v8檔案 — v7和v8的完整指南）
* [傳送失敗和隔離設定](delivery-failures-quarantine.md) （v7混合/內部部署特定設定）
