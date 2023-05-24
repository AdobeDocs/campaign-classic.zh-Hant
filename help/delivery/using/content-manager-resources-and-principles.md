---
product: campaign
title: 內容管理員資源與原則
description: 內容管理員資源與原則
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Templates
exl-id: ade3f1d1-2235-4148-9b6f-721d3f521a15
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 4%

---

# 內容管理員資源與原則{#content-manager-resources-and-principles}



您需要定義一個出版物範本，其中包含每個內容的轉換範本。

在XML檔案中建構內容區塊以儲存資料。 編輯介面可用於從Adobe Campaign使用者端主控台或透過網頁瀏覽器輸入內容。 您也可以透過擷取XML流程或資料庫中彙總的資料來自動輸入內容。

結合XML檔案和XSL或JavaScript範本樣式表會自動產生各種格式(HTML、文字)的出版物範本投影。

![](assets/d_ncs_content_process.png)

內容設定需要下列資源：

* 資料結構描述： XML內容結構的描述。 有關詳細資訊，請參閱 [資料結構描述](data-schemas.md).
* 資料輸入表單：建構資料輸入畫面。 有關詳細資訊，請參閱 [輸入表單](input-forms.md).
* 影像：資料輸入表單中使用的影像。 有關詳細資訊，請參閱 [影像管理](formatting.md#image-management).
* 樣式表：使用XSLT語言格式化輸出檔案。 有關詳細資訊，請參閱 [格式設定](formatting.md).
* JavaScript範本：使用JavaScript語言格式化輸出檔案。 有關詳細資訊，請參閱 [發佈範本](publication-templates.md).
* JavaScript程式碼：資料彙總的JavaScript程式碼。 有關詳細資訊，請參閱 [彙總](publication-templates.md#aggregator).
* 出版物範本：出版物範本的定義。 有關詳細資訊，請參閱 [發佈範本](publication-templates.md).
* 內容：要建立和發佈的內容例項。 有關詳細資訊，請參閱 [使用內容範本](using-a-content-template.md).
