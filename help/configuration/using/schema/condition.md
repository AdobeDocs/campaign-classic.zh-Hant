---
product: campaign
title: 結構元素和屬性 — 條件元素
description: 條件元素
feature: Schema Extension
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
TQID: 'https://experienceleague.adobe.com/Jx8bLCt1UEqAZDm0cSuexx25js-e5xTsvkeSMzVCUHw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
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
