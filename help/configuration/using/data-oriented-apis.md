---
product: campaign
title: 資料導向 API
description: 資料導向 API
feature: API
exl-id: a392c55e-541a-40b1-a910-4a6dc79abd2d
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '1857'
ht-degree: 0%

---

# 資料導向 API{#data-oriented-apis}

![](../../assets/v7-only.svg)

面向資料的API允許您處理整個資料模型。

## 資料模型概述 {#overview-of-the-datamodel}

Adobe Campaign不為每個實體提供專用的讀API（沒有getRecipient或getDelivery函式等）。 使用QUERY &amp; WRITER資料讀取和修改方法訪問模型的資料。

Adobe Campaign允許您管理收藏：查詢使您能夠恢復整個資料庫中收集的一組資訊。 與在SQL模式下的訪問不同，Adobe CampaignAPI返回XML樹而不是資料列。 Adobe Campaign因此建立包含所有收集資料的複合文檔。

此操作模式不提供XML文檔的屬性和元素以及資料庫中表的列之間的一對一映射。

XML文檔儲存在資料庫的MEMO類型欄位中。

## 模型描述 {#description-of-the-model}

您必須熟悉Adobe Campaign資料模型才能在指令碼中找到資料庫欄位。

有關資料模型的演示，請參閱 [Adobe Campaign資料模型描述](../../configuration/using/data-model-description.md)。

## 查詢和編寫器 {#query-and-writer}

下面的介紹架構詳細描述了資料庫和客戶(網頁或Adobe Campaign客戶端控制台)之間用於讀取(ExecuteQuery)和寫入(Writer)的低級別交換。

![](assets/s_ncs_integration_webservices_schema_writer.png)

### 執行查詢 {#executequery}

對於列和條件，可以使用查詢。

這允許您隔離基礎SQL。 查詢語言不依賴於基礎引擎：某些函式將被重新映射，這可能會生成多個SELECT SQL命令。

有關此內容的詳細資訊，請參閱 [架構「xtk:queryDef」的「ExecuteQuery」方法示例](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-)。

