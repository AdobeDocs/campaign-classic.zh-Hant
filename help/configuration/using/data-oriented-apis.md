---
product: campaign
title: 資料導向 API
description: 資料導向 API
feature: API
role: Data Engineer, Developer
exl-id: a392c55e-541a-40b1-a910-4a6dc79abd2d
source-git-commit: 517b85f5d7691acc2522bf4541f07c34c60c7fbf
workflow-type: tm+mt
source-wordcount: '1813'
ht-degree: 0%

---

# 資料導向 API{#data-oriented-apis}

資料導向API可讓您處理整個資料模型。

## 資料模型概觀 {#overview-of-the-datamodel}

Adobe Campaign未針對每個實體提供專用的讀取API （無getRecipient或getDelivery函式等）。 使用QUERY &amp; WRITER資料讀取和修改方法來存取模型的資料。

Adobe Campaign可讓您管理集合：查詢可讓您復原在資料庫中收集的一組資訊。 與SQL模式的存取不同，Adobe Campaign API會傳回XML樹狀結構而非資料欄。 因此，Adobe Campaign會建立包含所有收集資料的複合檔案。

此作業模式不提供XML檔案的屬性和元素與資料庫中表格欄之間的一對一對應。

XML檔案儲存在資料庫的MEMO型別欄位中。

## 模型說明 {#description-of-the-model}

您必須熟悉Adobe Campaign資料模型，才能在指令碼中處理資料庫的欄位。

如需資料模型的簡報，請參閱[Adobe Campaign資料模型說明](../../configuration/using/data-model-description.md)。

## 查詢與寫入器 {#query-and-writer}

下列簡介結構描述詳細說明資料庫和客戶(網頁或Adobe Campaign使用者端主控台)之間讀取(ExecuteQuery)和寫入(Writer)的低階交換。

![](assets/s_ncs_integration_webservices_schema_writer.png)

### Executequery {#executequery}

對於欄和條件，您可以使用查詢。

這可讓您隔離基礎SQL。 查詢語言不取決於基礎引擎：某些函式將會重新對應，可能會產生數個SELECT SQL順序。

如需詳細資訊，請參閱結構描述&#39;xtk：queryDef&#39;[&#128279;](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-)的&#39;ExecuteQuery&#39;方法的範例。

**ExecuteQuery**&#x200B;方法出現在[ExecuteQuery (xtk：queryDef)](#executequery--xtk-querydef-)中。

### 寫入 {#write}

「寫入」指令可讓您撰寫簡單或複雜的檔案，其專案位於基底的一或多個表格中。

異動API可讓您透過&#x200B;**updateOrInsert**&#x200B;命令管理調節：一個命令可讓您建立或更新資料。 您也可以設定修改合併（**合併**）：此作業模式可讓您授權部分更新。

XML結構提供資料的邏輯檢視，可讓您略過SQL表格的實體結構。

