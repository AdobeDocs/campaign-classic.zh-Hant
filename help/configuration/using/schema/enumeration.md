---
solution: Campaign Classic
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 5%

---


# 枚舉元素{#enumeration--element}

## 內容模型{#content-model-5}

枚舉：==(help| value)

## 屬性{#attributes-5}

* @basetype（字串）
* @default（字串）
* @desc（字串）
* @label（字串）
* @name（字串）
* @template（字串）

## 父代{#parents-5}

`<srcschema>`

## 子項{#children-5}

* `<help>`
* `<value>`

## 說明 {#description-5}

此元素可讓我們定義值列舉。 枚舉屬於它在中定義的模式，但可通過其他模式訪問它。

## 使用與使用內容{#use-and-context-of-use-4}

枚舉是在架構開始時（在定義主元素之前）定義的。

## 屬性說明{#attribute-description-5}

* **basetype(string)**:枚舉中儲存的值的類型。

   可用類型清單：

   * 任何
   * 賓
   * blob
   * 布林值
   * 位元組
   * CDATA
   * 日期時間
   * datetimetz
   * datetimenotz
   * 日期
   * DOMDocument
   * DOMElement
   * 雙倍
   * 列舉
   * 浮水
   * html
   * int64
   * link
   * long
   * 備忘錄
   * MNTOKEN
   * 百分比
   * primarykey
   * 短
   * 字串
   * 時間
   * 時間平移
   * uid

* **default(string)**:預設值。預設值也可以是枚舉中定義的值之一。
* **desc（字串）**:枚舉說明。
* **標籤（字串）**:枚舉標籤。
* **name(string)**:枚舉的內部名稱。
* **範本（字串）**:此屬性定義對由多個方案 `<enumeration>` 共用的元素的引用。定義會自動複製到當前模式。

## 範例 {#examples-4}

其值儲存在資料庫中的枚舉值示例：

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

定義具有預設值的枚舉：

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
