---
product: campaign
title: Web 服務呼叫
description: Web 服務呼叫
feature: API
exl-id: ce94e7e7-b8f8-4c82-937f-e87d15e50c34
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 1%

---

# Web 服務呼叫{#web-service-calls}

![](../../assets/v7-only.svg)

## 一般資訊 {#general-information}

所有API方法都以Web服務的形式呈現。 這使您能夠通過SOAP調用(即Adobe Campaign應用程式伺服器的本機入口點)管理所有Adobe Campaign函式。 Adobe Campaign控制台本身僅使用SOAP調用。

Web服務允許您從第三方系統建立許多應用程式：

* 從後台辦公室或交易系統執行同步警報、通知和即時交付模板，
* 開發具有簡化功能的特殊介面（Web介面等）,
* 在遵守貿易規則的同時饋送和查找資料庫中的資料，並與基礎物理模型保持隔離。

## Web服務定義 {#definition-of-web-services}

在Adobe Campaign應用伺服器上實現的Web服務的定義可從資料模式中獲得。

Web服務在資料模式的語法中描述，可從 **`<methods>`** 的子菜單。

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

這裡我們有一個定義方法的示例 **生成表單**。

服務的說明以 `<method>` 的子菜單。 方法的參數清單從  `<parameters>` 的子菜單。 每個參數都由名稱、類型（布爾、字串、DOMElement等）指定 和描述。 帶有&quot;out&quot;值的&quot;inout&quot;屬性允許您指定&quot;result&quot;參數位於SOAP調用輸出。

「static」屬性（帶有值「true」）的存在將此方法描述為靜態，這意味著必須聲明該方法的所有參數。

「const」方法隱式地將XML文檔以其關聯架構的格式作為其輸入。

對 `<method>` Adobe Campaign架構的元素可在「架構引用」一章中 [方法](../../configuration/using/schema/method.md)

「xtk:queryDef」架構中「const」類型的「ExecuteQuery」方法的示例：

```
<method name="ExecuteQuery" const="true">
  <help>Retrieve data from a query</help>
  <parameters>
    <param desc="Output xml document" name="output" type="DOMDocument" inout="out"/>
  </parameters>
</method>
```

此方法的輸入參數是格式為&quot;xtk:queryDef&quot;架構的XML文檔。

## Web服務說明：WSDL {#web-service-description--wsdl}

每個服務都有一個WSDL（Web服務說明庫）檔案。 此XML檔案使用metalage來描述服務並指定可用的方法、參數和要聯繫以執行服務的伺服器。

### WSDL檔案生成 {#wsdl-file-generation}

要生成WSDL檔案，必須從Web瀏覽器輸入以下URL:

https://`<server>`/nl/jsp/schemawsdl.jsp?schema=`<schema>`

使用：

* **`<server>`**:Adobe Campaign應用程式伺服器(nlserver web)
* **`<schema>`**:架構標識鍵(namespace:schema_name)

### 架構「xtk:queryDef」的「ExecuteQuery」方法示例 {#example-on-the--executequery--method-of-schema--xtk-querydef-}

WSDL檔案是從URL生成的：

[https://localhost/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef](https://my_serveur/nl/jsp/schemawsdl.jsp?schema=xtk:queryDef)

WSDL說明首先定義用於形成消息的類型，這些類型在「埠」中關聯，通過「綁定」形成Web服務連接到協定。

#### 類型 {#types}

類型定義基於XML架構。 在示例中，&quot;ExecuteQuery&quot;方法採用&quot;s:string&quot;字串和XML文檔(`<s:complextype>`)。 方法的返回值(「ExecuteQueryResponse」)是XML文檔(  `<s:complextype>`)。

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

#### 消息 {#messages}

的 `<message>` 描述了要發送的一組欄位的名稱和類型。 該方法使用兩條消息作為參數(「ExecuteQueryIn」)和返回值(「ExecuteQueryOut」)傳遞。

```
<message name="ExecuteQueryIn">
  <part element="tns:ExecuteQuery" name="parameters"/>
</message>

<message name="ExecuteQueryOut">
  <part element="tns:ExecuteQueryResponse" name="parameters"/>
</message> 
```

#### 埠類型 {#porttype}

的 `<porttype>` 將查詢（「輸入」）觸發的「ExecuteQuery」操作中的消息關聯，生成響應（「輸出」）。

```
<portType name="queryDefMethodsSoap">
  <operation name="ExecuteQuery">
    <input message="tns:ExecuteQueryIn"/>
    <output message="tns:ExecuteQueryOut"/>
  </operation>
</portType>
```

#### 綁定 {#binding}

的 `<binding>` part指定SOAP通信協定( `<soap:binding>` )、HTTP中的資料傳輸（「transport」屬性的值）和「ExecuteQuery」操作的資料格式。 SOAP信封的正文直接包含消息段，而不進行轉換。

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

的 `<service>` 部分描述了「XtkQueryDef」服務，其URI位於Adobe Campaign應用程式伺服器的URL上。

```
<service name="XtkQueryDef">
  <port binding="tns:queryDefMethodsSoap" name="queryDefMethodsSoap">
    <soap:address location="https://localhost/nl/jsp/soaprouter.jsp"/>
  </port>
</service>
```

## 連接 {#connectivity}

Adobe Campaign通過引入認證機制，提高了安全性 [安全區](../../installation/using/security-zones.md) 和會話管理設定。

有兩種可用的身份驗證模式：

* **通過調用logon方法()**。 此模式生成會話令牌和安全令牌。 它是最安全的模式，因此也是最推薦的模式。

或

* **通過Adobe Campaign登錄+密碼** 建立會話令牌。 會話令牌在設定時間段後自動過期。 不建議使用此模式，並需要減少某些區域設定（allowUserPassword=&quot;true&quot;和sessionTokenOnly=&quot;true&quot;）的應用程式安全設定。

### 會話令牌特性 {#session-token-characteristics}

會話令牌具有以下特徵：

* a X小時生命週期（在「serverConf.xml」檔案中可配置生命週期，預設時間為24小時）
* 隨機構造（不再包含用戶登錄和密碼）
* 通過Web訪問時：

   * 會話令牌成為永久令牌，瀏覽器關閉後不會銷毀
   * 它被放置在HTTP-ONLY Cookie中（必須為運算子激活Cookie）

### 安全令牌特性 {#security-token-characteristics}

安全令牌具有以下特徵：

* 它是從會話令牌生成的
* 它具有24小時的生命週期（可在「serverConf.xml」檔案中配置，預設時間為24小時）
* 存放在Adobe Campaign控制台
* 通過Web訪問時：

   * 它儲存在文檔中。__securityToken屬性
   * 更新頁面URL以更新安全令牌
   * 還通過包含令牌的隱藏欄位更新表單

#### 安全令牌移動 {#security-token-movement}

通過控制台訪問時，它是：

* 在登錄響應中傳輸（在HTTP標頭中）
* 用於每個查詢（在HTTP標頭中）

從POST和GETHTTP:

* 伺服器用令牌完成連結
* 伺服器將隱藏欄位添加到表單

從SOAP調用：

* 它添加到呼叫頭

### 調用示例 {#call-examples}

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

* 使用 **HttpServlet請求**:

>[!NOTE]
>
>下列中使用的URL **HttpServlet請求** 呼叫需要位於的url權限部分的允許清單中 **serverConf.xml** 的子菜單。 對於伺服器本身的URL，也是如此。

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
