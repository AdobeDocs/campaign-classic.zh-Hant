---
solution: Campaign Classic
product: campaign
title: 配置FDA連接器
description: 瞭解FDA的設定步驟
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0b53b165-a6d8-4604-b3f0-3fa6fce35146
translation-type: tm+mt
source-git-commit: 7ce5a01b57092043b8d9b52761b243f771cf74f2
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 5%

---

# 配置 FDA 連接器 {#specific-configurations-by-database-type}

根據您希望能夠從Adobe Campaign訪問的外部資料庫，您需要執行某些特定配置。 這些配置實際上涉及在Adobe Campaign伺服器上安裝驅動程式並聲明屬於每個RDBMS的環境變數。

通常，您需要在Adobe Campaign伺服器上的外部資料庫上安裝相應的客戶端層。

>[!NOTE]
>
>相容版本列在[促銷活動相容性矩陣](../../rn/using/compatibility-matrix.md#FederatedDataAccessFDA)中。


## 配置步驟 {#fda-configuration-steps}

要使用FDA設定對外部資料庫的訪問，配置步驟包括：

1. 安裝驅動程式並設定與Adobe Campaign伺服器上的資料庫對應的外部帳戶。 請參閱下面列出的資料庫特定頁[](#fda-specific-configuration)
1. 測試外部帳戶或在Adobe Campaign和外部資料庫之間建立臨時連接。 [了解更多](../../installation/using/connecting-to-database.md)
1. 在Adobe Campaign建立外部資料庫的模式。 這允許您標識外部資料庫的資料結構。 [了解更多](../../installation/using/creating-data-schema.md)
1. 如果需要，從先前建立的架構建立新的目標映射。 如果傳送的收件者來自外部資料庫，則此為必要項目。 此實作具有與訊息個人化相關的限制。 [了解更多](../../installation/using/defining-data-mapping.md)

建立資料架構後，您就可以在Adobe Campaign工作流程中處理資料。 如需詳細資訊，請參閱[本章節](../../workflow/using/accessing-an-external-database--fda-.md)。

## 資料庫特定配置{#fda-specific-configuration}

根據您希望能夠從Adobe Campaign訪問的外部資料庫，您需要執行某些特定配置。 這些配置實際上涉及在Adobe Campaign伺服器上安裝驅動程式並聲明屬於每個RDBMS的環境變數，以及配置外部帳戶。

請依照下列連結進一步瞭解：

* 連接促銷活動和[Azure synapse](../../installation/using/configure-fda-synapse.md)

* 連接促銷活動和[Snowflake](../../installation/using/configure-fda-snowflake.md)

* 連接促銷活動和[Hadoop](../../installation/using/configure-fda-hadoop.md)

* 連接促銷活動和[Oracle](../../installation/using/configure-fda-oracle.md)

* 連接促銷活動和[Netezza](../../installation/using/configure-fda-netezza.md)

* 連接促銷活動和[Sybase IQ](../../installation/using/configure-fda-sybase.md)

* 連接促銷活動和[Teradata](../../installation/using/configure-fda-teradata.md)

* 連接促銷活動和[SAP HANA](../../installation/using/configure-fda-sap-hana.md)
