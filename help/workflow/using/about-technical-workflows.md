---
product: campaign
title: 技術工作流程
description: 進一步瞭解Campaign Classic套件提供的技術工作流程
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 9aed2665-cd4b-419c-b9f2-ea04fc1d8f01
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1705'
ht-degree: 4%

---

# 技術工作流程{#about-technical-workflows}



## 關於技術工作流程 {#overview}

本節中詳述的工作流程會隨不同的Adobe Campaign內建套件安裝。 這些套件和相關的技術工作流程取決於您的授權合約。 有關內建套件的詳細資訊，請參閱 [本節](../../installation/using/installing-campaign-standard-packages.md).

依預設，技術工作流程可在以下節點的子資料夾中使用： **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

請注意，技術工作流程只能由具有管理許可權的運運算元啟動和修改。 如需許可權的詳細資訊，請參閱此 [區段](../../platform/using/access-management-groups.md#default-groups).

>[!NOTE]
>
>預設情況下，與訊息中心模組相關的技術工作流程可在 **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Message Center]** > **[!UICONTROL Technical workflows]** 節點。

如需如何監控技術工作流程的詳細資訊，請參閱 [專用區段](monitoring-technical-workflows.md).

## 技術工作流程清單 {#list-technical-workflows}

| 技術工作流程 | 套件 | 說明 |
|------|--------|-----------|
| **別名清除** (aliasCleaning) | 傳遞 | 此工作流程會將列舉值標準化。 預設會每天凌晨3:00觸發。 |
| **帳單** （帳單） | 傳遞 | 此工作流程會透過電子郵件將系統活動報告傳送給「帳單」操作員。 它會在每月25日在行銷執行個體上觸發。 |
| **計算Twitter統計資料** (statsTwitter) | 社交網路（社交行銷） — 僅限Campaign v7 | 此工作流程會計算連結至Twitter轉推和造訪的統計資料。 |
| **行銷活動工作** (operationMgt) | 行銷活動（行銷活動） | 此工作流程管理行銷活動的工作（啟動鎖定目標、檔案擷取等）。 也會建立與循環和定期行銷活動相關的工作流程。 |
| **收集熱度圖服務的資料** (collectDataHeatMapService) | 預設安裝 | 此工作流程會擷取HeatMap服務所需的資料。 |
| **收集隱私權請求** (collectPrivacyRequests) | 隱私權資料保護法規 | 此工作流程會產生儲存在Adobe Campaign中的收件者資料，並讓該資料可在隱私權請求的畫面中下載。 |
| **成本計算** (budgetM) | 行銷活動（行銷活動） | 此工作流程會開始計算預算、計畫、方案、行銷活動、傳遞和任務的費用和成本行。 |
| **資料庫清理** （清除） | 傳遞 | 此工作流程是資料庫維護工作流程：它會根據統計資料和程式進行不同的計算，並根據Deployment Assistant中定義的設定從資料庫刪除過時的資料。 預設會每天凌晨4:00觸發。 如需詳細資訊，請參閱[本頁面](../../production/using/database-cleanup-workflow.md#monitoring-campaign-classic)。 |
| **刪除封鎖的LINE使用者** (deleteBlockedLineUsersV2) | LINE 頻道 | 此工作流程可確保LINE V2使用者的資料在封鎖LINE正式帳戶180天後會被刪除。 |
| **刪除隱私權請求資料** (deletePrivacyRequestsData) | 隱私權資料保護法規 | 此工作流程會刪除收件者儲存在Adobe Campaign的資料。 |
| **傳遞指標** (deliveryIndicator) | 中間來源平台 | 此工作流程會更新傳送的傳送追蹤指標。 預設會每小時觸發此工作流程。 |
| **討論論壇程式** (newsgroupMgt) | 行銷資源(RM) | 此工作流程會管理討論區通知的傳送。 它會在收到核准訊號時觸發 |
| **分散式行銷流程** (centralLocalmgt) | 中央/地方行銷（分散式行銷） | 此工作流程會開始處理與使用分散式行銷模組相關。 它會啟動本機行銷活動的建立，並管理與訂單和行銷活動套件可用性相關的通知。 |
| **事件清除** (webAnalyticsPurgeWebEvents) | 網站分析聯結器 | 此工作流程可讓您根據「有效期限」欄位中設定的期間，從資料庫欄位中刪除每個事件。 |
| **將受眾匯出至Adobe Experience Cloud** (exportSharedAudience) | 與Adobe Experience Cloud整合 | 此工作流程會將受眾匯出為共用受眾/區段。 這些對象可用於您所使用的不同 Adobe Experience Cloud 解決方案。  |
| **預測** （預測） | 傳遞 | 此工作流程會分析臨時行事曆中儲存的傳遞（建立臨時記錄）。 預設會每天凌晨1:00觸發。 |
| **完整彙總計算(propositionrcp cube)** (agg_nmspropositionrcp_full) | 優惠方案引擎（互動） | 此工作流程會更新優惠方案主張Cube的完整彙總。 預設會每天早上6:00觸發。 此彙總會擷取下列維度：管道、傳送、行銷優惠方案和日期。 然後，優惠方案主張多維度資料集可用來根據優惠方案產生報表。 您可以在中進一步瞭解多維度資料集 [本節](../../reporting/using/ac-cubes.md). |
| **已轉換連絡人的識別** (webAnalyticsFindConverted) | 網站分析聯結器 | 此工作流程會索引在再次行銷活動後完成購買的網站訪客。 此工作流程所復原的資料可在再行銷效率報表中存取（請參閱本頁面）。 |
| **從Adobe Experience Cloud匯入對象** (importSharedAudience) | 與Adobe Experience Cloud整合 | 此工作流程可讓您將不同Adobe Experience Cloud解決方案中的對象/區段匯入至Adobe Campaign。 |
| **行銷活動中傳遞的工作** (deliveryMgt) | 行銷活動（行銷活動） | 此工作流程會觸發已核准的傳遞，並開始後續處理外部傳遞的服務提供者。 也會傳送核准通知和提醒。 |
| **服務提供者的工作** (supplierMgt) | 行銷活動（行銷活動） | 在核准傳遞後，此工作流程會開始處理提供者（傳送至路由器的電子郵件並進行後續處理）。 |
| **LINE V2存取權杖更新** (updateLineV2AccessToken) | LINE頻道 — 僅限Campaign v7 | 此工作流程會將存取Token重新整理至LINE V2。 |
| **MID到LineUserID移轉** (MIDToUserIDMigration) | LINE 頻道 | 此工作流程會產生LINE V2使用者ID，以便從LINE V1移轉至LINE V2。 |
| **行銷資源通知** (assetMgt) | 行銷資源(RM) | 此工作流程會管理連結至行銷資源核准和發佈的通知。 |
| **訊息中心 &lt;external_account_name>** (mcSynch_&lt;external_account_name>) | 異動訊息控制（訊息中心 — 控制） | 此工作流程： <ul><li>恢復作業處理的事件清單。</li><li>與NmsBroadLogMsg表格同步，以復原傳遞訊息資格。</li><li>與NmsBroadLogMsg表同步完成後，立即復原事件傳送記錄檔。</li><li>與NmsTrackingUrl表格同步，以復原傳遞URL的追蹤。</li><li>與NmsTrackingUrl表同步完成後，立即復原事件追蹤URL。</li><li>可讓您在傳送後，每三小時復原一次所有置於隔離的電子郵件地址。</li></ul> |
| **MessageCenter完整彙總計算** (agg_messageCenter_full) | 異動訊息控制（訊息中心 — 控制） | 此工作流程會更新訊息中心Cube的「完整」彙總。 預設會每天凌晨3:00觸發。 此彙總會擷取下列維度：管道、日期、狀態和事件型別。 然後，會使用訊息中心Cube來根據事件產生報表。 您可以在中進一步瞭解多維度資料集 [本節](../../reporting/using/ac-cubes.md) |
| **中間來源（傳遞計數器）** (defaultMidSourcingDlv) | 轉移至中間來源 | 此工作流程會收集中間來源伺服器上傳送的計數資訊。 計數資訊包括一般傳遞指標，例如已傳送的傳遞數量等。 未包含開啟之類的追蹤資訊。 預設會每十分鐘觸發一次。 |
| **中間來源（傳遞記錄）** (defaultMidSourcingLog) | 轉移至中間來源 | 此工作流程會在中間來源伺服器上收集傳遞記錄。 預設會每小時觸發一次。 |
| **NMAC選擇退出管理** (mobileAppOptOutMgt) | 行動應用程式頻道 | 此工作流程會更新行動裝置上的取消訂閱通知。 從上午1:00到午夜，每6小時觸發一次。 如需詳細資訊，請參閱 [本節](../../delivery/using/understanding-quarantine-management.md#push-notification-quarantines). |
| **優惠通知** (offerMgt) | 傳遞 | 此工作流程會將核准的優惠方案部署至線上環境，以及優惠方案目錄中包含的每個類別。 |
| **暫停的工作流程清理** (cleanupPausedWorkflows) | 傳遞 | 此工作流程會分析嚴重程度設定為正常的暫停工作流程，並在暫停太久時觸發警告和通知。 一個月後，暫停的技術工作流程會無條件停止。 預設會每週一早上5:00觸發。 如需詳細資訊，請參閱 [處理暫停的工作流程](monitoring-workflow-execution.md#handling-of-paused-workflows). |
| **隱私權請求清理** (cleanupPrivacyRequest) | 隱私權資料保護法規 | 此工作流程會清除90天以前的存取請求檔案。 |
| **處理批次事件** (batchEventsProcessing) | 異動訊息執行（訊息中心 — 執行） | 此工作流程可讓您在將批次事件與訊息範本產生關聯之前，先將批次事件放入佇列中。 |
| **處理即時事件** (rtEventsProcessing) | 異動訊息執行（訊息中心 — 執行） | 此工作流程可讓您在將即時事件與訊息範本產生關聯之前，先將其放入佇列中。 |
| **主張同步** (propositionSynch) | 透過執行例項控制優惠方案引擎 | 此工作流程會在行銷執行個體與用於互動的執行執行個體之間同步化主張。 |
| **復原Web事件** (webAnalyticsGetWebEvents) | 網站分析聯結器 | 每小時，此工作流程都會下載指定網站上網際網路使用者行為的區段，將其放入Adobe Campaign資料庫並啟動再行銷工作流程。 |
| **報告彙總** (reportingAggregates) | 傳遞 | 此工作流程會更新報告中使用的彙總。 預設會每天凌晨2:00觸發。 |
| **傳送指標和行銷活動屬性** (webAnalyticsSendMetrics) | 網站分析聯結器 | 此工作流程可讓您透過Adobe® Analytics聯結器，從Adobe Campaign傳送電子郵件行銷活動指標至Adobe Experience Cloud套裝。 相關指標如下： Sent (iSent)、開啟總數(iTotalRecipientOpen)、點按的收件者總數(iTotalRecipientClick)、錯誤(iError)、選擇退出（選擇退出） (iOptOut)。 |
| **庫存：訂單與警示** (stockMgt) | 行銷活動（行銷活動） | 此工作流程會啟動訂單明細行的庫存計算，並管理警告警示臨界值。 |
| **同步Facebook粉絲** (syncFacebookFans) | 社交網路（社交行銷） — 僅限Campaign v7 | 此工作流程每天早上7:00將Facebook粉絲匯入Adobe Campaign。 |
| **同步Facebook頁面** (syncFacebook) | 社交網路（社交行銷） — 僅限Campaign v7 | 此工作流程每天早上7:00與Adobe Campaign同步Facebook頁面。 |
| **同步Twitter頁面** (syncTwitter) | 社交網路（社交行銷） — 僅限Campaign v7 | 此工作流程每天早上7:00將Twitter追蹤者匯入Adobe Campaign。 |
| **任務通知** (taskM) | 行銷資源(MRM) — 僅限Campaign v7 | 此工作流程可讓您傳送與行銷活動中的任務相關的通知訊息。 |
| **追蹤** （追蹤） | 傳遞 | 此工作流程會執行追蹤資訊的復原與合併。 此外，還可確保重新計算追蹤和傳遞統計資料，尤其是訊息中心封存工作流程所使用的資料。 預設會每小時觸發一次。 |
| **更新事件狀態** (updateEventsStatus) | 異動訊息執行（訊息中心 — 執行） | 此工作流程可讓您為事件指派狀態。 事件狀態如下：<ul><li>擱置中：事件在佇列中。 尚未為其建立任何訊息範本的關聯。</li><li>擱置傳遞：事件在佇列中，訊息範本已與其建立關聯，且傳遞目前正在處理中。</li><li>已傳送：此狀態是從傳送記錄檔複製而來。 這表示傳遞已傳送。</li><li>已被傳送忽略：此狀態是從傳送記錄檔複製而來。 這表示已忽略傳遞。</li><li>傳送錯誤：此狀態是從傳送記錄檔複製而來。 這表示傳送失敗。</li><li>未涵蓋的事件：此事件無法與訊息範本建立關聯。 將不會重新處理事件。</li></ul> |
| **重新整理傳遞能力** (deliverabilityUpdate) | 傳遞 | 此工作流程每晚執行並管理退信電子郵件資格規則，以及網域和MX的清單。 這需要在平台上開啟HTTPS連線埠。 |