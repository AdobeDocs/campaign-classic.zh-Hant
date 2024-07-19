---
product: campaign
title: 資料庫對應
description: 資料庫對應
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 3%

---

# 資料庫對應{#database-mapping}

此頁面](schema-structure.md)中描述的範例結構描述[的SQL對應會產生下列XML檔案：

```sql
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">
  <enumeration basetype="byte" name="gender">    
    <value label="Not specified" name="unknown" value="0"/>    
    <value label="Male" name="male" value="1"/>    
    <value label="Female" name="female" value="2"/> 
  </enumeration>  

  <element name="recipient" sqltable="CusRecipient">    
    <attribute desc="Recipient email address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

結構描述的根專案變更為&#x200B;**`<srcschema>`**&#x200B;為&#x200B;**`<schema>`**。

這種其他型別的檔案會自動從來源結構描述產生，並僅被簡稱為結構描述。

SQL名稱是根據元素名稱和型別自動決定的。

SQL命名規則如下：

* **table**：結構描述名稱空間和名稱的串連

  在我們的範例中，資料表的名稱是透過&#x200B;**sqltable**&#x200B;屬性中結構描述的主要元素輸入的：

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **欄位**：前面有根據型別定義之前置詞的元素名稱：&#39;i&#39;代表整數，&#39;d&#39;代表雙精度，&#39;s&#39;代表字串，&#39;ts&#39;代表日期等。

  欄位名稱是透過每個型別&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**&#x200B;的&#x200B;**sqlname**&#x200B;屬性輸入的：

  ```sql
  <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
  ```

>[!NOTE]
>
>可以從來源結構描述多載SQL名稱。 若要這麼做，請在相關元素上填入「sqltable」或「sqlname」屬性。

用來建立從擴充綱要產生之表格的SQL命令檔如下：

```sql
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

SQL欄位限制如下：

* 數值和日期欄位中沒有null值
* 數值欄位已初始化為0

## XML欄位 {#xml-fields}

依預設，任何&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`** -typed專案都會對應到資料結構描述表格的SQL欄位。 不過，您可以用XML來參照此欄位，而非SQL，這表示資料會儲存在包含所有XML欄位值的表格之備忘錄欄位(「mData」)中。 這些資料的儲存是觀察結構描述結構的XML檔案。

若要在XML中填入欄位，您必須將值為「true」的&#x200B;**xml**&#x200B;屬性新增到相關專案。

**範例**：以下是兩個XML欄位使用範例。

* 多行註解欄位：

  ```sql
  <element name="comment" xml="true" type="memo" label="Comment"/>
  ```

* HTML格式的資料說明：

  ```sql
  <element name="description" xml="true" type="html" label="Description"/>
  ```

  「html」型別可讓您將HTML內容儲存在CDATA標籤中，並在Adobe Campaign使用者端介面中顯示特殊的HTML編輯檢查。

使用XML欄位來新增欄位，而不需修改資料庫的實體結構。 另一個優點是，您使用的資源較少（配置給SQL欄位的大小、限制每個表格的欄位數等）。 不過，請注意，您無法索引或篩選XML欄位。

## 索引欄位 {#indexed-fields}

索引可讓您最佳化應用程式中使用的SQL查詢效能。

從資料結構描述的主要元素宣告索引。

```sql
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

索引遵循下列規則：

* 索引可以參考表格中的一或多個欄位
* 如果&#x200B;**unique**&#x200B;屬性包含「true」值，則所有欄位中的索引都可以是唯一的（以避免重複）
* 索引的SQL名稱是由表格的SQL名稱和索引的名稱所決定

>[!NOTE]
>
>* 作為標準，索引是從結構描述的主要元素宣告的第一個元素。
>
>* 索引是在表格對應期間自動建立（標準或FDA）。

**範例**：

* 新增索引至電子郵件地址和城市：

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="email">
        <keyfield xpath="@email"/> 
        <keyfield xpath="location/@city"/> 
      </dbindex>
  
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
      <element name="location" label="Location">
        <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
      </element>
    </element>
  </srcSchema>
  ```

* 新增唯一索引至「id」名稱欄位：

  ```sql
  <srcSchema name="recipient" namespace="cus">
    <element name="recipient">
      <dbindex name="id" unique="true">
        <keyfield xpath="@id"/> 
      </dbindex>
  
      <dbindex name="email">
        <keyfield xpath="@email"/> 
      </dbindex>
  
      <attribute name="id" type="long" label="Identifier"/>
      <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    </element>
  </srcSchema>
  ```

## 了解更多

瀏覽以下連結以瞭解更多資訊：

* [開始使用結構描述](about-schema-reference.md)
* [方案結構](schema-structure.md)
* [金鑰管理](database-keys.md)
* [連結管理](database-links.md)
* [促銷活動資料模型](about-data-model.md)