---
solution: Campaign Classic
product: campaign
title: 內容管理員資源與原則
description: 內容管理員資源與原則
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 6%

---


# 內容管理員資源與原則{#content-manager-resources-and-principles}

您需要定義出版物範本，其中包含每個內容的轉換範本。

內容塊在XML文檔中構造用於資料儲存。 編輯介面可用來從Adobe Campaign用戶端主控台或透過網頁瀏覽器輸入內容。 此外，還可透過擷取XML流量或資料庫中匯整的資料，自動輸入內容。

結合XML文檔和XSL或JavaScript模板樣式表會自動生成各種格式（HTML、文本）的出版物模板投影。

![](assets/d_ncs_content_process.png)

內容設定需要下列資源：

* 資料結構：描述XML內容結構。 有關詳細資訊，請參閱[資料結構](../../delivery/using/data-schemas.md)。
* 資料輸入表單：建立資料輸入畫面。 有關詳細資訊，請參閱[Input forms](../../delivery/using/input-forms.md)。
* 影像：用於資料輸入表單的影像。 有關詳細資訊，請參閱[映像管理](../../delivery/using/formatting.md#image-management)。
* 樣式表：格式。 有關詳細資訊，請參閱[Formatting](../../delivery/using/formatting.md)。
* JavaScript範本：格式化輸出檔案。 有關詳細資訊，請參閱[出版物模板](../../delivery/using/publication-templates.md)。
* JavaScript代碼：資料匯整的JavaScript程式碼。 有關詳細資訊，請參閱[聚合器](../../delivery/using/publication-templates.md#aggregator)。
* 出版物範本：出版物範本的定義。 有關詳細資訊，請參閱[出版物模板](../../delivery/using/publication-templates.md)。
* 內容：要建立和發佈的內容例項。 有關詳細資訊，請參閱[使用內容模板](../../delivery/using/using-a-content-template.md)。
