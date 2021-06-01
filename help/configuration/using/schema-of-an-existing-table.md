---
product: campaign
title: 現有表格方案
description: 現有表格方案
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 9%

---

# 現有表格方案{#schema-of-an-existing-table}

## 概覽 {#overview}

當應用程式需要訪問現有表、SQL視圖或遠程資料庫中的資料時，請使用以下資料在Adobe Campaign中建立其架構：

* 表名：使用&quot;sqltable&quot;屬性輸入表的名稱（使用dblink時具有別名）,
* 方案密鑰：參考調解欄位，
* 索引：用於生成查詢，
* XML結構中的欄位及其位置：僅填寫應用程式中使用的欄位，
* 連結：如果與基的其他表存在連接。

## 實作 {#implementation}

若要建立對應的結構，請套用下列階段：

1. 編輯Adobe Campaign樹的&#x200B;**[!UICONTROL Administration>Configuration>Data schemas]**&#x200B;節點，然後按一下&#x200B;**[!UICONTROL New]** 。
1. 選取&#x200B;**[!UICONTROL Access data from an existing table or an SQL view]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Next]** 。

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. 選擇表或現有視圖：

   ![](assets/s_ncs_configuration_select_table.png)

1. 調整結構內容以符合您的需求。

   ![](assets/s_ncs_configuration_view_create_schema.png)

   必須在`<srcSchema>`根元素上以view=&quot;true&quot;屬性填充架構，才能不生成表建立SQL指令碼。

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

**同盟資料存取 — FDA**&#x200B;選項可讓您存取儲存在外部資料庫中的資料。

[本頁](../../installation/using/creating-data-schema.md)中詳細說明了要在結構上執行以訪問外部資料庫中的資料的配置。
