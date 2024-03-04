---
product: campaign
title: 資料庫對應
description: 資料庫對應
feature: Configuration, Instance Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
source-git-commit: f03e72d4ecd17446264adf74603aefca95f99d41
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 1%

---


# 連結管理 {#links--relation-between-tables}

連結說明一個表格與另一個表格之間的關聯。

關聯型別（也稱為基數）列於下方。

* 基數1-1：來源表格的一個執行個體最多可以具有目標表格的一個對應執行個體。
* 基數1-N：來源表格的一個出現次數可以具有多個目標表格的對應出現次數，但目標表格的一個出現次數最多可以具有來源表格的一個對應出現次數。
* 基數N-N：來源表格的一個出現次數可以具有多個目標表格的對應出現次數，反之亦然。

在使用介面中，基數會以特定圖示表示。

對於與Campaign資料表/資料庫的聯結關係：

* ![](assets/join_with_campaign11.png) ：基數1-1。 例如，在收件者和目前訂單之間。 收件者一次只能與目前訂單表格的一個執行個體相關。
* ![](assets/externaljoin11.png) ：基數1-1、外部聯結。 例如，在收件者與其國家/地區之間。 收件者只能與表格國家/地區的一個執行個體相關。 將不會儲存國家表格的內容。
* ![](assets/join_with_campaign1n.png) ：基數1-N。例如，在收件者和訂閱表格之間。 收件者可與訂閱表格上的數個相符專案建立關聯。

對於使用同盟資料庫存取(FDA)的加入關係：

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

   * **名稱**：來源表格中的連結名稱
   * **目標**：目標結構描述的名稱
   * **標籤**：連結的標籤
   * **revLink** （選用）：來自目標架構的反向連結名稱（預設會自動推斷）
   * **完整性** （選擇性）：來源表格出現位置與目標表格出現位置的參照完整性。
可能的值包括：

      * **定義**：如果來源發生次數不再由目標發生次數參考，則可將其刪除
      * **一般**：刪除來源出現位置會初始化指向目標出現位置的連結索引鍵（預設模式），此型別的完整性會初始化所有外來索引鍵
      * **擁有**：刪除來源出現位置會導致目標出現位置刪除
      * **owncopy**：與 **擁有** （若為刪除）或重複發生次數（若為重複）
      * **中立**：無特定行為

   * **revIntegrity** （選擇性）：目標綱要上的完整性（選擇性，預設為「一般」）
   * **revCardinality** （選用）：值為「single」時，會將型別1-1 （預設為1-N）填入基數
   * **externalJoin** （選用）：強制外部聯結
   * **revExternalJoin** （選用）：強制反向連結上的外部聯結

* 連結會參照來源表格到目的地表格的一或多個欄位。 構成聯結的欄位( `<join>`  元素)，因為預設會使用目標結構描述的內部索引鍵自動推斷。
* 索引會自動新增至擴充綱要中連結的外部索引鍵。
* 連結由兩個半連結組成，其中第一個是從來源綱要宣告，第二個是在目標綱要的延伸綱要中自動建立。
* 連線可以是外部連線，如果 **externalJoin** 加入屬性，值為「true」（PostgreSQL支援）。

>[!NOTE]
>
>作為標準，連結是在結構描述結尾宣告的元素。

## 範例：反向連結 {#example-1}

在以下範例中，我們會宣告與「cus：company」結構描述表格的1-N關係：

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

## 範例：簡單連結 {#example-2}

在此範例中，我們會宣告指向「nms：address」架構表格的連結。 此聯結是外部聯結，並明確填入收件者的電子郵件地址和連結表格(「nms：address」)的「@address」欄位。

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

## 範例：不重複基數 {#example-3}

在此範例中，我們會建立與「cus：extension」綱要表格的1-1關係：

```sql
<element integrity="own" label="Extension" name="extension" revCardinality="single" revLink="recipient" target="cus:extension" type="link"/>
```

## 範例：資料夾的連結 {#example-4}

在此範例中，我們會宣告資料夾（「xtk：folder」架構）的連結：

```sql
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

預設值會傳回在「DefaultFolder(&#39;nmsFolder&#39;)」函式中輸入的第一個合格引數型別檔案的識別碼。

## 範例：在連結上建立索引鍵 {#example-5}

在此範例中，我們會在連結（「company」至「cus：company」架構）上透過以下專案建立索引鍵： **xlink** （「電子郵件」）表格的屬性和欄位：

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
