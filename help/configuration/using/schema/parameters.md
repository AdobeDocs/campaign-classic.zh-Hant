---
product: campaign
title: 結構元素和屬性 — 引數元素
description: parameters元素
feature: Schema Extension
exl-id: 54538c3e-3232-4bf7-a09c-dacf0f072be5
TQID: 'https://experienceleague.adobe.com/tZyI-rIbEifWdgcO80ni6lSHinH0IEeM8UrHFAUpnFs'
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
source-wordcount: '48'
ht-degree: 12%
---
# parameters元素 {#parameters--element}


## 內容模型 {#content-model-13}

parameters：==param

## 屬性 {#attributes-13}

無

## 父項 {#parents-13}

`<method>`

## 子系 {#children-13}

`<param>`

## 說明 {#description-13}

此元素定義了一組`<parameter>`元素。

## 使用與使用內容 {#use-and-context-of-use-8}

此專案是必要的，即使是`<method>`專案的單一`<param>`子專案也是如此。

## 屬性說明 {#attribute-description-13}

無

## 範例 {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```
