---
product: campaign
title: 元素和屬性 — 計算字串元素
description: 計算字串元素
feature: Schema Extension
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 5%

---

# 計算字串元素 {#compute-string--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-1}

計算字串：==EMPTY

## 屬性 {#attributes-1}

@expr

## 父項 {#parents-1}

`<element>`

## 子系 {#children-1}

無

## 說明 {#description-1}

此 `<compute-string>` 元素可讓您根據XTK運算式產生字串，以根據數個值在介面中顯示「建置」標籤。

## 使用與使用內容 {#use-and-context-of-use-1}

當否 `<compute-string>` 已定義， `<compute-string>` 在預設情況下，會使用架構中主索引鍵的值輸入元素。

## 屬性說明 {#attribute-description-1}

* **expr （字串）**： XTK和/或Xpath運算式

## 範例 {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

對收件者計算的字串結果：「John Doe (john.doe@aol.com)」：

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
