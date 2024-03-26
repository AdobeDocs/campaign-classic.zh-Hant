---
product: campaign
title: 結構元素和屬性 — keyfield元素
description: keyfield元素
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 4%

---

# keyfield元素 {#keyfield--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-9}

keyfield：==EMPTY

## 屬性 {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## 父項 {#parents-9}

`<key>`  ，  `<dbindex />`

## 子系 {#children-9}

無

## 說明 {#description-9}

此元素會定義要整合至索引或索引鍵中的欄位。

## 屬性說明 {#attribute-description-9}

* **xlink (MNTOKEN)**：可讓您自動參照在連線中定義之關係表格（N-N連結）的外部索引鍵。
* **xpath (MNTOKEN)**：索引或索引鍵的定義 `<attribute>`  元素。 此屬性會接收Xpath，定義定義索引鍵或索引的結構描述屬性的路徑。

## 範例 {#examples-}

在索引中選取「sName」欄位(其中Xpath位於「@name」上)：

```
<keyfield xpath="@name"/>
```
