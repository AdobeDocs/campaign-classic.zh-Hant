---
solution: Campaign Classic
product: campaign
title: 設定原則
description: 設定原則
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---

# 設定原則{#configuration-principle}

Adobe Campaign平台基於實例的概念，類似於Apache使用的虛擬主機。 此操作模式允許您通過為伺服器分配多個實例來共用伺服器。 實例彼此完全分離，並使用它們自己的資料庫和配置檔案操作。

對於給定伺服器，有兩個元素是所有Adobe Campaign實例的共同元素：

* **internal**&#x200B;密碼：這是一般管理員密碼。 它對特定應用程式伺服器的所有執行個體都很常見。

   >[!IMPORTANT]
   >
   >若要使用&#x200B;**Internal**&#x200B;識別碼登入，您必須事先定義密碼。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

* 多種技術性伺服器組態：這些配置都可以在實例的特定配置中過載。

配置檔案保存在安裝目錄的&#x200B;**conf**&#x200B;目錄中。 此配置分為三個檔案：

* **serverConf.xml**:所有例項的整體設定。
* **config-**`<instance>`**.xml** (其中 **`<instance>`** 是實例名):實例的特定配置。
* **serverConf.xml.diff**:在初始配置和當前配置之間的delta。此檔案由應用程式自動產生，不得手動修改。 它用於在更新建置版本時自動傳播用戶修改。

實例配置的載入方式如下：

* 模組載入&#x200B;**serverConf.xml**&#x200B;檔案以獲取所有實例共用的參數。
* 然後，它會載入&#x200B;**config-**`<instance>`**.xml**&#x200B;檔案。 在此檔案中找到的值比&#x200B;**serverConf.xml**&#x200B;中包含的值具有優先順序。

   這兩個檔案的格式相同。 對於&#x200B;**config-`<instance>`.xml**&#x200B;檔案中的給定實例，**serverConf.xml**&#x200B;中的任何值都可以過載。

此操作模式為配置提供了極大的靈活性。
