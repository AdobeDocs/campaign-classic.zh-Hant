---
product: campaign
title: 配置FDA連接器
description: 瞭解FDA的配置步驟
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 5%

---

# 配置 FDA 連接器 {#specific-configurations-by-database-type}

![](../../assets/v7-only.svg)

根據您希望能夠從Adobe Campaign訪問的外部資料庫，您需要執行某些特定配置。 這些配置實質上涉及安裝驅動程式並聲明屬於Adobe Campaign伺服器上每個RDBMS的環境變數。

通常，您需要在Adobe Campaign伺服器上的外部資料庫上安裝相應的客戶端層。

>[!NOTE]
>
>相容版本列於 [市場活動相容性清單](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)。

## 設定步驟 {#fda-configuration-steps}

要使用FDA設定對外部資料庫的訪問，配置步驟包括：

1. 安裝驅動程式，並設定與Adobe Campaign伺服器上的資料庫對應的外部帳戶。 請參閱特定於資料庫的頁 [下面列出](#fda-specific-configuration)
1. Test外部帳戶或在Adobe Campaign和外部資料庫之間建立臨時連接。 [了解更多](../../installation/using/connecting-to-database.md)
1. 在Adobe Campaign建立外部資料庫的架構。 這允許您標識外部資料庫的資料結構。 [了解更多](../../installation/using/creating-data-schema.md)
1. 如果需要，從先前建立的架構建立新的目標映射。 如果交貨的收件人來自外部資料庫，則此為必需欄位。 此實現具有與消息個性化相關的限制。 [了解更多](../../installation/using/defining-data-mapping.md)

建立資料模式後，可以在Adobe Campaign工作流中處理資料。 如需詳細資訊，請參閱[本章節](../../workflow/using/accessing-an-external-database--fda-.md)。

## 特定於資料庫的配置 {#fda-specific-configuration}

根據您希望能夠從Adobe Campaign訪問的外部資料庫，您需要執行某些特定配置。 這些配置實質上涉及安裝驅動程式和聲明屬於Adobe Campaign伺服器上每個RDBMS的環境變數，以及配置外部帳戶。

按照以下連結瞭解詳細資訊：

* 連接市場活動和 [韋爾蒂卡](../../installation/using/configure-fda-vertica.md)

* 連接市場活動和 [Google大查詢](../../installation/using/configure-fda-google-big-query.md)

* 連接市場活動和 [azure synapse](../../installation/using/configure-fda-synapse.md)

* 連接市場活動和 [Snowflake](../../installation/using/configure-fda-snowflake.md)

* 連接市場活動和 [Hadoop](../../installation/using/configure-fda-hadoop.md)

* 連接市場活動和 [Oracle](../../installation/using/configure-fda-oracle.md)

* 連接市場活動和 [Netezza](../../installation/using/configure-fda-netezza.md)

* 連接市場活動和 [sybase IQ](../../installation/using/configure-fda-sybase.md)

* 連接市場活動和 [Teradata](../../installation/using/configure-fda-teradata.md)

* 連接市場活動和 [SAP HANA](../../installation/using/configure-fda-sap-hana.md)

* 連接市場活動和 [PostgreSQL](../../installation/using/configure-fda-postgresql.md)

* 連接市場活動和 [MicrosoftSQL Server](../../installation/using/configure-fda-sql.md)

* 連接市場活動和 [SAP HANA](../../installation/using/configure-fda-sap-hana.md)

