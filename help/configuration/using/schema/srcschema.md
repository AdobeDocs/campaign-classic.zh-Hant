---
product: campaign
title: 元素和屬性 — srcschema元素
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---

# srcschema元素 {#srcschema--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-14}

srcSchema:==（屬性） |建立者 |資料 |元素 |枚舉 |幫助 |介面 |方法 |修改者)

## 屬性 {#attributes-14}

created(datetime)、createdBy-id(long)、desc(string)、entitySchema(string)、extendedSchema(string)、img(string)、implements(string)、labelSingural(string)、lastModified(datetime)、library(boolean)、mppingBy-id(long)、name(sting(sting)、name(string)、name(sting, useRecycleBin（布爾）、view（布爾）、xtkschema（字串）

## 父母 {#parents-14}

無

## 兒童 {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## 說明 {#description-14}

的 `<srcschema>` 是架構的根元素。 它是模式定義的輸入點。

## 使用和使用上下文 {#use-and-context-of-use-9}

在中提供架構演示 [關於架構引用](../../../configuration/using/about-schema-reference.md) 和 [架構結構](../../../configuration/using/schema-structure.md)。

## 屬性說明 {#attribute-description-14}

* **已建立（日期時間）**:此屬性提供有關建立方案的日期和時間的資訊。 它有一個「日期時間」表單。 顯示的值是從伺服器獲取的。 時間以UTC格式顯示。
* **createdBy-id(long)**:是建立架構的運算子的標識符。
* **desc（字串）**:架構描述
* **entitySchema（字串）**:語法和批准所基於的基本架構(預設情況下，對於Adobe Campaign:xtk:srcSchema)。 保存當前架構時，Adobe Campaign將使用@xtkschema屬性中聲明的架構來批准其語法。
* **extendedSchema（字串）**:接收當前架構擴展所基於的現成架構的名稱。 表單為&quot;namespace:name&quot;。
* **img（字串）**:連結到架構的表徵圖（可以在架構建立嚮導中定義）。
* **標籤（字串）**:「架構」標籤。
* **labelSingular（字串）**:標籤（單數），用於在介面中顯示。
* **lastModified(datetime)**:此屬性提供有關上次修改的日期和時間的資訊。 它有一個「日期時間」表單。 顯示的值是從伺服器獲取的。 時間以UTC格式顯示。
* **庫（布爾型）**:將架構用作庫而不是實體。 因此，由於「@ref」和「@template」屬性，此架構可能被其他架構引用。
* **mappingType（字串）**:

   * &quot;sql&quot;:資料庫映射
   * &quot;textFile&quot;:文本檔案映射
   * &quot;xmlFile&quot;:XML格式文本檔案映射
   * &quot;binaryFile&quot;:二進位檔案映射

* **modifiedBy-id（長）**:匹配更改了架構的運算子的標識符。
* **名稱（字串）**:唯一架構名稱。
* **命名空間（字串）**:架構的命名空間(預設：nms、xtk、nl)。 為項目建立新架構時，建議您使用專用命名空間。
* **useRecycleBin（布爾型）**:激活應用程式中的垃圾特徵。 刪除的記錄將放在垃圾箱中，然後再進行最終刪除。 此函式僅在「傳遞」模式下可用。
* **視圖（布爾型）**:如果激活(@view=&quot;true&quot;)，則將使用該架構作為視圖。 資料庫結構更新嚮導將不考慮架構。 此選項主要用於引用外部表。
* **xtkschema（字串）**:定義架構語法的架構的名稱（預設情況下為xtk:srcSchema）。

## 範例 {#examples-11}

`<srcschema>` 「nms:delivery」框外模式的元素

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
