---
product: campaign
title: 方案特性
description: 方案特性
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 2%

---

# 方案特性{#schema-characteristics}



參照現有表格的綱要特性如下：

* Adobe Campaign不得修改相對於現有表格的SQL物件。
* 必須明確指定資料表和資料行的名稱，
* 必須宣告索引。

>[!IMPORTANT]
>
>請勿刪除內建收件者表格中的欄位，即使這些欄位沒有用處。 這可能會造成Adobe Campaign資料庫中的行為錯誤。

## 檢視屬性 {#the-view-attribute}

來源結構描述接受 **檢視** 屬性 **srcschema** 根元素。 在自訂表格中操作Adobe Campaign時，必須使用它。 此 **view=&quot;true&quot;** attribute會告訴資料庫結構更新精靈忽略此結構描述。 因此，禁止應用程式將表格、其欄位及其索引與對應的綱要同步。

當此屬性設定為 **true**，此結構描述僅用於產生SQL查詢，以存取此資料表的資料。

## 表格和欄的名稱 {#names-of-tables-and-columns}

當表格是由表格更新精靈建立時，表格和欄的名稱會根據個別結構描述和屬性的名稱自動產生。 不過，可以輸入下列屬性來強制使用SQL名稱：

* **sqltable** 在結構描述的主要元素中，若要指定表格，
* **sqlname** 在每個屬性中，指定欄。

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

在此範例中，如果未明確指定表格和欄的名稱，應用程式會使用 **Cusindividual** 對於表格， **姓氏** 和 **名字** 欄位的。

在結構描述中，可能只會填入現有表格的一部分欄。 使用者無法存取未填入的欄。

## 索引欄位 {#indexed-fields}

從使用者端主控台排序清單的記錄時，對索引欄位排序可獲得更好的效能。 在結構描述中宣告索引時，主控台會在欄標籤左側的排序順序箭頭下，以紅線顯示索引欄位，如下所示：

![](assets/s_ncs_integration_mapping_index.png)

在結構描述中，索引的定義如下：

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

這就是為什麼在相符的結構描述中宣告自訂表格的現有索引很重要的原因。

會針對來源結構描述的每個索引鍵和連結宣告以隱含方式宣告索引。 可藉由指定以下專案來避免索引宣告： **noDbIndex=&quot;true&quot;** 屬性：

**範例**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```
