---
solution: Campaign Classic
product: campaign
title: 綱要特性
description: 綱要特性
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---


# 綱要特性{#schema-characteristics}

引用現有表的模式的特徵如下：

* Adobe Campaign不得修改相對於現有表的SQL對象，
* 必須明確指定表和列的名稱，
* 必須聲明索引。

>[!IMPORTANT]
>
>請勿刪除標準收件者表格中的欄位，即使欄位無用亦然。 這可能會在Adobe Campaign資料庫中造成行為錯誤。

## 視圖屬性{#the-view-attribute}

源架構接受&#x200B;**srcSchema**&#x200B;根元素的&#x200B;**view**&#x200B;屬性。 在自訂表格中操控Adobe Campaign時，必須使用它。 **view=&quot;true&quot;**&#x200B;屬性會通知資料庫結構更新嚮導忽略此模式。 因此，禁止應用程式將表、其列及其索引與相應模式同步。

當此屬性設定為&#x200B;**true**&#x200B;時，模式僅用於生成SQL查詢以訪問此表的資料。

## 表和列的名稱{#names-of-tables-and-columns}

當表更新嚮導建立表時，表和列的名稱將根據各個方案和屬性的名稱自動生成。 但是，通過輸入以下屬性可以強制使用SQL名稱：

* **** sqltable在模式的主元素中，要指定表，
* **在** 每個屬性中指定列的sqlname。

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

在此示例中，如果未明確指定表和列的名稱，應用程式將使用&#x200B;**CusIndividual**&#x200B;表、**lastName**&#x200B;和&#x200B;**firstName**&#x200B;列。

在方案中，只能填充現有表的一部分列。 未填入的欄將不可供使用者存取。

## 索引欄位{#indexed-fields}

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

為源模式的每個鍵和連結聲明隱式聲明索引。 通過指定&#x200B;**noDbIndex=&quot;true&quot;**&#x200B;屬性，可以防止索引聲明：

**範例**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```

