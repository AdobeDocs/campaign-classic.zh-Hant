---
product: campaign
title: 效能和輸送量的相關問題
description: 效能和輸送量的相關問題
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 4%

---

# 效能和輸送量的相關問題{#performance-and-throughput-issues}



首先，您應檢查是否安裝了最新的內部版本。 這可確保您擁有最新的功能和錯誤修復程式。

請參閱 [發行說明](../../rn/using/latest-release.md) 的子菜單。

## 硬體和基礎架構 {#hardware-and-infrastructure}

本文詳細介紹了現場Campaign Classic硬體要求的一般准則 [頁](https://helpx.adobe.com/tw/campaign/kb/hardware-sizing-guide.html)。

咨詢團隊可以為托管客戶提供一個工具，讓您能夠輕鬆查看資料庫中各種類型的表使用了多少空間以及SFTP站點上使用了多少空間。 此外，它還提供了一些工具，讓您能夠清除不必要的資料。 聯繫人 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 如果您需要該工具，請執行。 以下是使用此工具檢查的一些重要內容：

* 如果索引大小大於表大小，則需要真空。
* 檢查具有最大Bloat的表。 如果這些桌子經常使用，就需要抽空。
* 阻止資料庫會導致電子郵件停止發送。

Adobe Campaign還提供 [工具](../../production/using/monitoring-processes.md#manual-monitoring) 檢查CPU和RAM的使用情況。 使用此工具並查看特定指標，如： **記憶體**。 **交換記憶體**。 **磁碟**。 **活動進程**。 如果值太高，可以嘗試減少工作流數或安排工作流在不同時間啟動。

## 資料庫檢查 {#database-performances}

大多數時候，效能問題都與資料庫維護相關。 以下是要檢查的主要項目：

* 配置：我們建議檢查初始的Adobe Campaign平台配置並運行完整的硬體檢查。
* 安裝和配置Adobe Campaign平台：檢查網路配置和平台可交付性選項。
* 資料庫維護：確保資料庫清理任務已運行，並且資料庫維護已正確計畫並執行。 檢查工作表的數量和大小。
* 即時診斷：檢查進程和平台日誌檔案，然後在重新建立問題時監視資料庫活動。

>[!NOTE]
>
>有關詳細資訊，請參閱本節： [資料庫效能](../../production/using/database-performances.md)。

## 應用程式配置 {#application-configuration}

以下是與應用程式配置最佳實踐相關的文章清單：

* MTA和MTAChild進程和記憶體：這樣 **門** 模組將消息分發到 **母體** 子模組。 每個 **母體** 在從統計伺服器請求授權併發送消息之前準備消息。 請參閱此 [頁](../../installation/using/email-deliverability.md) 的子菜單。
* TLS配置：不建議全局啟用TLS，因為它可以降低吞吐量。 相反，應根據需要調整由可交付性團隊管理的每域TLS設定。 請參閱此 [頁](../../installation/using/email-deliverability.md#mx-configuration) 的子菜單。
* DKIM:為確保DKIM的安全級別，建議採用最佳加密大小。 大多數訪問提供商將不認為低DKIM密鑰有效。 請參見[此頁面](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

## 可交付性問題 {#deliverability-issues}

以下是與可交付性相關的最佳實踐和文章清單：

* IP信譽：如果IP信譽不夠好，將對效能產生影響。 的 **可交付性監控** 模組提供各種工具來跟蹤平台的可交付效能。 請參閱此 [頁](../../delivery/using/monitoring-deliverability.md)。
* IP預熱：IP預熱由交付性團隊執行。 這包括在幾週內通過新IP逐漸增加電子郵件數量。
* IP關聯設定：不正確的IP關聯設定可以完全停止電子郵件（配置中的操作員/關聯名稱不正確）或降低吞吐量（關聯中的IP數量較少）。 請參閱此 [頁](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)。
* 電子郵件大小：電子郵件大小在吞吐量中起著重要作用。 建議的最大電子郵件大小為60 KB。 請參閱此 [頁](https://helpx.adobe.com/legal/product-descriptions/campaign.html)。 在 [交付吞吐量](../../reporting/using/global-reports.md#delivery-throughput) 報告，檢查按小時傳輸的位元組數。
* 大量無效收件人：當有大量無效收件人時，它會影響吞吐量。 MTA將繼續重試向無效收件人發送電子郵件。 請確保資料庫維護良好。
* 個性化數量：如果傳遞仍處於「正在個性化」中，請檢查個性化塊中使用的JavaScript。

>[!NOTE]
>
>另請參閱 [可交付性](../../delivery/using/about-deliverability.md) 的子菜單。 有關交付能力的更深入瞭解，請參閱 [Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant)。
