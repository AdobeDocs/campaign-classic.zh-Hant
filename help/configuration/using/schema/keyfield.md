---
solution: Campaign Classic
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 8%

---


# `<keyfield>` 元素  {#keyfield--element}

## 內容模型{#content-model-9}

keyfield:==EMPTY

## 屬性{#attributes-9}

* @xlink(MNTOKEN)
* @xpath(MNTOKEN)

## 父代{#parents-9}

`<key>`  ,  `<dbindex />`

## 子項{#children-9}

無

## 說明 {#description-9}

此元素定義要整合到索引或鍵中的欄位。

## 屬性說明{#attribute-description-9}

* **xlink(MNTOKEN)**:可讓您自動參照在關係表（N-N連結）的連接中定義的外鍵。
* **xpath(MNTOKEN)**:索引或元素上索引鍵的定 `<attribute>`  義。此屬性接收一個Xpath ，它定義了用於定義索引或索引的架構屬性的路徑。

## 範例 {#examples-}

在「@name」上具有Xpath的索引中選擇「sName」欄位：

```
<keyfield xpath="@name"/>
```
