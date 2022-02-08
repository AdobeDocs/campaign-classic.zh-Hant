---
product: campaign
title: 關於Adobe Campaign Classic中的模式引用
description: 瞭解如何配置擴展模式以擴展Adobe Campaign Classic資料庫的概念資料模型
feature: Schema Extension
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 7%

---

# 關於方案參考{#about-schema-reference}

![](../../assets/v7-only.svg)

本章介紹如何配置擴展架構以擴展Adobe Campaign資料庫的概念資料模型。

要更好地瞭解活動內置表及其交互作用，請參閱 [Campaign Classic資料模型](https://helpx.adobe.com/tw/campaign/kb/acc-datamodel.html)。

並以 XML 描述了應用程式中資料的實體和邏輯結構。它遵循Adobe Campaign特有的語法，稱為 **架構**。

模式是與資料庫表關聯的XML文檔。 它定義了資料結構並描述了表的SQL定義：

* 表的名稱
* 欄位
* 索引
* 與其他表的連結

還介紹了用於儲存資料的XML結構：

* 元素和屬性
* 元素層次
* 元素和屬性類型
* 預設值
* 標籤、說明和其他屬性。

方案使您能夠在資料庫中定義實體。 每個實體都有一個架構。

下圖顯示了架構在Adobe Campaign資料系統中的位置：

![](assets/reference_schema_intro.png)

## 架構語法 {#syntax-of-schemas}

架構的根元素為 **`<srcschema>`**。 它包含 **`<element>`** 和 **`<attribute>`** 子元素。

第一個 **`<element>`** 子元素與實體的根重合。

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

的 **`<element>`** 標籤定義實體元素的名稱。 **`<attribute>`** 模式的標籤定義 **`<element>`** 已連結到的標籤。

## 模式的標識 {#identification-of-a-schema}

資料架構由其名稱和命名空間標識。

使用命名空間可以按感興趣區域對一組架構進行分組。 例如， **番** 命名空間用於客戶特定的配置(**客戶**)。

架構的標識鍵是使用命名空間和名稱以冒號分隔的字串；例如： **cus：收件人**。

>[!IMPORTANT]
>
>命名空間的名稱必須簡潔，並且必須只包含根據XML命名規則授權的字元。
>
>標識符不能以數字字元開頭。
>
>以下命名空間是為Adobe Campaign應用程式操作所需的系統實體的說明而保留的，不得使用： **xtk**。 **n**。 **nms**。 **ncm**。 **溫度**。 **無**。 **crm**。 **xxl**。

