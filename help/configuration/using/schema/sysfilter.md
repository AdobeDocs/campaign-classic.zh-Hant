---
product: campaign
title: 元素和屬性 — sysfilter元素
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 13%

---

# sysfilter元素 {#sysfilter--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-15}

sysFilter:==condition

## 屬性 {#attributes-15}

無

## 父母 {#parents-15}

`<element>`

## 兒童 {#children-15}

`<condition>`

## 說明 {#description-15}

此元素用於定義篩選器。

## 屬性說明 {#attribute-description-15}

此元素沒有屬性。

## 範例 {#examples-12}

具有屬性上條件的篩選器的@name義：

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
