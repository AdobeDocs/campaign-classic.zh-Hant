---
title: Web服務呼叫
seo-title: Web服務呼叫
description: Web服務呼叫
seo-description: null
page-status-flag: never-activated
uuid: 7defe0e4-bb4a-4f6a-b6e8-e2ffac73b4c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 6934c165-6d27-4ce5-8607-170f299b4702
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a527f246c4b0bf84c2a83e8df74b7a92542fda7a

---


# Web服務呼叫{#web-service-calls}

## 一般資訊 {#general-information}

所有API方法都以Web services的形式呈現。 這可讓您透過SOAP呼叫管理所有Adobe Campaign功能，而SOAP呼叫是Adobe Campaign應用程式伺服器的原生入口點。 Adobe Campaign主控台本身僅使用SOAP呼叫。

Web services可讓您從協力廠商系統建立許多應用程式：

* 從後端辦公室或交易系統執行同步警報、通知和即時傳送範本，
* 開發具有簡化功能的特殊介面（Web介面等）、
* 在遵守貿易規則並與基礎物理模型保持隔離的同時，餵送和查找資料庫中的資料。

## Web服務的定義 {#definition-of-web-services}

Adobe Campaign應用程式伺服器上實作的網站服務定義可從資料結構描述中取得。

Web服務在資料模式的語法中描述，並且可從元素中 **`<methods>`** 使用。

```
<methods>
  <method name="GenerateForm" static="true">
    <help>Generates the form in Mail or Web mode</help>
    <parameters>
      <param name="formName" type="string" desc="Name of form"/>
      <param name="mailMode" type="boolean" desc="Generate a form of type Mail"/>
      <param name="result" type="string" inout="out" desc="Result "/>
    </parameters>
  </method>
</methods>
```

這裡我們有一個名為 **GenerateForm的方法定義示例**。

服務的說明從元素開 `<method>` 始。 從元素中完成方法的參數列 `<parameters>` 表。 每個參數都由名稱、類型（布林值、字串、DOMElement等）指定和說明。 具有&quot;out&quot;值的&quot;inout&quot;屬性可讓您指定&quot;result&quot;參數位於SOAP呼叫輸出。

存在&quot;static&quot;屬性（值為&quot;true&quot;）將此方法描述為static，這表示必須聲明方法的所有參數。

「const」方法隱式地將XML文檔以其相關模式的格式作為輸入。

Adobe Campaign結構描述 `<method>` 的元素完整說明，請參閱「結構描述參考」一章， <a href="../../configuration/using/elements-and-attributes.md#method--element" target="_blank">  `<method>`    元素。

&quot;xtk:queryDef&quot;架構中的&quot;const&quot;類型&quot;ExecuteQuery&quot;方法範例：

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

此方法的輸入參數是XML文檔，格式為&quot;xtk:queryDef&quot;模式。

## Web服務說明：WSDL {#web-service-description--wsdl}

每個服務都有一個WSDL（Web服務說明庫）檔案。 此XML檔案使用元語言來描述服務，並指定可用的方法、參數和伺服器，以便與其聯繫以執行服務。

### WSDL檔案產生 {#wsdl-file-generation}

要生成WSDL檔案，必須從Web瀏覽器輸入以下URL:

