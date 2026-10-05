---
product: campaign
title: 關於初始組態
description: 關於初始組態
feature: Installation, Configuration
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
TQID: 'https://experienceleague.adobe.com/rQT-wcpjGzyYfEV3thGlY0WD7Po-A08yD0pGMr13p7s'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 14%
---
# 設定和部署執行個體的關鍵步驟{#about-initial-configuration}



Adobe Campaign安裝完成後，您需要對其進行配置，以確保它在您的限制和技術架構下有效運作。 本章將依下列順序詳細說明設定Adobe Campaign執行個體的步驟：

1. 建立執行個體和相關連線，請參閱[建立執行個體並登入](../../installation/using/creating-an-instance-and-logging-on.md)。
1. 建立及設定資料庫，請參閱[建立及設定資料庫](../../installation/using/creating-and-configuring-the-database.md)。
1. 設定Adobe Campaign伺服器，請參閱[Campaign伺服器設定](../../installation/using/configuring-campaign-server.md)。
1. 部署執行個體，請參閱[部署執行個體](../../installation/using/deploying-an-instance.md)。

設定執行個體表示啟用流程（Web、mta、wfserver等） 從伺服器啟動，並設定傳送電子郵件、追蹤等模組。對於每個執行個體，都會在伺服器上啟動Adobe Campaign程式。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#enabling-processes)。

每個執行個體可能需要額外的設定（取決於使用的模組、您的架構和您的需求），以最佳化Adobe Campaign的操作。
