---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 17%

---

# 幫助元素{#help--element}

## 內容模型{#content-model-6}

幫助：==EMPTY

## 屬性{#attributes-6}

無

## 父級{#parents-6}

`<srcschema>`  ,   `<element>`   ,    `<attribute>`    ,     `<enumeration>`     ,      `<value>`      ,      `<param />`       `<method />`

## 子項{#children-6}

無

## 說明 {#description-6}

此元素可讓您說明`<element>`或`<attribute>`   元素。 它只能包含文本，並以XML儲存在資料庫中。

## 屬性說明{#attribute-description-6}

此元素沒有屬性。

## 範例 {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
