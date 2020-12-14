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
source-wordcount: '89'
ht-degree: 8%

---


# compute-string元素{#compute-string--element}

## 內容模型{#content-model-1}

compute-string:==EMPTY

## 屬性{#attributes-1}

@expr

## 父代{#parents-1}

`<element>`

## 子項{#children-1}

無

## 說明 {#description-1}

`<compute-string>`元素可讓您根據XTK運算式產生字串，以根據數個值在介面中顯示「build」標籤。

## 使用與使用內容{#use-and-context-of-use-1}

如果未定義`<compute-string>`，則預設情況下會輸入`<compute-string>`元素，其中包含方案中主鍵的值。

## 屬性說明{#attribute-description-1}

* **expr（字串）**:XTK和／或Xpath表達式

## 範例 {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

在收件者上計算的字串結果：「John Doe(john.doe@aol.com)」:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
