---
solution: Campaign Classic
product: campaign
title: 現有資料表的綱要
description: 現有資料表的綱要
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 9%

---


# 現有資料表的綱要{#schema-of-an-existing-table}

## 概觀 {#overview}

當應用程式需要存取現有表格、SQL檢視或遠端資料庫資料時，請使用下列資料在Adobe Campaign中建立其架構：

* 表名：在&quot;sqltable&quot;屬性中輸入表的名稱（使用dblink時使用其別名）,
* 方案鍵：引用協調欄位，
* 索引：用於生成查詢，
* XML結構中的欄位及其位置：只填寫應用程式中使用的欄位，
* 連結：是否與基的其他表存在連接。

## 實施{#implementation}

要建立相應的方案，請應用以下階段：

1. 編輯Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Administration>Configuration>Data schemas]**&#x200B;節點，然後按一下&#x200B;**[!UICONTROL New]**。
1. 選擇&#x200B;**[!UICONTROL Access data from an existing table or an SQL view]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. 選擇表或現有視圖：

   ![](assets/s_ncs_configuration_select_table.png)

1. 調整架構內容以符合您的需求。

   ![](assets/s_ncs_configuration_view_create_schema.png)

   必須在`<srcSchema>`根元素上以view=&quot;true&quot;屬性填充模式，才能不生成表建立SQL指令碼。

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

**同盟資料存取- FDA**&#x200B;選項允許您訪問儲存在外部資料庫中的資料。

要在結構上執行的訪問外部資料庫中資料的配置在[本頁](../../installation/using/creating-data-schema.md)中有詳細說明。
