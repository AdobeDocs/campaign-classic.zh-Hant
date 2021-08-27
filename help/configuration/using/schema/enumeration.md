---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 5%

---

# 分項清單 {#enumeration--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-5}

枚舉：==（help|值）

## 屬性 {#attributes-5}

* @basetype（字串）
* @default（字串）
* @desc（字串）
* @label（字串）
* @name（字串）
* @template（字串）

## 父母 {#parents-5}

`<srcschema>`

## 兒童 {#children-5}

* `<help>`
* `<value>`

## 說明 {#description-5}

此元素可讓我們定義值列舉。 枚舉屬於它在中定義的架構，但可通過其他架構訪問。

## 使用與使用內容 {#use-and-context-of-use-4}

列舉會在架構開始時（在定義主要元素之前）定義。

## 屬性說明 {#attribute-description-5}

* **basetype（字串）**:枚舉中儲存的值的類型。

   可用類型清單：

   * 任何
   * bin
   * blob
   * 布林值
   * 位元組
   * CDATA
   * 日期時間
   * datemetz
   * datetimenotz
   * 日期
   * DOMDocument
   * DOMElement
   * 兩次
   * 列舉
   * 浮點
   * html
   * int64
   * 連結
   * long
   * 備忘錄
   * MNTOKEN
   * 百分比
   * primarykey
   * short
   * 字串
   * 時間
   * 時間盤
   * uuid

* **預設值（字串）**:預設值。預設值也可以是枚舉中定義的值之一。
* **dsc（字串）**:枚舉說明。
* **標籤（字串）**:枚舉標籤。
* **name(string)**:枚舉的內部名稱。
* **範本（字串）**:此屬性定義對由多個結 `<enumeration>` 構共用的元素的引用。定義會自動複製到目前的架構中。

## 範例 {#examples-4}

其值儲存在資料庫中的枚舉值的示例：

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

以預設值列舉的定義：

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
