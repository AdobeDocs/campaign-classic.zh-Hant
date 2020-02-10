---
title: 使用Adobe Campaign Classic收件者表格
description: 瞭解如何在設計資料模型時，使用Adobe Campaign Classic中的現成可用收件者表格。
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
source-git-commit: 620724e283215df1fb3f10bd0211652b36284b57

---


# 資料模型最佳實務{#data-model-best-practices}

以下是使用大型表和複雜連接設計資料模型時應遵循的一些最佳實踐。

* 使用其他自訂收件者表格時，請確定每個傳送對應都有專用的記錄表。
* 減少欄數，尤其是識別未使用的欄數。
* 通過避免複雜的連接（如多個條件和／或多個列上的連接）來優化資料模型關係。
* 對於連接鍵，請始終使用數字資料，而不是字串。
* 盡可能減少日誌保留深度。 如果您需要更深入的歷史記錄，您可以匯整計算和／或處理自訂的日誌表，以儲存較大的歷史記錄。

有關如何針對較大的卷優化資料庫設計的更詳細的最佳實踐，請參 [閱Campaign Classic資料模型最佳實踐](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html)。
