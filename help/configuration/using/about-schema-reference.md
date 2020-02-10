---
title: 關於Adobe Campaign Classic中的架構參考
description: 瞭解如何設定擴充結構，以擴充Adobe Campaign Classic資料庫的概念資料模型。
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5130802f3723311bcd09e21fc405d298923dd20e

---


# 關於架構參考{#about-schema-reference}

本章說明如何設定擴充架構，以擴充Adobe Campaign資料庫的概念資料模型。

如需深入瞭解Campaign內建表格及其互動，請參閱 [Campaign Classic資料模型](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)。

在XML中描述了應用中資料的物理和邏輯結構。 它遵循Adobe Campaign的特定語法，稱為 **架構**。

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

## 結構的語法 {#syntax-of-schemas}

方案的根元素為 **`<srcschema>`**。 它包含** **`<element>`** 和 **`<attribute>`** 子元素。

第一 **`<element>`** 個子元素與圖元的根重合。

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

標 **`<element>`** 記定義實體元素的名稱。 **`<attribute>`** 架構的標籤定義了已連結到的標 **`<element>`** 記中屬性的名稱。

## 模式的標識 {#identification-of-a-schema}

資料架構由其名稱及其命名空間標識。

命名空間可讓您依目標區域對一組結構描述進行分組。 例如， **cus** namespace用於客戶特定的&#x200B;**配置(客戶**)。

>[!CAUTION]
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

模式的標識鍵是使用命名空間和名稱以冒號分隔的字串；例如： **cus:recipient**.
