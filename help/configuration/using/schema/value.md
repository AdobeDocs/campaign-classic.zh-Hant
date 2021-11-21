---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bad7fb4b-43d9-4033-ae0d-cf191d89114b
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 5%

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

此元素可讓您定義枚舉中儲存的值。

## 屬性說明 {#attribute-description-16}

* **applicatedIf（字串）**:此屬性可讓您將分項清單設為選用值。 它接收XTK運算式。
* **desc（字串）**:枚舉值的說明。
* **enabledIf（字串）**:啟用分項清單的條件。
* **img(string)**:連結至「namespace:image_name」表單中列舉的影像。 必須將映像導入應用程式伺服器。
* **標籤（字串）**:枚舉值的標籤。
* **名稱（字串）**:枚舉值的內部名稱。
* **值（字串）**:枚舉值的值。 值的類型是根據枚舉的類型定義的。 如果枚舉為字元字串類型，則它只能包含字元字串類型值。

## 範例 {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
