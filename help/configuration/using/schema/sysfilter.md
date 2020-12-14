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
source-wordcount: '43'
ht-degree: 18%

---


# sysfilter元素{#sysfilter--element}

## 內容模型{#content-model-15}

sysFilter:==condition

## 屬性{#attributes-15}

無

## 父代{#parents-15}

`<element>`

## 子項{#children-15}

`<condition>`

## 說明 {#description-15}

此元素可讓您定義篩選。

## 屬性說明{#attribute-description-15}

此元素沒有屬性。

## 範例 {#examples-12}

定義具有@name屬性上條件的篩選：

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```
