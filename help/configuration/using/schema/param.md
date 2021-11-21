---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 6%

---

# 參數元素 {#param--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-12}

param:==幫助

## 屬性 {#attributes-12}

* @_operation（字串）
* @desc（字串）
* @enum（字串）
* @inout（字串）
* @label（字串）
* @localizable（字串）
* @name(MNTOKEN)
* @namespace(MNTOKEN)
* @type（字串）

## 父母 {#parents-12}

`<parameters>`

## 兒童 {#children-12}

`<help>`

## 說明 {#description-12}

此元素可讓您定義呼叫SOAP方法的參數。

## 屬性說明 {#attribute-description-12}

* **desc（字串）**:說明與 `<param>` 元素。
* **inout（字串）**:此屬性定義參數是否在SOAP調用的輸入(in)或輸出(out)。 如果未指定此屬性，則預設參數為輸入(&quot;@inout=in&quot;)。
* **標籤（字串）**: `<param>` 標籤
* **可本地化（字串）**:如果已啟動，此屬性會告訴收集工具，以復原「@label」屬性的值，以供翻譯（內部使用）。
* **name(MNTOKEN)**:內部名稱 `<param>`
* **類型（字串）**:此屬性定義 `<param>` 元素

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

## 範例 {#examples-9}

字元字串類型「serviceName」入站設定的定義：

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
