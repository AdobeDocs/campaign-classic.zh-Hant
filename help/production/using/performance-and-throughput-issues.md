---
product: campaign
title: 效能和輸送量的相關問題
description: 效能和輸送量的相關問題
feature: Monitoring
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 2%

---

# 效能和輸送量的相關問題{#performance-and-throughput-issues}



首先，您應該檢查是否已安裝最新組建版本。 這可確保您擁有最新功能和錯誤修正。

請參閱 [發行說明](../../rn/using/latest-release.md) 以取得每個版本內容的詳細資訊。

## 硬體與基礎架構 {#hardware-and-infrastructure}

有關內部部署Campaign Classic硬體需求的一般准則，請參閱本節 [頁面](https://helpx.adobe.com/tw/campaign/kb/hardware-sizing-guide.html).

諮詢團隊可為託管客戶提供工具，讓您輕鬆檢視資料庫中各種表格型別的空間使用量，以及SFTP網站上的空間。 此外，還提供工具，讓您清除不必要的資料。 連絡人 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 若您需要實作此工具。 以下是使用此工具時需檢查的一些重要事項：

* 如果索引大小大於表格大小，則需要真空。
* 檢查具有最大膨脹量的表格。 如果經常使用這些表格，則需要為這些表格吸塵。
* 封鎖資料庫可能導致電子郵件停止傳送。

Adobe Campaign也提供 [工具](../../production/using/monitoring-processes.md#manual-monitoring) 以檢查CPU和RAM使用狀況。 使用此工具並檢視特定指標，例如： **記憶體**， **交換記憶體**， **磁碟**， **作用中的處理序**. 如果值太高，您可以嘗試減少工作流程的數量或排程工作流程以在不同時間開始。

## 資料庫檢查 {#database-performances}

在大多數情況下，效能問題都與資料庫維護有關。 以下是需要檢查的主要專案：

* 設定：建議您檢查初始Adobe Campaign平台設定，並執行完整的硬體檢查。
* Adobe Campaign平台的安裝和設定：檢查網路設定和平台傳遞能力選項。
* 資料庫維護：確定資料庫清理工作可正常運作，以及資料庫維護已正確排程並執行。 檢查工作表的數目和大小。
* 即時診斷：檢查流程和平台記錄檔，然後在重新建立問題的同時監控資料庫活動。

>[!NOTE]
>
>如需詳細資訊，請參閱本區段： [資料庫效能](../../production/using/database-performances.md).

## 應用程式設定 {#application-configuration}

以下是應用程式設定最佳實務的相關文章清單：

* MTA和MTAChild處理程式和記憶體： **mta** 模組將訊息分送至其 **mtachild** 子模組。 每個 **mtachild** 向統計伺服器請求授權並傳送訊息之前，請先準備訊息。 請參閱此 [頁面](../../installation/using/email-deliverability.md) 以取得詳細資訊。
* TLS組態：不建議全域啟用TLS，因為這樣可能會減少輸送量。 相反，由傳遞團隊管理的每個網域TLS設定應根據需求進行調整。 請參閱此 [頁面](../../installation/using/email-deliverability.md#mx-configuration) 以取得詳細資訊。
* DKIM：為了確保DKIM的安全性等級，1024b是建議的最佳實務加密大小。 大多數存取提供者不會將下層DKIM金鑰視為有效。 請參見[此頁面](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

## 傳遞能力問題 {#deliverability-issues}

以下是有關傳遞能力的最佳實務和文章清單：

* IP信譽：如果IP信譽不夠好，將會對效能造成影響。 此 **傳遞能力監視** 模組提供多種工具，用於追蹤平台的傳遞能力效能。 請參閱此 [頁面](../../delivery/using/monitoring-deliverability.md).
* IP熱身： IP熱身是由傳遞團隊執行。 這涉及在幾週內透過新IP逐漸增加電子郵件數量。
* IP相關性設定：不正確的IP相關性設定可能會完全停止電子郵件（設定中的運運算元/相關性名稱不正確）或減少輸送量（相關性中的少量IP）。 請參閱此 [頁面](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* 電子郵件大小：電子郵件大小在輸送量中起著重要作用。 建議的最大電子郵件大小為60 KB。 請參閱此 [頁面](https://helpx.adobe.com/legal/product-descriptions/campaign.html). 在 [傳遞總處理能力](../../reporting/using/global-reports.md#delivery-throughput) 報表，檢查依小時傳輸的位元組數。
* 大量無效收件者：當存在大量無效收件者時，可能會影響輸送量。 MTA不斷重試傳送電子郵件給無效的收件者。 請確定您的資料庫已妥善維護。
* 個人化的數量：如果傳送持續在「正在進行個人化」中，請檢查個人化區塊中使用的JavaScript。

>[!NOTE]
>
>另請參閱 [傳遞能力](../../delivery/using/about-deliverability.md) 區段。 如需傳送能力的更深入探討，請參閱 [Adobe傳遞性最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant).
