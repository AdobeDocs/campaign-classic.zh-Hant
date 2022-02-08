---
product: campaign
title: 資料庫對應
description: 資料庫對應
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '1974'
ht-degree: 0%

---

# 資料庫對應{#database-mapping}

![](../../assets/v7-only.svg)

我們示例架構的SQL映射提供了以下XML文檔：

```
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

## 說明 {#description}

架構的根元素不再 **`<srcschema>`**&#x200B;但 **`<schema>`**。

這將我們帶到另一種類型的文檔，該文檔是從源架構自動生成的，簡稱為架構。 此架構將由Adobe Campaign應用程式使用。

SQL名稱會根據元素名稱和類型自動確定。

SQL命名規則如下：

* 表：架構命名空間和名稱的串聯

   在本示例中，表的名稱是通過 **sqltable** 屬性：

   ```
   <element name="recipient" sqltable="CusRecipient">
   ```

* 欄位：元素的名稱，前面是根據類型定義的前置詞（「i」表示整數，「d」表示雙精度，「s」表示字串，「ts」表示日期等）

   通過 **sqlname** 每種類型的屬性 **`<attribute>`** 和 **`<element>`**:

   ```
   <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
   ```

>[!NOTE]
>
>SQL名稱可以從源架構重載。 為此，請在相關元素上填充「sqltable」或「sqlname」屬性。

用於建立從擴展架構生成的表的SQL指令碼如下：

```
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

SQL欄位約束如下：

* 數字和日期欄位中沒有空值，
* 數字欄位已初始化為0。

## XML欄位 {#xml-fields}

預設情況下，任何類型 **`<attribute>`** 和 **`<element>`** 元素映射到資料模式表的SQL欄位。 但是，您可以在XML中引用此欄位，而不是SQL ，這意味著資料儲存在包含所有XML欄位值的表的備注欄位(「mData」)中。 這些資料的儲存是一個觀察架構結構的XML文檔。

要填充XML中的欄位，必須添加 **xml** 值為&quot;true&quot;的屬性。

**示例**:下面是兩個XML欄位使用示例。

* 多行注釋欄位：

   ```
   <element name="comment" xml="true" type="memo" label="Comment"/>
   ```

* 以HTML格式描述資料：

   ```
   <element name="description" xml="true" type="html" label="Description"/>
   ```

   「html」類型允許您將HTML內容儲存在CDATA標籤中，並在Adobe Campaign客戶端介面中顯示特殊的HTML編輯檢查。

使用XML欄位，您可以添加欄位，而無需修改資料庫的物理結構。 另一個優勢是，使用的資源較少（分配給SQL欄位的大小、每個表的欄位數限制等）。

主要缺點是無法對XML欄位進行索引或篩選。

## 索引欄位 {#indexed-fields}

索引使您能夠優化應用程式中使用的SQL查詢的效能。

從資料模式的主元素聲明索引。

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

索引遵循以下規則：

* 索引可以引用表中的一個或多個欄位。
* 索引可以是所有欄位中唯一的（以避免重複），如果 **獨特** attribute包含值「true」。
* 索引的SQL名稱由表的SQL名稱和索引的名稱確定。

>[!NOTE]
>
>作為標準，索引是從架構的主元素聲明的第一個元素。

>[!NOTE]
>
>索引在表映射（標準或FDA）期間自動建立。

**範例**:

* 向電子郵件地址和城市添加索引：

   ```
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

* 將唯一索引添加到「id」名稱欄位：

   ```
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

## 密鑰管理 {#management-of-keys}

表必須至少具有一個用於標識表中記錄的鍵。

從資料模式的主元素聲明密鑰。

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

鍵遵循以下規則：

* 鍵可以引用表中的一個或多個欄位。
* 當鍵是要填充的架構中的第一個鍵或包含 **內部** 值為&quot;true&quot;的屬性。
* 為每個鍵定義隱式聲明一個唯一索引。 通過添加 **noDbIndex** 值為&quot;true&quot;的屬性。

>[!NOTE]
>
>作為標準，鍵是在定義索引後從架構的主元素聲明的元素。

>[!NOTE]
>
>鍵是在表映射（標準或FDA）期間建立的，Adobe Campaign會查找唯一的索引。

**範例**:

* 向電子郵件地址和城市添加密鑰：

   ```
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

   生成的架構：

   ```
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

* 在「id」名稱欄位中添加主鍵或內部鍵：

   ```
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

   生成的架構：

   ```
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

### 自動增量密鑰 {#auto-incremental-key}

大多數Adobe Campaign表的主鍵是由資料庫引擎自動生成的32位長整數。 鍵值的計算取決於序列(預設情況下， **XtkNewId** SQL函式)生成整個資料庫中唯一的數字。 在插入記錄時自動輸入密鑰的內容。

