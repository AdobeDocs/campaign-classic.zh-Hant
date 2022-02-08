---
product: campaign
title: 架構元素和屬性
description: 條件元素
exl-id: 71e98d45-3660-4d86-a5ca-8e55ae5896eb
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 3%

---

# 條件元素 {#condition--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-2}

條件：==EMPTY

## 屬性 {#attributes-2}

* @boolOperator（字串）
* @enabledIf（字串）
* @expr（字串）

## 父母 {#parents-2}

`<sysfilter>`

## 兒童 {#children-2}

無

## 說明 {#description-2}

此元素用於定義篩選條件。

## 使用和使用上下文 {#use-and-context-of-use-2}

一 `<sysfiler>`  元素可包含若幹過濾條件。

## 屬性說明 {#attribute-description-2}

* **boolOperator（字串）**:若 `<conditions>` 定義於  `<sysfilter>` 元素，此屬性允許您將它們組合。 預設情況下，邏輯連結位於 `<condition>` 元素為「AND」。 「@boolOperator」屬性允許您組合「OR」和「AND」類型連結。
* **enabledIf（字串）**:條件激活test。
* **expr（字串）**:XTK表達式。

## 範例 {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```
