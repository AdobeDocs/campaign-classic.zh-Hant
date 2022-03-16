---
product: campaign
title: 開發人員常見問題集
description: 開發人員常見問題集
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 20552812-5c58-4d48-9636-d5135197685d
source-git-commit: 36b10a49fe92853f98beeb9e7d2fea3f59b10b6f
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 97%

---

# 開發人員常見問題集 {#dev-faq}

![](../../assets/v7-only.svg)

作為一個開放式解決方案，Adobe Campaign 可進行自訂，以及供進階應用程式開發使用。

## 什麼是 Campaign 資料模型？ {#what-is-the-campaign-data-model}

Adobe Campaign 資料庫的概念資料模型由一組內建表格及其互動組成，並以 XML 描述了應用程式中資料的實體和邏輯結構。並且遵循 Adobe Campaign 專屬的語法，稱為綱要 (schema)。如需 Adobe Campaign 綱要的詳細資料，[請參閱本節](../../configuration/using/about-schema-edition.md)。

[按一下這裡以深入瞭解 Campaign 資料模型](https://helpx.adobe.com/tw/campaign/kb/acc-datamodel.html)。

[本文](https://helpx.adobe.com/tw/campaign/kb/acc-data-model-best-practices.html)列出最佳實務。

## 如何使用 Campaign 綱要？ {#how-to-work-with-campaign-schemas-}

在 Adobe Campaign 中，資料綱要用於：

* 定義應用程式內資料物件與基礎資料庫表的連結方式。
* 定義 Campaign 應用程式中不同資料物件之間的連結。
* 定義及描述每個物件中包含的個別欄位。

閱讀[資料表及綱要使用入門](../../configuration/using/about-schema-edition.md)瞭解如何使用資料綱要、擴充和自訂 Campaign，以滿足您的需求。

## 如何使用自訂的收件者表格？ {#how-to-use-a-custom-recipient-table-}

您可以在市場活動中建立並實施非內置的收件人表，以發送您的郵件。

[按一下這裡以獲得更多資訊。](../../configuration/using/about-custom-recipient-table.md)

## 在 Campaign 定義查詢的最佳實務是什麼？ {#what-are-the-best-practices-to-define-queries-in-campaign-}

Adobe Campaign 查詢編輯器是一種功能強大的工具，可探索資料和建立區段。

您可以在軟體的多個層級上找到 Adobe Campaign 查詢工具：建立目標母體、劃分客戶、擷取和篩選追蹤記錄、建立篩選器等。

您可以使用一般查詢編輯器查詢 Campaign 資料庫。可透過 **Tools > Generic query editor...** 功能表存取一般查詢編輯器。透過它，您可擷取儲存在資料庫中的資訊，將其整理、分組、排序等操作。例如，使用者可以在新聞稿的連結上，還原在給定時間內按一下連結超過 [n] 次以上的收件者。透過這個工具，您可根據您的需求收集、排序和顯示結果。此工具結合了 Adobe Campaign 的所有可行的查詢方式。例如，您可以建立和儲存限制篩選器。這表示在目標工作流程等的查詢方塊中，可以使用在一般查詢編輯器中建立的使用者篩選器。

透過使用所選資料表的欄位或公式可以建立查詢。[本頁面](../../platform/using/about-queries-in-campaign.md)對在 Campaign 資料庫中建立查詢的主要原則進行了闡述。

[按一下這裡](../../workflow/using/query.md) ，以探索 Campaign 查詢編輯器。

## 如何匯入資料包？ {#how-can-i-import-a-data-package-}

使用 Adobe Campaign，您可以透過資料包系統匯出或匯入平台配置和資料。資料包可以 XML 格式檔案的形式顯示 Adobe Campaign 資料庫的實體。資料包中包含的每個實體都會以其所有資料表示。

資料包用於匯出資料配置，並將它整合到另一個 Adobe Campaign 系統中。

[按一下這裡](../../platform/using/working-with-data-packages.md)瞭解如何使用資料包匯入和匯出 Campaign 配置。

## 我可以在哪裡找到 Campaign Classic API 清單？ {#where-can-i-find-the-list-of-campaign-classic-apis}

[本專屬文件](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant)提供所有 Campaign API，及個別完整說明。
