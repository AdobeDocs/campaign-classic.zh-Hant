---
title: 關於Adobe Campaign Classic資料模型
description: 本檔案說明Adobe Campaign Classic資料模型的基本概念。
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# 使用自訂收件者表格{#custom-recipient-table}

在設計您的Adobe Campaign資料模型時，您可以使用現成可用的「收件者」 [表格](../../configuration/using/default-recipient-table.md)，或決定建立非標準的收件者表格來儲存行銷設定檔。

事實上，如果您的資料模型不符合以收件者為中心的結構，您可以在Adobe Campaign中將其他表格設定為定位維度。 例如，當您需要鎖定家庭、帳戶（如行動電話）和公司／網站（而不只是收件者）時，這可能是相關的。

>[!NOTE]
>
>在這種情況下，您需要建立新的目 [標映射](../../configuration/using/target-mapping.md)。

使用自訂收件者表格時，所需的原則和步驟在本節中有詳細 [說明](../../configuration/using/about-custom-recipient-table.md)。

使用自訂「收件者」表格的優點如下：

## 彈性的資料模型 {#flexible-data-model}

如果您不需要大部分的「收件者」表格欄位，或者資料模型並非以收件者為中心，即裝即用的「收件者」表格是無用的。

## 可擴充性 {#scalability}

大型卷需要簡化的表格，而且欄位較少，才能有效率地設計。 現成可用的「收件者」表格中會有太多無用的欄位，這可能會影響效能並降低效率。

## 資料位置 {#data-location}

如果資料位於外部現有的行銷資料庫，使用現成可用的「收件者」表格可能需要耗費太多精力。 建立以現有結構為基礎的新結構更簡單。

## 輕鬆移轉 {#easy-migration}

不需要維護，即可檢查所有擴充功能是否在升級時仍然有效。

>[!IMPORTANT]
>
>使用自訂收件者表格會保留給進階使用者，並受到一些限制。 有關此內容的詳細資訊，請參閱本節。
