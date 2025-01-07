---
product: campaign
title: 結構元素和屬性 — 條件元素
description: 條件元素
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 5%

---

# 條件元素 {#condition--element}


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

一個`<sysfiler>`元素可以包含數個篩選條件。

## 屬性說明 {#attribute-description-2}

* **boolOperator （字串）**：如果在相同的`<sysfilter>`元素中定義了多個`<conditions>`，則此屬性可讓您組合它們。 依預設，邏輯連結介於`<condition>`個元素之間為&quot;AND&quot;。 「@boolOperator」屬性可讓您合併「OR」和「AND」型別連結。
* **enabledIf （字串）**：條件啟動測試。
* **expr （字串）**： XTK運算式。

## 範例 {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
