---
product: campaign
title: 內容管理員資源與原則
description: 內容管理員資源與原則
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 6%

---

# 內容管理員資源與原則{#content-manager-resources-and-principles}

您需要定義發佈範本，其中包含每個內容的轉換範本。

內容塊以XML文檔結構化以用於資料儲存。 編輯介面可用來從Adobe Campaign用戶端主控台或透過網頁瀏覽器輸入內容。 也可以通過捕獲XML流或資料庫中聚合的資料自動輸入內容。

組合XML文檔和XSL或JavaScript模板樣式表會自動以各種格式（HTML、文本）生成發佈模板的投影。

![](assets/d_ncs_content_process.png)

內容設定需要下列資源：

* 資料結構：XML內容結構的說明。 有關詳細資訊，請參閱[資料結構](data-schemas.md)。
* 資料輸入表單：資料輸入螢幕的構造。 有關詳細資訊，請參閱[輸入表單](input-forms.md)。
* 影像：用於資料輸入表單的影像。 有關詳細資訊，請參閱[影像管理](formatting.md#image-management)。
* 樣式表：使用XSLT語言對輸出文檔進行格式化。 有關詳細資訊，請參閱[Formatting](formatting.md)。
* JavaScript範本：格式化輸出文檔。 有關詳細資訊，請參閱[發佈範本](publication-templates.md)。
* JavaScript程式碼：資料匯總的JavaScript程式碼。 有關詳細資訊，請參閱[聚合器](publication-templates.md#aggregator)。
* 發佈範本：發佈範本的定義。 有關詳細資訊，請參閱[發佈範本](publication-templates.md)。
* 內容：要建立和發佈的內容例項。 有關詳細資訊，請參閱[使用內容範本](using-a-content-template.md)。
