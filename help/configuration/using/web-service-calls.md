---
product: campaign
title: Web 服務呼叫
description: Web 服務呼叫
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: API
role: Data Engineer, Developer
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 2%

---

# Web 服務呼叫{#web-service-calls}

## 一般資訊 {#general-information}

所有API方法都會以網站服務的形式呈現。 這可讓您透過SOAP呼叫管理所有Adobe Campaign函式，這是Adobe Campaign應用程式伺服器的原生入口點。 Adobe Campaign主控台本身只使用SOAP呼叫。

Web服務可讓您從協力廠商系統建立許多應用程式：

* 來自後台或交易系統的同步警報、通知和即時傳遞範本執行，
* 開發具有簡化功能的特殊介面（網頁介面等）；
* 在觀察交易規則並維持與基礎實體模型隔離的狀態下，饋送及查詢資料庫中的資料。

## Web服務的定義 {#definition-of-web-services}

在Adobe Campaign應用程式伺服器上實作的Web服務定義，可從資料結構描述取得。

Web服務在資料綱要的文法中說明，並且可從以下網址取得： **`<methods>`** 元素。

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

以下是方法定義的範例，稱為 **Generateform**.

服務的說明開頭為 `<method>` 元素。 方法的引數清單是從  `<parameters>` 元素。 每個引數由名稱、型別（布林值、字串、DOMElement等）指定 和說明。 具有「out」值的「inout」屬性可讓您指定「result」引數在SOAP呼叫輸出處。

「static」屬性（值為「true」）的存在說明此方法為static，這表示方法的所有引數都必須宣告。

「const」方法隱含地以關聯結構描述格式的XML檔案作為其輸入。

的完整說明 `<method>` Adobe Campaign結構描述的元素可在「結構描述參考」章節中取得，位於 [方法](../../configuration/using/schema/method.md)

「xtk：queryDef」結構描述中的「const」型別「ExecuteQuery」方法範例：

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

此方法的輸入引數是採用「xtk：queryDef」結構描述格式的XML檔案。

## Web服務說明：WSDL {#web-service-description--wsdl}

每個服務都有WSDL （Web服務描述庫）檔案。 此XML檔案使用元語言來說明服務，並指定要連絡以執行服務的可用方法、引數及伺服器。

### WSDL檔案產生 {#wsdl-file-generation}

若要產生WSDL檔案，您必須從Web瀏覽器輸入下列URL：

https://`<server>`/nl/jsp/schemawsdl.jsp？schema=`<schema>`

替換為：

* **`<server>`**：Adobe Campaign應用程式伺服器(nlserver web)
* **`<schema>`**：結構描述識別金鑰(namespace：schema_name)

### 結構描述「xtk：queryDef」的「ExecuteQuery」方法範例 {#example-on-the--executequery--method-of-schema--xtk-querydef-}

WSDL檔案是從URL產生：

`https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef`

WSDL說明首先會定義用來形成訊息的型別，這些訊息在「連線埠」中關聯，透過「連結」形成Web服務而連線到通訊協定。

#### 型別 {#types}

型別定義以XML結構描述為基礎。 在我們的範例中，「ExecuteQuery」方法採用「s：string」字串和XML檔案(`<s:complextype>`)作為引數。 方法(&quot;ExecuteQueryResponse&quot;)的傳回值是XML檔案(  `<s:complextype>`)。

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

#### 訊息 {#messages}

此 `<message>` 說明要傳送的一組欄位的名稱和型別。 方法使用兩則訊息作為引數(&quot;ExecuteQueryIn&quot;)及傳回值(&quot;ExecuteQueryOut&quot;)來傳遞。

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### 連線埠型別 {#porttype}

此 `<porttype>` 與產生回應（「輸出」）的查詢（「輸入」）所觸發的「ExecuteQuery」作業上的訊息建立關聯。

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### 繫結 {#binding}

此 `<binding>` 部分指定SOAP通訊協定( `<soap:binding>` )、HTTP中的資料傳輸（「transport」屬性的值）和「ExecuteQuery」作業的資料格式。 SOAP信封的主體直接包含訊息區段，而不進行轉換。

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

此 `<service>` 部分說明「XtkQueryDef」服務，其URI位於Adobe Campaign應用程式伺服器的URL上。

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## 連線能力 {#connectivity}

Adobe Campaign已引進以下內容，以提高驗證機制的安全性 [安全性區域](../../installation/using/security-zones.md) 和工作階段管理設定。

有兩種可用的驗證模式：

* **透過呼叫登入方法()**. 此模式會產生工作階段權杖和安全性權杖。 這是最安全的模式，因此也是最推薦的模式。

或

* **透過Adobe Campaign登入+密碼** 會建立工作階段權杖。 工作階段權杖會在設定的期間後自動到期。 不建議使用此模式，因為需要減少某些區域設定（allowUserPassword=&quot;true&quot;及sessionTokenOnly=&quot;true&quot;）的應用程式安全性設定。

### 工作階段權杖特性 {#session-token-characteristics}

工作階段權杖具有以下特性：

* X小時生命週期（可在「serverConf.xml」檔案中設定生命週期，預設期間為24小時）
* 隨機建構（不再包含使用者登入和密碼）
* 透過Web存取時：

   * 工作階段權杖會成為永久權杖，瀏覽器關閉後就不會損毀
   * 它會放在HTTP-ONLY Cookie中（必須為運運算元啟用Cookie）

### 安全性權杖特性 {#security-token-characteristics}

安全性權杖具有以下特性：

* 這會從工作階段權杖產生
* 其生命週期為24小時（可在「serverConf.xml」檔案中設定，預設期間為24小時）
* 它會儲存在Adobe Campaign主控台中
* 透過Web存取時：

   * 它會儲存在檔案中。__securityToken屬性
   * 頁面URL已更新，以更新安全性權杖
   * 表單也會透過包含代號的隱藏欄位進行更新

#### 安全性權杖移動 {#security-token-movement}

透過主控台存取時，它是：

* 在登入回應中傳輸（在HTTP標題中）
* 用於每個查詢（在HTTP標頭中）

從POST和GETHTTP：

* 伺服器會完成具有權杖的連結
* 伺服器會將隱藏欄位新增至表單

從SOAP呼叫：

* 它會新增到呼叫標題

### 呼叫範例 {#call-examples}

* 使用 **HttpSoapConnection/SoapService**：

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

* 使用 **HttpServletRequest**：

>[!NOTE]
>
>以下專案中使用的URL **HttpServletRequest** 呼叫必須位於的url許可權區段中的允許清單 **serverConf.xml** 檔案。 伺服器本身的URL亦是如此。

登入執行()：

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
