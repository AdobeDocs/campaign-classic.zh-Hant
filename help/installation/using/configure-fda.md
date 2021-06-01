---
product: campaign
title: 配置FDA連接器
description: 了解FDA的設定步驟
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 5%

---

# 配置 FDA 連接器 {#specific-configurations-by-database-type}

您需要執行特定設定，這取決於您要從Adobe Campaign存取的外部資料庫。 這些設定主要涉及安裝驅動程式和聲明屬於Adobe Campaign伺服器上每個RDBMS的環境變數。

一般而言，您需要在Adobe Campaign伺服器的外部資料庫上安裝對應的用戶端層。

>[!NOTE]
>
>相容版本列在[Campaign相容性矩陣](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)中。


## 設定步驟 {#fda-configuration-steps}

若要使用FDA設定外部資料庫的存取權，設定步驟為：

1. 安裝驅動程式，並設定與Adobe Campaign伺服器上的資料庫相對應的外部帳戶。 請參閱下方所列的資料庫特定頁面[](#fda-specific-configuration)
1. 測試外部帳戶或在Adobe Campaign和外部資料庫之間建立臨時連線。 [瞭解更多](../../installation/using/connecting-to-database.md)
1. 在Adobe Campaign中建立外部資料庫的架構。 這可讓您識別外部資料庫的資料結構。 [瞭解更多](../../installation/using/creating-data-schema.md)
1. 如有需要，從先前建立的架構建立新的目標對應。 如果傳送的收件者來自外部資料庫，則此為必要項目。 此實施隨附與訊息個人化相關的限制。 [瞭解更多](../../installation/using/defining-data-mapping.md)

建立資料結構後，即可在Adobe Campaign工作流程中處理資料。 如需詳細資訊，請參閱[本章節](../../workflow/using/accessing-an-external-database--fda-.md)。

## 資料庫特定配置{#fda-specific-configuration}

您需要執行特定設定，這取決於您要從Adobe Campaign存取的外部資料庫。 這些設定主要涉及安裝驅動程式和聲明屬於Adobe Campaign伺服器上每個RDBMS的環境變數，以及配置外部帳戶。

請依照下列連結了解更多：

* 連接促銷活動和[Azure synapse](../../installation/using/configure-fda-synapse.md)

* 連接促銷活動和[Snowflake](../../installation/using/configure-fda-snowflake.md)

* 連接促銷活動和[Hadoop](../../installation/using/configure-fda-hadoop.md)

* 連接促銷活動和[Oracle](../../installation/using/configure-fda-oracle.md)

* 連接促銷活動和[Netezza](../../installation/using/configure-fda-netezza.md)

* 連接促銷活動和[Sybase IQ](../../installation/using/configure-fda-sybase.md)

* 連接促銷活動和[Teradata](../../installation/using/configure-fda-teradata.md)

* 連接促銷活動和[SAP HANA](../../installation/using/configure-fda-sap-hana.md)
