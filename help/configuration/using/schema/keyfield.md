---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 7%

---

# 關鍵欄位元素{#keyfield--element}

## 內容模型{#content-model-9}

keyfield:==EMPTY

## 屬性{#attributes-9}

* @xlink(MNTOKEN)
* @xpath(MNTOKEN)

## 父級{#parents-9}

`<key>`  ,  `<dbindex />`

## 子項{#children-9}

無

## 說明 {#description-9}

此元素定義要整合至索引或索引鍵的欄位。

## 屬性說明{#attribute-description-9}

* **xlink(MNTOKEN)**:可讓您自動參照在關係表（N-N連結）的聯接中定義的外鍵。
* **xpath(MNTOKEN)**:元素上索引或鍵的定 `<attribute>`  義。此屬性會接收一個Xpath，該Xpath定義用於定義鍵或索引的架構屬性的路徑。

## 範例 {#examples-}

在索引中選擇「sName」欄位，並在「@name」上選擇Xpath:

```
<keyfield xpath="@name"/>
```
