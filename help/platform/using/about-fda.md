---
title: 訪問外部資料庫
seo-title: 訪問外部資料庫
description: 訪問外部資料庫
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 47fd157e369ddf6c67f0b2b467799cecc6e5a822

---


# 關於同盟資料存取 {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

>[!CAUTION]
>
>除雪花連接器外，只有現場安裝或混合安裝才能通過FDA訪問外部資料庫。 For more on this, refer to this [page](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## 操作原則 {#operating-principle}

FDA選項可讓您在協力廠商資料庫中擴充資料模型。 它將自動檢測目標表的結構並使用SQL源中的資料。


若要使用此功能，您必須：

1. 擁有與Adobe Campaign FDA模組相容的外部資料庫。 資料庫系統和相容版本清單在相容性清單中 [有詳細說明](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。 使用者也必須擁有 [Adobe Campaign](../../platform/using/remote-database-access-rights.md) 和外部資料庫的必要權限。
1. [在Adobe Campaign伺服器上](../../platform/using/specific-configuration-database.md) ，安裝與您的資料庫對應的驅動程式。
1. [建立並設定外部帳戶](../../platform/using/connecting-to-database.md) ，讓您建立Adobe Campaign與外部資料庫之間的連線。 有關可用外部帳戶的詳細資訊，請參閱本 [頁](../../platform/using/external-accounts.md)。
1. [在Adobe Campaign中建立外部資料庫的架構](../../platform/using/creating-data-schema.md) 。 這允許您識別外部資料庫的資料結構。
1. 最終， [從先前建立的架構建立新的目標對應](../../platform/using/defining-data-mapping.md) ，如果傳送的收件者來自外部資料庫的話。 這具有某些限制，特別是在個人化交貨方面。

建立資料結構後，您就可以在Adobe Campaign工作流程中處理資料。 如需詳細資訊，請參閱[本小節](../../workflow/using/executing-a-workflow.md#architecture)。

## 最佳實務與建議 {#best-practices-and-recommendations}

FDA選項是用來在工作流程中以批次模式控制外部資料庫中的資料。 在另一種情況下使用FDA，例如進行單一作業時，必須謹慎（個人化、互動、即時傳送等）。

請盡量避免需要同時使用Adobe Campaign和外部資料庫的作業。 若要這麼做，您可以：

* 將Adobe Campaign資料庫匯出至外部資料庫，並僅從外部資料庫執行作業，然後再將結果重新匯入Adobe Campaign。
* 從外部Adobe Campaign資料庫收集資料，並在本機執行作業。

如果您想要使用外部資料庫的資料在傳送中進行個人化，請收集要在工作流程中使用的資料，以便在臨時表格中使用。 然後使用臨時表格中的資料來個人化您的傳送。

## 限制 {#limitations}

FDA選項受到您所使用外部資料庫系統的軟性限制。

基於效能原因，我們不建議使用此功能來執行單一作業（傳送個人化、互動模組、即時）。
