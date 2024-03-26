---
product: campaign
title: 元素和屬性 — 值元素
description: 元素和屬性
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 2%

---

# 值元素 {#value--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-16}

value：==help

## 屬性 {#attributes-16}

* @applicableIf （字串）
* @desc （字串）
* @enabledIf （字串）
* @img （字串）
* @label （字串）
* @name （字串）
* @value （字串）

## 父項 {#parents-16}

`<enumeration>`

## 子系 {#children-16}

`<help>`

## 說明 {#description-16}

此元素可讓您定義儲存在分項清單中的值。

## 屬性說明 {#attribute-description-16}

* **appliedIf （字串）**：此屬性可讓您將列舉值設為選用。 它會接收XTK運算式。
* **desc （字串）**：分項清單值的說明。
* **enabledIf （字串）**：啟用分項清單值的條件。
* **img （字串）**：連結至「namespace：image_name」表單中分項清單的影像。 必須將影像匯入至應用程式伺服器。
* **標籤（字串）**：分項清單值的標籤。
* **名稱（字串）**：分項清單值的內部名稱。
* **值（字串）**：分項清單的值。 值的型別是根據分項清單的型別來定義。 如果列舉是字元字串型別，則只能包含字元字串型別值。

## 範例 {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
