---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 1%

---

# srschema元素{#srcschema--element}

## 內容模型{#content-model-14}

srcSchema:==(attribute) | createdBy |資料 |元素 |枚舉 |幫助 |介面 |方法 | modifiedBy)

## 屬性{#attributes-14}

created(datetime), createdBy-id(long), desc(string), entitySchema(string), extendedSchema(string), img(string), implements(string), label(string), lastModified(string), library(boolean), mappingType(string), modifiedBy-id(long), name(string), namespace(string), useRecycleBin(boolean), view(boolean), xtkschema(string)

## 父級{#parents-14}

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

`<srcschema>`是架構的根元素。 它是架構定義的輸入點。

## 使用與使用內容{#use-and-context-of-use-9}

[關於架構引用](../../../configuration/using/about-schema-reference.md)和[架構結構](../../../configuration/using/schema-structure.md)中提供了架構演示。

## 屬性說明{#attribute-description-14}

* **已建立(datetime)**:此屬性提供有關架構建立日期和時間的資訊。有「日期時間」表單。 顯示的值取自伺服器。 時間以UTC格式顯示。
* **createdBy-id(long)**:是建立架構的運算子的識別碼。
* **dsc（字串）**:方案說明
* **entitySchema(string)**:基本結構，其語法和核准是根據(Adobe Campaign預設為：xtk:srcSchema)。儲存目前的結構時，Adobe Campaign會以在@xtkschema屬性中宣告的結構來核准其語法。
* **extendedSchema(string)**:接收目前架構擴充功能所根據之現成可用架構的名稱。表單為「namespace:name」。
* **img(string)**:連結到架構的表徵圖（可在架構建立嚮導中定義）。
* **標籤（字串）**:方案標籤。
* **labelSingular（字串）**:標籤（單數）。
* **lastModified(datetime)**:此屬性提供上次修改的日期和時間資訊。有「日期時間」表單。 顯示的值取自伺服器。 時間以UTC格式顯示。
* **程式庫（布林值）**:將結構用作程式庫，而非實體。因此，由於「@ref」和「@template」屬性，其他結構可能會參考此結構。
* **mappingType(string)**:

   * &quot;sql&quot;:資料庫映射
   * &quot;textFile&quot;:文本檔案映射
   * &quot;xmlFile&quot;:XML格式文本檔案映射
   * &quot;binaryFile&quot;:二進位檔案映射

* **modifiedBy-id(long)**:匹配更改架構的運算子的標識符。
* **name(string)**:唯一架構名稱。
* **namespace（字串）**:架構的名稱空間(預設值：nms, xtk, nl)。為專案建立新結構時，建議您使用專用的命名空間。
* **useRecycleBin（布林值）**:在應用程式中啟用垃圾桶功能。刪除的記錄會放在垃圾桶中，然後才進行最終刪除。 此函式僅可在「傳送」模式中使用。
* **檢視（布林值）**:如果已啟動(@view=&quot;true&quot;)，則會將結構用作檢視。資料庫結構更新嚮導將不考慮該架構。 此選項主要用於參考外部表。
* **xtkschema(string)**:定義架構文法的架構名稱（預設為xtk:srcSchema）。

## 範例 {#examples-11}

`<srcschema>` 「nms:delivery」的元素

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
