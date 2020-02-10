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


# 使用預設的「收件者」(Recipient)表{#default-recipient-table}

Adobe Campaign中立即可用的「收件者」表格為您建立資料模型提供了良好的起點。 它有許多預先定義的欄位和表格連結，可輕鬆擴充。 當您主要針對收件者時，這特別有用，因為它適合簡單的收件者導向資料模型。

使用標準「收件者」(Recipient)表的優點如下：

* 立即可用的功能，例如訂閱、種子清單、調查、社交等。
* 提供以收件者為中心的資料模型為行銷資料庫。
* 更快速的實作。
* 由支援和合作夥伴輕鬆維護。

但是，可以擴展「收件人」(Recipient)表，但不能減少表中的欄位或連結數。

>[!IMPORTANT]
>
>建議不要刪除收件者表格中的欄位（即使欄位無用），因為這可能會導致內建模組發生錯誤。

此外，由於「收件者」(Recipient)表格是產品的一部分，因此表格及其關聯表格都會隨著產品的變更而改變。 因此，需要額外的維護功能，才能檢查升級時是否仍有任何擴充功能。
