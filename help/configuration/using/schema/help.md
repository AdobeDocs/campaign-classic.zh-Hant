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
source-wordcount: '47'
ht-degree: 17%

---


# 幫助元素{#help--element}

## 內容模型{#content-model-6}

help:==EMPTY

## 屬性{#attributes-6}

無

## 父代{#parents-6}

`<srcschema>`  、  `<element>`   、   `<attribute>`    、    `<enumeration>`     、     `<value>`           `<param />`、       `<method />`

## 子項{#children-6}

無

## 說明 {#description-6}

此元素可讓您說明`<element>`或`<attribute>`   元素。 它只能包含文本，並儲存在資料庫中的XML中。

## 屬性說明{#attribute-description-6}

此元素沒有屬性。

## 範例 {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
