---
product: campaign
title: 現有表格方案
description: 現有表格方案
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 9%

---

# 現有表格方案{#schema-of-an-existing-table}

![](../../assets/v7-only.svg)

## 概覽 {#overview}

當應用程式需要訪問現有表、SQL視圖或遠程資料庫中的資料時，請使用以下資料在Adobe Campaign建立其模式：

* 表名：使用&quot;sqltable&quot;屬性輸入表的名稱（使用dblink時使用其別名）,
* 方案鍵：引用協調欄位，
* 索引：用於生成查詢，
* XML結構中的欄位及其位置：僅填寫應用程式中使用的欄位，
* 連結：與基的其它表存在連接。

## 實施 {#implementation}

要建立相應的架構，請應用以下階段：

1. 編輯 **[!UICONTROL Administration>Configuration>Data schemas]** ，然後按一下 **[!UICONTROL New]** 。
1. 選擇 **[!UICONTROL Access data from an existing table or an SQL view]** 選項 **[!UICONTROL Next]** 。

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. 選擇表或現有視圖：

   ![](assets/s_ncs_configuration_select_table.png)

1. 調整架構內容以滿足您的需要。

   ![](assets/s_ncs_configuration_view_create_schema.png)

   必須使用上的view=&quot;true&quot;屬性填充架構 `<srcSchema>` 根元素，以便不生成表建立SQL指令碼。

**範例** :

```
<srcSchema name="recipient" namespace="cus" view="true">
  <element name="recipient" sqltable="dbsrv.recipient">
    <key name="email">
      <keyfield xpath="@email"/>
    </key>   
    <attribute name="email" type="string" length="80" sqlname="email"/>
  </element>
</srcSchema>
```

## 存取外部資料庫 {#accessing-an-external-database}

的 **聯合資料存取 — FDA** 選項授予您對儲存在外部資料庫中的資料的訪問權限。

在中詳細說明了訪問外部資料庫中資料的架構上要進行的配置 [此頁](../../installation/using/creating-data-schema.md)。
