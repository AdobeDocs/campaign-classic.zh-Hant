---
product: campaign
title: 結構描述元素和屬性 — param元素
description: 引數元素
feature: Schema Extension
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 9%

---

# 引數元素 {#param--element}


## 內容模型 {#content-model-12}

param：==help

## 屬性 {#attributes-12}

* @_operation （字串）
* @desc （字串）
* @enum （字串）
* @inout （字串）
* @label （字串）
* @localizable （字串）
* @name (MNTOKEN)
* @namespace (MNTOKEN)
* @type （字串）

## 父項 {#parents-12}

`<parameters>`

## 子系 {#children-12}

`<help>`

## 說明 {#description-12}

此元素可讓您定義用於呼叫SOAP方法的引數。

## 屬性說明 {#attribute-description-12}

* **desc （字串）**：與`<param>`專案相關的描述。
* **inout （字串）**：此屬性會定義引數是否在SOAP呼叫的輸入(in)或輸出(out)處。 如果未指定此屬性，預設引數為輸入(&quot;@inout=in&quot;)。
* **標籤（字串）**： `<param>`標籤
* **localizable （字串）**：如果啟用，此屬性會告訴收集工具復原「@label」屬性的值以供翻譯（內部使用）。
* **名稱(MNTOKEN)**： `<param>`的內部名稱
* **型別（字串）**：此屬性定義了`<param>`元素的型別

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

## 範例 {#examples-9}

字元字串型別「serviceName」輸入設定的定義：

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
