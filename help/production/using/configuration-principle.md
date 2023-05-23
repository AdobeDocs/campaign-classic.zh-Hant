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



Adobe Campaign平台基於實例的概念，類似於Apache使用的虛擬主機。 此操作模式允許您通過為伺服器分配多個實例來共用伺服器。 實例之間完全分離，並使用它們自己的資料庫和配置檔案進行操作。

對於給定的伺服器，有兩個元素是所有Adobe Campaign實例所共有的：

* 的 **內部** 密碼：這是一般管理員密碼。 它對特定應用程式伺服器的所有實例都是通用的。

   >[!IMPORTANT]
   >
   >使用 **內部** 標識符，您需要事先定義密碼。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

* 多種技術伺服器配置：這些配置在實例的特定配置中都可能過載。

配置檔案將保存在 **會議** 目錄。 配置分為三個檔案：

* **serverConf.xml**:所有實例的總體配置。
* **配置&#x200B;**`<instance>`**.xml** ( **`<instance>`** 是實例名稱):實例的特定配置。
* **serverConf.xml.diff**:初始配置與當前配置之間的增量。 此檔案由應用程式自動生成，不能手動修改。 它用於在更新生成版本時自動傳播用戶修改。

實例配置的載入方式如下：

* 模組將 **serverConf.xml** 檔案獲取所有實例共用的參數。
* 然後裝載 **配置&#x200B;**`<instance>`**.xml** 的子菜單。 此檔案中找到的值的優先順序高於包含在 **serverConf.xml**。

   這兩個檔案的格式相同。 中的任何值 **serverConf.xml** 對於中的給定實例可能超載 **配置`<instance>`.xml** 的子菜單。

此操作模式為配置提供了極大的靈活性。
