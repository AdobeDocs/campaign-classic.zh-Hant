---
product: campaign
title: 架構元素和屬性 — 枚舉元素
description: 枚舉元素
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 2%

---

# 枚舉元素 {#enumeration--element}

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

此元素使我們能夠定義值枚舉。 枚舉屬於在中定義的架構，但可以通過其他架構訪問它。

## 使用和使用上下文 {#use-and-context-of-use-4}

枚舉在架構的開始（在定義主元素之前）定義。

## 屬性說明 {#attribute-description-5}

* **basetype（字串）**:枚舉中儲存的值的類型。

   可用類型清單：

   * 任意
   * 賓
   * blob
   * 布爾
   * 位元組
   * CDATA
   * 日期
   * 日期表
   * 日期
   * 日期
   * 域文檔
   * DOMElement
   * 雙
   * 枚舉
   * 浮
   * html
   * int64
   * 連結
   * 長
   * 備忘錄
   * MNTOKEN
   * 百分比
   * 主鍵
   * 短
   * 字串
   * 時間
   * 時隙
   * uuid

* **預設（字串）**:預設值。 預設值也可以是枚舉中定義的值之一。
* **desc（字串）**:枚舉說明。
* **標籤（字串）**:枚舉標籤。
* **名稱（字串）**:枚舉的內部名稱。
* **模板（字串）**:此屬性定義對 `<enumeration>` 由多個架構共用的元素。 定義將自動複製到當前架構中。

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

具有預設值的枚舉的定義：

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
