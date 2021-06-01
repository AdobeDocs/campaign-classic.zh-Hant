---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 8%

---

# compute-string元素{#compute-string--element}

## 內容模型{#content-model-1}

compute-string:==EMPTY

## 屬性{#attributes-1}

@expr

## 父級{#parents-1}

`<element>`

## 子項{#children-1}

無

## 說明 {#description-1}

`<compute-string>`元素可讓您根據XTK運算式產生字串，以根據數個值在介面中顯示「已建置」標籤。

## 使用與使用內容{#use-and-context-of-use-1}

未定義`<compute-string>`時，預設會輸入`<compute-string>`元素，並包含架構中主鍵的值。

## 屬性說明{#attribute-description-1}

* **expr（字串）**:XTK和/或Xpath運算式

## 範例 {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

對收件者計算的字串結果：「無名氏(john.doe@aol.com)」：

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
