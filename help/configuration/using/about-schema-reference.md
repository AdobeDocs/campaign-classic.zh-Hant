---
product: campaign
title: 關於Adobe Campaign Classic中的綱要參考
description: 了解如何設定擴充功能結構，以擴充Adobe Campaign Classic資料庫的概念資料模型。
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 4a41aea9edfe5e6ca0454049cbb2892449eec153
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 7%

---

# 關於方案參考{#about-schema-reference}

本章說明如何設定擴充功能結構，以擴充Adobe Campaign資料庫的概念資料模型。

如需深入了解Campaign內建表格及其互動，請參閱[Campaign Classic資料模型](https://helpx.adobe.com/tw/campaign/kb/acc-datamodel.html)。

並以 XML 描述了應用程式中資料的實體和邏輯結構。它遵循Adobe Campaign特有的語法，稱為&#x200B;**schema**。

架構是與資料庫表關聯的XML文檔。 它定義了資料結構並描述了表的SQL定義：

* 表的名稱
* 欄位
* 索引
* 與其他表的連結

它還描述了用於儲存資料的XML結構：

* 元素和屬性
* 元素階層
* 元素和屬性類型
* 預設值
* 標籤、說明和其他屬性。

結構可讓您定義資料庫中的實體。 每個實體都有結構。

下圖顯示結構在Adobe Campaign資料系統中的位置：

![](assets/reference_schema_intro.png)

## 架構的語法{#syntax-of-schemas}

架構的根元素為&#x200B;**`<srcschema>`**。 它包含&#x200B;**`<element>`**&#x200B;和&#x200B;**`<attribute>`**&#x200B;子元素。

第一個&#x200B;**`<element>`**&#x200B;子元素與實體的根重合。

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">  
    <attribute name="lastName"/>
    <attribute name="email"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

>[!NOTE]
>
>實體的根元素與架構的名稱相同。

![](assets/s_ncs_configuration_schema_and_entity.png)

**`<element>`**&#x200B;標籤定義實體元素的名稱。 **`<attribute>`** 架構的標籤定義了已連結的標 **`<element>`** 簽中的屬性名稱。

## 架構{#identification-of-a-schema}的標識

資料結構以其名稱及其命名空間來識別。

命名空間可讓您依感興趣區域對一組結構進行分組。 例如， **cus**&#x200B;命名空間用於客戶特定配置(**customers**)。

架構的識別索引鍵是使用命名空間建立的字串，以及以冒號分隔的名稱；例如：**cus:recipient**。

>[!IMPORTANT]
>
>命名空間的名稱必須簡明，並且必鬚根據XML命名規則僅包含授權的字元。
>
>識別碼不得以數字字元開頭。
>
>系統會保留下列命名空間，以供Adobe Campaign應用程式作業所需之系統實體的說明使用，且不得使用：**xtk**, **nl**, **nms**, **ncm**, **temp**, **ncl**, **crm**, **xxl**。

