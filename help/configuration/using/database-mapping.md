---
product: campaign
title: 資料庫對應
description: 資料庫對應
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
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
    <attribute desc="Recipient e-mail address" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
    <attribute default="GetDate()" label="Date of creation" name="created" sqlname="tsCreated" type="datetime"/>    
    <attribute enum="gender" label="Gender" name="gender" sqlname="iGender" type="byte"/>    
    <element label="Location" name="location">      
      <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
    </element>  
  </element>
</schema>
```

## 說明 {#description}

架構的根元素不再是&#x200B;**`<srcschema>`**，而是&#x200B;**`<schema>`**。

這將我們帶到另一種類型的文檔，它自動從源架構生成，只稱為架構。 此結構將用於Adobe Campaign應用程式。

SQL名稱會根據元素名稱和類型自動確定。

SQL命名規則如下：

* 表格：架構命名空間和名稱的連接

   在本例中，表的名稱是通過&#x200B;**sqltable**&#x200B;屬性中架構的主要元素輸入的：

   ```
   <element name="recipient" sqltable="CusRecipient">
   ```

* 欄位：元素的名稱，前面加上根據類型定義的前置詞（「i」代表整數，「d」代表雙重，「s」代表字串，「ts」代表日期等）

   通過&#x200B;**sqlname**&#x200B;屬性為每個類型&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**&#x200B;輸入欄位名稱：

   ```
   <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/> 
   ```

>[!NOTE]
>
>SQL名稱可以從源架構中過載。 要執行此操作，請在相關元素上填入「sqltable」或「sqlname」屬性。

用於建立從擴展架構生成的表的SQL指令碼如下：

```
CREATE TABLE CusRecipient(
  iGender NUMERIC(3) NOT NULL Default 0,   
  sCity VARCHAR(50),   
  sEmail VARCHAR(80),
  tsCreated TIMESTAMP Default NULL);
```

SQL欄位約束如下：

* 數值和日期欄位中沒有空值，
* 數值欄位已初始化為0。

## XML欄位 {#xml-fields}

預設情況下，任何類型的&#x200B;**`<attribute>`**&#x200B;和&#x200B;**`<element>`**&#x200B;元素都映射到資料架構表的SQL欄位。 但是，您可以在XML中引用此欄位，而不是SQL，這意味著資料儲存在包含所有XML欄位值的表的備忘錄欄位(&quot;mData&quot;)中。 這些資料的儲存是一個XML文檔，用於觀察架構結構。

若要在XML中填入欄位，必須將&#x200B;**xml**&#x200B;屬性以「true」值新增至相關元素。

**範例**:以下是兩個XML欄位使用範例。

* 多行注釋欄位：

   ```
   <element name="comment" xml="true" type="memo" label="Comment"/>
   ```

* HTML格式的資料說明：

   ```
   <element name="description" xml="true" type="html" label="Description"/>
   ```

   「html」類型可讓您將HTML內容儲存在CDATA標籤中，並在Adobe Campaign用戶端介面中顯示特殊的HTML編輯檢查。

使用XML欄位可讓您添加欄位，而無需修改資料庫的物理結構。 另一個優點是，您使用的資源更少（分配給SQL欄位的大小、每個表的欄位數限制等）。

主要缺點是無法對XML欄位進行索引或篩選。

## 索引欄位 {#indexed-fields}

索引可讓您最佳化應用程式中使用的SQL查詢的效能。

從資料架構的主要元素中聲明索引。

```
<dbindex name="name_of_index" unique="true/false">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

索引遵循下列規則：

* 索引可以引用表中的一個或多個欄位。
* 如果&#x200B;**unique**&#x200B;屬性包含「true」值，則所有欄位中的索引都可以是唯一的（以避免重複）。
* 索引的SQL名稱由表的SQL名稱和索引的名稱確定。

>[!NOTE]
>
>作為標準，索引是從架構的主要元素中聲明的第一個元素。

>[!NOTE]
>
>在表格對應（標準或FDA）期間會自動建立索引。

**範例**:

* 向電子郵件地址和城市添加索引：

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <dbindex name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </dbindex>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
       <element name="location" label="Location">
         <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
       </element>
     </element>
   </srcSchema>
   ```

* 將唯一索引新增至「id」名稱欄位：

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
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
     </element>
   </srcSchema>
   ```

## 密鑰管理 {#management-of-keys}

表必須至少具有一個用於標識表中記錄的鍵。

從資料架構的主要元素中宣告索引鍵。

