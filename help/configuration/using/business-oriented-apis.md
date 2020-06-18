---
title: 商業導向API
seo-title: 商業導向API
description: 商業導向API
seo-description: null
page-status-flag: never-activated
uuid: ddb6e5cf-dfe0-4dc9-ac5b-fab21827b874
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: e7b3ffca-c85f-498d-89b4-23fcff59de49
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c51a51f175e9f3fe5a55f2b5f57872057f70909d
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---


# 商業導向API{#business-oriented-apis}

商業API是每種物件類型專屬的。 它們對以下方面有影響：

* 傳送：

   * 建立傳送動作，請參 [閱SubmitDelivery(nms:delivery)](#submitdelivery--nms-delivery-),
   * 傳送促銷活動（開始、暫停、停止、傳送校樣）,
   * 恢復交付日誌。

* 工作流程：

   * 啟動工作流程，
   * 驗證流程等。

      請參閱 [JavaScript中的SOAP方法](../../configuration/using/soap-methods-in-javascript.md)。

* 內容管理
* 訂閱管理，請參 [閱訂閱(nms:subscription)](#subscribe--nms-subscription-)[和取消訂閱(nms:subscription)](#unsubscribe--nms-subscription-)。
* 資料流程： 進出口。

本節詳細說明「訂閱」、「取消訂閱」和「提交傳送」服務的使用。

>[!IMPORTANT]
>
>[Campaign JSAPI檔案包含](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) Adobe Campaign中有關SOAP呼叫和使用Javascript的其他資訊，以及應用程式中所有使用方法與函式的完整參考。

## 訂閱(nms:subscription) {#subscribe--nms-subscription-}

此服務可讓您訂閱資訊服務的收件者，並更新收件者個人檔案。

呼叫服務時需要下列參數：

* 驗證，
* 訂閱服務的內部名稱、
* 包含收件者資訊的XML檔案（來自&quot;nms:recipient&quot;架構）,
* 布林值，若收件者尚未建立，則用於建立。

「nms:subscription」模式中「subscribe」方法的說明：

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

協調鍵的定義必須透過XML檔案元素&#x200B;**上的** _ `<recipient>` key屬性輸入。 此屬性的內容是逗號分隔的XPath清單。

此呼叫不會傳回任何資料，但錯誤除外。

### 範例 {#examples}

電子郵件地址上具有收件人協調密鑰的訂閱： 輸入的XML文檔必須引用此欄位中的電子郵件地址和鍵的定義。

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

更新收件者和訂閱。

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

此服務可讓您取消訂閱資訊服務的收件者，並更新收件者個人檔案。

呼叫服務時需要下列參數：

* 驗證，
* 要取消訂閱的服務的內部名稱，
* 包含收件者資訊的XML檔案（來自&quot;nms:recipient&quot;架構）,

「nms:subscription」模式中「取消訂閱」方法的說明：

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

協調鍵的定義必須透過XML檔案元素上的_key `<recipient>` 屬性輸入。 此屬性的內容是逗號分隔的XPath清單。

如果收件者不在資料庫中或未訂閱相關資訊服務，則服務不執行任何操作並且不生成錯誤。

>[!NOTE]
>
>如果未將服務名指定為參數，則收件者會自動顯示在塊清單(@blockList=&quot;1&quot;)上。

此呼叫不會傳回任何資料，但錯誤除外。

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

此服務可讓您建立和送出傳送動作。

呼叫服務時需要下列參數：

* 驗證，
* 傳送範本的內部名稱、
* 可選的XML檔案，包含其他傳送資料。

您不應因可能遇到效能問題而在卷中呼叫此API。

方法在其架構中的說明：

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

傳送範本必須從Adobe Campaign用戶端主控台建立。 它包含所有傳送的公用參數（傳送者位址或訊息有效期）。

輸入的XML文檔是遵守「nms:delivery」架構的傳送模板片段。 它將包含無法在傳送範本中靜態定義的所有其他資料（例如，要定位的收件者清單）。

此呼叫不會傳回任何資料，但錯誤除外。

### XML檔案範例 {#xml-document-example}

此範例以來自外部資料來源的自訂傳送範本（此例中為檔案）為基礎。 傳送範本中已完整說明此設定，因此在呼叫發生時仍要傳送的所有內容，都是元素中的檔案內 `<externalsource>` 容。

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

如果您沒有傳送範本，則可使用下列範例：

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

