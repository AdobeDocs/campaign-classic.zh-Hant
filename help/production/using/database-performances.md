---
product: campaign
title: 資料庫效能
description: 資料庫效能
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 8%

---

# 資料庫效能{#database-performances}

![](../../assets/v7-only.svg)

大多數效能問題都與資料庫維護相關。 以下是四個主要線索，可幫助您找出效能下降的原因：

* 設定
* 安裝及設定Adobe Campaign平台
* 資料庫維護
* 即時診斷

## 設定 {#configuration}

檢查初始Adobe Campaign平台設定是否仍有效，並視需要重新評估客戶的傳遞能力或資料庫大小需求。 我們還建議運行完整的硬體檢查（CPU、RAM、IO系統）。

>[!NOTE]
>
>如需深入分析，請參閱[Adobe Campaign硬體調整指南](https://helpx.adobe.com/tw/campaign/kb/hardware-sizing-guide.html)。

## 平台配置 {#platform-configuration}

不適當的配置可能會影響平台效能。 建議您在&#x200B;**serverConf.xml**&#x200B;檔案中檢查網路配置、平台傳遞選項以及MTA配置。

## 資料庫維護 {#database-maintenance}

**資料庫清理任務**

請確保資料庫清除任務已運行。 要執行此操作，請檢視記錄檔，查看其是否包含任何錯誤。 如需詳細資訊，請參閱[本章節](../../production/using/database-cleanup-workflow.md)。

**維護計畫**

確保正確排程並執行資料庫維護。 要執行此操作，請與資料庫管理員聯繫，以了解更多資訊：

* 他們的維護時間表
* 先前執行的維護計畫
* 查看指令碼日誌

如需詳細資訊，請參閱[本章節](../../production/using/recommendations.md)。

>[!IMPORTANT]
>
>如果您使用中間來源配置，則必須定期維護資料庫。 在行銷平台上分析傳送時，行銷例項會傳送資訊至中間來源例項。 如果程式變慢，行銷例項將會受到影響。

**管理工作表**

請檢查工作表的數量和大小。 當資料庫超過某個大小時，資料庫效能會受到影響。 這些表格是由工作流程和傳送所建立。 當工作流程和傳送作用中時，它們會保留在資料庫中。 要限制工作表的大小，可以執行以下操作：

* 停止或刪除具有下列狀態的傳送：**[!UICONTROL Failed]**、**[!UICONTROL In progress]**、**[!UICONTROL Ready for delivery]**&#x200B;或&#x200B;**[!UICONTROL Paused]**。
* 停止或刪除因錯誤而暫停的工作流程。
* 停止所有用於測試的工作流程，這些測試不含&#x200B;**[!UICONTROL End]**&#x200B;活動，因此其狀態仍為&#x200B;**[!UICONTROL Paused]**。

>[!IMPORTANT]
>
>如果操作耗時較長，釋放了大量空間，這意味著需要進行深入的維護（索引重建等）。 如需詳細資訊，請參閱[本章節](../../production/using/recommendations.md)。

**Adobe Campaign程式監控**

根據Adobe Campaign安裝設定，可使用兩種工具進行平台監控：

* 執行個體生產頁面。 有關詳細資訊，請參閱[手動監視](../../production/using/monitoring-processes.md#manual-monitoring)。
* *netreport*&#x200B;指令碼。 如需詳細資訊，請參閱[透過Adobe Campaign指令碼自動監控](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)。

## 細節 {#specifics}

可能需要執行即時診斷，以找出問題的原因。 首先檢查進程和平台日誌檔案，然後在重新建立問題時監視資料庫活動。 請特別注意下列事項：

* 維護執行計畫
* 正在執行的SQL查詢
* 是否同時運行外部進程（清除、導入、匯總計算等）。
