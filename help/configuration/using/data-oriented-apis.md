---
product: campaign
title: 資料導向 API
description: 資料導向 API
audience: configuration
content-type: reference
topic-tags: api
exl-id: a392c55e-541a-40b1-a910-4a6dc79abd2d
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '1881'
ht-degree: 0%

---

# 資料導向 API{#data-oriented-apis}

![](../../assets/v7-only.svg)

資料導向API可讓您處理整個資料模型。

## 資料模型概觀 {#overview-of-the-datamodel}

Adobe Campaign不為每個實體提供專用的讀取API（沒有getRecipient或getDelivery函式等）。 使用QUERY和WRITER資料讀取和修改方法訪問模型的資料。

Adobe Campaign可讓您管理集合：查詢使您能夠恢復整個資料庫中收集的一組資訊。 與在SQL模式下的存取不同，Adobe Campaign API會傳回XML樹狀結構，而非資料欄。 Adobe Campaign因此會建立包含所有收集資料的複合檔案。

此操作模式不提供XML文檔的屬性和元素以及資料庫中表的列之間的一對一映射。

XML文檔儲存在資料庫的MEMO類型欄位中。

## 模型說明 {#description-of-the-model}

您必須熟悉Adobe Campaign資料模型，才能處理指令碼中資料庫的欄位。

如需資料模型的簡報，請參閱 [Adobe Campaign資料模型說明](../../configuration/using/data-model-description.md).

