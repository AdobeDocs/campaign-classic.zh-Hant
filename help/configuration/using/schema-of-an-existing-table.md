---
product: campaign
title: 現有表格方案
description: 現有表格方案
feature: Custom Resources
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 10%

---

# 現有表格方案{#schema-of-an-existing-table}

## 概覽 {#overview}

當應用程式需要存取現有表格、SQL檢視或遠端資料庫的資料時，請使用下列資料在Adobe Campaign中建立其綱要：

* 表格名稱：輸入具有「sqltable」屬性的表格名稱（使用dblink時具有別名）。
* 方案索引鍵：參考調解欄位，
* 索引：用於產生查詢，
* 這些欄位及其在XML結構中的位置：僅填寫應用程式中使用的欄位，
* 連結：如果與基底的其他表格有聯結。

## 實施 {#implementation}

若要建立對應的綱要，請套用下列階段：

1. 編輯 **[!UICONTROL Administration>Configuration>Data schemas]** Adobe Campaign樹的節點，然後按一下 **[!UICONTROL New]** .
1. 選取 **[!UICONTROL Access data from an existing table or an SQL view]** 選項並按一下 **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. 選擇表格或現有檢視：

   ![](assets/s_ncs_configuration_select_table.png)

1. 調整結構描述內容以符合您的需求。

   ![](assets/s_ncs_configuration_view_create_schema.png)

   結構描述必須以view=&quot;true&quot;屬性填入， `<srcSchema>` 根元素，以便不產生表格建立SQL指令碼。

**範例** ：

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

此 **同盟資料存取 — FDA** 選項可讓您存取儲存在外部資料庫中的資料。

中詳細說明了要在結構描述上執行以存取外部資料庫中資料的設定 [此頁面](../../installation/using/creating-data-schema.md).
