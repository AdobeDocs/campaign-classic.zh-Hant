---
product: campaign
title: 資料庫對應
description: 資料庫對應
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
exl-id: 728b509f-2755-48df-8b12-449b7044e317
source-git-commit: bd1007ffcfa58ee60fdafa424c7827e267845679
workflow-type: tm+mt
source-wordcount: '1984'
ht-degree: 0%

---

# 資料庫對應{#database-mapping}

說明的範例綱要的SQL對應 [在此頁面中](schema-structure.md) 產生下列XML檔案：

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

## 說明 {#description}

結構的根元素已變更為 **`<srcschema>`** 至 **`<schema>`**.

這種其他型別的檔案會自動從來源結構描述產生，並僅被簡稱為結構描述。

SQL名稱是根據元素名稱和型別自動決定的。

SQL命名規則如下：

* **表格**：串連結構描述名稱空間和名稱

  在我們的範例中，表格的名稱是透過以下結構描述的主要元素輸入： **sqltable** 屬性：

  ```sql
  <element name="recipient" sqltable="CusRecipient">
  ```

* **欄位**：前面有根據型別定義之前置詞的元素名稱：「i」代表整數，「d」代表雙精度，「s」代表字串，「ts」代表日期等。

  欄位名稱是透過 **sqlname** 每個型別的屬性 **`<attribute>`** 和 **`<element>`**：

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

根據預設，任何  **`<attribute>`** 和 **`<element>`** -typed元素對應到資料結構描述表格的SQL欄位。 不過，您可以用XML來參照此欄位，而非SQL，這表示資料會儲存在包含所有XML欄位值的表格之備忘錄欄位(「mData」)中。 這些資料的儲存是觀察結構描述結構的XML檔案。

若要以XML填入欄位，您必須新增 **xml** 對相關元素具有「true」值的屬性。

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
* 如果符合下列條件，則索引在所有欄位中可以是唯一的（以避免重複） **獨特** 屬性包含「true」值
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

## 金鑰管理 {#management-of-keys}

表格必須至少有一個索引鍵用於識別表格中的記錄。

從資料結構描述的主要元素中宣告索引鍵。

```sql
<key name="name_of_key">
  <keyfield xpath="xpath_of_field1"/>
  <keyfield xpath="xpath_of_field2"/>
  ...
</key>
```

下列規則適用於機碼：

* 索引鍵可參考表格中的一或多個欄位
* 當索引鍵是結構描述中第一個要填入的索引鍵，或如果索引鍵包含 **內部** 值為「true」的屬性
* 每個索引鍵定義都會以隱含方式宣告唯一索引。 可以透過新增以下專案來防止在索引鍵上建立索引： **noDbIndex** 值為「true」的屬性

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

### 自動增量索引鍵 {#auto-incremental-key}

大部分Adobe Campaign表格的主要索引鍵是由資料庫引擎自動產生的32位元長整數。 機碼值的計算取決於順序(根據預設， **XtkNewId** SQL函式)產生在整個資料庫中唯一的數字。 插入記錄時會自動輸入金鑰的內容。

增量索引鍵的優點在於，它提供不可修改的技術索引鍵用於表格之間的聯結。 此外，此索引鍵使用雙位元組整數，因此不會佔用太多記憶體。

