---
title: 關於web services
seo-title: 關於web services
description: 關於web services
seo-description: null
page-status-flag: never-activated
uuid: f0b21cb3-aa75-4f54-a9f5-64e880f93e53
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 65919173-3ce0-4d98-936b-f4581df536ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a047e4af6e31c54fa2444943a18da5913e115c09

---


# 關於web services{#about-web-services}

## Adobe Campaign API的定義 {#definition-of-adobe-campaign-apis}

Adobe Campaign應用程式伺服器旨在開放並輕鬆與日益多樣化和複雜的公司資訊系統整合。

Adobe Campaign API用於應用程式內的JavaScript，以及應用程式外的SOAP中。 它們組成了一個通用功能庫，可以加以豐富。 如需詳細資訊，請參 [閱實作SOAP方法](../../configuration/using/implementing-soap-methods.md)。

>[!IMPORTANT]
>
>每天授權引擎呼叫的數目視您的授權合約而定。 有關詳細資訊，請參見[此頁面](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-classic---product-description.html)。\
>本專屬檔案提供所有API的清單，包括其完整 [說明](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)。

## 必要條件 {#prerequisites}

在使用Adobe Campaign API之前，您必須熟悉下列主題：

* Javascript
* SOAP協定
* Adobe Campaign資料模型

## 使用Adobe Campaign API {#using-adobe-campaign-apis}

Adobe Campaign使用兩種類型的API:

* 一般資料會存取API以查詢資料模型資料。 請參閱 [資料導向API](../../configuration/using/data-oriented-apis.md)。
* 可讓您對每個物件採取行動的商業專用API:傳送、工作流程、訂閱等。 請參閱 [商業導向API](../../configuration/using/business-oriented-apis.md)。

為了開發API並與Adobe Campaign互動，您必須熟悉您的資料模型。 Adobe Campaign可讓您產生基本內容的完整說明。 請參閱 [模型說明](../../configuration/using/data-oriented-apis.md#description-of-the-model)。

## SOAP呼叫 {#soap-calls}

SOAP通訊協定可讓您透過rich client、使用webservices的協力廠商應用程式或使用這些方法的JSP，來叫用API方法。

![](assets/s_ncs_configuration_architecture.png)

SOAP消息的結構如下：

* 一個封套，它定義了資訊的結構，
* 可選標題，
* 一個包含呼叫和回應資訊的機構，
* 定義錯誤條件的錯誤管理。

## 資源與交流 {#resources-and-exchanges}

下列結構說明使用Adobe Campaign API時涉及的各種資源：

![](assets/s_ncs_integration_webservices_schema_pres.png)

## 關於&#39;ExecuteQuery&#39;方法的SOAP消息示例 {#example-of-a-soap-message-on-the--executequery--method--}

在此範例中，SOAP查詢會叫用&quot;ExecuteQuery&quot;方法，此方法會將字元字串作為驗證（作業Token）的參數，並將XML內容用於要執行的查詢說明。

如需詳細資訊，請參 [閱ExecuteQuery(xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-)。

>[!NOTE]
>
>此服務的WSDL說明已在以下示例中完成：網 [站服務說明：WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl).

### SOAP查詢 {#soap-query}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQuery xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <__sessiontoken xsi:type='xsd:string'/>
        <entity xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <queryDef firstRows="true" lineCount="200" operation="select" schema="nms:rcpGrpRel" startLine="0" startPath="/" xtkschema="xtk:queryDef">
          ...
          </queryDef>
        </entity>
      </ExecuteQuery>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

元 `<soap-env:envelope>` 素是表示SOAP封套的訊息的第一個元素。

元 `<soap-env:body>` 素是封套的第一個子元素。 它包含訊息的說明，即查詢或回應的內容。

要調用的方法是從SOAP消 `<executequery>` 息的主體中在元素中輸入的。

在SOAP中，參數是按外觀順序識別的。 第一個參 `<__sessiontoken>`數，取用驗證鏈，第二個參數是元素中查詢的XML描 `<querydef>` 述。

### SOAP回應 {#soap-response}

```
<?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <ExecuteQueryResponse xmlns='urn:xtk:queryDef' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
        <pdomOutput xsi:type='ns:Element' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
          <rcpGrpRel-collection><rcpGrpRel group-id="1872" recipient-id="1362"></rcpGrpRel></rcpGrpRel-collection>
        </pdomOutput>
      </ExecuteQueryResponse>
    </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

查詢結果是從元素中輸 `<pdomoutput>` 入。

## 錯誤管理 {#error-management}

SOAP錯誤響應示例：

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <SOAP-ENV:Fault>
      <faultcode>SOAP-ENV:Server</faultcode>
      <faultstring>Error while executing 'Write' of the 'xtk:persist'.</faultstring> service
      <detail>ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]Cannot insert duplicate key row in object 'XtkOption' with unique index 'XtkOption_name'. SQLSTate: 23000
ODBC error: [Microsoft][ODBC SQL Server Driver][SQL Server]The statement has been terminated. SQLSTate: 01000 Cannot save the 'Options (xtk:option)' document </detail>
    </SOAP-ENV:Fault>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

SOAP `<soap-env:fault>` 消息本體中的元素用於傳送在Web服務處理期間產生的錯誤信號。 這由下列子元素組成：

* `<faultcode>` :表示錯誤的類型。 錯誤類型包括：

   * 如果與使用的SOAP版本不相容，
   * 如果消息標題中出現問題，則為&quot;MustUnderstand&quot;,
   * 「客戶端」，如果客戶端缺少某些資訊，
   * 「Server」（伺服器），在伺服器執行處理時發生問題。

* `<faultstring>` :描述錯誤的消息
* `<detail>` :長錯誤消息

當驗證該元素時，標識服務調用的成 `<faultcode>` 功或失敗。

>[!IMPORTANT]
>
>所有Adobe Campaign網站服務都會處理錯誤。 因此強烈建議您測試每個呼叫，以處理傳回的錯誤。

C#中的錯誤處理範例：

```
try 
{
  // Invocation of method
  ...
}
catch (SoapException e)
{
  System.Console.WriteLine("Soap exception: " + e.Message);        
  if (e.Detail != null)
    System.Console.WriteLine(e.Detail.InnerText);
}
```

## Web服務伺服器（或EndPoint）的URL {#url-of-web-service-server--or-endpoint-}

若要提交Web服務，必須聯絡實作相應服務方法的Adobe Campaign伺服器。

伺服器URL如下：

https://serverName/nl/jsp/soaprouter.jsp

使用 **`<server>`** Adobe Campaign應用程式伺服器(**nlserver web**)。
