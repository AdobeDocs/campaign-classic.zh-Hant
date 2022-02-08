---
product: campaign
title: 關於 Web 服務
description: 關於 Web 服務
feature: API
exl-id: 7aa2aef1-2eb6-48a6-82fa-4451bed66216
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 3%

---

# 關於 Web 服務{#about-web-services}

![](../../assets/v7-only.svg)

## Adobe CampaignAPI的定義 {#definition-of-adobe-campaign-apis}

Adobe Campaign應用伺服器旨在與日益多樣化和複雜的公司資訊系統實現開放和輕鬆整合。

Adobe CampaignAPI在應用程式內的JavaScript中和應用程式外的SOAP中使用。 它們組成了一個泛型函式館，可以加以豐富。 有關詳細資訊，請參閱 [實現SOAP方法](../../configuration/using/implementing-soap-methods.md)。

>[!IMPORTANT]
>
>每天授權引擎呼叫的數量因您的許可證合同而異。 如需詳細資訊，請參閱[此頁面](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-campaign-classic---product-description.html)。\
>所有API（包括其完整說明）的清單可在 [此專用文檔](https://experienceleague.adobe.com/developer/campaign-api/api/index.html)。

## 必要條件 {#prerequisites}

在使用Adobe CampaignAPI之前，您需要熟悉以下主題：

* Javascript
* SOAP協定
* Adobe Campaign資料模型

## 使用Adobe CampaignAPI {#using-adobe-campaign-apis}

Adobe Campaign使用兩種類型的API:

* 用於查詢資料模型資料的通用資料存取API。 請參閱 [面向資料的API](../../configuration/using/data-oriented-apis.md)。
* 業務特定的API，允許您對每個對象執行操作：交貨、工作流、訂閱等。 請參閱 [面向業務的API](../../configuration/using/business-oriented-apis.md)。

為了開發API並與Adobe Campaign進行交互，您需要熟悉您的資料模型。 Adobe Campaign讓您生成基礎的完整說明。 請參閱 [模型描述](../../configuration/using/data-oriented-apis.md#description-of-the-model)。

## SOAP調用 {#soap-calls}

SOAP協定允許您通過富客戶端、使用web服務的第三方應用程式或使用這些方法的JSP來調用API方法。

![](assets/s_ncs_configuration_architecture.png)

SOAP消息的結構如下：

* 一個信封，它定義了資訊的結構，
* 可選標題，
* 一個包含有關呼叫和應答資訊的機構，
* 定義錯誤條件的錯誤管理。

## 資源和交流 {#resources-and-exchanges}

以下模式顯示了使用Adobe CampaignAPI時涉及的各種資源：

![](assets/s_ncs_integration_webservices_schema_pres.png)

## 「ExecuteQuery」方法上的SOAP消息示例 {#example-of-a-soap-message-on-the--executequery--method--}

在本示例中，SOAP查詢調用&quot;ExecuteQuery&quot;方法，該方法將字串作為驗證（會話令牌）的參數和要執行的查詢描述的XML內容。

有關詳細資訊，請參閱 [ExecuteQuery(xtk:queryDef)](../../configuration/using/data-oriented-apis.md#executequery--xtk-querydef-)。

>[!NOTE]
>
>此服務的WSDL說明在下面所示的示例中完成： [Web服務說明：WSDL](../../configuration/using/web-service-calls.md#web-service-description--wsdl)。

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

的 `<soap-env:envelope>` element是表示SOAP信封的消息的第一個元素。

的 `<soap-env:body>` 元素是封套的第一個子元素。 它包含消息的說明，即查詢或響應的內容。

要調用的方法在 `<executequery>` SOAP消息正文中的元素。

在SOAP中，參數按外觀順序識別。 第一個參數， `<__sessiontoken>`，採用驗證鏈，第二個參數是來自 `<querydef>` 的子菜單。

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

查詢的結果是從 `<pdomoutput>` 的子菜單。

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

的 `<soap-env:fault>` SOAP消息本體中的元素用於傳送在Web服務處理過程中產生的錯誤信號。 這由以下子元素組成：

* `<faultcode>` :指示錯誤類型。 錯誤類型為：

   * 在與使用的SOAP版本不相容時，
   * 如果郵件頭中出現問題，
   * 如果客戶端缺少某些資訊，
   * 如果伺服器在執行處理時出現問題，則為「伺服器」。

* `<faultstring>` :描述錯誤的消息
* `<detail>` :長錯誤消息

當服務調用 `<faultcode>` 元素已驗證。

>[!IMPORTANT]
>
>所有Adobe CampaignWeb服務都處理錯誤。 因此，強烈建議test每個調用以處理返回的錯誤。

C#中錯誤處理示例：

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

要提交Web服務，必須聯繫執行相應服務方法的Adobe Campaign伺服器。

伺服器URL如下所示：

https://serverName/nl/jsp/soaprouter.jsp

與 **`<server>`** Adobe Campaign應用程式伺服器(**nlserver web**)。
