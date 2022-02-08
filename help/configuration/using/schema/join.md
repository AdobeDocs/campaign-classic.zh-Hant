---
product: campaign
title: 架構元素和屬性
description: 聯接元素
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 1%

---

# 聯接元素 {#join--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-7}

聯接：==空

## 屬性 {#attributes-7}

* @dstFilterExpr（字串）
* @xpath-dst（字串）
* @xpath-src（字串）

## 父母 {#parents-7}

`<element>`

## 兒童 {#children-7}

無

## 說明 {#description-7}

用於定義在SQL表之間建立聯接的欄位。

## 使用和使用上下文 {#use-and-context-of-use-5}

A `<join>`  僅當父項  `<element>`  元素為「link」類型。 這意味著父元素必須聲明「@type=link」屬性。

無需在 `<join>`  的子菜單。 需要在父級中指定  `<element>`。

按照約定，在架構的末尾定義連結。

如果 `<join>` 定義連結類型元素時未指定元素，連結將自動置於兩個表的主鍵上。

## 屬性說明 {#attribute-description-7}

* **dstFilterExpr（字串）**:此屬性允許您限制遠程表中合格值的數量。
* **xpath-dst（字串）**:此屬性接收Xpath(遠程表的@name屬性)。
* **xpath-src（字串）**:此屬性接收Xpath(當前架構中的@name屬性)。

## 範例 {#examples-6}

當前表的「email」欄位與遠程表的「@compagny-id」欄位之間的連結：

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

根據「@country」欄位的內容篩選指向「cus:Country」表的連結，該欄位必須包含「EN」值：

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
