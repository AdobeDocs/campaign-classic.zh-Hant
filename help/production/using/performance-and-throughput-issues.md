---
solution: Campaign Classic
product: campaign
title: 效能和輸送量的相關問題
description: 效能和輸送量的相關問題
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: d1b38acc5209a5c96ab7a35fe9640159141b110f
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 2%

---


# 效能和輸送量的相關問題{#performance-and-throughput-issues}

首先，您應檢查您是否已安裝最新的組建版本。 這可確保您擁有最新的功能和錯誤修正。

有關每個版本內容的詳細資訊，請參閱[發行說明](../../rn/using/latest-release.md)。

## 硬體和基礎架構{#hardware-and-infrastructure}

本[頁](https://helpx.adobe.com/tw/campaign/kb/hardware-sizing-guide.html)中詳細說明了現場Campaign Classic硬體要求的一般指南。

諮詢團隊可為代管客戶提供工具，讓您輕鬆檢視資料庫中各種表格使用了多少空間，以及SFTP網站上使用多少空間。 此外，它還提供工具，讓您能夠清除不必要的資料。 如果您需要實作此工具，請聯絡[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 以下是使用此工具檢查的幾項重要事項：

* 如果索引大小大於表格大小，則需要真空。
* 檢查具有最大部落格的表。 如果這些表格經常使用，則需要抽空。
* 封鎖資料庫可能會導致電子郵件停止傳送。

Adobe Campaign也提供[工具](../../production/using/monitoring-processes.md#manual-monitoring)來檢查CPU和RAM的使用情況。 使用此工具並查看特定指標，例如：**記憶體**、**交換記憶體**、**磁碟**、**活動進程**。 如果值過高，您可以嘗試減少工作流程數量，或排程工作流程以在不同時間啟動。

## 資料庫檢查{#database-performances}

大多數時候，效能問題都與資料庫維護相關。 以下是要檢查的主要項目：

* 配置：我們建議檢查初始的Adobe Campaign平台配置並運行完整的硬體檢查。
* Adobe Campaign平台的安裝與配置：檢查網路組態和平台傳遞能力選項。
* 資料庫維護：確保資料庫清理任務可以運行，並確保資料庫維護已正確排程並執行。 檢查工作表的數量和大小。
* 即時診斷：檢查進程和平台日誌檔案，然後在重新建立問題時監視資料庫活動。

>[!NOTE]
>
>如需詳細資訊，請參閱本節：[資料庫效能](../../production/using/database-performances.md)。

## 應用程式配置{#application-configuration}

以下是與應用程式設定最佳實務相關的文章清單：

* MTA和MTAChild進程和記憶體：**mta**&#x200B;模組將消息分發到其&#x200B;**mtachild**&#x200B;子模組。 每個&#x200B;**mtachild**&#x200B;在向統計伺服器請求授權併發送消息之前準備消息。 如需詳細資訊，請參閱此[頁面](../../installation/using/email-deliverability.md)。
* TLS配置：不建議全局啟用TLS，因為它可以降低吞吐量。 相反，應視需要調整由可傳遞性團隊管理的每網域TLS設定。 如需詳細資訊，請參閱此[頁面](../../installation/using/email-deliverability.md#mx-configuration)。
* DKIM:為確保DKIM的安全級別，建議使用1024b作為最佳做法。 大部分的存取提供者不會將低DKIM金鑰視為有效。 請參見[此頁面](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

## 傳遞能力問題{#deliverability-issues}

以下是與傳遞能力相關的最佳實務和文章清單：

* IP信譽：如果IP信譽不夠好，將對效能產生影響。 **傳送性監控**&#x200B;模組提供多種工具，可追蹤平台的傳送效能。 請參閱此[頁](../../delivery/using/monitoring-deliverability.md)。
* IP預熱：ip預熱由交付能力團隊執行。 這包括在數週內，透過新IP逐步增加電子郵件數量。
* IP相似性設定：不正確的IP相似性設定可以完全停止電子郵件（設定中的運算元／相似性名稱不正確），或降低總處理能力（相似性中的IP數量較少）。 請參閱此[頁](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)。
* 電子郵件大小：電子郵件大小在吞吐量中扮演了重要的角色。 建議的電子郵件大小上限為60 KB。 請參閱此[頁](https://helpx.adobe.com/legal/product-descriptions/campaign.html)。 在[傳送吞吐量](../../reporting/using/global-reports.md#delivery-throughput)報告中，檢查按小時傳輸的位元組數。
* 大量無效收件者：當有大量無效收件者時，可能會影響總處理能力。 MTA會持續重試傳送電子郵件給無效的收件者。 請確定您的資料庫已妥善維護。
* 個人化金額：如果傳送仍在「個人化進行中」，請檢查個人化區塊中使用的JavaScript。

>[!NOTE]
>
>另請參閱[Deliverability](../../delivery/using/about-deliverability.md)一節。 有關交付能力的深入探討，請參閱[Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html)。