```
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

鍵遵循下列規則：

* 鍵可以引用表中的一個或多個欄位。
* 當鍵是要填入的架構中的第一個鍵，或者它包含&#x200B;**internal**&#x200B;屬性且值為「true」時，該鍵稱為「primary」（或「priority」）。
* 每個鍵定義隱式聲明一個唯一索引。 通過將&#x200B;**noDbIndex**&#x200B;屬性添加為「true」，可以阻止在鍵上建立索引。

>[!NOTE]
>
>作為標準，鍵是在定義索引後從架構的主要元素聲明的元素。

>[!NOTE]
>
>索引鍵是在表格對應期間建立（標準或FDA）,Adobe Campaign會尋找唯一索引。

**範例**:

* 向電子郵件地址和城市添加密鑰：

   ```
   <srcSchema name="recipient" namespace="cus">
     <element name="recipient">
       <key name="email">
         <keyfield xpath="@email"/> 
         <keyfield xpath="location/@city"/> 
       </key>
   
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
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
   
      <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>    
      <element label="Location" name="location">      
        <attribute label="City" length="50" name="city" sqlname="sCity" type="string" userEnum="city"/>    
      </element>  
     </element>
   </schema>
   ```

* 在&quot;id&quot;名稱欄位中新增主要或內部索引鍵：

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
       <attribute name="email" type="string" length="80" label="Email" desc="E-mail address of recipient"/>
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
       <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>  
     </element>
   </schema>
   ```

### 自動增量密鑰 {#auto-incremental-key}

大部分Adobe Campaign表的主鍵是資料庫引擎自動生成的32位長整數。 鍵值的計算取決於一個序列（預設情況下，**XtkNewId** SQL函式），該序列生成的數字在整個資料庫中是唯一的。 在插入記錄時自動輸入密鑰的內容。

增量密鑰的優點在於，它為表之間的連接提供了不可修改的技術密鑰。 此外，此鍵不會佔用太多記憶體，因為它使用雙位元組整數。

可以在源架構中指定要與&#x200B;**pkSequence**&#x200B;屬性一起使用的序列的名稱。 如果未在源架構中提供此屬性，則將使用&#x200B;**XtkNewId**&#x200B;預設序列。 應用程式使用專用序列&#x200B;**nms:broadLog**&#x200B;和&#x200B;**nms:trackingLog**&#x200B;架構（分別為&#x200B;**NmsBroadLogId**&#x200B;和&#x200B;**NmsTrackingLogId**），因為這些表包含最多記錄。

從ACC 18.10開始，**XtkNewId**&#x200B;不再是現成可用結構中序列的預設值。 您現在可以建立架構，或以專用順序擴充現有架構。

>[!IMPORTANT]
>
>在建立新架構或架構擴充期間，您需要為整個架構保留相同的主鍵序列值(@pkSequence)。

>[!NOTE]
>
>Adobe Campaign架構(**NmsTrackingLogId**)中參考的序列必須與傳回參數中ID數的SQL函式相關聯，並以逗號分隔。 此函式必須稱為&#x200B;**GetNew** XXX **Ids**，其中&#x200B;**XXX**&#x200B;是序列的名稱（例如&#x200B;**GetNewNmsTrackingLogIds**）。 查看&#x200B;**postgres-nms.sql**、**mssql-nmssql**&#x200B;或&#x200B;**&lt;datakit/nms/eng/sql/**&#x200B;目錄中隨應用程式提供的&#x200B;**oracle-nms.sql**&#x200B;檔案，以恢復為每個資料庫引擎建立「NmsTrackingLogId」序列的示例。

若要宣告唯一索引鍵，請在資料結構的主要元素上填入&#x200B;**autopk**&#x200B;屬性（以「true」值表示）。

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

除了索引和索引的定義之外，擴充架構中還新增了名為「id」的數值欄位，以包含自動產生的主要索引鍵。

>[!IMPORTANT]
>
>在建立表時自動插入主鍵設定為0的記錄。 此記錄用於避免對卷表無效的外連接。 預設情況下，所有外鍵都使用值0初始化，以便在資料項未填充時始終在連接時返回結果。

## 連結：表之間的關係 {#links--relation-between-tables}

連結描述了一個表和另一個表之間的關聯。

各種類型的關聯（稱為「基數」）如下：

* 基數1-1:源表的一個實例最多可以具有目標表的一個相應實例。
* 基數1-N:源表的一個實例可以具有多個目標表的相應實例，但目標表的一個實例最多可以具有源表的一個相應實例。
* 基數N-N:來源表格的一個執行個體可以具有多個目標表格的相應執行個體，反之亦然。

在介面中，由於其表徵圖，您可以輕鬆區分不同類型的關係。

要連接與促銷活動表/資料庫的關係：

* ![](assets/join_with_campaign11.png) :基數1-1。例如，收件者與目前訂單之間。 收件者一次只能與目前訂單表的一個出現次數相關。
* ![](assets/externaljoin11.png) :基數1-1，外部連接。例如，在收件者與其國家之間。 收件者只能與表國家/地區的一個出現次數相關。 不會儲存國家/地區表格的內容。
* ![](assets/join_with_campaign1n.png) :基數1-N。例如，在收件者和訂閱表格之間。收件者可與訂閱表格上的數個發生次數相關聯。

