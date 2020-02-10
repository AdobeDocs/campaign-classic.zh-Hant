---
title: 關於網頁追蹤
seo-title: 關於網頁追蹤
description: 關於網頁追蹤
seo-description: null
page-status-flag: never-activated
uuid: 59d18ffb-c26e-4571-8364-5e85ec587349
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 38ba9be9-dabc-41d4-878c-d772955301fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 關於網頁追蹤{#about-web-tracking}

除了顯示網際網路使用者點按電子郵件訊息中連結的行為的標準追蹤外，Adobe Campaign平台還可讓您收集網際網路使用者瀏覽您網站的相關資訊。 此資料收集由網頁追蹤模組執行。

當網際網路使用者從指定的傳送點按電子郵件中的追蹤連結時，重新導向伺服器所聯絡的作業Cookie會儲存包含廣播識別碼(broadlogId)和傳送識別碼(deliveryId)。

然後，當使用者每次造訪包含網頁追蹤標籤的頁面時，網頁用戶端就會傳送此Cookie至伺服器。 在整個會話期間，即直到Web客戶端關閉。

重新導向伺服器會以這種方式收集下列資料：

* 透過以參數形式傳送的識別碼，檢視之頁面的URL
* 透過工作階段Cookie瀏覽網頁的傳送，
* 透過作業Cookie點按的網際網路使用者識別碼，
* 其他資訊，例如產生的業務量。

下圖顯示了客戶機和各種伺服器之間對話的階段。

![](assets/d_ncs_integration_webtracking_structure1.png)

