---
title: 內容管理員資源與原則
seo-title: 內容管理員資源與原則
description: 內容管理員資源與原則
seo-description: null
page-status-flag: never-activated
uuid: 3560e392-129a-471d-a211-05481cdda224
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: b22b3abb-6fe5-4f4d-93fc-0d00d426edb6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 內容管理員資源與原則{#content-manager-resources-and-principles}

您需要定義出版物範本，其中包含每個內容的轉換範本。

內容塊在XML文檔中構造用於資料儲存。 編輯介面可用來從Adobe Campaign用戶端主控台或透過網頁瀏覽器輸入內容。 此外，還可透過擷取XML流量或資料庫中匯整的資料，自動輸入內容。

結合XML文檔和XSL或JavaScript模板樣式表會自動生成各種格式（HTML、文本）的出版物模板投影。

![](assets/d_ncs_content_process.png)

內容設定需要下列資源：

* 資料結構：描述XML內容結構。 For more on this, refer to [Data schemas](../../delivery/using/data-schemas.md).
* 資料輸入表單：建立資料輸入畫面。 For more on this, refer to [Input forms](../../delivery/using/input-forms.md).
* 影像：用於資料輸入表單的影像。 For more on this, refer to [Image management](../../delivery/using/formatting.md#image-management).
* 樣式表：格式。 For more on this, refer to [Formatting](../../delivery/using/formatting.md).
* JavaScript範本：格式化輸出檔案。 For more on this, refer to [Publication templates](../../delivery/using/publication-templates.md).
* JavaScript代碼：資料匯整的JavaScript程式碼。 For more on this, refer to [Aggregator](../../delivery/using/publication-templates.md#aggregator).
* 出版物範本：出版物範本的定義。 For more on this, refer to [Publication templates](../../delivery/using/publication-templates.md).
* 內容：要建立和發佈的內容例項。 如需詳細資訊，請參閱「使 [用內容範本」](../../delivery/using/using-a-content-template.md)。