增量密鑰的優點是它為表之間的連接提供了不可修改的技術密鑰。 此外，此鍵不佔用太多記憶體，因為它使用雙位元組整數。

可以在源方案中指定與 **pk序列** 屬性。 如果源架構中未提供此屬性， **XtkNewId** 將使用預設序列。 應用程式使用專用序列 **nms:broadLog** 和 **nms：跟蹤日誌** 模式(S)**NmsBroadLogId** 和 **NmsTrackingLogId** 因為這些表包含的記錄最多。

從ACC 18.10起， **XtkNewId** 不再是現成模式中序列的預設值。 現在，您可以構建模式或使用專用序列擴展現有模式。

>[!IMPORTANT]
>
>建立新架構或在架構擴展期間，需要為整個架構保留相同的主鍵序列值(@pkSequence)。

>[!NOTE]
>
>Adobe Campaign架構中引用的序列(**NmsTrackingLogId** 例如)必須與SQL函式關聯，該函式返回參數中ID的數量（以逗號分隔）。 必須調用此函式 **新建** XXX **ID**，也請參見Wiki頁。 **XXX** 是序列的名稱(**GetNewNmsTrackingLogId** 例如)。 查看 **postgres-nms sql**。 **mssql-nms-sql** 或 **oracle-nms.sql** 與應用程式一起提供的檔案 **datakit/nms/eng/sql/** 目錄，以恢復每個資料庫引擎的「NmsTrackingLogId」序列建立示例。

要聲明唯一鍵，請填充 **奧托普** 資料架構的主元素上的屬性（帶有值「true」）。

**範例**:

在源架構中聲明增量密鑰：

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient" autopk="true">
  ...
  </element>
</srcSchema>
```

生成的架構：

```
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

除了鍵及其索引的定義之外，還向擴展架構中添加了一個名為&quot;id&quot;的數字欄位，以包含自動生成的主鍵。

>[!IMPORTANT]
>
>在建立表時，主鍵設定為0的記錄將自動插入。 此記錄用於避免對卷表無效的外連接。 預設情況下，所有外鍵都使用值0初始化，以便在未填充資料項時，始終可以在連接中返回結果。

## 連結：表之間的關係 {#links--relation-between-tables}

連結描述一個表和另一個表之間的關聯。

各種類型的關聯（稱為「基數」）如下：

* 基數1-1:源表的一個出現最多可以具有目標表的一個相應出現。
* 基數1-N:源表的一次出現可以具有目標表的多個對應出現，但目標表的一次出現最多可以具有源表的一次對應出現。
* 基數N-N:源表的一個實例可以具有目標表的多個相應實例，反之亦然。

在介面中，由於關係的表徵圖，您可以輕鬆地區分不同類型的關係。

對於與市場活動表/資料庫的聯接關係：

* ![](assets/join_with_campaign11.png) :基數1-1 例如，在收件人和當前訂單之間。 一次只能與當前訂單表的一次出現相關。
* ![](assets/externaljoin11.png) :基數1-1，外部連接。 例如，在接受國和其國家之間。 收件人只能與表國家/地區的一次事件相關。 將不保存國家/地區表的內容。
* ![](assets/join_with_campaign1n.png) :基數1-N例如，在收件人和預訂表之間。 收件人可以與預訂表上的幾個事件相關。

對於使用聯合資料庫訪問的連接關係：

* ![](assets/join_fda_11.png) :基數1-1
* ![](assets/join_fda_1m.png) :基數1-N

有關FDA表的詳細資訊，請參閱 [訪問外部資料庫](../../installation/using/about-fda.md)。

必須在包含通過主元素連結的表的外鍵的架構中聲明連結：

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

連結遵循以下規則：

* 連結的定義是在 **連結** — 類型 **`<element>`** 具有以下屬性：

   * **名稱**:源表中連結的名稱，
   * **目標**:目標架構的名稱，
   * **標籤**:連結標籤，
   * **修訂連結** （可選）:目標架構中反向連結的名稱（預設情況下自動推導）,
   * **完整性** （可選）:源表的出現與目標表的出現之間的參照完整性。 可能的值如下：

      * **定義**:如果源事件不再被目標事件引用，則可以刪除它，
      * **正**:刪除源實例將初始化指向目標實例的連結的鍵（預設模式），此類完整性將初始化所有外鍵，
      * **自己**:刪除源事件會導致目標事件的刪除，
      * **下載**:與 **自己** （刪除時）或重複（重複時）,
      * **中性**:什麼也不做。
   * **修訂完整性** （可選）:目標架構上的完整性（可選，預設為&quot;normal&quot;）,
   * **rev基數** （可選）:使用值&quot;single&quot;填充1-1類型（預設為1-N）的基數。
   * **外部連接** （可選）:強制外部連接
   * **revExternalJoin** （可選）:強制反向連接上的外連接


* 連結將源表中的一個或多個欄位引用到目標表。 組成連接的欄位( `<join>`  元素)，因為預設情況下使用目標架構的內部鍵自動推斷這些元素。
* 索引自動添加到擴展模式中連結的外鍵。
* 連結由兩個半連結組成，其中從源架構聲明第一個連結，在目標架構的擴展架構中自動建立第二個連結。
* 如果 **外部連接** 屬性被添加，並且值為&quot;true&quot;（在PostgreSQL中受支援）。

>[!NOTE]
>
>作為標準，連結是在架構的末尾聲明的元素。

### 示例1 {#example-1}

1-N與「cus:company」架構表的關係：

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

生成的架構：

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>
    ...
    <element label="Company" name="company" revLink="recipient" target="cus:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of 'Company' link (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

連結定義由組成連接的欄位來補充，即在目標架構中主鍵及其XPath(「@id」)，在架構中外鍵及其XPath(「@company-id」)。

外鍵自動添加到與目標表中的關聯欄位具有相同特性的元素中，並使用以下命名約定：目標架構的名稱，後跟關聯欄位的名稱（本例中為「company-id」）。

目標的擴展架構(「cus:company」):

```
<schema mappingType="sql" name="company" namespace="cus" xtkschema="xtk:schema">  
  <element name="company" sqltable="CusCompany" autopk="true"> 
    <dbindex name="id" unique="true">     
      <keyfield xpath="@id"/>    
    </dbindex>   
    <key internal="true" name="id">      
      <keyfield xpath="@id"/>    
    </key>
    ...
    <attribute desc="Internal primary key" label="Primary key" name="id" sqlname="iCompanyId" type="long"/>
    ...
    <element belongsTo="cus:recipient" integrity="define" label="Contact" name="recipient" revLink="company" target="nms:recipient" type="link" unbound="true">      
      <join xpath-dst="@company-id" xpath-src="@id"/>    
    </element>
  </element>
</schema>
```

添加了指向「cus:recipient」表的反向連結，其參數如下：

* **名稱**:自動從源架構的名稱推導（可以強制使用源架構的連結定義中的「revLink」屬性）
* **修訂連結**:反向連結名稱
* **目標**:連結架構的鍵（&quot;cus:recipient&quot;架構）
* **解除**:連結聲明為1-N基數的集合元素（預設情況下）
* **完整性**:預設情況下，「define」（源架構上的連結定義中的「revIntegrity」屬性可強制使用）。

### 示例2 {#example-2}

在本示例中，我們將聲明指向「nms:address」架構表的連結。 連接是外部連接，並顯式填充有收件人的電子郵件地址和連結表(「nms:address」)的「@address」欄位。

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient"> 
    ...
    <element integrity="neutral" label="Info about email" name="emailInfo" revIntegrity="neutral" revLink="recipient" target="nms:address" type="link" externalJoin="true">      
      <join xpath-dst="@address" xpath-src="@email"/>
    </element>
  </element>
</srcSchema>
```

### 示例3 {#example-3}

與「cus:extension」架構表的1-1關係：

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### 示例4 {#example-4}

連結到資料夾（&quot;xtk:folder&quot;架構）:

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

預設值返回在「DefaultFolder(&#39;nmsFolder&#39;)」函式中輸入的第一個合格參數類型檔案的標識符。

### 示例5 {#example-5}

在本示例中，我們希望在連結（「company」到「cus:company」架構）上建立一個鍵 **x連結** 屬性和(「email」)表的欄位：

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <key name="companyEmail"> 
      <keyfield xpath="@email"/>
      <keyfield xlink="company"/>
    </key>
    
    <attribute name="email" type="string" length="80" label="Email" desc="Recipient email"/>
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

生成的架構：

```
<schema mappingType="sql" name="recipient" namespace="cus" xtkschema="xtk:schema">  
  <element name="recipient" sqltable="CusRecipient"> 
    <dbindex name="companyId">      
      <keyfield xpath="@company-id"/>    
    </dbindex>

    <dbindex name="companyEmail" unique="true">
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </dbindex>    

    <key name="companyEmail">      
      <keyfield xpath="@email"/>      
      <keyfield xpath="@company-id"/>    
    </key>

    <attribute desc="Email address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

「companyEmail」名稱鍵的定義擴展為「company」連結的外鍵。 此鍵在兩個欄位上都生成唯一索引。
