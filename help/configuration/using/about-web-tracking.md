---
product: campaign
title: 關於網路追蹤
description: 關於網路追蹤
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 91c31703-75e6-47a4-a877-35682dd687a9
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 4%

---

# 關於網路追蹤{#about-web-tracking}

除了顯示網際網路使用者點按電子郵件訊息中連結之行為的標準追蹤以外，Adobe Campaign平台還可讓您收集網際網路使用者如何瀏覽您網站的相關資訊。 此資料收集由Web追蹤模組執行。

當網際網路使用者按一下來自指定傳送之電子郵件中的追蹤連結時，重新導向伺服器聯絡的會話Cookie會儲存包含broadlog識別碼(broadlogId)和傳送識別碼(deliveryId)。

然後，當使用者每次造訪包含網頁追蹤標籤的頁面時，Web用戶端就會將此Cookie傳送至伺服器。 這會持續到整個工作階段，即直到Web用戶端關閉為止。

重定向伺服器以此方式收集以下資料：

* 透過以參數形式傳送的識別碼，檢視的頁面URL
* 透過工作階段cookie來瀏覽網頁時所透過的傳送，
* 透過工作階段cookie點按的網際網路使用者識別碼，
* 其他資訊，如生成的業務量。

下圖顯示了客戶端與各伺服器之間對話的各個階段。

![](assets/d_ncs_integration_webtracking_structure1.png)
