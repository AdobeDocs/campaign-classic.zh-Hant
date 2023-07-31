---
product: campaign
title: 關於網路追蹤
feature: Configuration, Instance Settings
description: 關於網路追蹤
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 5%

---

# 關於網路追蹤{#about-web-tracking}

除了可顯示網際網路使用者點按電子郵件訊息中連結之行為的標準追蹤之外，Adobe Campaign平台還讓您收集網際網路使用者如何瀏覽您網站的資訊。 此資料收集由網頁追蹤模組執行。

當網際網路使用者點按來自指定傳遞的電子郵件中的追蹤連結時，已聯絡的重新導向伺服器會儲存包含broadlog識別碼(broadlogId)和傳遞識別碼(deliveryId)的工作階段Cookie。

接著，每當使用者造訪包含網頁追蹤標籤的頁面時，Web使用者端就會將此Cookie傳送至伺服器。 這會在整個工作階段中持續進行，亦即直到Web使用者端關閉為止。

重新導向伺服器會以此方式收集下列資料：

* 已檢視頁面URL，透過當作引數傳送的識別碼，
* 透過工作階段Cookie存取網頁的來源傳遞，
* 透過工作階段Cookie點按的網際網路使用者識別碼，
* 其他資訊，例如產生的業務量。

下圖顯示使用者端與各種伺服器之間的對話階段。

![](assets/d_ncs_integration_webtracking_structure1.png)
