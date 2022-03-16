---
product: campaign
title: 架構元素和屬性 — 關鍵元素
description: 鍵元素
exl-id: 3d0ef574-27a3-40f2-91a0-70e9583d9980
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# 鍵元素 {#key--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-8}

鍵：==keyfield

## 屬性 {#attributes-8}

* @allowEmptyPart（布爾值）
* @applicableIf（字串）
* @internal（布爾值）
* @label（字串）
* @name(MNTOKEN)
* @noDbIndex（布爾值）

## 父母 {#parents-8}

`<element>`

## 兒童 {#children-8}

`<keyfield>`

## 說明 {#description-8}

此元素允許您定義用於標識表中記錄的鍵。

表必須至少有一個鍵。

## 使用和使用上下文 {#use-and-context-of-use-6}

通常，鍵在模式和索引的主元素後聲明。

如果鍵包括多個欄位(即多個 `<keyfield>` 孩子)。 不要使用複合鍵定義主鍵。

如果架構的主元素包含「@autopk=true」屬性，則主鍵是唯一的。 每個架構只能有一個主鍵。

保留前1000個標識符，因此，如果需要為鍵定義值範圍，則從1000開始。

## 屬性說明 {#attribute-description-8}

* **allowEmptyPart（布爾值）**:在複合鍵的情況下，如果激活了此屬性，則當其至少一個鍵不為空時，這些鍵將被視為有效。 如果是這種情況，則空概念值為&quot;0&quot;（布爾值或所有類型的數字資料）。 預設情況下，需要輸入組成複合鍵的所有鍵。
* **appliatedIf（字串）**:此屬性允許您使鍵成為可選項。 它定義了將應用關鍵定義的條件。 此屬性接收XTK表達式。
* **內部（布爾型）**:如果激活了該鍵，則此屬性使Adobe Campaign知道該鍵是主鍵。
* **標籤（字串）**:鍵的標籤。
* **名稱(MNTOKEN)**:密鑰的內部名稱。
* **noDbIndex（布爾）**:如果已激活(noDbIndex=&quot;true&quot;)，則不會為與密鑰匹配的欄位編製索引。

## 範例 {#examples-------}

授權「@expr」或「別名」欄位為空的複合鍵的聲明：

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

在中STRING類型的「名稱」欄位上聲明主鍵 `<srcschema>`  和匹配的SQL查詢：

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```
