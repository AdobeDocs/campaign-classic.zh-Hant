---
solution: Campaign Classic
product: campaign
title: 關於Adobe Campaign Classic中的架構參考
description: 瞭解如何設定擴充結構，以擴充Adobe Campaign Classic資料庫的概念資料模型。
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 7%

---


# 關於綱要參考{#about-schema-reference}

本章說明如何設定擴充架構，以擴充Adobe Campaign資料庫的概念資料模型。

如需深入瞭解Campaign內建表格及其互動，請參閱[Campaign Classic資料模型](https://helpx.adobe.com/tw/campaign/kb/acc-datamodel.html)。

並以 XML 描述了應用程式中資料的實體和邏輯結構。它遵循Adobe Campaign專屬的語法，稱為&#x200B;**schema**。

方案是與資料庫表關聯的XML文檔。 它定義了資料結構，並描述了表的SQL定義：

* 表的名稱
* 欄位
* 索引
* 與其他表格的連結

此外，也說明用來儲存資料的XML結構：

* 元素和屬性
* 元素階層
* 元素和屬性類型
* 預設值
* 標籤、說明和其他屬性。

結構使您能夠定義資料庫中的實體。 每個實體都有一個架構。

下圖顯示Adobe Campaign資料系統中結構描述的位置：

![](assets/reference_schema_intro.png)

## 結構{#syntax-of-schemas}的語法

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
>實體的根元素與架構同名。

![](assets/s_ncs_configuration_schema_and_entity.png)

**`<element>`**&#x200B;標籤定義實體元素的名稱。 **`<attribute>`** 架構的標籤定義了已連結到的標 **`<element>`** 記中屬性的名稱。

## 方案{#identification-of-a-schema}的標識

資料架構由其名稱及其命名空間標識。

命名空間可讓您依目標區域對一組結構描述進行分組。 例如，**cus**&#x200B;命名空間用於客戶特定的配置(**customers**)。

>[!IMPORTANT]
>
>作為標準，命名空間的名稱必須簡明扼要，且必須只包含符合XML命名規則的授權字元。
>
>標識符不能以數字字元開頭。

某些名稱空間會保留，以說明Adobe Campaign應用程式運作所需的系統實體：

* **xtk**:平台系統資料，
* **nl**:關於應用程式的整體使用，
* **nms**:傳送（收件者、傳送、追蹤等）,
* **ncm**:內容管理，
* **臨時**:為臨時方案保留。

模式的標識鍵是使用命名空間和名稱以冒號分隔的字串；例如：**cus:recipient**。
