---
solution: Campaign Classic
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 1%

---


# `<srcschema>` 元素  {#srcschema--element}

## 內容模型{#content-model-14}

srcSchema:==(attribute |建立者 |資料 |元素 |枚舉 |說明 |介面 |方法 |修改者)

## 屬性{#attributes-14}

created(datetime)、createdBy-id(long)、desc(string)、entitySchema(string)、extendedSchema(string)、img(string)、implements(string)、labelSingular(string)、lastModified(datetime)、library(string)、mappingBy-id(long)、name(string)、name(string)、nameste, useRecycleBin（布林值）, view（布林值）, xtkschema（字串）

## 父代{#parents-14}

無

## 子項{#children-14}

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

`<srcschema>`是架構的根元素。 它是模式定義的輸入點。

## 使用與使用內容{#use-and-context-of-use-9}

[關於架構引用](../../configuration/using/about-schema-reference.md)和[架構結構](../../configuration/using/schema-structure.md)中提供了架構表示。

## 屬性說明{#attribute-description-14}

* **已建立（日期時間）**:此屬性提供了建立方案的日期和時間資訊。它有「日期時間」表單。 顯示的值取自伺服器。 時間以UTC格式顯示。
* **createdBy-id(long)**:是建立架構的運算子的標識符。
* **desc（字串）**:架構描述
* **entitySchema（字串）**:基本架構，其語法和核准是以(Adobe Campaign的預設值：xtk:srcSchema)。當您儲存目前的架構時，Adobe Campaign會核准其語法，其中架構在@xtkschema屬性中宣告。
* **extendedSchema（字串）**:接收當前模式擴展所基於的現成可用模式的名稱。表單為「namespace:name」。
* **img(string)**:連結到架構的表徵圖（可在架構建立嚮導中定義）。
* **標籤（字串）**:方案標籤。
* **labelSingular(string)**:標籤（單數），以顯示在介面中。
* **lastModified(datetime)**:此屬性提供上次修改的日期和時間資訊。它有「日期時間」表單。 顯示的值取自伺服器。 時間以UTC格式顯示。
* **庫（布林）**:將架構用作庫而非實體。因此，由於&quot;@ref&quot;和&quot;@template&quot;屬性，其他方案可能會引用此方案。
* **mappingType（字串）**:

   * &quot;sql&quot;:資料庫映射
   * &quot;textFile&quot;:文本檔案映射
   * &quot;xmlFile&quot;:XML格式文本檔案映射
   * &quot;binaryFile&quot;:二進位檔案映射

* **modifiedBy-id(long)**:與變更結構的運算子的識別碼相符。
* **name(string)**:唯一方案名稱。
* **namespace(string)**:架構的名稱空間(預設值：nms、xtk、nl)。為項目建立新模式時，建議您使用專用的名稱空間。
* **useRecycleBin（布林值）**:在應用程式中啟動垃圾筒功能。刪除的記錄將放在垃圾筒中，然後再進行最終刪除。 此函式僅在「傳送」模式中可用。
* **view(boolean)**:如果它已激活(@view=&quot;true&quot;)，則模式將用作視圖。資料庫結構更新嚮導將不考慮模式。 此選項主要用於引用外部表。
* **xtkschema（字串）**:定義模式語法的模式的名稱（預設情況下為xtk:srcSchema）。

## 範例 {#examples-11}

`<srcschema>` 「nms:delivery」的出廠模式元素

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
