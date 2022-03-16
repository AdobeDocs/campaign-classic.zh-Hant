---
product: campaign
title: 元素和屬性 — 值元素
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 3%

---

# 值元素 {#value--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-16}

值：==幫助

## 屬性 {#attributes-16}

* @applicableIf（字串）
* @desc（字串）
* @enabledIf（字串）
* @img（字串）
* @label（字串）
* @name（字串）
* @value（字串）

## 父母 {#parents-16}

`<enumeration>`

## 兒童 {#children-16}

`<help>`

## 說明 {#description-16}

此元素用於定義在枚舉中儲存的值。

## 屬性說明 {#attribute-description-16}

* **appliatedIf（字串）**:此屬性允許您使枚舉值成為可選值。 它接收XTK表達式。
* **desc（字串）**:枚舉值的說明。
* **enabledIf（字串）**:用於激活枚舉值的條件。
* **img（字串）**:連結到&quot;namespace:image_name&quot;表單中枚舉的映像。 必須將映像導入到應用程式伺服器。
* **標籤（字串）**:枚舉值的標籤。
* **名稱（字串）**:枚舉值的內部名稱。
* **值（字串）**:枚舉值的值。 值類型根據枚舉類型定義。 如果枚舉為字串類型，則它只能包含字串類型值。

## 範例 {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
