---
product: campaign
title: 結構元素和屬性 — 說明元素
description: 說明元素
feature: Schema Extension
exl-id: 8207868c-25ff-4ca9-afdd-41b324c7ac0d
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 12%

---

# 說明元素 {#help--element}


## 內容模型 {#content-model-6}

help：==EMPTY

## 屬性 {#attributes-6}

無

## 父項 {#parents-6}

`<srcschema>` ， `<element>`   ，   `<attribute>`    ，    `<enumeration>`     ，     `<value>`      ，     `<param />`，      `<method />`

## 子系 {#children-6}

無

## 說明 {#description-6}

此元素可讓您描述`<element>`或`<attribute>`   元素。 它只能包含文字，並儲存在資料庫的XML中。

## 屬性說明 {#attribute-description-6}

此元素沒有屬性。

## 範例 {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```
