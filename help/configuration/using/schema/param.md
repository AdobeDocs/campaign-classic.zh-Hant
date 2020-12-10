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
source-wordcount: '174'
ht-degree: 6%

---


# `<param>` 元素  {#param--element}

## 內容模型{#content-model-12}

param:==help

## 屬性{#attributes-12}

* @_operation（字串）
* @desc（字串）
* @enum（字串）
* @inout（字串）
* @label（字串）
* @localized（字串）
* @name(MNTOKEN)
* @namespace(MNTOKEN)
* @type（字串）

## 父代{#parents-12}

`<parameters>`

## 子項{#children-12}

`<help>`

## 說明 {#description-12}

此元素可讓您定義用於呼叫SOAP方法的參數。

## 屬性說明{#attribute-description-12}

* **desc（字串）**:與元素相關的 `<param>` 說明。
* **inout（字串）**:此屬性定義參數是否在SOAP調用的輸入(in)或輸出(out)處。如果未指定此屬性，則預設參數為input(&quot;@inout=in&quot;)。
* **標籤（字串）**: `<param>` 標籤
* **可定位（字串）**:如果已激活，此屬性將告訴收集工具恢復「@label」屬性的值以進行轉換（內部使用）。
* **名稱(MNTOKEN)**:內部名稱  `<param>`
* **type(string)**:此屬性定義元素的類 `<param>` 型

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

## 範例 {#examples-9}

字串類型&quot;serviceName&quot;入站設定的定義：

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
