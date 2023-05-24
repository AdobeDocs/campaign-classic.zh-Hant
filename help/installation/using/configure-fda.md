---
product: campaign
title: 設定FDA聯結器
description: 瞭解FDA的設定步驟
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 5%

---

# 配置 FDA 連接器 {#specific-configurations-by-database-type}



根據您想要從Adobe Campaign存取的外部資料庫，您將需要執行某些特定設定。 這些設定基本上包括在Adobe Campaign伺服器上安裝驅動程式和宣告屬於每個RDBMS的環境變數。

一般而言，您需要在Adobe Campaign伺服器的外部資料庫上安裝對應的使用者端層。

>[!NOTE]
>
>中列出了相容的版本 [Campaign相容性對照表](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA).

## 設定步驟 {#fda-configuration-steps}

若要使用FDA設定外部資料庫的存取權，設定步驟如下：

1. 安裝驅動程式並設定與Adobe Campaign伺服器上的資料庫對應的外部帳戶。 請參閱資料庫專屬頁面 [以下列出](#fda-specific-configuration)
1. 測試外部帳戶，或在Adobe Campaign和外部資料庫之間建立暫時連線。 [了解更多](../../installation/using/connecting-to-database.md)
1. 在Adobe Campaign中建立外部資料庫的結構描述。 這可讓您識別外部資料庫的資料結構。 [了解更多](../../installation/using/creating-data-schema.md)
1. 如有需要，請從先前建立的結構描述建立新的目標對應。 如果您的傳遞收件者來自外部資料庫，則需要此專案。 此實作隨附與訊息個人化相關的限制。 [了解更多](../../installation/using/defining-data-mapping.md)

建立資料結構描述後，即可在Adobe Campaign工作流程中處理資料。 如需詳細資訊，請參閱[本章節](../../workflow/using/accessing-an-external-database--fda-.md)。

## 資料庫特定設定 {#fda-specific-configuration}

根據您想要從Adobe Campaign存取的外部資料庫，您將需要執行某些特定設定。 這些設定基本上包括在Adobe Campaign伺服器上安裝屬於每個RDBMS的驅動程式和宣告環境變數，以及設定外部帳戶。

請依照下列連結深入瞭解：

* 連線Campaign和 [azure synapse](../../installation/using/configure-fda-synapse.md)
* 連線Campaign和 [Google BigQuery](../../installation/using/configure-fda-google-big-query.md)
* 連線Campaign和 [hadoop](../../installation/using/configure-fda-hadoop.md)
* 連線Campaign和 [Microsoft SQL Server](../../installation/using/configure-fda-sql.md)
* 連線Campaign和 [netezza](../../installation/using/configure-fda-netezza.md)
* 連線Campaign和 [oracle](../../installation/using/configure-fda-oracle.md)
* 連線Campaign和 [PostgreSQL](../../installation/using/configure-fda-postgresql.md)
* 連線Campaign和 [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* 連線Campaign和 [Snowflake](../../installation/using/configure-fda-snowflake.md)
* 連線Campaign和 [sybase IQ](../../installation/using/configure-fda-sybase.md)
* 連線Campaign和 [teradata](../../installation/using/configure-fda-teradata.md)
* 連線Campaign和 [vertica analytics](../../installation/using/configure-fda-vertica.md)
