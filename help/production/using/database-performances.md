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



大多數效能問題都與資料庫維護有關。 以下四個主要線索可協助您找出效能緩慢的原因：

* 設定
* Adobe Campaign平台的安裝和設定
* 資料庫維護
* 即時診斷

## 設定 {#configuration}

檢查初始Adobe Campaign平台設定是否仍然有效，並視需要重新評估客戶的可傳遞性或資料庫大小需求。 我們也建議執行完整的硬體檢查（CPU、RAM、IO系統）。

>[!NOTE]
>
>您可參閱 [Adobe Campaign硬體大小調整指南](https://helpx.adobe.com/tw/campaign/kb/hardware-sizing-guide.html) 以取得深入分析。

## 平台設定 {#platform-configuration}

不當的設定可能會影響平台效能。 建議您檢視「 」中的網路設定、平台傳遞能力選項以及MTA設定 **serverConf.xml** 檔案。

## 資料庫維護 {#database-maintenance}

**資料庫清理工作**

請確定資料庫清理工作可正常運作。 要執行此操作，請檢視記錄檔以檢視它們是否包含任何錯誤。 如需詳細資訊，請參閱[本章節](../../production/using/database-cleanup-workflow.md)。

**維護計畫**

請確定資料庫維護已正確排程並執行。 若要這麼做，請聯絡資料庫管理員以進一步瞭解：

* 他們的維護排程
* 先前執行的維護計畫
* 檢視指令碼記錄

如需詳細資訊，請參閱[本章節](../../production/using/recommendations.md)。

>[!IMPORTANT]
>
>如果您使用中間來源組態，則必須定期維護資料庫。 在行銷平台上分析傳遞時，行銷執行個體會傳送資訊給中間來源執行個體。 如果流程速度變慢，行銷執行個體將受到影響。

**管理工作表**

請檢查工作表的數目和大小。 當它們超過特定大小時，資料庫效能會受到影響。 這些表格是由工作流程和傳遞建立的。 當工作流程和傳遞作用中時，它們會留在資料庫中。 若要限制工作表的大小，您可以執行下列操作：

* 停止或刪除狀態為下列的傳遞： **[!UICONTROL Failed]**， **[!UICONTROL In progress]**， **[!UICONTROL Ready for delivery]**，或 **[!UICONTROL Paused]**.
* 停止或刪除因錯誤而暫停的工作流程。
* 停止所有用於測試的工作流程，這些工作流程不包含 **[!UICONTROL End]** 活動及其狀態維持不變 **[!UICONTROL Paused]**.

>[!IMPORTANT]
>
>如果操作需要很長時間並釋放了大量空間，這表示需要進行深入維護（重建索引等）。 如需詳細資訊，請參閱[本章節](../../production/using/recommendations.md)。

**Adobe Campaign程式監控**

根據Adobe Campaign安裝設定，可使用兩種工具進行平台監視：

* 執行個體生產頁面。 有關詳細資訊，請參閱 [手動監視](../../production/using/monitoring-processes.md#manual-monitoring).
* 此 *netreport* 指令碼。 有關詳細資訊，請參閱 [透過Adobe Campaign指令碼自動監視](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## 細節 {#specifics}

您可能需要執行即時診斷，以找出問題的原因。 首先檢查流程和平台記錄檔，然後在重新建立問題的同時監控資料庫活動。 請特別留意下列事項：

* 維護執行計畫
* 正在執行的SQL查詢
* 外部程式是否同時執行（清除、匯入、彙總計算等）。
