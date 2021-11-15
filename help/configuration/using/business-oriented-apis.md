---
product: campaign
title: 商業導向 API
description: 商業導向 API
audience: configuration
content-type: reference
topic-tags: api
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: 5d9e2f7d7cea9e6d1243b0e3a790f3990772e603
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 2%

---

# 商業導向 API{#business-oriented-apis}

![](../../assets/v7-only.svg)

業務API是每種物件類型專屬的。 它們對以下方面有影響：

* 傳遞:

   * 建立傳送動作，請參閱 [SubmitDelivery(nms:delivery)](#submitdelivery--nms-delivery-),
   * 傳送促銷活動（開始、暫停、停止、傳送校樣）,
   * 正在恢復傳送記錄。

* 工作流程:

   * 啟動工作流，
   * 驗證流程等

      請參閱 [JavaScript中的SOAP方法](../../configuration/using/soap-methods-in-javascript.md).

* 內容管理
* 訂閱管理，請參閱 [訂閱(nms:subscription)](#subscribe--nms-subscription-) 和 [取消訂閱(nms:subscription)](#unsubscribe--nms-subscription-).
* 資料流程：進口，出口。

本節詳細說明「訂閱」、「取消訂閱」和「提交交付」服務的使用。

>[!IMPORTANT]
>
>[Campaign JSAPI檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html) 包含有關Adobe Campaign中SOAP呼叫與使用Javascript的其他資訊，以及應用程式中所用所有方法和函式的完整參考。

## 訂閱(nms:subscription) {#subscribe--nms-subscription-}

此服務可讓您訂閱資訊服務的收件者，並更新收件者設定檔。

呼叫服務需要下列參數：

* 驗證，
* 訂閱服務的內部名稱，
* 包含收件者資訊的XML文檔（來自&quot;nms:recipient&quot;方案）,
* 收件者建立的布林值（如果尚未建立）。

「nms:subscription」方案中「subscribe」方法的描述：

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

調解金鑰的定義必須透過_輸入&#x200B;**key** 屬性 `<recipient>` 元素。 此屬性的內容是逗號分隔的XPath清單。

除錯誤外，此呼叫不會傳回任何資料。

### 範例 {#examples}

電子郵件地址上具有收件者調解金鑰的訂閱：輸入XML文檔必須參考此欄位上的電子郵件地址和鍵的定義。

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

更新收件者及訂閱。

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### SOAP消息的示例 {#example-of-soap-messages}

* 查詢:

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:Subscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
         <sessiontoken xsi:type='xsd:string'/>
         <service xsi:type='xsd:string'>SVC1</service>
         <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
           <recipient _key="@email" email= "john.doe@adobe.com/>
         </content>
         <create xsi:type='xsd:boolean'>true</create>
       </m:Subscribe>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* 回應：

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </m:SubscribeResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## 取消訂閱(nms:subscription) {#unsubscribe--nms-subscription-}

此服務可讓您從資訊服務中取消訂閱收件者，並更新收件者設定檔。

呼叫服務需要下列參數：

* 驗證，
* 要取消訂閱的服務的內部名稱，
* 包含收件者資訊的XML文檔（來自&quot;nms:recipient&quot;方案）,

「nms:subscription」方案中「取消訂閱」方法的說明：

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

調解金鑰的定義必須透過 `<recipient>` 元素。 此屬性的內容是逗號分隔的XPath清單。

如果收件者不在資料庫中或未訂閱相關資訊服務，則服務不執行任何操作，也不會產生錯誤。

>[!NOTE]
>
>如果未將服務名指定為參數，則收件人將自動列在封鎖清單(@blackList=&quot;1&quot;)上。

除錯誤外，此呼叫不會傳回任何資料。

### SOAP消息的示例 {#example-of-soap-messages-1}

查詢:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:Unsubscribe xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    <sessiontoken xsi:type='xsd:string'/>
    <service xsi:type='xsd:string'>SVC1</service>
    <content xsi:type='' SOAP-ENV:encodingStyle='http://xml.apache.org/xml-soap/literalxml'>
      <recipient _key="@email" email= "john.doe@adobe.com/>
    </content>
  </m:Unsubscribe>
</SOAP-ENV:Body>
```

回應：

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## SubmitDelivery(nms:delivery) {#submitdelivery--nms-delivery-}

此服務可讓您建立和提交傳送動作。

呼叫服務需要下列參數：

* 驗證，
* 傳遞範本的內部名稱，
* 包含其他傳送資料的選用XML檔案。

由於您可能遇到效能問題，因此不應大量呼叫此API。

方法在其架構中的說明：

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

傳遞範本必須從Adobe Campaign用戶端主控台建立。 它包含所有傳送的公用參數（寄件者地址或訊息有效期間）。

輸入的XML文檔是符合「nms:delivery」架構結構的傳遞模板片段。 它將包含無法在傳遞範本中靜態定義的所有其他資料（例如要定位的收件者清單）。

除錯誤外，此呼叫不會傳回任何資料。

### XML文檔示例 {#xml-document-example}

此範例以來自外部資料來源的自訂傳送範本為基礎（此為檔案）。 傳送範本中會完整說明設定，因此呼叫發生時所有仍待傳送的內容，都是 `<externalsource>` 元素。

```
<delivery>
  <targets fromExternalSource="true">
    <externalSource>
      MsgId|ClientId|Title|Name|FirstName| Mobile|Email| Market_segment|Product_affinity1 |Product_affinity2|Product_affinity3| Product_affinity4| Support_Number|Amount|Threshold1|000001234|M.| Doe|John|0650201020| john.doe@adobe.com
|1| A1|A2|A3|A4|E12|120000|100000
    </externalSource>
  </target>
</delivery>
```

如果您沒有傳遞範本，可使用下列範例：

```
<delivery>
<targets fromExternalSource="true" targetMode="1" noReconciliation="true" addressField="Email" >  
    <fileFormat active="true">  
      <source format="text" type="text">  
        <dataSourceConfig >  
          <dataSourceColumn label="Email" name="Email" type="string"/>  
        </dataSourceConfig>  
      </source>  
      <destination type="xtkDataStore"/>  
    </fileFormat>  
    <externalSource><![CDATA[not-a-repicipient@domain.com]]></externalSource>  
  </targets> 
</delivery> 
```
