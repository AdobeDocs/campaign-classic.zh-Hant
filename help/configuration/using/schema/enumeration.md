---
product: campaign
title: 結構描述元素和屬性 — 列舉元素
description: 列舉元素
feature: Schema Extension
exl-id: 4cd67278-2623-4508-9a9f-9007c6a5f8ac
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 8%

---

# 列舉元素 {#enumeration--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-5}

分項清單：==(help| value)

## 屬性 {#attributes-5}

* @basetype （字串）
* @default （字串）
* @desc （字串）
* @label （字串）
* @name （字串）
* @template （字串）

## 父項 {#parents-5}

`<srcschema>`

## 子系 {#children-5}

* `<help>`
* `<value>`

## 說明 {#description-5}

此元素可讓我們定義值列舉。 分項清單屬於其定義所在的結構描述，但可透過其他結構描述存取。

## 使用與使用內容 {#use-and-context-of-use-4}

列舉是在結構描述的開頭定義（在定義主要元素之前）。

## 屬性說明 {#attribute-description-5}

* **basetype （字串）**：列舉中儲存的值的型別。

  可用型別清單：

   * 任何
   * 紙匣
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
   * 雙精度浮點數
   * 列舉
   * 浮點數
   * html
   * int64
   * 連結
   * 長
   * 備忘錄
   * MNTOKEN
   * 百分比
   * 主要金鑰
   * 短
   * 字串
   * 時間
   * 時間範圍
   * uuid

* **預設（字串）**：預設值。 預設值也可以是列舉中定義的其中一個值。
* **desc （字串）**：列舉描述。
* **標籤（字串）**：列舉標籤。
* **名稱（字串）**：列舉的內部名稱。
* **範本（字串）**：此屬性會定義數個結構描述共用之`<enumeration>`元素的參考。 定義會自動複製到目前的結構描述中。

## 範例 {#examples-4}

值儲存在資料庫中的列舉值範例：

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

具有預設值的分項清單定義：

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```
