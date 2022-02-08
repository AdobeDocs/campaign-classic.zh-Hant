---
product: campaign
title: 架構元素和屬性
description: param element（參數元素）
exl-id: d8960a2e-6900-4346-9f06-e7dd9d7b5139
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 2%

---

# param element（參數元素） {#param--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-12}

參數：==幫助

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

此元素用於定義用於調用SOAP方法的參數。

## 屬性說明 {#attribute-description-12}

* **desc（字串）**:描述 `<param>` 的子菜單。
* **inout（字串）**:此屬性定義參數是否位於SOAP調用的輸入(in)或輸出(out)。 如果未指定此屬性，則預設參數為輸入(「@inout=in」)。
* **標籤（字串）**: `<param>` 標籤
* **可本地化（字串）**:如果激活了該屬性，則此屬性將告訴收集工具恢復「@label」屬性的值以進行轉換（內部使用）。
* **名稱(MNTOKEN)**:內部名稱 `<param>`
* **類型（字串）**:此屬性定義 `<param>` 元素

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

## 範例 {#examples-9}

字串類型的「serviceName」入站設定的定義：

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```
