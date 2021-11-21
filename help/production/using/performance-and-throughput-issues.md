---
product: campaign
title: 效能和輸送量的相關問題
description: 效能和輸送量的相關問題
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 4%

---

# 效能和輸送量的相關問題{#performance-and-throughput-issues}

![](../../assets/v7-only.svg)

首先，您應檢查是否已安裝最新的組建。 這可確保您擁有最新功能和錯誤修正。

請參閱 [發行說明](../../rn/using/latest-release.md) 以取得每個版本內容的詳細資訊。

## 硬體和基礎架構 {#hardware-and-infrastructure}

有關內部部署Campaign Classic硬體需求的一般准則，請詳閱以下內容 [頁面](https://helpx.adobe.com/tw/campaign/kb/hardware-sizing-guide.html).

諮詢團隊可為托管客戶提供工具，讓您輕鬆檢視資料庫中各種類型表格使用的空間，以及SFTP站台上使用的空間。 此外，它還提供工具，讓您清除不必要的資料。 連絡人 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 如果您需要實作此工具。 以下是使用此工具要檢查的一些重要事項：

* 如果索引大小大於表大小，則需要真空。
* 檢查最大Bloat的表。 如果這些表格經常使用，則需要清空。
* 資料庫封鎖可導致電子郵件停止傳送。

Adobe Campaign也提供 [工具](../../production/using/monitoring-processes.md#manual-monitoring) 檢查CPU和RAM的使用情況。 使用此工具並查看特定指標，例如： **記憶體**, **交換記憶體**, **磁碟**, **活動進程**. 如果值太高，您可以嘗試減少工作流程數量或排程在不同時間開始的工作流程。

## 資料庫檢查 {#database-performances}

大多數情況下，效能問題都與資料庫維護相關。 以下是要檢查的主要項目：

* 配置：建議您檢查初始Adobe Campaign平台配置，並執行完整的硬體檢查。
* 安裝及設定Adobe Campaign平台：檢查網路配置和平台傳遞能力選項。
* 資料庫維護：確保資料庫清理任務正常運行，並確保正確計畫和執行資料庫維護。 檢查工作表的數量和大小。
* 即時診斷：檢查進程和平台日誌檔案，然後在重新建立問題時監視資料庫活動。

>[!NOTE]
>
>如需詳細資訊，請參閱本區段： [資料庫效能](../../production/using/database-performances.md).

## 應用程式配置 {#application-configuration}

以下是與應用程式設定最佳實務相關的文章清單：

* MTA和MTAChild進程和記憶體：the **mta** 模組將報文分發到 **mtachild** 子模組。 每個 **mtachild** 在向統計伺服器請求授權併發送之前準備消息。 請參閱 [頁面](../../installation/using/email-deliverability.md) 以取得更多資訊。
* TLS配置：不建議全域啟用TLS，因為這可能會降低總處理能力。 而是應視需要調整由傳遞團隊管理的每網域TLS設定。 請參閱 [頁面](../../installation/using/email-deliverability.md#mx-configuration) 以取得更多資訊。
* DKIM:為確保DKIM的安全級別，建議的加密大小為1024b。 大多數訪問提供商將不認為較低的DKIM密鑰有效。 請參見[此頁面](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

## 傳遞能力問題 {#deliverability-issues}

以下是與傳遞能力相關的最佳實務和文章清單：

* IP信譽：如果IP信譽不夠好，將會影響效能。 此 **傳遞能力監控** 模組提供多種工具，可追蹤您平台的傳遞效能。 請參閱 [頁面](../../delivery/using/monitoring-deliverability.md).
* IP熱身：IP熱身由傳遞團隊執行。 這需要在數週內，透過新IP逐漸增加電子郵件數量。
* IP相關性設定：不正確的IP相關性設定可以完全停止電子郵件（設定中的運算子/相關性名稱不正確）或降低吞吐量（相關性中的IP數量很少）。 請參閱 [頁面](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* 電子郵件大小：電子郵件大小在吞吐量中扮演著重要角色。 建議的電子郵件大小上限為60 KB。 請參閱 [頁面](https://helpx.adobe.com/legal/product-descriptions/campaign.html). 在 [傳送總處理能力](../../reporting/using/global-reports.md#delivery-throughput) 報告，檢查按小時傳輸的位元組數。
* 大量無效收件者：當有大量無效收件者時，可能會影響輸送量。 MTA會持續重新嘗試傳送電子郵件給無效的收件者。 請確定您的資料庫已妥善維護。
* 個人化金額：如果傳送保留在「進行中個人化」中，請檢查個人化區塊中使用的JavaScript。

>[!NOTE]
>
>另請參閱 [傳遞能力](../../delivery/using/about-deliverability.md) 區段。 如需有關傳遞能力的更深入探討，請參閱 [Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant).
