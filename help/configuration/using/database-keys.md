---
product: campaign
title: 資料結構描述中的金鑰管理
description: 瞭解資料結構中的金鑰管理
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: faf63c8f-9d10-43c1-a990-91361594af9f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 2%

---

# 結構描述中的金鑰管理 {#management-of-keys}

每個與資料結構描述關聯的表格必須至少有一個索引鍵來識別表格中的記錄。

從資料結構描述的主要元素中宣告索引鍵。

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

當索引鍵是結構描述中第一個要填入的索引鍵，或是包含設定為「true」的`internal`屬性時，就稱為「主索引鍵」。

下列規則適用於機碼：

* 索引鍵可參考表格中的一或多個欄位
* 每個索引鍵定義都會以隱含方式宣告唯一索引。 可透過將`noDbIndex`屬性設定為「true」來防止在索引鍵上建立索引。

>[!NOTE]
>
>* 作為標準，索引鍵是在定義索引後，從結構描述的主要元素宣告的元素。
>
>* 金鑰是在表格對應期間建立（標準或FDA），Adobe Campaign會尋找唯一索引。

**範例**：

* 將金鑰新增至電子郵件地址和城市：

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </key>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

  產生的結構描述：

  ```sql
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
     <dbindex name="email" unique="true">      
       <keyfield xpath="@email"/>      
       <keyfield xpath="location/@city"/>    
     </dbindex>    
  
     <key name="email">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="location/@city"/>    
     </key>    
  
     <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
     <element label="Location" name="location">      
       <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
     </element>  
    </element>
  </schema>
  ```

* 在「id」名稱欄位中新增主要或內部索引鍵：

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <key name="id" internal="true">
        <keyfield xpath="@id"/> 
      </key>
  
      <key name="email" noDbIndex="true">
        <keyfield xpath="@email"/> 
      </key>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

  產生的結構描述：

  ```sql
  <schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
    <element name="recipient" sqltable="CusRecipient">    
      <key name="email">      
        <keyfield xpath="@email"/>    
      </key>    
  
      <dbindex name="id" unique="true">      
        <keyfield xpath="@id"/>    
      </dbindex>    
  
      <key internal="true" name="id">      
       <keyfield xpath="@id"/>    
      </key>    
  
      <attribute label="Identifier" name="id" sqlname="iRecipientId" type="long"/>    
      <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
    </element>
  </schema>
  ```

## 自動增量索引鍵 {#auto-incremental-key}

大部分Adobe Campaign表格的主要索引鍵是由資料庫引擎自動產生的32位元長整數。 索引鍵值的計算取決於產生在整個資料庫中唯一數字的序列（預設為&#x200B;**XtkNewId** SQL函式）。 插入記錄時會自動輸入金鑰的內容。

增量索引鍵的優點在於，它提供不可修改的技術索引鍵用於表格之間的聯結。 此外，此索引鍵使用雙位元組整數，因此不會佔用太多記憶體。

您可以在來源結構描述中指定要與&#x200B;**pkSequence**&#x200B;屬性搭配使用的序列名稱。 如果來源結構描述中未指定此屬性，則會使用&#x200B;**XtkNewId**&#x200B;預設序列。 應用程式對&#x200B;**nms：broadLog**&#x200B;和&#x200B;**nms：trackingLog**&#x200B;結構描述使用專用序列（分別為&#x200B;**NmsBroadLogId**&#x200B;和&#x200B;**NmsTrackingLogId**），因為這些是包含最多記錄的表格。

從ACC 18.10開始，**XtkNewId**&#x200B;不再是現成可用結構描述中順序的預設值。 您現在可以使用專用序列來建置方案或擴充現有方案。

>[!IMPORTANT]
>
>建立新結構描述或在結構描述擴充期間，您需要為整個結構描述保留相同的主要索引鍵序列值(@pkSequence)。

在Adobe Campaign結構描述中參考的序列（例如&#x200B;**NmsTrackingLogId**）必須與SQL函式相關聯，該函式會傳回引數中的識別碼數目（以逗號分隔）。 此函式必須稱為&#x200B;**GetNew** XXX **Ids**，其中&#x200B;**XXX**&#x200B;是序列的名稱（例如&#x200B;**GetNewNmsTrackingLogIds**）。 檢視&#x200B;**datakit/nms/eng/sql/**&#x200B;目錄中隨應用程式提供的&#x200B;**postgres-nms.sql**、**mssql-nms.sql**&#x200B;或&#x200B;**oracle-nms.sql**&#x200B;檔案，以復原每個資料庫引擎的&#39;NmsTrackingLogId&#39;序列建立範例。

若要宣告唯一金鑰，請在資料結構描述的主要元素上填入&#x200B;**autopk**&#x200B;屬性（值為「true」）。

**範例**：

在來源結構描述中宣告增量金鑰：

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

產生的結構描述：

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" autopk="true" pkSequence="XtkNewId" sqltable="CusRecipient"> 
    <dbindex name="id" unique="true">
      <keyfield xpath="@id"/>
    </dbindex>

    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key>

    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iRecipientId" type="long"/>
  </element>
</schema>
```

除了索引鍵及其索引的定義外，名為「id」的數值欄位已新增至擴充架構，以包含自動產生的主要索引鍵。

>[!IMPORTANT]
>
>主鍵設為0的記錄會在建立表格時自動插入。 此記錄用於避免外部聯結，這些外部聯結在磁碟區表格上無效。 依預設，所有外部索引鍵都是以值0初始化，如此一來，當資料專案未填入時，就可以在聯結上傳回結果。


## 了解更多

瀏覽以下連結以瞭解更多資訊：

* [開始使用結構描述](about-schema-reference.md)
* [方案結構](schema-structure.md)
* [資料庫對應](database-mapping.md)
* [連結管理](database-links.md)
* [促銷活動資料模型](about-data-model.md)
