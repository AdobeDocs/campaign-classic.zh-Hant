---
solution: Campaign Classic
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 3%

---


# 聯接元素{#join--element}

## 內容模型{#content-model-7}

join:==EMPTY

## 屬性{#attributes-7}

* @dstFilterExpr（字串）
* @xpath-dst（字串）
* @xpath-src（字串）

## 父代{#parents-7}

`<element>`

## 子項{#children-7}

無

## 說明 {#description-7}

可讓您定義在SQL表之間建立聯接的欄位。

## 使用與使用內容{#use-and-context-of-use-5}

`<join>`元素僅能在父`<element>`元素為&#39;link&#39;類型時使用。 這表示父元素必須聲明&quot;@type=link&quot;屬性。

不需要在`<join>`元素中指定遠程表的名稱和名稱空間。 必須在父`<element>`中指定這些值。

依慣例，連結會定義在架構的結尾。

如果在定義連結類型元素時未指定`<join>`元素，則連結將自動放置在兩個表的主鍵上。

## 屬性說明{#attribute-description-7}

* **dstFilterExpr（字串）**:此屬性可讓您限制遠端表格中符合資格的值數目。
* **xpath-dst（字串）**:此屬性接收遠程表的Xpath（@name屬性）。
* **xpath-src（字串）**:此屬性接收當前模式中的Xpath（@name屬性）。

## 範例 {#examples-6}

在當前表的「email」欄位和遠程表的「@compagny-id」欄位之間連結：

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

根據必須包含&#39;EN&#39;值的&quot;@country&quot;欄位內容，篩選指向&quot;cus:Country&quot;表格的連結：

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```
