---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 8%

---

# 條件元素 {#condition--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-2}

條件： ==EMPTY

## 屬性 {#attributes-2}

* @boolOperator（字串）
* @enabledIf（字串）
* @expr（字串）

## 父母 {#parents-2}

`<sysfilter>`

## 兒童 {#children-2}

無

## 說明 {#description-2}

此元素可讓您定義篩選條件。

## 使用與使用內容 {#use-and-context-of-use-2}

一 `<sysfiler>`  元素可包含數個篩選條件。

## 屬性說明 {#attribute-description-2}

* **boolOperator（字串）**:若數 `<conditions>` 定義於相同  `<sysfilter>` 元素，此屬性可讓您結合這些元素。 依預設，邏輯連結介於 `<condition>` 元素為「AND」。 「@boolOperator」屬性可讓您結合「OR」和「AND」類型連結。
* **enabledIf（字串）**:條件啟動測試。
* **expr（字串）**:XTK運算式。

## 範例 {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
