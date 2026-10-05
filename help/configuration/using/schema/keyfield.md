---
product: campaign
title: 結構元素和屬性 — keyfield元素
description: keyfield元素
feature: Schema Extension
exl-id: fb0862f9-5dcc-49f2-b99b-9822aaf3a680
TQID: 'https://experienceleague.adobe.com/tVWLlgg97dREZZHvUW81FhDVhS-uNvUHlbhH0YBrAdY'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
    internal-label: Schema extension
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 6%
---
# keyfield元素 {#keyfield--element}


## 內容模型 {#content-model-9}

keyfield：==EMPTY

## 屬性 {#attributes-9}

* @xlink (MNTOKEN)
* @xpath (MNTOKEN)

## 父項 {#parents-9}

`<key>`  ,  `<dbindex />`

## 子系 {#children-9}

無

## 說明 {#description-9}

此元素會定義要整合至索引或索引鍵中的欄位。

## 屬性說明 {#attribute-description-9}

* **xlink (MNTOKEN)**：可讓您自動參考關聯資料表（N-N連結）之聯結中所定義的外來索引鍵。
* **xpath (MNTOKEN)**： `<attribute>`專案上索引或索引鍵的定義。 此屬性會接收Xpath，定義定義索引鍵或索引的結構描述屬性的路徑。

## 範例 {#examples-}

在索引中選取「sName」欄位（其中Xpath位於「@name」上）：

```
<keyfield xpath="@name"/>
```