的 **執行查詢** 方法 [ExecuteQuery(xtk:queryDef)](#executequery--xtk-querydef-)。

### 寫入 {#write}

Write命令允許您編寫簡單或複雜的文檔，其中包含基表的一個或多個表中的條目。

事務API允許您通過 **更新或插入** 命令：一個命令用於建立或更新資料。 您還可以配置修改合併(**合併**):此操作模式允許您授權部分更新。

XML結構提供了資料的邏輯視圖，並允許您迴避SQL表的物理結構。

Write方法在中介紹 [寫/寫集合(xtk:session)](#write---writecollection--xtk-session-)。

## ExecuteQuery(xtk:queryDef) {#executequery--xtk-querydef-}

此方法允許您從與架構關聯的資料中執行查詢。 它需要一個驗證字串（必須登錄）和一個XML文檔，該文檔將要提交的查詢描述為參數。 返回參數是XML文檔，包含查詢結果的格式為查詢引用的架構。

&quot;xtk:queryDef&quot;架構中&quot;ExecuteQuery&quot;方法的定義：

```
<method name="ExecuteQuery" const="true">
  <parameters>
    <param desc="Output XML document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

>[!NOTE]
>
>這是&quot;const&quot;方法。 輸入參數以&quot;xtk:queryDef&quot;架構的格式包含在XML文檔中。

### 輸入查詢的XML文檔格式 {#format-of-the-xml-document-of-the-input-query}

查詢的XML文檔的結構在「xtk:queryDef」架構中進行了描述。 本文檔介紹SQL查詢的子句：&quot;select&quot;、&quot;where&quot;、&quot;order by&quot;、&quot;group by&quot;、&quot;having&quot;。

```
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

子查詢( `<subquery>`  )可在  `<condition> `  的子菜單。 的語法   `<subquery> `   元素基於    `<querydef>`。

示例 `<subquery>  : </subquery>`

```
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

查詢必須引用 **架構** 屬性。

所需操作的類型在 **操作** 屬性，並包含以下值之一：

* **得**:從表中檢索記錄，並在資料不存在時返回錯誤，
* **getIfExists**:從表中檢索記錄，並在資料不存在時返回空文檔，
* **選擇**:建立游標以返回多個記錄，如果沒有資料則返回空文檔，
* **計數**:返回資料計數。

的 **XPath** 語法用於基於輸入模式來定位資料。 有關XPath的詳細資訊，請參閱 [資料架構](../../configuration/using/data-schemas.md)。

#### 帶&quot;get&quot;操作的示例 {#example-with-the--get--operation}

在電子郵件上檢索帶過濾器的收件人（「nms:recipient」架構）的姓氏和名字。

```
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

#### 帶「select」操作的示例 {#example-with-the--select--operation}

返回在出生日期按降序排序的資料夾和電子郵件域上篩選的收件人清單。

```
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

表達式可以是簡單欄位或複雜表達式，如算術運算或字串串聯。

要限制要返回的記錄數，請添加 **行計數** 屬性 `<querydef>` 的子菜單。

要將查詢返回的記錄數限制為100:

```
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

要檢索下100條記錄，請再次運行同一查詢，並添加 **開始行** 屬性。

```
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### 帶「count」操作的示例 {#example-with-the--count--operation}

要計數查詢上的記錄數：

```
<queryDef schema="nms:recipient" operation="count"">
  <!-- condition on the folder and domain of the email -->
  <where>  
    <condition expr="[@folder-id] = 1234" and @domain like 'Adobe%'"/>
  </where>
</queryDef>
```

>[!NOTE]
>
>我們再次使用上例中的條件。 的 `<select>` 和子句。 `</select>`

#### 資料分組 {#data-grouping}

要檢索多次引用的電子郵件地址：

```
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

通過添加 **分組依據** 屬性直接到要分組的欄位：

```
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>不再需要填充 `<groupby>` 的子菜單。

#### 條件中的括弧 {#bracketing-in-conditions}

以下是兩個在相同條件下進行括弧的例子。

* 單個表達式中的簡單版本：

   ```
   <where>
     <condition expr="(@age > 15 or @age <= 45) and  (@city = 'Newton' or @city = 'Culver City') "/>
   </where>
   ```

* 具有 `<condition>` 元素：

   ```
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

當多個條件應用於同一欄位時，可以將「OR」運算子替換為「IN」運算：

```
<where>
  <condition>
    <condition expr="@age IN (15, 45)"/>
    <condition expr="@city IN ('Newton', 'Culver City')"/>
  </condition>
</where>
```

此語法在條件中使用兩個以上資料時簡化了查詢。

#### 連結示例 {#examples-on-links}

* 連結1-1或N1:當表具有外鍵（連結從表開始）時，可以直接過濾或檢索連結表的欄位。

   資料夾標籤上的篩選器示例：

   ```
   <where>
     <condition expr="[folder/@label] like 'Segment%'"/>
   </where>
   ```

   要從「nms:recipient」架構檢索資料夾的欄位，請執行以下操作：

   ```
   <select>
     <!-- label of recipient folder -->
     <node expr="[folder/@label]"/>
     <!-- displays the string count of the folder -->
     <node expr="partition"/>
   </select>
   ```

* 集合連結(1N):必須通過 **存在** 或 **不存在** 運算子。

   要篩選訂閱「新聞簡訊」資訊服務的收件人：

   ```
   <where>
     <condition expr="subscription" setOperator="EXISTS">
       <condition expr="@name = 'Newsletter'"/>
     </condition>
   </where>
   ```

   從中直接檢索集合連結的欄位 `<select>` 不建議使用子句，因為查詢返回主要產品。 僅當連結表僅包含一條記錄時才使用它（示例） `<node expr="">`)。

   「訂閱」集合連結示例：

   ```
   <select>
     <node expr="subscription/@label"/>
   </select>
   ```

   可以檢索包含集合連結元素的子清單 `<select>` 。 引用欄位的XPaths是集合元素中的上下文。

   篩選( `<orderby>`  )和限制(  `<where>`  )元素可添加到集合元素。

   在此示例中，對於每個收件人，查詢將返回收件人訂閱的電子郵件和資訊服務清單：

   ```
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

#### 綁定「where」和「select」子句的參數 {#binding-the-parameters-of-the--where--and--select--clause}

通過綁定參數，引擎可以設定查詢中使用的參數的值。 這非常有用，因為引擎負責值的轉義，而且快取對於要檢索的參數還有額外的好處。

構造查詢時，「綁定」值將替換為字元(?) 在ODBC中， `#[index]#` 在SQL查詢的正文中。)

```
<select>
  <!--the value will be bound by the engine -->
  <node expr="@startDate = #2002/02/01#"/>                   
  <!-- the value will not be bound by the engine but visible directly in the query -->
  <node expr="@startDate = #2002/02/01#" noSqlBind="true"/> 
</select>
```

要避免綁定參數，必須使用值「true」填充「noSqlBind」屬性。

>[!IMPORTANT]
>
>如果查詢包含「order-by」或「group-by」指令，則資料庫引擎將無法「綁定」值。 必須將@noSqlBind=&quot;true&quot;屬性放在查詢的&quot;select&quot;和/或&quot;where&quot;說明上。

#### 查詢生成提示： {#query-building-tip-}

要幫助處理查詢的語法，可以使用Adobe Campaign客戶端控制台中的通用查詢編輯器( **[!UICONTROL Tools/ Generic query editor...]** )的正平方根。 操作步驟：

1. 選擇要檢索的資料：

   ![](assets/s_ncs_integration_webservices_queyr1.png)

1. 定義篩選器條件：

   ![](assets/s_ncs_integration_webservices_queyr2.png)

1. 執行查詢，然後按CTRL+F4查看查詢原始碼。

   ![](assets/s_ncs_integration_webservices_queyr3.png)

### 輸出文檔格式 {#output-document-format}

返回參數是與查詢關聯的架構格式的XML文檔。

從&quot;nms:recipient&quot;架構返回「get」操作的示例：

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

在「select」操作中，返回的文檔是元素的枚舉：

```
<!-- the name of the first element does not matter -->
<recipient-collection>   
  <recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
  <recipient email="peter.martinez@adobe.com" lastName"Martinez" firstName="Peter"/>
  <recipient...
</recipient-collection>  
```

為「計數」類型操作返回的文檔示例：

```
<recipient count="3"/>
```

#### 別名 {#alias}

使用別名可以修改輸出文檔中資料的位置。 的 **別名** 屬性必須在相應欄位上指定XPath。

```
<queryDef schema="nms:recipient" operation="get">
  <select>
    <node expr="@firstName" alias="@firstName"/>
    <node expr="@lastName"/>
    <node expr="[folder/@label]" alias="@My_folder"/>
  </select> 
</queryDef>
```

返回：

```
<recipient My_folder="Recipients" First name ="John" lastName="Doe"/>
```

而不是：

```
<recipient firstName="John" lastName="Doe">
  <folder label="Recipients"/>
</recipient>
```

### SOAP消息示例 {#example-of-soap-messages}

* 查詢:

   ```
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

* 響應：

   ```
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

## 寫/寫集合(xtk:session) {#write---writecollection--xtk-session-}

這些服務用於插入、更新或刪除實體（「寫」方法）或實體集合（「寫」集合方法）。

要更新的實體與資料模式相關聯。 輸入參數是驗證字串（必須登錄）和包含要更新的資料的XML文檔。

本文檔還附有配置寫入過程的說明。

除錯誤外，調用不返回任何資料。

&quot;xtk:session&quot;架構中&quot;Write&quot;和&quot;WriteCollection&quot;方法的定義：

```
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
>這是&quot;靜態&quot;方法。 輸入參數以要更新的模式的格式包括在XML文檔中。

### 概覽 {#overview}

資料協調基於在關聯模式中輸入的鍵的定義操作。 寫入過程基於輸入文檔中輸入的資料來查找第一合格密鑰。 根據實體在資料庫中的存在，插入或更新該實體。

要更新的實體的架構的密鑰根據 **xtkschema** 屬性。

因此，可以使用 **鍵** 屬性包含構成鍵的XPath的清單（以逗號分隔）。

通過填充 **操作** 屬性，其值如下：

* **插入**:強制插入記錄（未使用協調密鑰）,
* **插入或更新**:根據對帳鍵（預設模式）更新或插入記錄，
* **更新**:更新記錄；如果資料不存在，
* **刪除**:刪除記錄，
* **無**:僅用於連結協調，不進行更新或插入。

### 帶「Write」方法的示例 {#example-with-the--write--method}

使用電子郵件地址、出生日期和鎮更新或插入收件人（隱式「insertOrUpdate」操作）:

```
<recipient xtkschema="nms:recipient" email="john.doe@adobe.com" birthDate="1956/05/04" folder-id=1203 _key="@email, [@folder-id]">
  <location city="Newton"/>
</recipient>
```

刪除收件人：

```
<recipient xtkschema="nms:recipient" _operation="delete" email="rene.dupont@adobe.com" folder-id=1203 _key="@email, [@folder-id]"/>
```

>[!NOTE]
>
>對於刪除操作，輸入文檔只能包含構成協調鍵的欄位。

### 「WriteCollection」方法示例 {#example-with-the--writecollection--method}

更新或插入多個收件人：

```
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### 連結示例 {#example-on-links}

#### 示例1 {#example-1}

根據資料夾的內部名稱(@name)將其與收件人關聯。

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

可以在連結的元素上輸入「_key」和「_operation」屬性。 此元素上的行為與輸入架構的主元素上的行為相同。

主實體(「nms:recipient」)的鍵的定義由連結表（元素）中的欄位組成 `<folder>`  架構「xtk:folder」)和電子郵件。

>[!NOTE]
>
>在資料夾元素上輸入的操作「無」定義了在資料夾上進行的協調，而不進行更新或插入。

#### 示例2 {#example-2}

從收件人更新公司（「cus:company」架構中的連結表）:

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### 示例3 {#example-3}

將收件人添加到具有組關係表(「nms:rcpGrpRel」)的組：

```
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>未在 `<rcpgroup>` 元素，因為基於組名的隱式鍵是在「nms:group」架構中定義的。

### XML集合元素 {#xml-collection-elements}

預設情況下，必須填充所有收集要素，才能更新XML收集要素。 來自資料庫的資料將替換為來自輸入文檔的資料。 如果文檔只包含要更新的元素，則必須在要更新的所有收集元素上填充「_operation」屬性，以強制與資料庫的XML資料合併。

### SOAP消息示例 {#example-of-soap-messages-1}

* 查詢:

   ```
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

* 響應：

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <WriteResponse xmlns='urn:' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </WriteResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

   返回時出錯：

   ```
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
