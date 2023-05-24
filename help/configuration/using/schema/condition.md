---
product: campaign
title: 結構描述元素和屬性 — 條件元素
description: 條件元素
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%

---

# 條件元素 {#condition--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-2}

condition：==EMPTY

## 屬性 {#attributes-2}

* @boolOperator （字串）
* @enabledIf （字串）
* @expr （字串）

## 父項 {#parents-2}

`<sysfilter>`

## 子系 {#children-2}

無

## 說明 {#description-2}

此元素可讓您定義篩選條件。

## 使用與使用內容 {#use-and-context-of-use-2}

一 `<sysfiler>`  元素可包含數個篩選條件。

## 屬性說明 {#attribute-description-2}

* **boolOperator （字串）**：若有多個 `<conditions>` 在同一個  `<sysfilter>` 元素，此屬性可讓您組合它們。 依預設，邏輯連結介於 `<condition>` 元素為「AND」。 「@boolOperator」屬性可讓您合併「OR」和「AND」型別連結。
* **enabledIf （字串）**：條件啟動測試。
* **expr （字串）**：XTK運算式。

## 範例 {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
