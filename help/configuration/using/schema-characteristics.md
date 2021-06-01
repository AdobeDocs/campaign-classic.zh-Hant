---
product: campaign
title: 方案特性
description: 方案特性
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---

# 方案特性{#schema-characteristics}

引用現有表的架構的特點如下：

* Adobe Campaign不得修改相對於現有表的SQL對象，
* 必須顯式指定表和列的名稱，
* 必須聲明索引。

>[!IMPORTANT]
>
>請勿刪除標準收件者表格中的欄位，即使這些欄位毫無用處。 這可能會在Adobe Campaign資料庫中造成行為錯誤。

## 視圖屬性{#the-view-attribute}

源架構接受&#x200B;**srcSchema**&#x200B;根元素的&#x200B;**view**&#x200B;屬性。 在自訂表格中操作Adobe Campaign時，必須使用它。 **view=&quot;true&quot;**&#x200B;屬性告知資料庫結構更新嚮導忽略此架構。 因此，禁止應用程式將表、其列及其索引與相應模式同步。

當此屬性設定為&#x200B;**true**&#x200B;時，該架構僅用於生成SQL查詢以訪問此表的資料。

## 表和列的名稱{#names-of-tables-and-columns}

當表由表更新嚮導建立時，表和列的名稱將根據各個結構和屬性的名稱自動生成。 但可以通過輸入以下屬性來強制使用SQL名稱：

* **** sqltable在架構的主元素內，要指定表，
* **** sqlname（在每個屬性內），以指定列。

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

在此示例中，如果未顯式指定表和列的名稱，則應用程式將使用&#x200B;**CusIndividual**&#x200B;表、**lastName**&#x200B;和&#x200B;**firstName**&#x200B;列。

在結構中，只能填入現有表格的一部分欄。 未填入的欄將無法供使用者存取。

## 索引欄位{#indexed-fields}

從客戶端控制台對清單的記錄進行排序時，通過對索引欄位進行排序可獲得更好的效能。 在架構中聲明索引，使控制台在列標籤左側的排序順序箭頭下顯示索引欄位，並顯示紅線，如下所示：

![](assets/s_ncs_integration_mapping_index.png)

在架構中，索引的定義如下：

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

因此，在相符的架構中宣告自訂表格的現有索引非常重要。

為源架構的每個鍵和連結聲明隱式聲明索引。 通過指定&#x200B;**noDbIndex=&quot;true&quot;**&#x200B;屬性，可以阻止索引聲明：

**範例**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```
