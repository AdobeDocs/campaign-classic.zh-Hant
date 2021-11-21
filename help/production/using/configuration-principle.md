---
product: campaign
title: 設定原則
description: 設定原則
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---

# 設定原則{#configuration-principle}

![](../../assets/v7-only.svg)

Adobe Campaign平台以例項概念為基礎，與Apache使用的虛擬主機概念類似。 此操作模式可讓您指派數個執行個體來共用伺服器。 實例之間完全分離，並使用其自己的資料庫和配置檔案操作。

對於指定的伺服器，有兩個元素是所有Adobe Campaign例項的共同元素：

* 此 **內部** 密碼：這是一般管理員密碼。 它對特定應用程式伺服器的所有實例都很常見。

   >[!IMPORTANT]
   >
   >若要使用 **內部** 識別碼，您必須預先定義密碼。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

* 多項技術伺服器配置：這些設定在執行個體的特定設定中皆可能過載。

組態檔會儲存在 **conf** 安裝目錄的目錄。 設定會劃分為三個檔案：

* **serverConf.xml**:所有執行個體的整體設定。
* **config-**`<instance>`**.xml** (其中 **`<instance>`** 是例項名稱):例項的特定設定。
* **serverConf.xml.diff**:初始配置與當前配置之間的差值。 此檔案由應用程式自動生成，不能手動修改。 它可用來在更新組建版本時自動傳播使用者修改。

執行個體設定的載入方式如下：

* 模組會載入 **serverConf.xml** 檔案，以取得所有執行個體共用的參數。
* 接著會載入 **config-**`<instance>`**.xml** 檔案。 在此檔案中找到的值優先順序高於 **serverConf.xml**.

   這兩個檔案的格式相同。 中的任何值 **serverConf.xml** 在中，可以是多載的指定例項 **config-`<instance>`.xml** 檔案。

此操作模式為配置提供了極大的靈活性。
