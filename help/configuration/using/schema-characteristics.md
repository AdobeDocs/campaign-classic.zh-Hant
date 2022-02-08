---
product: campaign
title: 方案特性
description: 方案特性
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---

# 方案特性{#schema-characteristics}

![](../../assets/common.svg)

引用現有表的架構的特徵如下：

* Adobe Campaign不得修改相對於現有表的SQL對象，
* 必須顯式指定表和列的名稱，
* 必須聲明索引。

>[!IMPORTANT]
>
>請勿刪除內置收件人表中的欄位，即使這些欄位無用。 這可能導致Adobe Campaign資料庫中的行為錯誤。

## 視圖屬性 {#the-view-attribute}

源架構接受 **視圖** 屬性 **src架構** 根元素。 在自定義表中操作Adobe Campaign時，必須使用它。 的 **view=&quot;true&quot;** 屬性指示資料庫結構更新嚮導忽略此模式。 因此，禁止應用程式將表、其列及其索引與相應的架構同步。

當此屬性設定為 **真**，該模式僅用於生成SQL查詢以訪問此表的資料。

## 表和列的名稱 {#names-of-tables-and-columns}

當表由表更新嚮導建立時，表和列的名稱將基於各個方案和屬性的名稱自動生成。 但是，可以通過輸入以下屬性來強制使用SQL名稱：

* **sqltable** 在架構的主元素中，要指定表，
* **sqlname** 指定列。

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

在本示例中，如果未顯式指定表和列的名稱，則應用程式將使用 **定制** 桌子， **姓氏** 和 **名字** 的雙曲餘切值。

在架構中，只能填充現有表的部分列。 未填充的列將不能由用戶訪問。

## 索引欄位 {#indexed-fields}

當從客戶端控制台對清單的記錄進行排序時，通過對索引欄位進行排序可以獲得更好的效能。 在架構中聲明索引使控制台在列標籤左側的排序順序箭頭下顯示索引欄位，如下所示：

![](assets/s_ncs_integration_mapping_index.png)

在架構中，索引定義如下：

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

因此，在匹配架構中聲明自定義表的現有索引非常重要。

為源架構的每個鍵和連結聲明隱式聲明索引。 通過指定 **noDbIndex=&quot;true&quot;** 屬性：

**範例**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```
