---
product: campaign
title: 結構元素和屬性 — 關鍵元素
description: 關鍵元素
feature: Schema Extension
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 1%

---

# 關鍵元素 {#key--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-8}

key：==keyfield

## 屬性 {#attributes-8}

* @allowEmptyPart （布林值）
* @applicableIf （字串）
* @internal （布林值）
* @label （字串）
* @name (MNTOKEN)
* @noDbIndex （布林值）

## 父項 {#parents-8}

`<element>`

## 子系 {#children-8}

`<keyfield>`

## 說明 {#description-8}

此元素可讓您定義用來識別表格中記錄的索引鍵。

表格必須至少有一個索引鍵。

## 使用與使用內容 {#use-and-context-of-use-6}

作為規則，索引鍵會在結構描述的主要元素和索引之後宣告。

如果金鑰包含數個欄位（亦即數個欄位），則該金鑰稱為「複合」 `<keyfield>` 子項)。 請勿使用複合索引鍵來定義主索引鍵。

如果結構描述的主要元素包含「@autopk=true」屬性，則主索引鍵是唯一的。 每個結構描述只能有一個主索引鍵。

前1000個識別碼是保留的，因此，如果需要為索引鍵定義值的範圍，請從1000開始。

## 屬性說明 {#attribute-description-8}

* **allowEmptyPart （布林值）**：在使用複合金鑰的情況下，如果已啟用此屬性，則在其中至少一個金鑰非空白時，系統會將複合金鑰視為有效。 如果是這種情況，空的概念值為「0」（布林值或適用於所有型別的數值資料）。 依預設，需要輸入組成複合鍵的所有鍵。
* **appliedIf （字串）**：此屬性可讓您將金鑰設為選用。 它會定義套用索引鍵定義的條件。 此屬性會接收XTK運算式。
* **內部（布林值）**：如果已啟動，此屬性可讓Adobe Campaign知道索引鍵是主要金鑰。
* **標籤（字串）**：索引鍵的標籤。
* **名稱(MNTOKEN)**：索引鍵的內部名稱。
* **noDbIndex （布林值）**：如果已啟動(noDbIndex=&quot;true&quot;)，則符合索引鍵的欄位將不會編制索引。

## 範例 {#examples-------}

授權空白「@expr」或「alias」欄位的複合金鑰宣告：

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

在URL中STRING型別的「Name」欄位上的主索引鍵宣告 `<srcschema>`  和相符的SQL查詢：

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
