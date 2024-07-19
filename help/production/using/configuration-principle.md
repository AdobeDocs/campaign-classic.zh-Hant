---
product: campaign
title: 設定原則
description: 設定原則
feature: Monitoring, Configuration
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 5%

---

# 設定原則{#configuration-principle}



Adobe Campaign平台以例項概念為基礎，類似於Apache使用的虛擬主機。 此作業模式可讓您透過指派多個執行個體來共用伺服器。 執行個體彼此完全獨立，並使用自己的資料庫和組態檔進行操作。

對於指定的伺服器，有兩個元素是所有Adobe Campaign執行個體共同的：

* **內部**&#x200B;密碼：這是一般管理員密碼。 這是特定應用程式伺服器的所有執行個體所共有的。

  >[!IMPORTANT]
  >
  >若要使用&#x200B;**內部**&#x200B;識別碼登入，您必須預先定義密碼。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

* 多個技術伺服器設定：在執行個體的特定設定中，這些設定都可以多載。

組態檔儲存在安裝目錄的&#x200B;**conf**&#x200B;目錄中。 此設定分為三個檔案：

* **serverConf.xml**：所有執行個體的整體組態。
* **config-**`<instance>`**.xml** （其中&#x200B;**`<instance>`**&#x200B;為執行個體名稱）：執行個體的特定設定。
* **serverConf.xml.diff**：初始設定與目前設定之間的差異。 此檔案由應用程式自動產生，且不得手動修改。 它用於在更新組建版本時自動傳播使用者修改。

執行個體設定載入如下：

* 模組載入&#x200B;**serverConf.xml**&#x200B;檔案，以取得所有執行個體共用的引數。
* 然後載入&#x200B;**config-**`<instance>`**.xml**&#x200B;檔案。 此檔案中找到的值優先順序高於&#x200B;**serverConf.xml**&#x200B;中包含的值。

  這兩個檔案的格式相同。 可以為&#x200B;**config-`<instance>`.xml**&#x200B;檔案中的指定執行個體載入&#x200B;**serverConf.xml**&#x200B;中的任何值。

此作業模式提供組態絕佳的彈性。