若要產生其結構，請參閱本文章： [如何產生資料模型或資料字典](https://helpx.adobe.com/campaign/kb/generate-data-model.html).

## 查詢和寫入程式 {#query-and-writer}

以下介紹結構詳細說明了資料庫和客戶(網頁或Adobe Campaign客戶端控制台)之間的讀取(ExecuteQuery)和寫入（寫入器）的低級交換。

![](assets/s_ncs_integration_webservices_schema_writer.png)

### ExecuteQuery {#executequery}

對於欄和條件，您可以使用查詢。

這可讓您隔離基礎SQL。 查詢語言不依賴基礎引擎：某些函式將重新映射，這可能會生成多個SELECT SQL順序。

有關詳細資訊，請參閱 [架構「xtk:queryDef」的「ExecuteQuery」方法範例](../../configuration/using/web-service-calls.md#example-on-the--executequery--method-of-schema--xtk-querydef-).

此 **ExecuteQuery** 方法如 [ExecuteQuery(xtk:queryDef)](#executequery--xtk-querydef-).

### 寫入 {#write}

「寫入」命令可以編寫簡單或複雜的文檔，其中的條目位於基表的一個或多個表中。

交易API可讓您透過 **updateOrInsert** 命令：一個命令可讓您建立或更新資料。 您也可以配置修改合併(**合併**):此作業模式可讓您授權部分更新。

XML結構提供資料的邏輯視圖，並允許您繞過SQL表的物理結構。

寫入方法如下所示： [Write/WriteCollection(xtk:session)](#write---writecollection--xtk-session-).

## ExecuteQuery(xtk:queryDef) {#executequery--xtk-querydef-}

此方法可讓您從與架構相關聯的資料執行查詢。 它會使用驗證字串（必須登入）和XML檔案，以描述要提交的查詢為參數。 返回參數是XML文檔，包含查詢結果的格式為查詢引用的架構。

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
>這是「const」方法。 輸入參數以&quot;xtk:queryDef&quot;架構的格式包含在XML文檔中。

### 輸入查詢的XML文檔格式 {#format-of-the-xml-document-of-the-input-query}

查詢的XML文檔結構在「xtk:queryDef」架構中描述。 本文檔描述SQL查詢的子句：&quot;select&quot;、&quot;where&quot;、&quot;order by&quot;、&quot;group by&quot;、&quot;having&quot;。

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

子查詢( `<subquery>`  )，可在  `<condition> `  元素。 的語法   `<subquery> `   元素是以    `<querydef>`.

範例 `<subquery>  : </subquery>`

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

查詢必須參考 **綱要** 屬性。

需要的操作類型在 **操作** 屬性和包含下列其中一個值：

* **get**:從表格中擷取記錄，並在資料不存在時傳回錯誤，
* **getIfExists**:從表中檢索記錄，如果資料不存在，則返回空文檔，
* **選取**:建立游標以返回多個記錄，如果沒有資料，則返回空文檔，
* **計數**:傳回資料計數。

此 **XPath** 語法用於根據輸入架構來定位資料。 有關XPath的詳細資訊，請參閱 [資料結構](../../configuration/using/data-schemas.md).

#### &#39;get&#39;操作的範例 {#example-with-the--get--operation}

在電子郵件上帶有篩選器，擷取收件者的姓氏和名字（「nms:recipient」架構）。

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

#### 「select」操作的示例 {#example-with-the--select--operation}

傳回在資料夾和電子郵件網域上篩選的收件者清單，其排序在出生日期以遞減順序排序。

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

運算式可以是簡單欄位或複雜的運算式，例如算術運算或字串的串連。

若要限制要傳回的記錄數，請新增 **lineCount** 屬性 `<querydef>` 元素。

要將查詢返回的記錄數限制為100:

```
<queryDef schema="nms:recipient" operation="select" lineCount="100">
...
```

若要擷取接下來的100筆記錄，請再次執行相同的查詢，並新增 **startLine** 屬性。

```
<queryDef schema="nms:recipient" operation="select" lineCount="100" startLine="100">
...
```

#### 「count」操作的範例 {#example-with-the--count--operation}

要計算查詢上的記錄數：

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
>我們再次使用上一個範例中的條件。 此 `<select>` 不會使用和子句。 `</select>`

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

可借由新增 **groupBy** 屬性直接歸類至要分組的欄位：

```
<select>
  <node expr="@email" groupBy="true"/>
</select>
```

>[!NOTE]
>
>不再需要填入 `<groupby>` 元素。

#### 條件中的括弧 {#bracketing-in-conditions}

以下是兩個在相同條件下加括弧的範例。

* 單一運算式中的簡單版本：

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

若有數個條件套用至相同欄位時，可將「OR」運算子取代為「IN」運算：

```
<where>
  <condition>
    <condition expr="@age IN (15, 45)"/>
    <condition expr="@city IN ('Newton', 'Culver City')"/>
  </condition>
</where>
```

條件中使用超過兩個資料時，此語法可簡化查詢。

#### 連結範例 {#examples-on-links}

* 連結1-1或N1:當表具有外鍵時（連結從表開始），可以篩選或直接檢索連結表的欄位。

   資料夾標籤的篩選器範例：

   ```
   <where>
     <condition expr="[folder/@label] like 'Segment%'"/>
   </where>
   ```

   要從「nms:recipient」架構中檢索資料夾的欄位，請執行以下操作：

   ```
   <select>
     <!-- label of recipient folder -->
     <node expr="[folder/@label]"/>
     <!-- displays the string count of the folder -->
     <node expr="partition"/>
   </select>
   ```

* 集合連結(1N):篩選集合表格的欄位必須透過 **存在** 或 **不存在** 運算元。

   若要篩選已訂閱「電子報」資訊服務的收件者：

   ```
   <where>
     <condition expr="subscription" setOperator="EXISTS">
       <condition expr="@name = 'Newsletter'"/>
     </condition>
   </where>
   ```

   從 `<select>` 不建議使用子句，因為查詢返回主產品。 只有在連結的表只包含一個記錄時才會使用（範例） `<node expr="">`)。

   「訂閱」集合連結的範例：

   ```
   <select>
     <node expr="subscription/@label"/>
   </select>
   ```

   您可以擷取包含 `<select>` 條。 參考欄位的XPath與集合元素相關。

   篩選( `<orderby>`  )和限制(  `<where>`  )元素。

   在此示例中，對於每個收件者，查詢將返回收件者訂閱的電子郵件和資訊服務清單：

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

#### 綁定&#39;where&#39;和&#39;select&#39;子句的參數 {#binding-the-parameters-of-the--where--and--select--clause}

參數的捆綁可讓引擎設定查詢中使用的參數的值。 這非常有用，因為引擎負責值的逸出，而且快取對於要擷取的參數有額外的好處。

建構查詢時，「界定」值會由字元(? 在ODBC中， `#[index]#` （在postgres...），在SQL查詢的正文中。

```
<select>
  <!--the value will be bound by the engine -->
  <node expr="@startDate = #2002/02/01#"/>                   
  <!-- the value will not be bound by the engine but visible directly in the query -->
  <node expr="@startDate = #2002/02/01#" noSqlBind="true"/> 
</select>
```

要避免綁定參數，必須用值「true」填充「noSqlBind」屬性。

>[!IMPORTANT]
>
>如果查詢包含「order-by」或「group-by」指令，則資料庫引擎將無法「綁定」值。 必須將@noSqlBind=&quot;true&quot;屬性放置在查詢的&quot;select&quot;和/或&quot;where&quot;指示上。

#### 查詢建立提示： {#query-building-tip-}

若要協助處理查詢的語法，您可以使用Adobe Campaign用戶端主控台中的一般查詢編輯器( **[!UICONTROL Tools/ Generic query editor...]** 功能表)。 操作步驟：

1. 選取要擷取的資料：

   ![](assets/s_ncs_integration_webservices_queyr1.png)

1. 定義篩選條件：

   ![](assets/s_ncs_integration_webservices_queyr2.png)

1. 執行查詢並按CTRL+F4以查看查詢原始碼。

   ![](assets/s_ncs_integration_webservices_queyr3.png)

### 輸出文檔格式 {#output-document-format}

返回參數是與查詢關聯的架構格式的XML文檔。

從&quot;get&quot;操作上的&quot;nms:recipient&quot;架構傳回的範例：

```
<recipient email="john.doe@adobe.com" lastName"Doe" firstName="John"/>
```

在「select」操作中，傳回的檔案是元素的列舉：

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

別名可讓您修改輸出檔案中的資料位置。 此 **別名** 屬性必須在對應欄位上指定XPath。

```
<queryDef schema="nms:recipient" operation="get">
  <select>
    <node expr="@firstName" alias="@firstName"/>
    <node expr="@lastName"/>
    <node expr="[folder/@label]" alias="@My_folder"/>
  </select> 
</queryDef>
```

傳回：

```
<recipient My_folder="Recipients" First name ="John" lastName="Doe"/>
```

而非：

```
<recipient firstName="John" lastName="Doe">
  <folder label="Recipients"/>
</recipient>
```

### SOAP消息的示例 {#example-of-soap-messages}

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

* 回應：

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

## Write/WriteCollection(xtk:session) {#write---writecollection--xtk-session-}

這些服務用於插入、更新或刪除實體（「寫入」方法）或實體集合（「寫入收集」方法）。

要更新的實體與資料架構相關聯。 輸入參數是驗證字串（必須登錄）和包含要更新資料的XML文檔。

本文檔還附有配置寫程式的說明。

呼叫不會傳回任何資料，但發生錯誤除外。

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
>這是「靜態」方法。 輸入參數以要更新的架構格式包含在XML文檔中。

### 概覽 {#overview}

資料協調會根據在相關聯架構中輸入之索引鍵的定義而運作。 寫入過程基於輸入文檔中輸入的資料來查找第一合格密鑰。 根據實體在資料庫中的存在，插入或更新實體。

要更新之實體架構的索引鍵會根據 **xtkschema** 屬性。

因此，調解金鑰可以使用 **_key** 包含組成索引鍵的XPaths清單的屬性（以逗號分隔）。

可借由填入 **_operation** 屬性，且值如下：

* **插入**:強制插入記錄（不使用調解金鑰）,
* **insertOrUpdate**:根據調解鍵（預設模式）更新或插入記錄，
* **更新**:更新記錄；若資料不存在，則不會執行任何動作，
* **刪除**:刪除記錄，
* **無**:僅用於連結調解，不需更新或插入。

### 「Write」方法的範例 {#example-with-the--write--method}

使用電子郵件地址、出生日期和鎮更新或插入收件者（隱含的「insertOrUpdate」操作）:

```
<recipient xtkschema="nms:recipient" email="john.doe@adobe.com" birthDate="1956/05/04" folder-id=1203 _key="@email, [@folder-id]">
  <location city="Newton"/>
</recipient>
```

刪除收件者：

```
<recipient xtkschema="nms:recipient" _operation="delete" email="rene.dupont@adobe.com" folder-id=1203 _key="@email, [@folder-id]"/>
```

>[!NOTE]
>
>對於刪除操作，輸入文檔只能包含構成調解密鑰的欄位。

### &#39;WriteCollection&#39;方法的範例 {#example-with-the--writecollection--method}

更新或插入多個收件者：

```
<recipient-collection xtkschema="nms:recipient">    
  <recipient email="john.doe@adobe.com" firstName="John" lastName="Doe" _key="@email"/>
  <recipient email="peter.martinez@adobe.com" firstName="Peter" lastName="Martinez" _key="@email"/>
  <recipient ...
</recipient-collection>
```

### 連結範例 {#example-on-links}

#### 範例1 {#example-1}

根據資料夾的內部名稱(@name)將資料夾與收件者關聯。

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <folder name="Folder2" _operation="none"/>
</recipient>
```

可在連結的元素上輸入「_key」和「_operation」屬性。 此元素上的行為與輸入架構之主要元素上的行為相同。

主實體(「nms:recipient」)的鍵的定義由連結表（元素）中的欄位組成 `<folder>`  結構&quot;xtk:folder&quot;)和電子郵件。

>[!NOTE]
>
>在資料夾元素上輸入的操作「無」定義了資料夾上的協調，無需更新或插入。

#### 範例2 {#example-2}

從收件者更新公司（「cus:company」架構中的連結表格）:

```
<recipient _key="[folder/@name], @email" email="john.doe@adobe.net" lastName="Doe" firstName="John" xtkschema="nms:recipient">
  <company name="adobe" code="ERT12T" _key="@name" _operation="update"/>
</recipient>
```

#### 範例3 {#example-3}

將收件者新增至具有群組關係表(&quot;nms:rcpGrpRel&quot;)的群組：

```
<recipient _key="@email" email="martin.ledger@adobe.net" xtkschema="nms:recipient">
  <rcpGrpRel _key="[rcpGroup/@name]">
    <rcpGroup name="GRP1"/>
  </rcpGrpRel>
</recipient>
```

>[!NOTE]
>
>未在 `<rcpgroup>` 元素，因為在「nms:group」架構中定義了基於組名的隱式鍵。

### XML集合元素 {#xml-collection-elements}

預設情況下，必須填入所有集合元素，才能更新XML集合元素。 來自資料庫的資料將替換為來自輸入文檔的資料。 如果文檔僅包含要更新的元素，則必須在要更新的所有收集元素上填充「_operation」屬性，以強制與資料庫的XML資料合併。

### SOAP消息的示例 {#example-of-soap-messages-1}

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

* 回應：

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <WriteResponse xmlns='urn:' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </WriteResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

   返回，但出現錯誤：

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
