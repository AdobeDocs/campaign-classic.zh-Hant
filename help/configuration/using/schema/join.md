---
product: campaign
title: 結構描述元素和屬性 — 連線元素
description: 連線元素
feature: Schema Extension
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# 連線元素 {#join--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-7}

join：==EMPTY

## 屬性 {#attributes-7}

* @dstFilterExpr （字串）
* @xpath-dst （字串）
* @xpath-src （字串）

## 父項 {#parents-7}

`<element>`

## 子系 {#children-7}

無

## 說明 {#description-7}

可讓您定義在SQL表格之間建立聯結的欄位。

## 使用與使用內容 {#use-and-context-of-use-5}

A `<join>`  元素只能在父項時使用  `<element>`  元素為&#39;link&#39;型別。 這表示父元素必須宣告「@type=link」屬性。

不需要在「 」中指定遠端資料表的名稱和名稱空間 `<join>`  元素。 它們需要在父項中指定  `<element>`.

依照慣例，連結會在結構描述結尾定義。

如果 `<join>` 定義連結型別元素時，未指定元素，連結會自動置於兩個表格的主索引鍵上。

## 屬性說明 {#attribute-description-7}

* **dstFilterExpr （字串）**：此屬性可讓您限制遠端表格中符合資格值的數量。
* **xpath-dst （字串）**：此屬性會接收Xpath (遠端表格@name屬性)。
* **xpath-src （字串）**：此屬性會接收Xpath (@name目前結構描述中的屬性)。

## 範例 {#examples-6}

目前表格的「email」欄位與遠端表格的「@compagny-id」欄位之間的連結：

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

根據「@country」欄位的內容（必須包含「EN」值），篩選指向「cus：Country」表格的連結：

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
