---
product: campaign
title: 關於 Web 服務
description: 關於 Web 服務
feature: API
role: Data Engineer, Developer
exl-id: 7aa2aef1-2eb6-48a6-82fa-4451bed66216
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 3%

---

# 關於 Web 服務{#about-web-services}

## Adobe Campaign API的定義 {#definition-of-adobe-campaign-apis}

Adobe Campaign應用程式伺服器的設計初衷是開放性以及可輕鬆整合日益多樣化且複雜的公司資訊系統。

Adobe Campaign API可用於應用程式內的JavaScript中，以及應用程式外的SOAP中。 它們構成了可以擴充的一般函式庫。 如需進一步資訊，請參閱[實作SOAP方法](../../configuration/using/implementing-soap-methods.md)。

>[!IMPORTANT]
>
>授權引擎每日的通話次數視您的授權合約而定。 如需詳細資訊，請參閱[此頁面](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-campaign-classic---product-description.html)。\
>[此專屬檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html)提供所有API的清單，包括其完整說明。

## 先決條件 {#prerequisites}

使用Adobe Campaign API之前，您必須熟悉下列主題：

* JavaScript
* SOAP通訊協定
* Adobe Campaign資料模型

## 使用Adobe Campaign API {#using-adobe-campaign-apis}

Adobe Campaign使用兩種型別的API：

* 用於查詢資料模型資料的一般資料存取API。 請參閱[資料導向API](../../configuration/using/data-oriented-apis.md)。
* 業務特定API可讓您對每個物件執行動作：傳送、工作流程、訂閱等。 請參閱[商業導向API](../../configuration/using/business-oriented-apis.md)。

為了開發API並與Adobe Campaign互動，您需要熟悉您的資料模型。 Adobe Campaign可讓您產生基底的完整說明。 請參閱模型](../../configuration/using/data-oriented-apis.md#description-of-the-model)的[描述。

## SOAP 呼叫 {#soap-calls}

SOAP通訊協定可讓您透過豐富使用者端、使用Web服務的協力廠商應用程式或原生使用這些方法的JSP來叫用API方法。

![](assets/s_ncs_configuration_architecture.png)

SOAP訊息的結構如下：

* 定義訊息結構的封套，
* 選用的標頭，
* 內含呼叫和回應相關資訊的主體，
* 定義錯誤條件的錯誤管理。

## 資源與交換 {#resources-and-exchanges}

下列結構描述顯示與使用Adobe Campaign API有關的各種資源：

![](assets/s_ncs_integration_webservices_schema_pres.png)

## &#39;ExecuteQuery&#39;方法上的SOAP訊息範例 {#example-of-a-soap-message-on-the--executequery--method--}

在此範例中，SOAP查詢會叫用「ExecuteQuery」方法，此方法會將字元字串當作用於驗證（工作階段權杖）的引數，以及當作要執行之查詢說明的XML內容。

如需進一步資訊，請參閱[ExecuteQuery (xtk：queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-)。

>[!NOTE]
>
>此服務的WSDL描述在此範例中完成： [Web服務描述： WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl)。

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

`<soap-env:envelope>`元素是代表SOAP信封之訊息的第一個元素。

`<soap-env:body>`專案是信封的第一個子專案。 它包含訊息的說明，即查詢或回應的內容。

要叫用的方法是在SOAP訊息本文的`<executequery>`元素中輸入。

在SOAP中，會依外觀順序來辨識引數。 第一個引數`<__sessiontoken>`採用驗證鏈結，第二個引數是來自`<querydef>`元素的查詢的XML描述。

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

查詢結果是從`<pdomoutput>`專案輸入的。

## 錯誤管理 {#error-management}

SOAP錯誤回應範例：

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

SOAP訊息內文中的`<soap-env:fault>`元素是用來傳達處理網站服務期間產生的錯誤訊號。 它由下列子元素組成：

* `<faultcode>` ：指出錯誤的型別。 錯誤型別為：

   * 若與所使用的SOAP版本不相容，
   * 「MustUnderstand」在訊息標頭發生問題的情況下，
   * 「使用者端」在使用者端遺失某些資訊時，
   * 「伺服器」（在伺服器執行處理時發生問題的事件中）。

* `<faultstring>` ：描述錯誤的訊息
* `<detail>` ：長錯誤訊息

驗證`<faultcode>`專案時，會識別服務引動成功或失敗。

>[!IMPORTANT]
>
>所有Adobe Campaign Web服務都會處理錯誤。 因此，強烈建議您測試每個呼叫，以便處理傳回的錯誤。

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

## Web服務伺服器（或端點）的URL {#url-of-web-service-server--or-endpoint-}

若要提交Web服務，必須聯絡實作對應服務方法的Adobe Campaign伺服器。

伺服器URL如下：

https://serverName/nl/jsp/soaprouter.jsp

使用&#x200B;**`<server>`** Adobe Campaign應用程式伺服器(**nlserver web**)。
