---
product: campaign
title: 架構元素和屬性
description: 鍵場元素
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 2%

---

# 鍵場元素 {#keyfield--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-9}

keyfield:==EMPTY

## 屬性 {#attributes-9}

* @xlink(MNTOKEN)
* @xpath(MNTOKEN)

## 父母 {#parents-9}

`<key>`  ,  `<dbindex />`

## 兒童 {#children-9}

無

## 說明 {#description-9}

此元素定義要整合到索引或鍵中的欄位。

## 屬性說明 {#attribute-description-9}

* **xlink(MNTOKEN)**:用於自動引用在關係表（N-N連結）的聯接中定義的外鍵。
* **xpath(MNTOKEN)**:索引或鍵的定義 `<attribute>`  的子菜單。 此屬性接收一個Xpath，它定義了定義鍵或索引的架構屬性的路徑。

## 範例 {#examples-}

在「@name」上具有Xpath的索引中選擇「sName」欄位：

```
<keyfield xpath="@name"/>
```
