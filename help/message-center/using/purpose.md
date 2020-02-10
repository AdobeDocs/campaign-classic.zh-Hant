---
title: 目的
seo-title: 目的
description: 目的
seo-description: null
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 目的{#purpose}

此使用案例的目的是即時將電子郵件附件添加到出站派單。

在此案例中，我們將瞭解如何透過個別／個人化附件傳送交易電子郵件。 附件不會預先上傳到Transactional Messaging伺服器上，但是會即時生成。

當您擷取客戶互動或詳細資訊時，您可能需要在程式結束時將此資訊傳回給客戶，例如附在電子郵件的PDF檔案。 以下是此情況的一般步驟。

1. 客戶進入網站，尋找想要購買的產品。
1. 客戶選擇產品並自訂一些選項。
1. 客戶完成交易。
1. 系統會傳送電子郵件給客戶確認交易。 我們不想在電子郵件中傳送PII（個人識別資訊），因此我們會產生安全的PDF並附加至電子郵件。
1. 客戶收到包含所有所需資料的電子郵件及其附件。

在此案例中，附件並非預先建立，而是即時新增至傳出電子郵件。 這也可讓您個人化附件的內容。 此外，如果附件與事務關聯（如上例所示），則您可能需要附件包含在客戶流程期間生成的動態資料。 以這種方式附加PDF也能最佳化安全性，因為您可以加密PDF並透過HTTPS傳送。
