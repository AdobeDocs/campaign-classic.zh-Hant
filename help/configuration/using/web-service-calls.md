---
product: campaign
title: Web 服務呼叫
description: Web 服務呼叫
audience: configuration
content-type: reference
topic-tags: api
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 1%

---

# Web 服務呼叫{#web-service-calls}

![](../../assets/v7-only.svg)

## 一般資訊 {#general-information}

所有API方法都以Web服務的形式呈現。 這可讓您透過SOAP呼叫(即Adobe Campaign應用程式伺服器的原生入口點)來管理所有Adobe Campaign函式。 Adobe Campaign主控台本身僅使用SOAP呼叫。

網站服務可讓您從協力廠商系統建立許多應用程式：

* 從後台或交易系統執行同步警報、通知和即時傳遞模板
* 開發具有簡化功能的特殊介面（Web介面等）,
* 在遵守貿易規則的同時饋送和查詢資料庫中的資料，並與基礎物理模型保持隔離。

## Web服務的定義 {#definition-of-web-services}

Adobe Campaign應用程式伺服器上實作的Web服務定義，可從資料結構中取得。

資料結構的語法中描述了Web服務，可從&#x200B;**`<methods>`**&#x200B;元素中使用。

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

以下是名為&#x200B;**GenerateForm**&#x200B;的方法定義的示例。

服務的說明以`<method>`元素開頭。 方法的參數清單從`<parameters>`元素中完成。 每個參數都由名稱、類型（布林值、字串、DOMElement等）指定 和描述。 具有「out」值的「inout」屬性可讓您指定「result」參數位於SOAP呼叫輸出。

存在「static」屬性（值為「true」）將此方法描述為靜態，這表示必須聲明方法的所有參數。

「const」方法隱式地將XML文檔作為其輸入，其格式為其關聯架構。

[Method](../../configuration/using/schema/method.md)下的「架構參考」章節提供Adobe Campaign架構的`<method>`元素的完整說明

來自&quot;xtk:queryDef&quot;架構的&quot;const&quot;-type &quot;ExecuteQuery&quot;方法的示例：

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

此方法的輸入參數是格式為「xtk:queryDef」架構的XML文檔。

## Web服務描述：WSDL {#web-service-description--wsdl}

每個服務都有一個WSDL（Web服務描述庫）檔案。 此XML檔案使用元語言來描述服務，並指定可用的方法、參數以及要聯繫執行服務的伺服器。

### WSDL檔案生成 {#wsdl-file-generation}

要生成WSDL檔案，必須從Web瀏覽器輸入以下URL:

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

使用：

* **`<server>`**:Adobe Campaign應用程式伺服器(nlserver web)
* **`<schema>`**:方案標識鍵(namespace:schema_name)

### 架構「xtk:queryDef」的「ExecuteQuery」方法範例 {#example-on-the--executequery--method-of-schema--xtk-querydef-}

WSDL檔案是從URL中生成的：

[https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef](https://my_serveur/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef)

WSDL描述首先定義用於形成消息的類型，這些類型與「埠」關聯，通過「綁定」形成Web服務連接到協定。

#### 類型 {#types}

類型定義以XML結構為基礎。 在我們的範例中，「ExecuteQuery」方法以「s:string」字串和XML檔案(`<s:complextype>`)作為參數。 方法的返回值(&quot;ExecuteQueryResponse&quot;)是XML文檔(`<s:complextype>`)。

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

`<message>`描述了要發送的一組欄位的名稱和類型。 方法使用兩條消息作為參數(&quot;ExecuteQueryIn&quot;)和返回值(&quot;ExecuteQueryOut&quot;)傳遞。

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### 埠類型 {#porttype}

`<porttype>`將查詢(&quot;input&quot;)觸發的&quot;ExecuteQuery&quot;操作上的消息關聯，以生成響應(&quot;output&quot;)。

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### 綁定 {#binding}

`<binding>`部分指定SOAP通信協定(`<soap:binding>`)、HTTP中的資料傳輸（&quot;transport&quot;屬性的值）和&quot;ExecuteQuery&quot;操作的資料格式。 SOAP信封的正文直接包含消息段，無需轉換。

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

`<service>`部分在Adobe Campaign應用程式伺服器的URL上描述了「XtkQueryDef」服務及其URI。

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## 連接 {#connectivity}

Adobe Campaign已引入[安全區域](../../installation/using/security-zones.md)和工作階段管理設定，借此提高驗證機制的安全性。

可用的驗證模式有兩種：

* **透過對logon方法()的呼叫**。此模式會產生工作階段代號和安全代號。 這是最安全的模式，因此也是最建議的模式。

或

* **透過Adobe Campaign登入+** 密碼建立工作階段Token。工作階段代號會在設定的時段後自動過期。 不建議使用此模式，因此需要減少某些區域設定的應用程式安全設定（allowUserPassword=&quot;true&quot;和sessionTokenOnly=&quot;true&quot;）。

### 工作階段代號特性 {#session-token-characteristics}

工作階段代號具有下列特性：

* a X小時生命週期（生命週期可在&#39;serverConf.xml&#39;檔案中設定，預設期間為24小時）
* 隨機建構（不再包含使用者登入和密碼）
* 透過網路存取時：

   * 工作階段代號會變成永久代號，但瀏覽器關閉後不會銷毀
   * 會放置在HTTP-ONLY Cookie中（運算子必須啟用Cookie）

### 安全令牌特性 {#security-token-characteristics}

安全令牌具有以下特性：

* 會從工作階段權杖產生
* 其生命週期為24小時（可在&#39;serverConf.xml&#39;檔案中設定，預設期間為24小時）
* 它會儲存在Adobe Campaign主控台中
* 透過網路存取時：

   * 它儲存在文檔中。__securityToken屬性
   * 頁面URL會更新，以更新安全權杖
   * 表單也會透過包含代號的隱藏欄位來更新

#### 安全令牌移動 {#security-token-movement}

透過主控台存取時，其為：

* 在登錄響應中傳輸（在HTTP標題中）
* 用於每個查詢（在HTTP標題中）

從POST和GETHTTP:

* 伺服器會使用token完成連結
* 伺服器向表單中添加隱藏欄位

從SOAP調用：

* 它已新增至呼叫標題

### 呼叫範例 {#call-examples}

* 使用&#x200B;**HttpSoapConnection/SoapService**:

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

* 使用&#x200B;**HttpServletRequest**:

>[!NOTE]
>
>下列&#x200B;**HttpServletRequest**&#x200B;呼叫中使用的URL必須位於&#x200B;**serverConf.xml**&#x200B;檔案的url權限區段中的允許清單中。 伺服器本身的URL也是如此。

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
