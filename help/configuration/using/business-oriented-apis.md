---
product: campaign
title: 商業導向 API
description: 商業導向 API
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: API
role: Data Engineer, Developer
exl-id: e6638870-3141-4f12-b904-db436127c0d1
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 4%

---

# 商業導向 API{#business-oriented-apis}

Business API是每種物件型別專屬的。 它們會影響：

* 傳遞:

   * 建立傳遞動作，請參閱 [提交傳遞(nms：delivery)](#submitdelivery--nms-delivery-)，
   * 傳送行銷活動（開始、暫停、停止、傳送證明）、
   * 復原傳遞記錄。

* 工作流程:

   * 啟動工作流程，
   * 驗證流程等。

     請參閱 [javascript中的SOAP方法](../../configuration/using/soap-methods-in-javascript.md).

* 內容管理
* 訂閱管理，請參閱 [訂閱(nms：subscription)](#subscribe--nms-subscription-) 和 [取消訂閱(nms：subscription)](#unsubscribe--nms-subscription-).
* 資料程式：匯入、匯出。

本節詳細說明了「訂閱」、「取消訂閱」和「SubmitDelivery」服務的使用。

>[!IMPORTANT]
>
>[Campaign JSAPI檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant) 包含在Adobe Campaign中SOAP呼叫和使用Javascript的其他資訊，以及應用程式中使用之所有方法和函式的完整參考。

## 訂閱(nms：subscription) {#subscribe--nms-subscription-}

此服務可讓您為收件者訂閱資訊服務並更新收件者設定檔。

呼叫服務需要下列引數：

* 驗證，
* 訂閱服務的內部名稱，
* 包含收件者資訊的XML檔案（來自「nms：recipient」綱要），
* 如果還沒有布林值，則為建立收件者的布林值。

「nms：subscription」結構描述中「subscription」方法的說明：

```
<method name="Subscribe" static="true">
  <parameters>
     <param name="serviceName" type="string"  desc="List of information service names (comma separated)"/>
     <param name="recipient" type="DOMElement" desc="Recipient"/>
     <param name="create" type="Boolean" desc="Create recipient if it does not exist"/>
   </parameters>
</method>
```

調解金鑰的定義必須透過_輸入&#x200B;**key** 上的屬性 `<recipient>` XML檔案的元素。 此屬性的內容是以逗號分隔的XPath清單。

此呼叫不會傳回任何資料，錯誤除外。

### 範例 {#examples}

電子郵件地址上具有收件者調解金鑰的訂閱：輸入XML檔案必須參考此欄位上的電子郵件地址和金鑰定義。

```
<recipient _key="email" email= "john.doe@adobe.com"/>
```

更新收件者及訂閱。

```
<recipient _key="email, [folder-id]" email= "john.doe@adobe.com" folder-id="1305" firstName="John" lastName="Doe"/>
```

### SOAP訊息範例 {#example-of-soap-messages}

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

* 回應:

  ```
  <?xml version='1.0' encoding='ISO-8859-1'?>
  <SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
    <SOAP-ENV:Body>
      <m:SubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
      </m:SubscribeResponse>
    </SOAP-ENV:Body>
  </SOAP-ENV:Envelope>
  ```

## 取消訂閱(nms：subscription) {#unsubscribe--nms-subscription-}

此服務可讓您取消訂閱資訊服務的收件者，並更新收件者設定檔。

呼叫服務需要下列引數：

* 驗證，
* 要取消訂閱之服務的內部名稱，
* 包含收件者資訊的XML檔案（來自「nms：recipient」綱要），

「nms：subscription」結構描述中「Unsubscription」方法的說明：

```
<method name="Unsubscribe" static="true">
  <parameters>
    <param name="serviceName" type="string" desc="List of information service names (comma separated)"/>
    <param name="recipient" type="DOMElement"  desc="Recipient"/>
  </parameters>
</method>
```

調解金鑰的定義必須透過 `<recipient>` XML檔案的元素。 此屬性的內容是以逗號分隔的XPath清單。

如果收件者不在資料庫中，或未訂閱相關的資訊服務，則服務不會執行任何動作，也不會產生錯誤。

>[!NOTE]
>
>如果未將服務名稱指定為引數，則收件者會自動加入封鎖清單(@blackList=&quot;1&quot;)。

此呼叫不會傳回任何資料，錯誤除外。

### SOAP訊息範例 {#example-of-soap-messages-1}

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

回應:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<SOAP-ENV:Envelope xmlns:xsd='http://www.w3.org/2001/XMLSchema' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ns='http://xml.apache.org/xml-soap' xmlns:SOAP-ENV='http://schemas.xmlsoap.org/soap/envelope/'>
  <SOAP-ENV:Body>
    <m:UnsubscribeResponse xmlns:m='urn:nms:subscription' SOAP-ENV:encodingStyle='http://schemas.xmlsoap.org/soap/encoding/'>
    </m:UnsubscribeResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## 提交傳遞(nms：delivery) {#submitdelivery--nms-delivery-}

此服務可讓您建立並提交傳遞動作。

呼叫服務需要下列引數：

* 驗證，
* 傳遞範本的內部名稱，
* 包含其他傳遞資料的選用XML檔案。

因為您可能會遇到效能問題，所以不應在磁碟區中呼叫此API。

方法在其結構描述中的說明：

```
<method name="SubmitDelivery" static="true">
  <parameters>
    <param name="scenarioName" type="string" inout="in" desc="Internal name of the delivery template"/>
    <param name="content" type="DOMElement"  inout="in" desc="XML content of the delivery template" />
  </parameters>
</method>
```

必須從Adobe Campaign使用者端主控台建立傳遞範本。 它包含所有傳遞的通用引數（寄件者地址或訊息有效期間）。

輸入XML檔案是符合「nms：delivery」結構描述的傳遞範本片段。 它會包含所有無法在傳遞範本中靜態定義的其他資料（例如要定位的收件者清單）。

此呼叫不會傳回任何資料，錯誤除外。

### XML檔案範例 {#xml-document-example}

此範例是根據來自外部資料來源（此案例中的檔案）的自訂傳遞範本。 傳遞範本中已完整說明設定，因此呼叫發生時唯一需要傳送的就是來自的檔案內容 `<externalsource>` 元素。

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

如果您沒有傳遞範本，可以使用下列範例：

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
