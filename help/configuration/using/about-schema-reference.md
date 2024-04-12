---
product: campaign
title: 開始使用Adobe Campaign中的結構描述
description: 瞭解如何使用方案並延伸Adobe Campaign資料庫的概念資料模型
feature: Schema Extension
role: Data Engineer, Developer
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 1%

---

# 開始使用結構描述 {#about-schema-reference}

## 什麼是結構描述 {#what-is-a-schema}

本章說明如何設定擴充功能綱要，以擴充Adobe Campaign資料庫的概念資料模型。

如需Campaign內建表格及其互動的詳細資訊，請參閱 [Campaign Classic資料模型](about-data-model.md).

在Adobe Campaign中，應用程式中所攜帶資料的實體和邏輯結構會以XML進行說明。 A **綱要** 是與資料庫表格相關聯的XML檔案。 它會定義資料結構，並描述表格的SQL定義：

* 資料表的名稱
* 欄位
* 索引
* 與其他表格的連結

它也會說明用來儲存資料的XML結構：

* 元素和屬性
* 元素的階層
* 元素和屬性型別
* 預設值
* 標籤、說明和其他屬性。

結構描述可讓您定義資料庫中的實體。 每個實體都有一個結構描述。

下圖顯示結構在Adobe Campaign資料系統中的位置：

![](assets/reference_schema_intro.png)

## 結構描述的語法 {#syntax-of-schemas}

結構的根元素為 **`<srcschema>`**. 它包含 **`<element>`** 和 **`<attribute>`** 子元素。

第一個 **`<element>`** 子元素與實體的根一致。

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
>實體的根元素與結構描述同名。

![](assets/s_ncs_configuration_schema_and_entity.png)

此 **`<element>`** 標籤定義圖元元素的名稱。 **`<attribute>`** 架構的標籤會定義 **`<element>`** 連結至的標籤。

## 結構描述的識別 {#identification-of-a-schema}

資料結構是以其名稱和名稱空間來識別。

名稱空間可讓您依感興趣的區域來分組一組結構描述。 例如， **cus** 名稱空間用於客戶特定的設定(**客戶**)。

綱要的識別索引鍵是使用名稱空間和以冒號分隔的名稱所建立的字串；例如： **cus：recipient**.

>[!IMPORTANT]
>
>名稱空間的名稱必須簡潔，而且只能包含符合XML命名規則的授權字元。
>
>識別碼不能以數字字元開頭。
>
>以下名稱空間是保留給操作Adobe Campaign應用程式所需的系統實體說明，不得使用： **xtk**， **nl**， **nms**， **ncm**， **臨時**， **ncl**， **crm**， **xxl**.

