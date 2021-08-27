---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 2%

---

# 鍵元素 {#key--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-8}

索引鍵： ==keyfield

## 屬性 {#attributes-8}

* @allowEmptyPart（布林值）
* @applicableIf（字串）
* @internal（布林值）
* @label（字串）
* @name(MNTOKEN)
* @noDbIndex（布林值）

## 父母 {#parents-8}

`<element>`

## 兒童 {#children-8}

`<keyfield>`

## 說明 {#description-8}

此元素可讓您定義用於識別表格中記錄的索引鍵。

表必須至少包含一個鍵。

## 使用與使用內容 {#use-and-context-of-use-6}

規則是在架構的主要元素和索引之後宣告索引鍵。

如果鍵包含多個欄位（即多個`<keyfield>`子項），則稱為複合鍵。 請勿使用複合鍵來定義主鍵。

如果架構的主要元素包含「@autopk=true」屬性，則主鍵是唯一的。 每個架構只能有一個主鍵。

保留前1000個標識符，因此，如果需要為密鑰定義一系列值，則從1000開始。

## 屬性說明 {#attribute-description-8}

* **allowEmptyPart(boolean)**:在複合鍵的情況下，如果激活了此屬性，則如果其至少一個鍵不為空，則它們被視為有效。如果是這種情況，空的概念值是&quot;0&quot;（布林值或所有數值資料類型）。 依預設，需要輸入組成複合鍵的所有鍵。
* **applicableIf（字串）**:此屬性可讓您將索引鍵設為選用。它定義將根據其套用鍵定義的條件。 此屬性會接收XTK運算式。
* **內部（布林值）**:如果已啟用，此屬性可讓Adobe Campaign知道索引鍵為主要。
* **標籤（字串）**:索引鍵的標籤。
* **name(MNTOKEN)**:金鑰的內部名稱。
* **noDbIndex（布林值）**:如果已激活(noDbIndex=&quot;true&quot;)，則與鍵匹配的欄位將不會建立索引。

## 範例 {#examples-------}

複合密鑰的聲明，該密鑰授權&quot;@expr&quot;或&quot;別名&quot;欄位為空：

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

在`<srcschema>`中STRING類型的「Name」欄位上聲明主鍵，以及匹配的SQL查詢：

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
