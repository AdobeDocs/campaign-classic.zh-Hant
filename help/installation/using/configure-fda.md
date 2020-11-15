---
title: 配置FDA連接器
description: 瞭解FDA的設定步驟
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 3d6515ca291715e5e02f9b5404803e9087555284
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---


# 配置 FDA 連接器 {#specific-configurations-by-database-type}

根據您想要能夠從Adobe Campaign存取的外部資料庫，您需要執行特定的組態。 這些配置實際上涉及在Adobe Campaign伺服器上安裝驅動程式並聲明屬於每個RDBMS的環境變數。

一般而言，您必須在Adobe Campaign伺服器的外部資料庫上安裝對應的用戶端層。

>[!NOTE]
>
>相容版本會列在「促銷活動相 [容性矩陣」中](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)。


## 配置步驟 {#fda-configuration-steps}

要使用FDA設定對外部資料庫的訪問，配置步驟包括：

1. 在Adobe Campaign伺服器上安裝對應至您資料庫的驅動程式。 驅動程式列在下面列出的特定於資料庫 [的頁面中](#fda-specific-configuration)。
1. [建立並設定外部帳戶](../../installation/using/connecting-to-database.md) ，讓您建立Adobe Campaign與外部資料庫之間的連線。 如需促銷活動中外部帳戶的詳細資訊，請參 [閱此頁](../../installation/using/external-accounts.md)。
1. [在Adobe Campaign中建立外部資料庫的架構](../../installation/using/creating-data-schema.md) 。 這允許您識別外部資料庫的資料結構。
1. 如果需要， [從先前建立的架構](../../installation/using/defining-data-mapping.md) 建立新的目標映射。 如果傳送的收件者來自外部資料庫，則此為必要項目。 此實作具有與訊息個人化相關的限制。

建立資料結構後，您就可以在Adobe Campaign工作流程中處理資料。 如需詳細資訊，請參閱[本章節](../../workflow/using/accessing-an-external-database--fda-.md)。

## 資料庫特定配置 {#fda-specific-configuration}

根據您想要能夠從Adobe Campaign存取的外部資料庫，您需要執行特定的組態。 這些配置實際上涉及在Adobe Campaign伺服器上安裝驅動程式並聲明屬於每個RDBMS的環境變數。

請依照下列連結進一步瞭解：

* [Azure突觸](../../installation/using/configure-fda-synapse.md)

* [雪花](../../installation/using/configure-fda-snowflake.md)

* [Hadoop](../../installation/using/configure-fda-hadoop.md)

* [Oracle](../../installation/using/configure-fda-oracle.md)

* [內泰扎](../../installation/using/configure-fda-netezza.md)

* [Sybase IQ](../../installation/using/configure-fda-sybase.md)

* [Teradata](../../installation/using/configure-fda-teradata.md)

* [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
