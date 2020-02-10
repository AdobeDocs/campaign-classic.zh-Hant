---
title: 配置原則
seo-title: 配置原則
description: 配置原則
seo-description: null
page-status-flag: never-activated
uuid: 6315d526-b820-46ab-96c7-e64e101c6a7d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: d08ff769-da93-4f86-8802-f0fb5b051ece
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# 配置原則{#configuration-principle}

Adobe Campaign平台是以例項的概念為基礎，類似於Apache所使用的虛擬主機。 此操作模式允許您通過為伺服器分配多個實例來共用伺服器。 實例彼此完全分離，並使用它們自己的資料庫和配置檔案操作。

對於指定的伺服器，有兩個元素是所有Adobe Campaign例項的共同元素：

* 內部 **密碼** :這是一般管理員密碼。 它對特定應用程式伺服器的所有執行個體都很常見。

   >[!CAUTION]
   >
   >若要使用內部識 **別碼登入** ，您必須事先定義密碼。 如需詳細資訊，請參閱[本小節](../../installation/using/campaign-server-configuration.md#internal-identifier)。

* 多種技術性伺服器組態：這些配置都可以在實例的特定配置中過載。

配置檔案將保存在安 **裝目錄** 的conf目錄中。 此配置分為三個檔案：

* **serverConf.xml**:所有例項的整體設定。
* **config-**`<instance>`**.xml** (其中 **`<instance>`** 是實例名稱):實例的特定配置。
* **serverConf.xml.diff**:在初始配置和當前配置之間的delta。 此檔案由應用程式自動產生，不得手動修改。 它用於在更新建置版本時自動傳播用戶修改。

實例配置的載入方式如下：

* 模組載入 **serverConf.xml檔案** ，以獲取所有實例共用的參數。
* 然後載入 **config-**`<instance>`**.xml檔案** 。 在此檔案中找到的值比 **serverConf.xml中包含的值具有優先順序**。

   這兩個檔案的格式相同。 serverConf.xml中 **的任何值** ，都可對 **config-`<instance>`.xml檔案中的指定例項過載** 。

此操作模式為配置提供了極大的靈活性。
