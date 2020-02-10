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
source-git-commit: 65affa58a66090c3bffc837fdbd85aa46338bd3e

---


# 擴充資料模型{#extending-data-model}

從Adobe Campaign開始，您需要評估預設資料模型，以檢查哪個表格最適合儲存行銷資料。

如果相關，您可以使用預設的「收件者」表格和現成可用的欄位，如本節所述 [內容](../../configuration/using/default-recipient-table.md)。

如有需要，您可以使用兩種機制來擴充它：

* 使用新欄位擴充現有表格。 例如，您可以在「收件者」表格中新增「忠誠度」欄位。
* 建立新表格，例如列出資料庫每個描述檔所有購買項目的「購買」表格，並將其連結至「收件者」表格。

有關配置擴展模式以擴展概念資料模型的詳細資訊，請參 [閱關於模式版](../../configuration/using/about-schema-edition.md)。

>[!IMPORTANT]
>
>擴充資料模型會保留給進階使用者。
