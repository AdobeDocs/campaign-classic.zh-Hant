---
product: campaign
title: 關於 Web 服務
description: 關於 Web 服務
audience: configuration
content-type: reference
topic-tags: api
exl-id: 7aa2aef1-2eb6-48a6-82fa-4451bed66216
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 4%

---

# 關於 Web 服務{#about-web-services}

![](../../assets/v7-only.svg)

## Adobe Campaign API的定義 {#definition-of-adobe-campaign-apis}

Adobe Campaign應用程式伺服器旨在實現開放性，與日益多樣化和複雜的公司資訊系統輕鬆整合。

Adobe Campaign API用於應用程式內的JavaScript中，以及其外部的SOAP中。 它們組成可擴充的通用函式程式庫。 有關詳細資訊，請參閱[實作SOAP方法](../../configuration/using/implementing-soap-methods.md)。

>[!IMPORTANT]
>
>每日授權的引擎呼叫數視您的授權合約而定。 如需詳細資訊，請參閱[此頁面](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-campaign-classic---product-description.html)。\
>[此專屬檔案](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)中提供所有API（包括其完整說明）的清單。

## 先決條件 {#prerequisites}

使用Adobe Campaign API之前，您需先熟悉下列主題：

* Javascript
* SOAP協定
* Adobe Campaign資料模型

## 使用Adobe Campaign API {#using-adobe-campaign-apis}

Adobe Campaign使用兩種API:

* 查詢資料模型資料的一般資料存取API。 請參閱[資料導向API](../../configuration/using/data-oriented-apis.md)。
* 可讓您對每個物件採取動作的業務專屬API:傳遞、工作流程、訂閱等。 請參閱[商業導向API](../../configuration/using/business-oriented-apis.md)。

若要開發API並與Adobe Campaign互動，您必須熟悉資料模型。 Adobe Campaign可讓您產生基礎的完整說明。 請參閱[模型說明](../../configuration/using/data-oriented-apis.md#description-of-the-model)。

## SOAP調用 {#soap-calls}

SOAP協定可讓您透過rich用戶端、使用webservices的協力廠商應用程式或原生使用這些方法的JSP來叫用API方法。

![](assets/s_ncs_configuration_architecture.png)

SOAP消息的結構如下：

* 一個信封，它定義了資訊的結構，
* 可選標題，
* 包含呼叫和回應資訊的內文，
* 定義錯誤條件的錯誤管理。

## 資源和交流 {#resources-and-exchanges}

下列結構顯示使用Adobe Campaign API時涉及的各種資源：

![](assets/s_ncs_integration_webservices_schema_pres.png)

## 關於&#39;ExecuteQuery&#39;方法的SOAP消息示例 {#example-of-a-soap-message-on-the--executequery--method--}

在此示例中，SOAP查詢調用「ExecuteQuery」方法，該方法將字元字串作為驗證（會話令牌）的參數，並將XML內容作為要執行的查詢的說明。

有關詳細資訊，請參閱[ExecuteQuery(xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-)。

>[!NOTE]
>
>此服務的WSDL描述已完成，如下所示：[Web服務描述：WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl)。

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

`<soap-env:envelope>`元素是代表SOAP信封的消息的第一個元素。

`<soap-env:body>`元素是信封的第一個子元素。 它包含訊息的說明，即查詢或回應的內容。

要調用的方法是在SOAP消息正文的`<executequery>`元素中輸入的。

在SOAP中，參數是按外觀順序識別的。 第一個參數`<__sessiontoken>`取用驗證鏈，第二個參數是`<querydef>`元素中查詢的XML說明。

### SOAP響應 {#soap-response}

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

查詢結果從`<pdomoutput>`元素中輸入。

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

SOAP消息正文中的`<soap-env:fault>`元素用於傳送在處理Web服務期間產生的錯誤信號。 這由下列子元素組成：

* `<faultcode>` :指示錯誤的類型。錯誤類型為：

   * 若與使用的SOAP版本不相容，則為「VersionMismatch」，
   * 如果郵件標題出現問題，
   * 「客戶」，如果客戶端缺少某些資訊，
   * 「伺服器」，以防伺服器執行處理時發生問題。

* `<faultstring>` :描述錯誤的消息
* `<detail>` :長錯誤消息

驗證`<faultcode>`元素時，識別服務調用的成功或失敗。

>[!IMPORTANT]
>
>所有Adobe Campaign Web服務都會處理錯誤。 因此，強烈建議測試每個呼叫，以處理傳回的錯誤。

C#中的錯誤處理示例：

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

要提交Web服務，必須聯繫實施相應服務方法的Adobe Campaign伺服器。

伺服器URL如下：

https://serverName/nl/jsp/soaprouter.jsp

使用&#x200B;**`<server>`**&#x200B;時，Adobe Campaign應用程式伺服器(**nlserver web**)。