您可以在來源綱要中指定要與搭配使用的序列名稱 **pkSequence** 屬性。 如果來源結構描述中未指定此屬性， **XtkNewId** 將會使用預設序列。 應用程式使用專用的序列 **nms：broadLog** 和 **nms：trackingLog** 結構描述(**NmsBroadLogId** 和 **NmsTrackingLogId** 這些是包含最多記錄的表格。

從ACC 18.10， **XtkNewId** 不再是現成可用結構中序列的預設值。 您現在可以使用專用序列來建置方案或擴充現有方案。

>[!IMPORTANT]
>
>建立新結構描述或在結構描述擴充期間，您需要為整個結構描述保留相同的主要索引鍵序列值(@pkSequence)。

>[!NOTE]
>
>Adobe Campaign結構描述中參照的序列(**NmsTrackingLogId** 例如)必須與SQL函式相關聯，此函式會傳回引數中的ID數目（以逗號分隔）。 必須呼叫此函式 **GetNew** XXX **Id**，其中 **XXX** 是序列的名稱(**GetNewNmsTrackingLogIds** 例如)。 檢視 **postgres-nms.sql**， **mssql-nms.sql** 或 **oracle-nms.sql** 中隨應用程式提供的檔案 **datakit/nms/eng/sql/** 目錄，以復原每個資料庫引擎的「NmsTrackingLogId」序列建立範例。

若要宣告唯一金鑰，請填入 **autopk** 屬性（值為「true」）。

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

## 連結：表格之間的關係 {#links--relation-between-tables}

連結說明一個表格與另一個表格之間的關聯。

各種關聯（稱為「基數」）型別如下：

* 基數1-1：來源表格的一個執行個體最多可以具有目標表格的一個對應執行個體。
* 基數1-N：來源表格的一個出現次數可以具有多個目標表格的對應出現次數，但目標表格的一個出現次數最多可以具有來源表格的一個對應出現次數。
* 基數N-N：來源表格的一個出現次數可以具有多個目標表格的對應出現次數，反之亦然。

在介面中，您可以透過圖示輕鬆區分不同型別的關係。

對於與Campaign資料表/資料庫的聯結關係：

* ![](assets/join_with_campaign11.png) ：基數1-1。 例如，在收件者和目前訂單之間。 收件者一次只能與目前訂單表格的一個執行個體相關。
* ![](assets/externaljoin11.png) ：基數1-1、外部聯結。 例如，在收件者與其國家/地區之間。 收件者只能與表格國家/地區的一個執行個體相關。 將不會儲存國家表格的內容。
* ![](assets/join_with_campaign1n.png) ：基數1-N。例如，在收件者和訂閱表格之間。 收件者可與訂閱表格上的數個相符專案建立關聯。

對於使用同盟資料庫存取的聯結關係：

* ![](assets/join_fda_11.png) ：基數1-1
* ![](assets/join_fda_1m.png) ：基數1-N

如需FDA表格的詳細資訊，請參閱 [存取外部資料庫](../../installation/using/about-fda.md).

在包含透過主要元素連結之表格外部索引鍵的結構描述中，必須宣告連結：

```sql
<element name="name_of_link" type="link" target="key_of_destination_schema">
  <join xpath-dst="xpath_of_field1_destination_table" xpath-src="xpath_of_field1_source_table"/>
  <join xpath-dst="xpath_of_field2_destination_table" xpath-src="xpath_of_field2_source_table"/>
  ...
</element>
```

連結遵循下列規則：

* 連結的定義輸入於 **連結**-type **`<element>`** 具有下列屬性：

   * **名稱**：來源表格中的連結名稱，
   * **目標**：目標結構描述的名稱，
   * **標籤**：連結的標籤，
   * **revLink** （選用）：來自目標架構的反向連結名稱（預設會自動衍生），
   * **完整性** （選擇性）：來源表格出現位置與目標表格出現位置的參照完整性。 可能的值如下：

      * **定義**：如果來源發生次數不再由目標發生次數參考，則可能會刪除該來源發生次數，
      * **一般**：刪除來源出現位置會初始化指向目標出現位置的連結索引鍵（預設模式），此型別的完整性會初始化所有外來索引鍵，
      * **擁有**：刪除來源出現位置會導致目標出現位置刪除，
      * **owncopy**：與 **擁有** （若為刪除）或重複發生次數（若為重複），
      * **中立**：不會執行任何動作。

   * **revIntegrity** （選擇性）：目標綱要上的完整性（選擇性，預設為「一般」），
   * **revCardinality** （選用）：值為「single」時，會將型別1-1 （預設為1-N）填入基數。
   * **externalJoin** （選用）：強制外部聯結
   * **revExternalJoin** （選用）：強制反向連結上的外部聯結

* 連結會參照來源表格到目的地表格的一或多個欄位。 構成聯結的欄位( `<join>`  元素)，因為預設會使用目標結構描述的內部索引鍵自動推斷。
* 索引會自動新增至擴充綱要中連結的外部索引鍵。
* 連結由兩個半連結組成，其中第一個是從來源綱要宣告，第二個是在目標綱要的延伸綱要中自動建立。
* 連線可以是外部連線，如果 **externalJoin** 加入屬性，值為「true」（PostgreSQL支援）。

>[!NOTE]
>
>作為標準，連結是在結構描述結尾宣告的元素。

### 範例1 {#example-1}

與「cus：company」結構描述表格相關的1-N：

```sql
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    ...
    <element label="Company" name="company" revIntegrity="define" revLabel="Contact" target="cus:company" type="link"/>
  </element>
</srcSchema>
```

產生的結構描述：

```sql
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

組成聯結的欄位可補充連結定義，也就是在目的地結構描述中主索引鍵及其XPath (「@id」)，在結構描述中主索引鍵及其XPath (「@company-id」)。

外部索引鍵會自動新增至與目的地表格中相關欄位使用相同特性的元素中，並遵循下列命名慣例：目標結構描述名稱后面接著相關欄位名稱（範例中為「company-id」）。

目標(「cus：company」)的延伸結構描述：

```sql
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

已新增指向「cus：recipient」表格的反向連結，其中包含下列引數：

* **名稱**：自動從來源結構描述的名稱衍生（可在來源結構描述的連結定義中使用「revLink」屬性強制執行）
* **revLink**：反向連結的名稱
* **目標**：連結綱要的索引鍵（「cus：recipient」綱要）
* **未繫結**：連結會宣告為1-N基數的收集要素（依預設）
* **完整性**：預設為「定義」（可在來源架構上的連結定義中使用「revIntegrity」屬性強制執行）。

### 範例2 {#example-2}

在此範例中，我們將宣告指向「nms：address」架構表格的連結。 此聯結是外部聯結，並明確填入收件者的電子郵件地址和連結表格(「nms：address」)的「@address」欄位。

```sql
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

與「cus：extension」綱要表格的1-1關係：

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

### 範例4 {#example-4}

連結至資料夾（「xtk：folder」架構）：

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

預設值會傳回在「DefaultFolder(&#39;nmsFolder&#39;)」函式中輸入的第一個合格引數型別檔案的識別碼。

### 範例5 {#example-5}

在此範例中，我們希望透過在連結（「company」到「cus：company」架構）上建立索引鍵 **xlink** （「電子郵件」）表格的屬性和欄位：

```sql
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

產生的結構描述：

```sql
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

「companyEmail」名稱金鑰的定義已擴充為「company」連結的外部金鑰。 此索引鍵會在兩個欄位上產生唯一索引。
