---
product: campaign
title: 關於初始配置
description: 關於初始配置
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 8%

---

# 配置和部署實例的關鍵步驟{#about-initial-configuration}



Adobe Campaign安裝完成後，您需要對其進行配置，以確保其在滿足您的限制和技術體系結構的情況下高效運行。 配置Adobe Campaign實例的步驟按以下順序在本章中詳細介紹：

1. 建立實例和相關連接，請參閱 [建立實例並登錄](../../installation/using/creating-an-instance-and-logging-on.md)。
1. 建立和配置資料庫，請參閱 [建立和配置資料庫](../../installation/using/creating-and-configuring-the-database.md)。
1. 配置Adobe Campaign伺服器，請參閱 [市場活動伺服器配置](../../installation/using/configuring-campaign-server.md)。
1. 部署實例，請參閱 [部署實例](../../installation/using/deploying-an-instance.md)。

配置實例意味著啟用進程（web、mta、wfserver等） 要在伺服器上啟動，並配置用於發送電子郵件、跟蹤等的模組。 對於每個實例，在伺服器上激活Adobe Campaign進程。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#enabling-processes)。

每個實例（取決於使用的模組、您的體系結構和您的需要）可能需要其他配置來優化Adobe Campaign操作。