Write方法以[Write / WriteCollection (xtk：session)](#write---writecollection--xtk-session-)顯示。

## ExecuteQuery (xtk：queryDef) {#executequery--xtk-querydef-}

此方法可讓您從與結構描述相關聯的資料執行查詢。 它需要驗證字串（必須登入）和說明要作為引數提交的查詢的XML檔案。 return引數是XML檔案，包含查詢的結果，其格式為查詢所參照的結構描述格式。

「xtk：queryDef」結構描述中「ExecuteQuery」方法的定義：

```xml
<method name="ExecuteQuery" const="true">
  <parameters>
    <param desc="Output XML document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

>[!NOTE]
>
>這是「const」方法。 輸入引數會以「xtk：queryDef」結構描述的格式包含在XML檔案中。

### 輸入查詢的XML檔案格式 {#format-of-the-xml-document-of-the-input-query}

查詢的XML檔案結構在「xtk：queryDef」架構中進行了說明。 本檔案說明SQL查詢的子句：「select」、「where」、「order by」、「group by」、「having」。

```xml
<queryDef schema="schema_key" operation="operation_type">
  <select>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </select>
  <where> 
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ... 
  </where>
  <orderBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </orderBy>
  <groupBy>
    <node expr="expression1">
    <node expr="expression2">
    ...
  </groupBy>
  <having>
    <condition expr="expression1"/> 
    <condition expr="expression2"/>
    ...
  </having>
</queryDef>
```

可以在`<condition> `元素中定義子查詢( `<subquery>` )。 的語法   `<subquery> `   元素是根據    `<querydef>`。

`<subquery>  : </subquery>`的範例

```xml
<condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
  <subQuery schema="xtk:operatorGroup">
     <select>
       <node expr="[@operator-id]" />
     </select>
     <where>
       <condition expr="[@group-id]=$long(../@owner-id)"/>
     </where>
   </subQuery>
</condition>  
  
```

查詢必須參照&#x200B;**結構描述**&#x200B;屬性的開始結構描述。

所需的作業型別輸入於&#x200B;**operation**&#x200B;屬性中，且包含下列其中一個值：

* **get**：從資料表中擷取記錄，如果資料不存在，則傳回錯誤，
* **getIfExists**：從資料表中擷取記錄，如果資料不存在，則傳回空白檔案。
* **選取**：建立游標以傳回數筆記錄，如果沒有資料，則傳回空白檔案。
* **count**：傳回資料計數。

**XPath**&#x200B;語法是用來根據輸入結構描述來尋找資料。 如需XPath的詳細資訊，請參閱[資料結構描述](../../configuration/using/data-schemas.md)。

#### 具有&#39;get&#39;操作的範例 {#example-with-the--get--operation}

使用電子郵件上的篩選條件擷取收件者（「nms：recipient」綱要）的姓氏和名字。

```xml
<queryDef schema="nms:recipient" operation="get">
  <!-- fields to retrieve -->
  <select>
    <node expr="@firstName"/>
    <node expr="@lastName"/>
  </select> 

  <!-- condition on email -->
  <where>  
    <condition expr="@email= 'john.doe@aol.com'"/>
  </where>
</queryDef>
```

#### 「選取」操作的範例 {#example-with-the--select--operation}

傳回在資料夾上篩選的收件者清單，以及依據出生日期以降序排序的電子郵件網域。

```xml
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <!-- builds a string with the concatenation of the last name and first name separated by a dash -->      
    <node expr="@lastName+'-'+@firstName"/>
    <!-- get year of birth date -->
    <node expr="Year(@birthDate)"/>
  </select> 

  <where>  
     <condition expr="[@folder-id] = 1234 and @domain like 'Adobe%'"/>
  </where>

  <!-- order by birth date -->
  <orderBy>
    <node expr="@birthDate" sortDesc="true"/> <!-- by default sortDesc="false" -->
  </orderBy>
</queryDef>
```

運算式可以是簡單欄位或複雜運算式，例如算術運算或字串串連結。

若要限制要傳回的記錄數，請將&#x200B;**lineCount**&#x200B;屬性新增至`<querydef>`元素。

若要將查詢傳回的記錄數限製為100：

```xml
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

若要擷取接下來的100筆記錄，請再次執行相同的查詢，新增&#x200B;**startLine**&#x200B;屬性。

```xml
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### 「count」操作的範例 {#example-with-the--count--operation}

若要計算查詢的記錄數，請執行下列步驟：

```xml
<queryDef schema="nms:recipient" operation="count"">
  <!-- condition on the folder and domain of the email -->
  <where>  
    <condition expr="[@folder-id] = 1234" and @domain like 'Adobe%'"/>
  </where>
</queryDef>
```

>[!NOTE]
>
>我們再次使用上一個範例的條件。 未使用`<select>`和子句。`</select>`

#### 資料分組 {#data-grouping}

若要擷取多次參照的電子郵件地址：

```xml
<queryDef schema="nms:recipient" operation="select">
  <select>
    <node expr="@email"/>
    <node expr="count(@email)"/>
  </select>

  <!-- email grouping clause -->
  <groupby>
    <node expr="@email"/>
  </groupby>

  <!-- grouping condition -->
  <having>
    <condition expr="count(@email) > 1"/>
  </having>

</queryDef>
```

您可以將&#x200B;**groupBy**&#x200B;屬性直接新增至要分組的欄位，以簡化查詢：

```xml
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>不再需要填入`<groupby>`元素。

#### 在條件中括住 {#bracketing-in-conditions}

以下是兩個相同條件括弧的範例。

* 單一運算式中的簡單版本：

  ```xml
  <where>
    <condition expr="(@age > 15 or @age <= 45) and  (@city = 'Newton' or @city = 'Culver City') "/>
  </where>
  ```

* 包含`<condition>`個元素的結構化版本：

  ```xml
  <where>
    <condition bool-operator="AND">
      <condition expr="@age > 15" bool-operator="OR"/>
      <condition expr="@age <= 45"/>
    </condition>
    <condition>
      <condition expr="@city = 'Newton'" bool-operator="OR"/>
      <condition expr="@city = 'Culver City'"/>
    </condition>
  </where>
  ```

當多個條件套用至相同欄位時，可以用「IN」運運算元取代「OR」運運算元：

```xml
<where>
  <condition>
    <condition expr="@age IN (15, 45)"/>
    <condition expr="@city IN ('Newton', 'Culver City')"/>
  </condition>
</where>
```

當條件中使用兩個以上的資料時，此語法會簡化查詢。

#### 連結範例 {#examples-on-links}

* 連結1-1或N1：當表格具有外部索引鍵（連結從表格開始）時，可以直接篩選或擷取連結表格的欄位。

  資料夾標籤上的篩選範例：

  ```xml
  <where>
    <condition expr="[folder/@label] like 'Segment%'"/>
  </where>
  ```

  若要從「nms：recipient」綱要擷取資料夾的欄位：

  ```xml
  <select>
    <!-- label of recipient folder -->
    <node expr="[folder/@label]"/>
    <!-- displays the string count of the folder -->
    <node expr="partition"/>
  </select>
  ```

* 集合連結(1N)：集合資料表的欄位篩選必須透過&#x200B;**EXISTS**&#x200B;或&#x200B;**NOT EXISTS**&#x200B;運運算元執行。

  若要篩選已訂閱「電子報」資訊服務的收件者：

  ```xml
  <where>
    <condition expr="subscription" setOperator="EXISTS">
      <condition expr="@name = 'Newsletter'"/>
    </condition>
  </where>
  ```

  不建議從`<select>`子句直接擷取集合連結的欄位，因為查詢會傳回基數產品。 僅當連結的資料表只包含一個記錄（範例`<node expr="">`）時才使用。

  「訂閱」集合連結範例：

  ```xml
  <select>
    <node expr="subscription/@label"/>
  </select>
  ```

  可以在`<select>`子句中擷取包含集合連結專案的子清單。 參考欄位的XPath與收集元素相關。

  篩選( `<orderby>` )和限制( `<where>` )元素可以新增至集合元素。

  在此範例中，對於每個收件者，查詢會傳回收件者訂閱的電子郵件和資訊服務清單：

  ```xml
  <queryDef schema="nms:recipient" operation="select">
    <select>
      <node expr="@email"/>
  
      <!-- collection table (unbound type) -->
      <node expr="subscription">  
        <node expr="[service/@label]"/>    
        <!-- sub-condition on the collection table -->
        <where>  
          <condition expr="@expirationDate >= GetDate()"/>
        </where>
        <orderBy>
          <node expr="@expirationDate"/> 
        </orderBy>
      </node>
    </select> 
  </queryDef>
  ```

#### 繫結&#39;where&#39;和&#39;select&#39;子句的引數 {#binding-the-parameters-of-the--where--and--select--clause}

引數的繫結可讓引擎設定查詢中使用的引數值。 這非常有用，因為引擎負責逸出值，而且快取還有一個好處，就是可以擷取引數。

當建構查詢時，「界限」值會以字元(？ 在ODBC中，在SQL查詢主體中的`#[index]#` postgres...)。

```xml
<select>
  <!--the value will be bound by the engine -->
  <node expr="@startDate = #2002/02/01#"/>                   
  <!-- the value will not be bound by the engine but visible directly in the query -->
  <node expr="@startDate = #2002/02/01#" noSqlBind="true"/> 
</select>
```

若要避免繫結引數，「noSqlBind」屬性必須填入「true」值。

>[!IMPORTANT]
>
>如果查詢包含「order-by」或「group-by」指示，資料庫引擎將無法「繫結」值。 您必須將@noSqlBind=&quot;true&quot;屬性放置在查詢的&quot;select&quot;及/或&quot;where&quot;指示上。


### 輸出檔案格式 {#output-document-format}

return引數是XML檔案，採用與查詢相關聯的結構描述格式。

從「nms：recipient」綱要對「get」作業傳回的範例：

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

在「選取」操作中，傳回的檔案是元素的列舉：

```xml
<!-- the name of the first element does not matter -->
<recipient-collection>   
  <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
  <recipient email="peter.martinez@adobe.com" lastName"Martinez" firstName="Peter"/>
  <recipient...
</recipient-collection>  
```

針對「count」型別作業傳回的檔案範例：

```xml
<recipient count="3"/>
```

#### 別名 {#alias}

別名可讓您修改輸出檔案中資料的位置。 **別名**&#x200B;屬性必須在對應欄位上指定XPath。

```xml
<queryDef schema="nms:recipient" operation="get">
  <select>
    <node expr="@firstName" alias="@firstName"/>
    <node expr="@lastName"/>
    <node expr="[folder/@label]" alias="@My_folder"/>
  </select> 
</queryDef>
```

傳回：

```xml
<recipient My_folder="Recipients" First name ="John" lastName="Doe"/>
```

而非：

```xml
<recipient firstName="John" lastName="Doe">
  <folder label="Recipients"/>
</recipient>
```

### SOAP訊息範例 {#example-of-soap-messages}

* 查詢：

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <queryDef operation="get" schema="nms:recipient" xtkschema="xtk:queryDef">
            <select>
              <node expr="@email"/>
              <node expr="@lastName"/>
              <node expr="@firstName"/>
            </select>
            <where>
              <condition expr="@id = 3599"/>
            </where>
          </queryDef>
        </entity>
      </ExecuteQuery>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* 回應：

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
        </pdomOutput>
      </ExecuteQueryResponse>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

## 寫入/寫入集合(xtk：session) {#write---writecollection--xtk-session-}

這些服務用於插入、更新或刪除實體（「寫入」方法）或實體集合（「WriteCollection」方法）。

要更新的實體會與資料結構描述相關聯。 輸入引數是驗證字串（必須登入）以及包含要更新資料的XML檔案。

本檔案以設定寫入程式的指示作為補充。

呼叫不會傳回任何資料，錯誤除外。

「xtk：session」結構描述中「Write」和「WriteCollection」方法的定義：

```xml
<method name="Write" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference document"/>
  </parameters>
</method>
<method name="WriteCollection" static="true">
  <parameters>
    <param name="doc" type="DOMDocument" desc="Difference collection document"/>
  </parameters>
</method>
```

>[!NOTE]
>
>這是「靜態」方法。 輸入引數會以要更新的結構描述格式包含在XML檔案中。

### 概覽 {#overview}

資料協調會根據在關聯結構描述中輸入的索引鍵定義來運作。 寫入程式會根據輸入檔案中輸入的資料，尋找第一個符合條件的索引鍵。 會根據實體在資料庫中的存在性來插入或更新實體。

要更新之實體的結構描述索引鍵是根據&#x200B;**xtkschema**&#x200B;屬性完成的。

因此，調解金鑰可以使用&#x200B;**_key**&#x200B;屬性來強制，該屬性包含構成金鑰的XPath清單（以逗號分隔）。

可以使用下列值填入&#x200B;**_operation**&#x200B;屬性，以強制使用作業型別：

* **insert**：強制插入記錄（未使用調解金鑰），
* **insertOrUpdate**：根據調解金鑰（預設模式）更新或插入記錄，
* **更新**：更新記錄；如果資料不存在，
* **刪除**：刪除記錄，
* **none**：僅用於連結調解，不更新或插入。

### &#39;Write&#39;方法的範例 {#example-with-the--write--method}

以電子郵件地址、出生日期和城鎮更新或插入收件者（隱含的「insertOrUpdate」作業）：

```xml
<recipient xtkschema="nms:recipient" email="john.doe@adobe.com" birthDate="1956/05/04" folder-id=1203 _key="@email, [@folder-id]">
  <location city="Newton"/>
</recipient>
```

刪除收件者：

```xml
<recipient xtkschema="nms:recipient" _operation="delete" email="rene.dupont@adobe.com" folder-id=1203 _key="@email, [@folder-id]"/>
```

>[!NOTE]
>
>對於刪除操作，輸入檔案必須僅包含組成調解金鑰的欄位。

### &#39;WriteCollection&#39;方法的範例 {#example-with-the--writecollection--method}

多個收件者的更新或插入：

```xml
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### 連結範例 {#example-on-links}

#### 範例1 {#example-1}

根據收件者的內部名稱(@name)，將資料夾與收件者建立關聯。

```xml
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

可以在連結的元素上輸入「_key」和「_operation」屬性。 此元素的行為與輸入結構描述的主要元素相同。

主要實體(&quot;nms：recipient&quot;)的索引鍵定義包含連結表格（元素`<folder>`結構描述&quot;xtk：folder&quot;）和電子郵件的欄位。

>[!NOTE]
>
>在資料夾元素上輸入的「none」作業會在資料夾上定義調解，而不需要更新或插入。

#### 範例2 {#example-2}

從收件者更新公司（在「cus：company」綱要中連結的表格）：

```xml
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### 範例3 {#example-3}

使用群組關係表(「nms：rcpGrpRel」)將收件者新增至群組：

```xml
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>`<rcpgroup>`元素中未輸入索引鍵的定義，因為「nms：group」結構描述中已定義以群組名稱為基礎的隱含索引鍵。

### XML集合元素 {#xml-collection-elements}

依預設，必須植入所有收集要素，才能更新XML收集要素。 資料庫的資料將由輸入檔案中的資料取代。 如果檔案只包含要更新的元素，則必須在要更新的所有收集元素上填入「_operation」屬性，以強制與資料庫的XML資料合併。

### SOAP訊息範例 {#example-of-soap-messages-1}

* 查詢：

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <Write xmlns='urn:xtk:persist' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <domDoc xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <recipient xtkschema="nms:recipient" email="rene.dupont@adobe.com" firstName="René" lastName="Dupont" _key="@email">
        </domDoc>
      </Write>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

* 回應：

  ```xml
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <WriteResponse xmlns='urn:' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
      </WriteResponse>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

  傳回錯誤：

  ```xml
  <?xml version='1.0'?>
  <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <SOAP-ENV:Fault>
        <faultcode>SOAP-ENV:Server</faultcode>
        <faultstring xsi:type="xsd:string">Error while executing the method 'Write' of service 'xtk:persist'.</faultstring>
        <detail xsi:type="xsd:string">PostgreSQL error: ERROR:  duplicate key violates unique constraint &quot;nmsrecipient_id&quot;Impossible to save document of type 'Recipients (nms:recipient)'</detail>
      </SOAP-ENV:Fault>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```
