---
product: campaign
title: 商業導向 API
description: 商業導向 API
feature: API
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 3%

---

# 商業導向 API{#business-oriented-apis}

![](../../assets/v7-only.svg)

業務API特定於每種類型的對象。 它們對以下方面有影響：

* 傳遞:

   * 建立交貨操作，請參閱 [提交交付（nms：交付）](#submitdelivery--nms-delivery-)。
   * 發送活動（開始、暫停、停止、發送證據）,
   * 恢復交付日誌。

* 工作流程:

   * 啟動工作流，
   * 驗證進程等。

      請參閱 [JavaScript中的SOAP方法](../../configuration/using/soap-methods-in-javascript.md)。

* 內容管理
* 訂閱管理，請參閱 [訂閱（nms：訂閱）](#subscribe--nms-subscription-) 和 [取消訂閱（nms：訂閱）](#unsubscribe--nms-subscription-)。
* 資料進程：進口，出口。

本節詳細介紹「訂閱」、「取消訂閱」和「提交交付」服務的使用。

>[!IMPORTANT]
>
>[市場活動JSAPI文檔](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant) 包含有關SOAP調用和在Adobe Campaign使用Javascript的其他資訊，以及對應用程式中使用的所有方法和函式的完全引用。

## 訂閱（nms：訂閱） {#subscribe--nms-subscription-}

此服務允許您為收件人訂閱資訊服務並更新收件人配置檔案。

調用服務需要以下參數：

* 驗證，
* 訂閱服務的內部名稱，
* 包含收件人資訊（來自「nms:recipient」架構）的XML文檔，
* 一個布爾值，用於在尚未建立收件人時建立收件人。

「nms:subscription」架構中「subscribe」方法的說明：

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

協調鍵的定義必須通過_輸入&#x200B;**鍵** 屬性 `<recipient>` XML文檔的元素。 此屬性的內容是逗號分隔的XPath清單。

除錯誤外，此調用不返回任何資料。

### 範例 {#examples}

電子郵件地址上具有收件人對帳密鑰的訂閱：輸入XML文檔必須引用此欄位上的電子郵件地址和鍵的定義。

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

正在更新收件人和訂閱。

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### SOAP消息示例 {#example-of-soap-messages}

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

* 響應：

   ```
   <?xml version='1.0' encoding='ISO-8859-1'?>
   <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
     <SOAP-ENV:Body>
       <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
       </m:SubscribeResponse>
     </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

## 取消訂閱（nms：訂閱） {#unsubscribe--nms-subscription-}

此服務允許您從資訊服務中取消訂閱收件人並更新收件人配置檔案。

調用服務需要以下參數：

* 驗證，
* 要取消訂閱的服務的內部名稱，
* 包含收件人資訊（來自「nms:recipient」架構）的XML文檔，

「nms:subscription」架構中「取消訂閱」方法的說明：

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

必須通過上的_key屬性輸入協調鍵的定義 `<recipient>` XML文檔的元素。 此屬性的內容是逗號分隔的XPath清單。

如果接收方不在資料庫中或未訂閱相關資訊服務，則該服務不執行任何操作並且不生成錯誤。

>[!NOTE]
>
>如果未將服務名稱指定為參數，則收件人將自動在denylist(@blackList=&quot;1&quot;)上。

除錯誤外，此調用不返回任何資料。

### SOAP消息示例 {#example-of-soap-messages-1}

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

響應：

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## 提交交付（nms：交付） {#submitdelivery--nms-delivery-}

此服務允許您建立和提交交貨操作。

調用服務需要以下參數：

* 驗證，
* 交貨模板的內部名稱，
* 包含附加傳遞資料的可選XML文檔。

不應在卷中調用此API，因為您可能遇到效能問題。

在其架構中對方法的說明：

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

必須從Adobe Campaign客戶端控制台建立傳遞模板。 它包含所有傳遞的公用參數（發送者地址或消息有效期）。

輸入XML文檔是服從「nms:delivery」模式結構的傳遞模板片段。 它將包含無法在傳遞模板中靜態定義的所有附加資料（例如，目標收件人清單）。

除錯誤外，此調用不返回任何資料。

### XML文檔示例 {#xml-document-example}

此示例基於來自外部資料源（本例中為檔案）的自定義傳遞模板。 該配置在傳遞模板中已完全描述，因此在調用發生時仍要發送的所有內容都是來自 `<externalsource>` 的子菜單。

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

如果沒有交貨模板，則可以使用以下示例：

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
