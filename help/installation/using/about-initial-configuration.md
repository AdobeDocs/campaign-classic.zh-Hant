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

# 設定和部署執行個體的重要步驟{#about-initial-configuration}



Adobe Campaign安裝完成後，您需要進行設定，以確保它在您的限制和技術架構下有效運作。 本章將依下列順序詳細說明設定Adobe Campaign執行個體的步驟：

1. 建立執行個體和相關連線，請參閱 [建立執行個體並登入](../../installation/using/creating-an-instance-and-logging-on.md).
1. 建立及設定資料庫，請參閱 [建立和設定資料庫](../../installation/using/creating-and-configuring-the-database.md).
1. 設定Adobe Campaign伺服器，請參閱 [Campaign伺服器設定](../../installation/using/configuring-campaign-server.md).
1. 部署執行個體，請參閱 [部署執行個體](../../installation/using/deploying-an-instance.md).

設定執行個體表示啟用流程（web、mta、wfserver等） 開始於伺服器上，並設定用於傳送電子郵件、追蹤等的模組。 對於每個執行個體，都會在伺服器上啟動Adobe Campaign程式。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#enabling-processes)。

每個執行個體可能需要額外的設定（取決於使用的模組、您的架構和您的需求），以最佳化Adobe Campaign操作。
