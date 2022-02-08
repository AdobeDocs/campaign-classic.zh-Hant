---
product: campaign
title: 元素和屬性
description: 計算字串元素
exl-id: 8a079bb8-3f53-4144-a065-5bd402649cc7
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '88'
ht-degree: 6%

---

# 計算字串元素 {#compute-string--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-1}

compute-string:==EMPTY

## 屬性 {#attributes-1}

@expr

## 父母 {#parents-1}

`<element>`

## 兒童 {#children-1}

無

## 說明 {#description-1}

的 `<compute-string>` 元素使您能夠基於XTK表達式生成字串，以便根據多個值在介面中顯示「built」標籤。

## 使用和使用上下文 {#use-and-context-of-use-1}

不 `<compute-string>` 定義， `<compute-string>` 預設情況下，元素與架構中主鍵的值一起輸入。

## 屬性說明 {#attribute-description-1}

* **expr（字串）**:XTK和/或Xpath表達式

## 範例 {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

在收件人上計算的字串的結果：「無名氏(john.doe@aol.com)」：

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```
