---
product: campaign
title: 設定原則
description: 設定原則
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---

# 設定原則{#configuration-principle}



Adobe Campaign平台以例項概念為基礎，類似於Apache使用的虛擬主機。 此作業模式可讓您透過指派多個執行個體來共用伺服器。 執行個體彼此完全分開，並使用自己的資料庫和組態檔進行操作。

對於指定的伺服器，有兩個元素是所有Adobe Campaign執行個體共同的：

* 此 **內部** 密碼：這是一般管理員密碼。 它對於特定應用程式伺服器的所有執行個體都是通用的。

   >[!IMPORTANT]
   >
   >若要使用 **內部** 識別碼，您必須預先定義密碼。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

* 多個技術伺服器設定：在執行個體的特定設定中，這些設定都可多載。

組態檔案會儲存在 **conf** 安裝目錄的目錄。 此設定分為三個檔案：

* **serverConf.xml**：所有執行個體的整體設定。
* **config-**`<instance>`**.xml** (其中 **`<instance>`** 執行個體名稱)：執行個體的特定設定。
* **serverConf.xml.diff**：初始設定和目前設定之間的差值。 此檔案由應用程式自動產生，且不得手動修改。 它用於在更新組建版本時自動傳播使用者修改。

執行個體設定載入如下：

* 模組載入 **serverConf.xml** 檔案來取得所有例證共用的引數。
* 然後載入 **config-**`<instance>`**.xml** 檔案。 此檔案中的值優先順序高於中包含的值 **serverConf.xml**.

   這兩個檔案的格式相同。 中的任何值 **serverConf.xml** 可以在的指定執行個體中多載 **config-`<instance>`.xml** 檔案。

此作業模式為設定提供絕佳的彈性。
