---
solution: Campaign Classic
product: campaign
title: 技術工作流程
description: 進一步瞭解Campaign Classic套件提供的技術工作流程。
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: f57f52d8807eb771e2416b6648e1d746a206fa96
workflow-type: tm+mt
source-wordcount: '1816'
ht-degree: 6%

---


# 技術工作流程{#about-technical-workflows}

## 關於技術工作流程 {#overview}

本節中詳述的工作流程會與不同的Adobe Campaign內建套件一起安裝。 這些套件和相關的技術工作流程取決於您的授權合約。 [本節](../../installation/using/installing-campaign-standard-packages.md)中詳細介紹了內置軟體包。

預設情況下，技術工作流可在以下節點的子資料夾中使用：**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**。

>[!NOTE]
>
>預設情況下，**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]**&#x200B;節點中提供與消息中心模組相關的技術工作流。

有關如何監控技術工作流的詳細資訊，請參閱[專用部分](../../workflow/using/monitoring-technical-workflows.md)。

## 技術工作流程清單 {#list-technical-workflows}

| 技術工作流程 | 封裝 | 說明 |
|------|--------|-----------|
| **別名清除** （別名清除） | 傳送 | 此工作流程標準化了列舉值。 預設每天凌晨3點觸發。 |
| **帳單** （帳單） | 傳送 | 此工作流程會透過電子郵件將系統活動報表傳送至「帳單」運算元。 預設會觸發每月25日。 |
| **計算Twitter統計資料** (statsTwitter) | 社交網路（Social行銷） | 此工作流程會計算連結至Twitter上回推和瀏覽的統計資料。 |
| **促銷活動工作** (operationMgt) | 行銷促銷活動（促銷活動） | 此工作流程管理行銷促銷活動的工作（啟動定位、檔案擷取等）。 它也會建立與週期性和週期性促銷活動相關的工作流程。 |
| **收集HeatMap服務的資料** (collectDataHeatMapService) | 依預設安裝 | 此工作流程會擷取HeatMap服務所需的資料。 |
| **收集隱私權要求** (collectPrivacyRequests) | 隱私權資料保護法規 | 此工作流程會產生儲存在Adobe Campaign中的收件者資料，並讓該資料可在隱私權要求的畫面中下載。 |
| **成本計算** (budgetMagt) | 行銷促銷活動（促銷活動） | 此工作流將開始計算預算、計畫、方案、促銷活動、交貨和任務上的費用和成本行。 |
| **資料庫清理** （清理） | 傳送 | 此工作流是資料庫維護工作流：它根據部署助理中定義的配置從資料庫中刪除過時資料，從而與統計和進程進行不同的計算。 預設每天凌晨4點觸發。 如需詳細資訊，請參閱[本頁面](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic)。 |
| **刪除已阻止的LINE用戶** (deleteBlockedLineUsersV2) | LINE 頻道 | 此工作流程可確保在LINE V2用戶封鎖180天的LINE正式帳戶後，刪除其資料。 |
| **刪除隱私權要求資料** (deletePrivacyRequestsData) | 隱私權資料保護法規 | 此工作流程會刪除Adobe Campaign中儲存的收件者資料。 |
| **交付指標** (deliveryIndicators) | 中間來源平台 | 此工作流程會更新傳送的傳送追蹤指標。 依預設，此工作流程會每小時觸發一次。 |
| **討論論壇流程** （新聞群組管理） | 行銷資源(MRM) | 此工作流程可管理論壇通知的傳送。 在收到核准訊號時觸發 |
| **分散式行銷流程** (centralLocalMagt) | 中央／本地行銷（分佈式行銷） | 此工作流程會開始處理與使用分散式行銷模組相關的處理。 它會啟動本機促銷活動的建立，並管理與訂購和促銷活動套件可用性相關的通知。 |
| **事件清除** (webAnalyticsPurgeWebEvents) | 網頁分析連接器 | 此工作流允許您根據「期限」(Lifetime)欄位中配置的期間，從資料庫欄位中刪除每個事件。 |
| **將觀眾匯出至Adobe Experience Cloud** (exportSharedAudience) | 與Adobe Experience Cloud整合 | 此工作流程會將觀眾匯出為共用的觀眾／區段。 這些受眾可用於您所使用的不同Adobe Experience Cloud解決方案。 |
| **預測** （預測） | 傳送 | 此工作流程會分析儲存在臨時日曆中的傳送（建立臨時記錄）。 預設會在每天凌晨1點觸發。 |
| **完全集合計算(propositionrcp cube)** (agg_nmspropositionrcp_full) | 選件引擎（互動） | 此工作流程會更新選件提案立方的完整匯總。 預設會在每天早上6點觸發。 此匯總會擷取下列維度：渠道、傳送、行銷優惠和日期。 然後，「選件」提案立方會用來根據選件產生報表。 您可以在[本節](../../reporting/using/about-cubes.md)中進一步瞭解立方體。 |
| **已轉換的連絡人識別** (webAnalyticsFindConverted) | 網頁分析連接器 | 此工作流程會為在重新行銷促銷活動後完成購買的網站訪客建立索引。 此工作流程所復原的資料可在重新行銷效率報告中存取（請參閱本頁）。 |
| **從Adobe Experience Cloud匯入觀眾** (importSharedAudience) | 與Adobe Experience Cloud整合 | 此工作流程可讓您將不同Adobe Experience Cloud解決方案的受眾／細分匯入Adobe Campaign。 |
| **促銷活動中傳送的工作** (deliveryMgt) | 行銷促銷活動（促銷活動） | 此工作流程會觸發已核准的傳送，並開始對外部傳送的服務提供者進行後處理。 它也會傳送核准通知和提醒。 |
| **服務提供商上的任務** （供應商管理） | 行銷促銷活動（促銷活動） | 一旦交件獲得批准，此工作流將開始處理提供程式（向路由器發送電子郵件和後處理）。 |
| **LINE V2存取Token更新** (updateLineV2AccessToken) | LINE 頻道 | 此工作流程會將存取Token重新整理為LINE V2。 |
| **MID到LineUserID遷移** (MIDToUserIDMigration) | LINE 頻道 | 此工作流將生成LINE V2用戶的ID，以便從LINE V1遷移到LINE V2。 |
| **行銷資源通知** （資產管理） | 行銷資源(MRM) | 此工作流程管理連結至核准和發佈行銷資源的通知。 |
| **消息中 &lt;external_account_name>** 心(mcSynch_&lt;external_account_name>) | 事務性消息控制（消息中心——控制） | 此工作流程： <ul><li>恢復由操作處理的事件清單。</li><li>與NmsBroadLogMsg表同步，以恢復發送消息的資格。</li><li>當與NmsBroadLogMsg表的同步完成時，可以立即恢復事件發送日誌。</li><li>與NmsTrackingUrl表同步，以便恢復傳送URL的追蹤。</li><li>當與NmsTrackingUrl表的同步完成時，會立即恢復事件追蹤URL。</li><li>可讓您在傳送傳送後每三小時恢復隔離中放置的所有電子郵件地址。</li></ul> |
| **MessageCenter完整聚合計算** (agg_messageCenter_full) | 事務性消息控制（消息中心——控制） | 此工作流將更新消息中心多維資料集的完全聚合。 預設每天凌晨3點觸發。 此匯總會擷取下列維度：渠道、日期、狀態和事件類型。 然後，消息中心多維資料集用於根據事件生成報告。 您可以在[本節](../../reporting/using/about-cubes.md)中進一步瞭解立方 |
| **中間採購（傳送計數器）** (defaultMidSourcingDlv) | 轉移至中間來源 | 此工作流程會收集中間採購伺服器上傳送的計數資訊。 計數資訊包括一般傳送指標，例如傳送的傳送數量等。 不包含開啟等追蹤資訊。 預設每10分鐘觸發一次。 |
| **中端採購（傳送記錄）** (defaultMidSourcingLog) | 轉移至中間來源 | 此工作流程會收集中端採購伺服器上的傳送記錄。 預設會每小時觸發一次。 |
| **NMAC退出管理** (mobileAppOptOutMagt) | 行動應用程式頻道 | 此工作流程會更新行動裝置上取消訂閱的通知。 每6小時從凌晨1點到午夜觸發一次。 有關詳細資訊，請參閱[本節](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines)。 |
| **有效帳單設定檔數** (billingActiveContactCount) | 傳送 | 此工作流程會計算作用中描述檔的數目。 預設會在每晚1點觸發。 「設定檔」是指一筆代表終端客戶或潛在客戶之資訊的記錄 (例如：nmsRecipient 表格或外部表格中的記錄，包含 cookie 識別碼、客戶識別碼、行動識別碼或特定通路相關的其他資訊)。計費只涉及「作用中」的設定檔。 如果描述檔在過去12個月內已透過任何通道鎖定或傳達，則描述檔會被視為「作用中」。 Facebook 和 Twitter 通路不包含在內。您可以從 Administration > Campaign Management > Customer metrics 選單中獲得 Number of active profiles 的概要。 |
| **選件通知** （選件管理） | 傳送 | 此工作流程會將核准的選件部署至線上環境，以及選件目錄中包含的每個類別。 |
| **暫停的工作流程清理** (cleanupPausedWorkflows) | 傳送 | 此工作流程會分析嚴重性設為一般的暫停工作流程，並在暫停過久時觸發警告和通知。 一個月後，暫停的技術工作流程會無條件停止。 預設情況下，每週一早上5點觸發。 如需詳細資訊，請參閱[處理暫停的工作流程](../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows)。 |
| **隱私權要求清除** (cleanupPrivacyRequests) | 隱私權資料保護法規 | 此工作流程會清除90天以前的存取要求檔案。 |
| **處理批次事件** (batchEventsProcessing) | 事務性消息執行（消息中心——執行） | 此工作流程可讓您在將批次事件與訊息範本建立關聯之前，先將它們放入佇列。 |
| **處理即時事件** (rtEventsProcessing) | 事務性消息執行（消息中心——執行） | 此工作流程可讓您在將即時事件與訊息範本建立關聯之前，將即時事件放入佇列。 |
| **命題同步** （命題同步） | 具有執行例項的選件引擎控制 | 此工作流程會同步行銷實例和用於互動的執行實例之間的陳述。 |
| **網頁事件的復原** (webAnalyticsGetWebEvents) | 網頁分析連接器 | 此工作流程每小時都會下載特定網站上網際網路使用者行為的區段，並將它們放入Adobe Campaign資料庫，然後啟動再行銷工作流程。 |
| **Reporting aggregates** (reportingAggregates) | 傳送 | 此工作流程會更新報表中使用的匯總。 預設會在每天凌晨2點觸發。 |
| **傳送指標和促銷活動屬性** (webAnalyticsSendMetrics) | 網頁分析連接器 | 此工作流程可讓您透過Adobe® Genesis連接器，從Adobe Campaign傳送電子郵件宣傳指標至Adobe Experience Cloud Suite。 相關指標如下：已傳送(iSent)、開啟總數(iTotalRecipientOpen)、點按的收件者總數(iTotalRecipientClick)、錯誤(iError)、退出（選擇退出）(iOptOut)。 |
| **股票：訂購與警報** (StockMagt) | 行銷促銷活動（促銷活動） | 此工作流會在訂單行上啟動庫存計算並管理警告警報閾值。 |
| **同步Facebook粉絲** （syncFacebook粉絲） | 社交網路（Social行銷） | 此工作流程每天早上7點將Facebook粉絲匯入Adobe Campaign。 |
| **同步Facebook頁面** (syncFacebook) | 社交網路（Social行銷） | 此工作流程每天早上7點將Facebook頁面與Adobe Campaign同步。 |
| **同步Twitter頁面** (syncTwitter) | 社交網路（Social行銷） | 此工作流程會每天早上7點將Twitter追隨者匯入Adobe Campaign。 |
| **任務通知** (taskMgt) | 行銷資源(MRM) | 此工作流程可讓您傳送與行銷促銷活動中的工作相關的通知訊息。 |
| **追蹤** (追蹤 | 傳送 | 此工作流程會執行追蹤資訊的復原與整合。 它還可確保重新計算跟蹤和傳送統計資訊，特別是郵件中心歸檔工作流中使用的統計資訊。 依預設，每小時會觸發一次。 |
| **更新事件狀態** (updateEventsStatus) | 事務性消息執行（消息中心——執行） | 此工作流程可讓您指派狀態給事件。 事件狀態如下：<ul><li>待定：事件在隊列中。 尚未與消息模板關聯。</li><li>待定傳送：事件在佇列中，訊息範本已與其關聯，且目前正由傳送處理。</li><li>已傳送：此狀態會從傳送記錄複製。 這表示傳送已傳送。</li><li>傳送忽略：此狀態會從傳送記錄複製。 這表示傳送已被忽略。</li><li>傳送錯誤：此狀態會從傳送記錄複製。 這意味著交付失敗。</li><li>未涵蓋的事件：事件無法與消息模板關聯。 不會重新處理事件。</li></ul> |
| **可傳遞性更新** （可傳遞性更新） | 傳送 | 一旦安裝「傳送能力」監控（電子郵件傳送能力）套件後，此工作流程會在夜間執行，並管理反彈電子郵件的資格規則以及網域和MX清單。 這需要在平台上開啟HTTPS埠 |
| **更新收件箱轉換的種子網路** (updateRenderingSeeds) | 收件箱呈現(IR) | 此工作流程會更新用於「收件匣」轉譯的電子郵件地址，而且只有在HTTPS連接埠已開啟以提供傳送功能。neolane.net時，這個工作流程才會運作。 |