[https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

使用：

* **`<server>`**:Adobe Campaign應用程式伺服器(nlserver web)
* **`<schema>`**:方案標識鍵(namespace:schema_name)

### 模式&#39;xtk:queryDef&#39;的&#39;ExecuteQuery&#39;方法範例 {#example-on-the--executequery--method-of-schema--xtk-querydef-}

WSDL檔案是從URL生成的：

[https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef](https://my_serveur/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef)

WSDL說明首先定義用於形成消息的類型，這些消息與&quot;ports&quot;關聯，通過&quot;bindings&quot;形成Web服務，與協定連接。

#### 類型 {#types}

類型定義基於XML結構描述。 在我們的範例中，&quot;ExecuteQuery&quot;方法會使用&quot;s:string&quot;字串和XML檔案(`<s:complextype>`)做為參數。 方法的返回值(&quot;ExecuteQueryResponse&quot;)是XML文檔( `<s:complextype>`)。

```
<types>
<s:schema elementFormDefault="qualified" targetNamespace="urn:xtk:queryDef">
  <s:element name="ExecuteQuery">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="sessiontoken" type="s:string"/>
        <s:element maxOccurs="1" minOccurs="1" name="entity">
          <s:complexType>
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
  <s:element name="ExecuteQueryResponse">
    <s:complexType>
      <s:sequence>
        <s:element maxOccurs="1" minOccurs="1" name="pdomOutput">
          <s:complexType mixed="true">
            <s:sequence>
              <s:any/>
            </s:sequence>
          </s:complexType>
        </s:element>
      </s:sequence>
    </s:complexType>
  </s:element>
```

#### Messages {#messages}

說 `<message>` 明要發送的一組欄位的名稱和類型。 該方法使用兩條消息作為參數(&quot;ExecuteQueryIn&quot;)和返回值(&quot;ExecuteQueryOut&quot;)進行傳遞。

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### 埠類型 {#porttype}

關 `<porttype>` 聯由查詢（「輸入」）觸發的&quot;ExecuteQuery&quot;操作的消息，生成響應（「輸出」）。

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### 系結 {#binding}

該 `<binding>` 部分指定SOAP通信協定( `<soap:binding>` )、HTTP中的資料傳輸（&quot;transport&quot;屬性的值）和&quot;ExecuteQuery&quot;操作的資料格式。 SOAP封套的內文直接包含訊息區段，而不需進行轉換。

```
<binding name="queryDefMethodsSoap" type="tns:queryDefMethodsSoap">
  <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
  <operation name="ExecuteQuery">
    <soap:operation soapAction="xtk:queryDef#ExecuteQuery" style="document"/>
    <input>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </input>
    <output>
      <soap:body encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:xtk:queryDef" use="literal"/>
    </output>
  </operation>
</binding>
```

#### 服務 {#service}

本 `<service>` 部分說明「XtkQueryDef」服務及其URI（位於Adobe Campaign應用程式伺服器的URL）。

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## 連接性 {#connectivity}

Adobe Campaign透過引入安全區(請參閱本節中的「定義安全區 **」一章**[](../../installation/using/configuring-campaign-server.md#defining-security-zones))以及會話管理設定，提高了驗證機制的安全性。

有兩種可用的驗證模式：

* **透過對logon方法()的呼叫**。 此模式會產生作業Token與安全Token。 這是最安全的模式，因此建議使用最多。

或

* **透過Adobe Campaign登入+密碼** ，建立工作階段Token。 作業Token會在設定的時段後自動過期。 不建議使用此模式，並需要減少某些區域設定的應用程式安全性設定（allowUserPassword=&quot;true&quot;和sessionTokenOnly=&quot;true&quot;）。

### 作業Token特性 {#session-token-characteristics}

工作階段Token具有下列特性：

* a X hour life cycle(life cycle is configurable in the &#39;serverConf.xml&#39; file, the default period is 24 hours)
* 隨機構造（不再包含使用者登入和密碼）
* 透過Web存取時：

   * 作業Token會變成永久Token，但瀏覽器關閉後不會銷毀它
   * 它會置於HTTP-ONLY Cookie（必須為運算子啟用Cookie）

### 安全令牌特性 {#security-token-characteristics}

安全令牌具有以下特徵：

* 它是從工作階段Token產生
* 其生命週期為24小時（可在&#39;serverConf.xml&#39;檔案中設定，預設期間為24小時）
* 它會儲存在Adobe Campaign主控台中
* 透過Web存取時：

   * 會儲存在檔案中。__securityToken屬性
   * 頁面URL會更新，以更新安全性Token
   * 表單也會透過包含代號的隱藏欄位來更新

#### 安全令牌移動 {#security-token-movement}

通過控制台訪問時，它是：

* 在登錄響應中傳輸（在HTTP標題中）
* 用於每個查詢（在HTTP標題中）

從POST和GET HTTP:

* 伺服器使用Token完成連結
* 伺服器在表格中新增隱藏欄位

從SOAP呼叫：

* 新增至呼叫標題

### 呼叫範例 {#call-examples}

* 使用 **HttpSoapConnection/SoapService**:

   ```
     var cnx = new HttpSoapConnection("https://serverURL/nl/jsp/soaprouter.jsp");
   var session = new SoapService(cnx, 'urn:xtk:session');
   session.addMethod("Logon", "xtk:session#Logon",
                       ["sessiontoken", "string", "Login", "string", "Password", "string", "Parameters", "NLElement"],
                       ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
   
   var res = session.Logon("", "admin", "pwd", <param/>);
   var sessionToken = res[0];
   var securityToken = res[2];
   
   cnx.addTokens(sessionToken, securityToken);
   var query = new SoapService(cnx, 'urn:xtk:queryDef');
   query.addMethod("ExecuteQuery", "xtk:queryDef#ExecuteQuery",
                       ["sessiontoken", "string", "entity", "NLElement"],
                       ["res", "NLElement"]);
   
   var queryRes = query.ExecuteQuery("", <queryDef operation="select" schema="nms:recipient">
             <select>
               <node expr="@email"/>
               <node expr="@lastName"/>
               <node expr="@firstName"/>
             </select>
             <where>
               <condition expr="@email = 'joe.doe@aol.com'"/>
             </where>
           </queryDef>);
   logInfo(queryRes[0].toXMLString())
   ```

* 使用 **HttpServletRequest**:

>[!NOTE]
>
>下列 **HttpServletRequest** Calls中使用的URL，必須在serverConf.xml檔案的url權限區 **** 段中加入白名單。 伺服器本身的URL也是如此。

登錄執行():

```
var req = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req.header["Content-Type"] = "text/xml; charset=utf-8";
req.header["SOAPAction"] =   "xtk:session#Logon";
req.method = "POST";
req.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:session">' +
  '<soapenv:Header/>' +
  '<soapenv:Body>' +
      '<urn:Logon>' +
          '<urn:sessiontoken></urn:sessiontoken>' +
          '<urn:strLogin>LOGIN_HERE</urn:strLogin>' +
          '<urn:strPassword>PASSWORD_HERE</urn:strPassword>' +
          '<urn:elemParameters></urn:elemParameters>' +
      '</urn:Logon>' +
  '</soapenv:Body>' +
'</soapenv:Envelope>';
req.execute();
         
var resp = req.response;
var xmlRes = new XML(String(resp.body).replace("<?xml version='1.0'?>",""));
var sessionToken = String(xmlRes..*::pstrSessionToken);;
var securityToken = String(xmlRes..*::pstrSecurityToken);
```

查詢執行：

```
var req2 = new HttpClientRequest("https://serverURL/nl/jsp/soaprouter.jsp");
req2.header["Content-Type"] = "text/xml; charset=utf-8";
req2.header["SOAPAction"] =   "xtk:queryDef#ExecuteQuery";req2.header["X-Security-Token"] = securityToken;
req2.header["cookie"]           = "__sessiontoken="+sessionToken;
req2.method = "POST";
req2.body = '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:xtk:queryDef">' +
           '<soapenv:Header/><soapenv:Body><urn:ExecuteQuery><urn:sessiontoken/><urn:entity>' +
              '<queryDef operation="select" schema="nms:recipient">' +
                '<select><node expr="@email"/><node expr="@lastName"/><node expr="@firstName"/></select>' +
                '<where><condition expr="@email = \'john.doe@aol.com\'"/></where>' +
              '</queryDef>' +
         '</urn:entity></urn:ExecuteQuery></soapenv:Body></soapenv:Envelope>';
req2.execute();
var resp2 = req2.response;
logInfo(resp2.body)
```

