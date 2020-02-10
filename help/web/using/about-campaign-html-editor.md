---
title: 關於促銷活動HTML編輯器
seo-title: 關於促銷活動HTML編輯器
description: 關於促銷活動HTML編輯器
seo-description: null
page-status-flag: never-activated
uuid: 1b1d392d-4f19-4092-b57d-02051a242675
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 1ffe9f58-7258-4794-a314-524065f8a33b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 關於促銷活動HTML編輯器{#about-campaign-html-editor}

數位 **內容編輯器(DCE)** 是HTML內容編輯器，可讓您在Adobe Campaign中輕鬆建立或修改HTML格式的範本或內容。

「數位內容編輯器」可讓您插入頁面元素並設定其格式，並將資料庫欄位與HTML頁面的元素建立關聯。 在為Web應用程式建立頁面時，預設會提供此選項，或在根據作用中的範本建立傳送時提供。

>[!NOTE]
>
>DCE僅允許您執行本節中詳細介紹的操作。
>
>如果您想要新增伺服器端JavaScript程式碼，最好將它新增至個人化區塊。 有關建立和修改個性化塊的詳細資訊，請參 [閱此頁](../../delivery/using/personalization-blocks.md)。

>[!CAUTION]
>
>基於隱私權原因，我們建議對所有外部資源使用HTTPS。

## 內容編輯器一般操作 {#content-editor-general-operation}

本節介紹在Web應用程式框架內和交付環境中編輯和上傳使用DCE編輯的內容的主要步驟。

一般操作如下：

![](assets/dce_schema.png)

要建立簡單的Web應用程式，請執行以下步驟：

* 建立Web應用程式，如需詳細資訊，請參閱「 [建立著陸頁面」](../../web/using/creating-a-landing-page.md),
* 選擇現有內容或從標準範本建立內容，如需詳細資訊，請參閱范 [本管理](../../web/using/template-management.md)。
* 編輯和設定內容，如需詳細資訊，請參閱「編輯 [內容](../../web/using/editing-content.md)」
* 發佈Web應用程式，如需詳細資訊，請參閱 [發佈內容](../../web/using/creating-a-landing-page.md#step-3---publishing-content)[和本頁](../../web/using/publishing-a-web-form.md#managing-web-forms-delivery-and-tracking)。

>[!NOTE]
>
>有關詳細說明在Web應用程式框架內實施DCE的完整示例，請參閱 [建立登錄頁](../../web/using/creating-a-landing-page.md)。

若要建立電子郵件傳送，步驟如下：

* 從DCE處於活動狀態的電子郵件類型模板建立發送，
* 選擇現有內容或從標準範本建立內容，
* 編輯和設定線上內容、
* 傳送傳送，如需詳細資訊，請參閱 [本節](../../delivery/using/communication-channels.md)。

>[!NOTE]
>
>有關詳細說明在電子郵件發送框架內實施DCE的完整示例，請參 [閱此使用案例](../../web/using/use-case--creating-an-email-delivery.md)。

