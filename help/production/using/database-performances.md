---
product: campaign
title: 資料庫效能
description: 資料庫效能
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 8%

---

# 資料庫效能{#database-performances}



大多數效能問題都與資料庫維護相關。 以下是四個主要線索，幫助您找到效能下降的原因：

* 設定
* 安裝和配置Adobe Campaign平台
* 資料庫維護
* 即時診斷

## 設定 {#configuration}

檢查初始的Adobe Campaign平台配置是否仍然有效，如有必要，請根據交付能力或資料庫大小重新評估客戶的需求。 我們還建議運行完整的硬體檢查（CPU、RAM、IO系統）。

>[!NOTE]
>
>您可以參考 [Adobe Campaign硬體調整指南](https://helpx.adobe.com/tw/campaign/kb/hardware-sizing-guide.html) 來獲得見解。

## 平台配置 {#platform-configuration}

配置不當可能會影響平台效能。 建議您檢查中的網路配置、平台可交付性選項以及MTA配置 **serverConf.xml** 的子菜單。

## 資料庫維護 {#database-maintenance}

**資料庫清理任務**

請確保資料庫清理任務已運行。 為此，請查看日誌檔案以查看它們是否包含任何錯誤。 如需詳細資訊，請參閱[本章節](../../production/using/database-cleanup-workflow.md)。

**維護計畫**

確保資料庫維護已正確計畫並執行。 要執行此操作，請與資料庫管理員聯繫以瞭解有關以下內容的詳細資訊：

* 他們的維護計畫
* 以前執行的維護計畫
* 查看指令碼日誌

如需詳細資訊，請參閱[本章節](../../production/using/recommendations.md)。

>[!IMPORTANT]
>
>如果您使用中間採購配置，則定期維護資料庫至關重要。 當分析市場營銷平台上的交貨時，市場營銷實例將資訊發送到中間採購實例。 如果流程減慢，將影響營銷實例。

**管理工作表**

請檢查工作表的數量和大小。 超過一定大小時，資料庫效能會受到影響。 這些表由工作流和交貨建立。 當工作流和交貨處於活動狀態時，它們仍保留在資料庫中。 要限制工作表的大小，可執行以下操作：

* 停止或刪除具有以下狀態的交貨： **[!UICONTROL Failed]**。 **[!UICONTROL In progress]**。 **[!UICONTROL Ready for delivery]**&#x200B;或 **[!UICONTROL Paused]**。
* 停止或刪除因錯誤而暫停的工作流。
* 停止所有用於不包含test的工作流 **[!UICONTROL End]** 活動，因此其狀態仍然 **[!UICONTROL Paused]**。

>[!IMPORTANT]
>
>如果操作耗時較長，並且釋放了大量空間，則意味著需要進行深入的維護（索引重建等）。 如需詳細資訊，請參閱[本章節](../../production/using/recommendations.md)。

**Adobe Campaign過程監控**

根據Adobe Campaign安裝設定，可以使用兩種工具進行平台監控：

* 實例生產頁。 有關此內容的詳細資訊，請參閱 [手動監控](../../production/using/monitoring-processes.md#manual-monitoring)。
* 的 *netreport* 的下界。 有關此內容的詳細資訊，請參閱 [通過Adobe Campaign指令碼自動監視](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)。

## 細節 {#specifics}

可能需要運行即時診斷來確定問題的原因。 首先檢查進程和平台日誌檔案，然後在重新建立問題時監視資料庫活動。 請特別注意：

* 維護執行計畫
* 正在執行的SQL查詢
* 是否同時運行外部進程（清理、導入、聚合計算等）。
