---
title: 資料庫效能
seo-title: 資料庫效能
description: 資料庫效能
seo-description: null
page-status-flag: never-activated
uuid: 47ff7532-1fe7-47c2-bc3b-0f46d3a4a288
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 6358c8fd-2b75-4462-acd1-887ee44d3110
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# 資料庫效能{#database-performances}

大多數效能問題都與資料庫維護相關。 以下是四個主要線索，可協助您找出效能緩慢的原因：

* 配置、
* Adobe Campaign平台的安裝與設定、
* 資料庫維護、
* 即時診斷。

## 配置 {#configuration}

檢查初始的Adobe Campaign平台設定是否仍然有效，並視需要重新評估客戶的傳遞能力或資料庫大小需求。 我們也建議執行完整硬體檢查（CPU、RAM、IO系統）。

>[!NOTE]
>
>如需深入資訊， [請參閱Adobe Campaign硬體調整指南](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html) 。

## 平台配置 {#platform-configuration}

不當的配置可能會影響平台效能。 建議您檢查serverConf.xml檔案中的網路組態、平台傳遞能力選項 **以及MTA組態** 。

## 資料庫維護 {#database-maintenance}

**資料庫清理任務**

請確保資料庫清理任務已運行。 若要這麼做，請檢視記錄檔，以查看其中是否包含任何錯誤。 如需詳細資訊，請參閱[本小節](../../production/using/database-cleanup-workflow.md)。

**維護計畫**

確保正確排程並執行資料庫維護。 若要這麼做，請連絡您的資料庫管理員以進一步瞭解：

* 他們的維護計畫，
* 先前執行的維護計畫，
* 查看指令碼日誌。

如需詳細資訊，請參閱[本小節](../../production/using/recommendations.md)。

>[!CAUTION]
>
>如果您使用中間採購配置，則必須定期維護資料庫。 分析行銷平台上的傳送時，行銷例項會傳送資訊至中間採購例項。 如果程式變慢，行銷例項將會受到影響。

**管理工作表**

請檢查工作表的數量和大小。 當資料庫超過某一大小時，資料庫效能會受到影響。 這些表格是由工作流程和傳送所建立。 它們會保留在資料庫中，而工作流程和傳送則會處於作用中。 要限制工作表的大小，可執行以下操作：

* 停止或刪除具有下列狀態的傳送： **[!UICONTROL Failed]** 、 **[!UICONTROL In progress]** 、 **[!UICONTROL Ready for delivery]** 或 **[!UICONTROL Paused]** 。
* 停止或刪除因錯誤而暫停的工作流程，
* 停止所有測試所用的工作流程，這些測試不包含活 **[!UICONTROL End]** 動，因此其狀態仍然 **[!UICONTROL Paused]** 。

>[!CAUTION]
>
>如果操作時間長，佔用空間大，則表示需要深入維護（索引重建等）。 如需詳細資訊，請參閱[本小節](../../production/using/recommendations.md)。

**Adobe Campaign流程監控**

視Adobe Campaign安裝設定而定，平台監控可使用兩種工具：

* 例項生產頁面。 For more on this, refer to [Manual monitoring](../../production/using/monitoring-processes.md#manual-monitoring).
* netreport指令碼。 如需詳細資訊，請參閱「透過Adobe Campaign [指令碼自動監控」](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)。

## 細節 {#specifics}

可能需要執行即時診斷以找出問題的原因。 首先檢查進程和平台日誌檔案，然後在重新建立問題時監視資料庫活動。 請特別注意：

* 維護執行計畫，
* 正在執行的SQL查詢、
* 是否同時運行外部進程（清洗、導入、匯總計算等）。

