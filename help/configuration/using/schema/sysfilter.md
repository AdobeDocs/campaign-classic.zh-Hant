---
product: campaign
title: 元素和屬性 — sysfilter元素
description: 元素和屬性
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: a0069688-fd05-42e9-91dd-adc10bea3461
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 11%

---

# sysfilter元素 {#sysfilter--element}


## 內容模型 {#content-model-15}

sysFilter：==condition

## 屬性 {#attributes-15}

無

## 父項 {#parents-15}

`<element>`

## 子系 {#children-15}

`<condition>`

## 說明 {#description-15}

此元素可讓您定義篩選器。

## 屬性說明 {#attribute-description-15}

此元素沒有屬性。

## 範例 {#examples-12}

在@name屬性上具有條件的篩選定義：

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
