---
title: 模式特性
seo-title: 模式特性
description: 模式特性
seo-description: null
page-status-flag: never-activated
uuid: ca8eb7af-ef22-403a-8f04-ece5dc903174
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 441e80e1-0559-41fd-83e8-afdf94279e75
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 模式特性{#schema-characteristics}

引用現有表的模式的特徵如下：

* Adobe Campaign不得修改相對於現有表的SQL對象，
* 必須明確指定表和列的名稱，
* 必須聲明索引。

>[!IMPORTANT]
>
>請勿刪除標準收件者表格中的欄位，即使欄位無用亦然。 這可能會在Adobe Campaign資料庫中造成行為錯誤。

## 視圖屬性 {#the-view-attribute}

源架構接受 **srcSchema** 根元素 **的view** 屬性。 在自訂表格中操控Adobe Campaign時，必須使用它。 view= **** &quot;true&quot;屬性會通知資料庫結構更新嚮導忽略此模式。 因此，禁止應用程式將表、其列及其索引與相應模式同步。

當此屬性設定為 **true**&#x200B;時，模式僅用於生成SQL查詢以訪問此表的資料。

## 表和列的名稱 {#names-of-tables-and-columns}

當表更新嚮導建立表時，表和列的名稱將根據各個方案和屬性的名稱自動生成。 但是，通過輸入以下屬性可以強制使用SQL名稱：

* **sqltable** ，在模式的主元素中，指定表，
* **sqlname** ，以指定列。

**範例**:

```
<element label="Individual" name="individual" sqltable="individual">
    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key> 
    <attribute name="id" type="long" length="32" />
    <attribute name="lastName" type="string" length="100" sqlname="Last_Name"/>
    <attribute name="firstName" type="string" length="100" sqlname="First_Name"/>
    <attribute name="email" type="string" length="100"/>
    <attribute name="mobile" type="string" length="100"/>
</element>
```

在此示例中，如果未明確指定表和列的名稱，應用程式將為表使用 **CusIndividual** 、 **lastName** 和 **firstName** 。

在方案中，只能填充現有表的一部分列。 未填入的欄將不可供使用者存取。

## 索引欄位 {#indexed-fields}

從客戶機控制台排序清單記錄時，通過對索引欄位排序可以獲得更好的效能。 在模式中聲明索引使控制台在列標籤左側的排序順序箭頭下顯示帶有紅線的索引欄位，如下所示：

![](assets/s_ncs_integration_mapping_index.png)

在架構中，索引的定義如下：

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

這就是為什麼在匹配方案中聲明自定義表的現有索引非常重要。

為源模式的每個鍵和連結聲明隱式聲明索引。 指定 **noDbIndex=&quot;true&quot;屬性可防止索引聲明** :

**範例**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```

