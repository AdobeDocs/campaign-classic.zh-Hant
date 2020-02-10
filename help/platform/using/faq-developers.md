---
title: 常見問題
seo-title: 常見問題
description: Campaign Classic常見問答集
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 994ec35e37a1c26e83a8dd2ae31f6594cadd4c45

---


# 開發人員常見問答集 {#dev-faq}

作為一個開放式解決方案，Adobe Campaign 可進行自訂，以及供進階應用程式開發使用。

## 什麼是促銷活動資料模型？ {#what-is-the-campaign-data-model}

Adobe Campaign資料庫的概念資料模型由一組內建表格及其互動組成。 在XML中描述了應用中資料的物理和邏輯結構。 它遵循Adobe Campaign專屬的語法，稱為結構。 如需Adobe Campaign結構描述的詳細資訊， [請參閱本節](../../configuration/using/about-schema-edition.md)。

[按一下這裡以進一步瞭解Campaign資料模型](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)。

本文列出最 [佳實務](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html)。

## How to work with Campaign schemas? {#how-to-work-with-campaign-schemas-}

在 Adobe Campaign 中，資料綱要用於：

* 定義應用程式內資料物件與基礎資料庫表的連結方式。
* 定義 Campaign 應用程式中不同資料物件之間的連結。
* 定義及描述每個物件中包含的個別欄位。

閱讀[資料表及綱要使用入門](../../configuration/using/about-schema-edition.md)了解如何使用資料綱要、擴充和自訂 Campaign，以滿足您的需求。

## How to use a custom recipient table? {#how-to-use-a-custom-recipient-table-}

您可以在 Campaign 中建立和實作非標準式收件者表格，以傳送訊息。

[按一下這裡以獲得更多資訊。](../../configuration/using/about-custom-recipient-table.md)

## What are the best practices to define queries in Campaign? {#what-are-the-best-practices-to-define-queries-in-campaign-}

Adobe Campaign 查詢編輯器是一種功能強大的工具，可探索資料和建立細分。

您可以在軟體的多個層級上找到 Adobe Campaign 查詢工具：建立目標母體、細分客戶、擷取和篩選追蹤記錄、建立篩選器等。

您可以使用一般查詢編輯器查詢 Campaign 資料庫。可透過 **Tools>Generic query editor...** 選單存取一般查詢編輯器。透過它，您可擷取儲存在資料庫中的資訊，將其整理、分組、排序等操作。例如，使用者可以在新聞稿的連結上，還原在給定時間內點擊連結超過 [n] 次以上的收件者。透過這個工具，您可根據您的需求收集、排序和顯示結果。此工具結合了 Adobe Campaign 的所有可行的查詢方式。例如，您可以建立和儲存限制篩選器。這表示在目標工作流程等的查詢方塊中，可以使用在一般查詢編輯器中建立的使用者篩選器。

透過使用所選資料表的欄位或公式可以建立查詢。[本頁面](../../platform/using/about-queries-in-campaign.md)對在 Campaign 資料庫中建立查詢的主要原則進行了闡述。

[按一下這裡](../../workflow/using/query.md) ，以探索促銷活動查詢編輯器。

## How can I import a data package? {#how-can-i-import-a-data-package-}

使用 Adobe Campaign，您可以透過資料包系統匯出或匯入平台設定和資料。資料包可以 XML 格式檔案的形式顯示 Adobe Campaign 資料庫的實體。資料包中包含的每個實體都會以其所有資料表示。

資料包用於匯出資料設定，並將它整合到另一個 Adobe Campaign 系統中。

[按一下這裡](../../platform/using/working-with-data-packages.md)了解如何使用資料包匯入和匯出 Campaign 設定。

## 我可以在哪裡找到Campaign Classic API的清單？ {#where-can-i-find-the-list-of-campaign-classic-apis}

本專屬檔案提供所有促銷活動API，包括其完整 [說明](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。
