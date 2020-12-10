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
source-wordcount: '316'
ht-degree: 2%

---


# `<key>` 元素  {#key--element}

## 內容模型{#content-model-8}

key:==keyfield

## 屬性{#attributes-8}

* @allowEmptyPart（布林值）
* @applicableIf（字串）
* @internal（布林值）
* @label（字串）
* @name(MNTOKEN)
* @noDbIndex（布林）

## 父代{#parents-8}

`<element>`

## 子項{#children-8}

`<keyfield>`

## 說明 {#description-8}

此元素可讓您定義用於識別表格中記錄的索引鍵。

表必須至少有一個鍵。

## 使用與使用內容{#use-and-context-of-use-6}

作為規則，鍵在模式的主要元素和索引之後聲明。

如果密鑰包含多個欄位（即多個`<keyfield>`子項），則該密鑰稱為複合密鑰。 請勿使用複合鍵來定義主鍵。

如果架構的主要元素包含&quot;@autopk=true&quot;屬性，則主鍵是唯一的。 每個方案只能有一個主鍵。

保留前1000個標識符，因此如果需要為鍵定義一系列值，則從1000開始。

## 屬性說明{#attribute-description-8}

* **allowEmptyPart（布林值）**:在複合鍵的情況下，如果此屬性被激活，則如果其至少一個鍵不為空，則它們的鍵被視為有效。如果是這種情況，空的概念值是&quot;0&quot;（布林值或所有數值資料類型）。 預設情況下，需要輸入組成複合密鑰的所有密鑰。
* **appliableIf（字串）**:此屬性可讓您將索引鍵設為選用。它定義了將應用密鑰定義的條件。 此屬性接收XTK表達式。
* **內部（布林值）**:如果啟用，此屬性可讓Adobe Campaign知道金鑰是主要金鑰。
* **標籤（字串）**:索引鍵標籤。
* **名稱(MNTOKEN)**:索引鍵的內部名稱。
* **noDbIndex（布林值）**:如果它已激活(noDbIndex=&quot;true&quot;)，則不對與鍵匹配的欄位編製索引。

## 範例 {#examples-------}

複合密鑰的聲明，該密鑰授權&quot;@expr&quot;或&quot;alias&quot;欄位為空：

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

`<srcschema>`中STRING類型的&quot;Name&quot;欄位和匹配的SQL查詢上的主鍵聲明：

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