對於使用聯合資料庫訪問的連接關係：

* ![](assets/join_fda_11.png) :基數1-1
* ![](assets/join_fda_1m.png) :基數1-N

有關FDA表格的詳細資訊，請參閱[存取外部資料庫](../../installation/using/about-fda.md)。

必須在包含透過主要元素連結之表格的外鍵的架構中宣告連結：

```
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

連結遵循下列規則：

* 連結的定義是在&#x200B;**link**-type **`<element>`**&#x200B;上輸入的，具有以下屬性：

   * **名稱**:源表中的連結名稱，
   * **目標**:目標架構的名稱，
   * **標籤**:連結標籤，
   * **revLink** （可選）:來自目標架構的反向連結名稱（預設會自動推斷）,
   * **完整性** （可選）:源表實例與目標表實例的參考完整性。可能的值如下：

      * **定義**:如果源實例不再被目標實例引用，則可以刪除該源實例，
      * **正常**:刪除源出現器將初始化指向目標出現器的連結的密鑰（預設模式），此類型的完整性將初始化所有外鍵，
      * **擁有**:刪除源事件會導致刪除目標事件，
      * **下載**:與 **own** （若是刪除）或重複發生次數（若是重複）,
      * **中性**:什麼都不做。
   * **revIntegrity** （可選）:目標架構的完整性（預設為「正常」）,
   * **revCardinality** （可選）:若值為「single」，則會以類型1-1填入基數（預設為1-N）。
   * **externalJoin** （可選）:強制外連接
   * **revExternalJoin** （可選）:強制反向連接上的外連接


* 連結將從源表引用一個或多個欄位到目標表。 組成連接（`<join>`元素）的欄位無需填充，因為預設情況下，會使用目標架構的內部鍵自動推斷這些欄位。
* 索引會自動新增至延伸架構中連結的外鍵。
* 連結由兩個半連結組成，其中第一個連結從源架構中聲明，第二個連結在目標架構的擴展架構中自動建立。
* 如果添加了&#x200B;**externalJoin**&#x200B;屬性，且值為「true」（在PostgreSQL中支援），則連接可以是外連接。

>[!NOTE]
>
>作為標準，連結是在架構結尾宣告的元素。

### 範例1 {#example-1}

1 — 與「cus:company」架構表相關：

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

連結定義由組成連接的欄位補充，即目標架構中包含其XPath(&quot;@id&quot;)的主鍵，以及架構中包含其XPath(&quot;@company-id&quot;)的外鍵。

外鍵會自動添加到與目標表中關聯欄位具有相同特性的元素中，並具有以下命名慣例：目標架構的名稱，後面接著關聯欄位的名稱（在此範例中為「company-id」）。

目標的延伸架構(「cus:company」):

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

已新增「cus:recipient」表格的反向連結，並附有下列參數：

* **名稱**:自動從源架構的名稱推導（可強制使用源架構的連結定義中的「revLink」屬性）
* **revLink**:反向連結名稱
* **目標**:連結結構的索引鍵（「cus:recipient」結構）
* **未綁定**:連結會宣告為1-N基數的集合元素（預設為）
* **完整性**:預設情況下，「define」（可強制使用源架構上的連結定義中的「revIntegrity」屬性）。

### 範例2 {#example-2}

在此範例中，我們將宣告指向「nms:address」架構表的連結。 連接是外部連接，並顯式填入收件人的電子郵件地址和連結表的「@address」欄位(「nms:address」)。

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

### 範例3 {#example-3}

與「cus:extension」架構表的1-1關係：

```
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### 範例4 {#example-4}

連結至資料夾（「xtk:folder」架構）:

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

預設值返回在「DefaultFolder(&#39;nmsFolder&#39;)」函式中輸入的第一個合格參數類型檔案的標識符。

### 範例5 {#example-5}

在此範例中，我們想在連結（「company」至「cus:company」架構）上建立索引鍵，其中包含&#x200B;**xlink**&#x200B;屬性，以及(「email」)表格的欄位：

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

    <attribute desc="E-mail address of recipient" label="Email" length="80" name="email" sqlname="sEmail" type="string"/>
    <element label="Company" name="company" revLink="recipient" target="sfa:company" type="link">      
      <join xpath-dst="@id" xpath-src="@company-id"/>    
    </element>    
    <attribute advanced="true" label="Foreign key of link 'Company' (field 'id')" name="company-id" sqlname="iCompanyId" type="long"/>
  </element>
</schema>
```

「companyEmail」名稱索引鍵的定義已擴充為「company」連結的外鍵。 此索引鍵會在兩個欄位上產生唯一索引。
