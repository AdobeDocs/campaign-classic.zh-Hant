---
title: 效能和吞吐量問題
seo-title: 效能和吞吐量問題
description: 效能和吞吐量問題
seo-description: null
page-status-flag: never-activated
uuid: 28c35453-9a15-44a3-9961-f4c604c209c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: ec66e3e3-b09a-44a4-914d-e3b38c7643f8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d80e3d47b06b7a03974d9cfdd465861b3c5bcf81
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---


# 效能和吞吐量問題{#performance-and-throughput-issues}

>[!NOTE]
>
>首先，您應檢查您是否已安裝最新的組建版本。 這可確保您擁有最新的功能和錯誤修正。 如需每個版 [本內容的詳細資訊](https://docs.campaign.adobe.com/doc/AC/en/RN.html) ，請參閱版本注意事項。

## 硬體和基礎架構 {#hardware-and-infrastructure}

本文詳細說明內部部署Campaign Classic硬體需求的一般指 [引](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)。

諮詢團隊可為代管客戶提供工具，讓您輕鬆檢視資料庫中各種表格使用了多少空間，以及SFTP網站上使用多少空間。 此外，它還提供工具，讓您能夠清除不必要的資料。 如果您需要實作此工具，請聯絡諮詢或支援團隊。 以下是使用此工具檢查的幾項重要事項：

* 如果索引大小大於表格大小，則需要真空。
* 檢查具有最大部落格的表。 如果這些表格經常使用，則需要抽空。
* 封鎖資料庫可能會導致電子郵件停止傳送。

Adobe Campaign也提供檢查 [CPU和](../../production/using/monitoring-processes.md#manual-monitoring) RAM使用狀況的工具。 使用此工具並查看特定指標，例如： **記憶體**、交 **換記憶體**、磁碟 **、活**&#x200B;動進程 ****。 如果值過高，您可以嘗試減少工作流程數量，或排程工作流程以在不同時間啟動。

## 資料庫效能 {#database-performances}

大多數時候，效能問題都與資料庫維護相關。 以下是要檢查的主要項目：

* 配置： 我們建議檢查初始Adobe Campaign平台設定，並執行完整硬體檢查。
* Adobe Campaign平台的安裝與設定： 檢查網路組態和平台傳遞能力選項。
* 資料庫維護： 確保資料庫清理任務可以運行，並確保資料庫維護已正確排程並執行。 檢查工作表的數量和大小。
* 即時診斷： 檢查進程和平台日誌檔案，然後在重新建立問題時監視資料庫活動。

>[!NOTE]
>
>For more information, refer to this section: [Database performances](../../production/using/database-performances.md).

## 應用程式設定 {#application-configuration}

以下是與應用程式設定最佳實務相關的文章清單：

* MTA和MTAChild進程和記憶體： mta模 **塊將消息分發到其** 匹配子模組 **** 。 每個 **模板** 在向統計伺服器請求授權併發送消息之前準備消息。 Refer to this [page](../../installation/using/email-deliverability.md) for more information.
* TLS配置： 不建議全局啟用TLS，因為它可以降低吞吐量。 相反，應視需要調整由可傳遞性團隊管理的每網域TLS設定。 Refer to this [page](../../installation/using/email-deliverability.md#mx-configuration) for more information.
* DKIM: 為確保DKIM的安全級別，建議的加密大小為1024b。 大部分的存取提供者不會將低DKIM金鑰視為有效。 請參閱本 [頁](../../delivery/using/technical-recommendations.md#dkim) 和此 [技術](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html)。

## 傳遞能力問題 {#deliverability-issues}

以下是與傳遞能力相關的最佳實務和文章清單：

* IP信譽： 如果IP信譽不夠好，將對效能產生影響。 Deliverability **Monitoring** （可傳送性監控）模組提供多種工具，可追蹤平台的可傳送效能。 Refer to this [page](../../delivery/using/monitoring-deliverability.md).
* IP預熱： ip預熱由交付能力團隊執行。 這包括在數週內，透過新IP逐步增加電子郵件數量。
* IP相似性設定： 不正確的IP相似性設定可以完全停止電子郵件（設定中的運算元／相似性名稱不正確），或降低總處理能力（相似性中的IP數量較少）。 Refer to this [page](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* 電子郵件大小： 電子郵件大小在吞吐量中扮演了重要的角色。 建議的電子郵件大小上限為60 KB。 Refer to this [page](https://helpx.adobe.com/legal/product-descriptions/campaign.html). 在「傳 [送總處理量](../../reporting/using/delivery-reports.md#delivery-throughput) 」報表中，檢查按小時傳送的位元組數。
* 大量無效收件者： 當有大量無效收件者時，可能會影響總處理能力。 MTA會持續重試傳送電子郵件給無效的收件者。 請確定您的資料庫已妥善維護。
* 個人化金額： 如果傳送仍在「個人化進行中」，請檢查個人化區塊中使用的JavaScript。

>[!NOTE]
>
>請記得參考「傳遞性」快 [速入門指南](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 。

