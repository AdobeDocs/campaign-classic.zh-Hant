---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 18%

---

# sysfilter元件 {#sysfilter--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-15}

sysFilter:==條件

## 屬性 {#attributes-15}

無

## 父母 {#parents-15}

`<element>`

## 兒童 {#children-15}

`<condition>`

## 說明 {#description-15}

此元素可讓您定義篩選器。

## 屬性說明 {#attribute-description-15}

此元素沒有屬性。

## 範例 {#examples-12}

在屬性上具有條件的篩選器@name定：

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
