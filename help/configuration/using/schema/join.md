---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a7ca0300-d250-429c-8ae1-2ae7dee82cf5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 3%

---

# 聯接元素&lt;a0/{#join--element}

## 內容模型{#content-model-7}

join:==EMPTY

## 屬性{#attributes-7}

* @dstFilterExpr（字串）
* @xpath-dst（字串）
* @xpath-src（字串）

## 父級{#parents-7}

`<element>`

## 子項{#children-7}

無

## 說明 {#description-7}

用於定義在SQL表之間建立聯接的欄位。

## 使用與使用內容{#use-and-context-of-use-5}

`<join>`元素只有在父`<element>`元素為「link」類型時才可使用。 這表示父元素必須已宣告「@type=link」屬性。

無需在`<join>`元素中指定遠程表的名稱和命名空間。 需要在父`<element>`中指定。

根據慣例，連結會定義在結構結尾。

如果定義連結類型元素時未指定`<join>`元素，則該連結將自動放置在兩個表的主鍵上。

## 屬性說明{#attribute-description-7}

* **dstFilterExpr（字串）**:此屬性可讓您限制遠端表格中符合條件的值數目。
* **xpath-dst（字串）**:此屬性接收Xpath(遠程表的@name屬性)。
* **xpath-src（字串）**:此屬性會接收Xpath(目前架構中的@name屬性)。

## 範例 {#examples-6}

在當前表的「email」欄位和遠程表的「@compagny-id」欄位之間連結：

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

根據「@country」欄位的內容篩選連結，指向「cus:Country」表格，該欄位必須包含「EN」值：

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
