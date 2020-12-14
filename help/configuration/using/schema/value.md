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
source-wordcount: '147'
ht-degree: 5%

---


# 值元素{#value--element}

## 內容模型{#content-model-16}

value:==help

## 屬性{#attributes-16}

* @applicableIf（字串）
* @desc（字串）
* @enabledIf（字串）
* @img（字串）
* @label（字串）
* @name（字串）
* @value（字串）

## 父代{#parents-16}

`<enumeration>`

## 子項{#children-16}

`<help>`

## 說明 {#description-16}

此元素可讓您定義枚舉中儲存的值。

## 屬性說明{#attribute-description-16}

* **appliableIf（字串）**:此屬性可讓您使枚舉值成為可選值。它接收XTK表達式。
* **desc（字串）**:枚舉值的說明。
* **enabledIf（字串）**:條件，以啟動枚舉值。
* **img(string)**:連結至&quot;namespace:image_name&quot;表單中列舉的影像。映像必須導入到應用程式伺服器。
* **標籤（字串）**:枚舉值的標籤。
* **name(string)**:枚舉值的內部名稱。
* **值（字串）**:枚舉值的值。值的類型是根據枚舉的類型定義的。 如果枚舉為字串類型，則它只能包含字串類型值。

## 範例 {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
