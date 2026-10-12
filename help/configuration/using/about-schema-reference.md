---
product: campaign
title: 開始使用Adobe Campaign中的結構描述
description: 瞭解如何使用方案並延伸Adobe Campaign資料庫的概念資料模型
feature: Schema Extension
role: Developer
level: Intermediate, Experienced
exl-id: f36a1b01-a002-4a21-9255-ea78b5f173fe
TQID: 'https://experienceleague.adobe.com/ikQVjdkvhTM-361S7mcpRYsuhpqjHxX-Y-9wdRCYldg'
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
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a97306b73a2b577841e6f24536c62b2526e9fda9
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 3%
---
# 開始使用結構描述 {#about-schema-reference}

## 什麼是結構描述 {#what-is-a-schema}

本章說明如何設定擴充功能綱要，以擴充Adobe Campaign資料庫的概念資料模型。

如需Campaign內建表格及其互動的詳細資訊，請參閱[Campaign Classic資料模型](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/datamodel){target="_blank"} （Campaign v8檔案）。

在Adobe Campaign中，應用程式中所攜帶資料的實體和邏輯結構會以XML進行說明。 **結構描述**&#x200B;是與資料庫表格關聯的XML檔案。 它會定義資料結構，並描述表格的SQL定義：

* 資料表的名稱
* 欄位
* 索引
* 與其他表格的連結

它也會說明用來儲存資料的XML結構：

* 元素和屬性
* 元素的階層
* 元素和屬性型別
* 預設值
* 標籤、說明和其他屬性。

結構描述可讓您定義資料庫中的實體。 每個實體都有一個結構描述。

下圖顯示結構在Adobe Campaign資料系統中的位置：

![](assets/reference_schema_intro.png)

作為從Campaign v7轉變到v8的一部分，Campaign Classic檔案集已簡化並重新組織。 Campaign v8檔案集中現在提供常見功能。 若要瞭解結構描述的語法和識別，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}。

[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/schemas){target=_blank}
