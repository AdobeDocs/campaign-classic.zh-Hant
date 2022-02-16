---
product: campaign
title: 事件說明
description: 瞭解如何使用SOAP方法在Adobe Campaign Classic管理事務性消息傳遞事件。
audience: message-center
content-type: reference
topic-tags: introduction
exl-id: 9f7f4b6c-2ee8-4091-847d-f616d6abeb6b
source-git-commit: c30d64e6930cb97f4a3c15acd97654d57d1bbf85
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---

# 事件說明 {#event-description}

![](../../assets/v7-only.svg)

## 事務性消息傳遞資料模型 {#about-transactional-messaging-datamodel}

事務性消息傳遞依賴於Adobe Campaign資料模型，並使用另外兩個單獨的表。 這些 [表](../../configuration/using/data-model-description.md#message-center-module)。 **NmsRtEvent** 和 **NmsBatchEvent**，包含相同的欄位，允許您管理即時事件和批處理事件。

## SOAP方法 {#soap-methods}

本節詳細介紹與事務性消息模組架構關聯的SOAP方法。

二 **推送事件** 或 **推送事件** SOAP方法已連結到 **nms:rtEvent** 和 **nms:BatchEvent** 資料化學。 確定事件是「批處理」還是「即時」類型的資訊系統。

* **推送事件** 讓您在消息中插入一個事件，
* **推送事件** 允許您在消息中插入一系列事件。

用於訪問兩種方法的WSDL路徑為：

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent** 訪問即時類型架構。
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:batchEvent** 訪問批類型架構。

有關生成WSDL檔案的詳細資訊，請參見 [此部分](../../configuration/using/web-service-calls.md#web-service-description--wsdl)。

兩種方法都包含 **`<urn:sessiontoken>`** 用於登錄到事務消息傳遞模組的元素。 我們建議使用通過可信IP地址的標識方法。 要檢索會話令牌，請執行登錄SOAP調用，然後執行獲取令牌和註銷。 對多個RT調用使用相同的令牌。 本節中包括的示例使用的是推薦的會話令牌方法。

如果您使用的是負載平衡伺服器，則可以使用用戶/密碼驗證（在RT消息的級別）。 範例:

```
<PushEvent xmlns="urn:nms:rtEvent">
<sessiontoken>mc/PASSWORD</sessiontoken>
<domEvent>
<rtEvent wishedChannel="41" type="rt_MobileJourney_iOS_Push" registrationToken="c3ddc8aaecc24822df25d0f49865cca61ea3f86c61bfa53ae4d37294e37f4a1c" hashlpId="27EE7571EC14DBA23B9B5CC0EF79BB782DAECF4C03C88E5D92CC9B9DAC4E5DDA" correlationId="415b7593-4f6f-e911-811f-00505691247c" xmlns="">
<mobileApp uuid="236B24DC-C073-412F-8BCB-AC7207096258" _operation="none"/>
<ctx>...</ctx>
</rtEvent>
</domEvent>
</PushEvent>
```

的 **推送事件** 方法由 **`<urn:domevent>`** 包含事件的參數。

的 **推送事件** 方法由 **`<urn:domeventcollection>`** 包含事件的參數。

使用PushEvent的示例：

```
<urn:PushEvent>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEvent>
 
   <rtEvent>
   
   ...
   
   </rtEvent>
 
 </urn:domEvent>

</urn:PushEvent>
```

>[!NOTE]
>
>如果呼叫 **推送事件** 方法，需要添加一個父XML元素來符合標準XML。 此XML元素將對 **`<rtevent>`** 事件中包含的元素。

使用PushEvents的示例：

```
<urn:PushEvents>

 <sessiontoken>___921f9b38-72ac-49ad-b481-ab32973efc50</sessiontoken>
 
 <urn:domEventCollection>
 
   <Events>
   
     <rtEvent>... </rtEvent>
     
     <rtEvent>... </rtEvent>
     
     ...
   
   </Events>
 
 </urn:domEventCollection>

</urn:PushEvents>
```

的 **`<rtevent>`** 和 **`<batchevent>`** 元素具有一組屬性以及必需的子元素： **`<ctx>`** 用於整合消息資料。

>[!NOTE]
>
>的 **`<batchevent>`** 元素允許您將事件添加到「批處理」隊列。 的 **`<rtevent>`** 將事件添加到「即時」隊列。

的強制屬性 **`<rtevent>`** 和 **`<batchevent>`** 元素是@type和@email。 值@type必須與配置執行實例時定義的明細清單值相同。 此值允許您定義要在傳遞期間連結到事件內容的模板。

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

在本示例中，提供了兩個通道：電子郵件地址和手機號碼。 的 **希望頻道** 允許您選擇將事件轉換為消息時要使用的通道。 「0」值對應於電子郵件通道、「1」值對應於移動通道等。

如果要推遲事件交付，請添加 **[!UICONTROL scheduled]** 欄位後跟首選日期。 該事件將在此日期轉換為消息。

我們建議用數值填@wishedChannel和@emailFormat屬性。 在資料架構說明中找到連結數值和標籤的函式表。

>[!NOTE]
>
>有關所有授權屬性及其值的詳細說明，請參閱 **nms:rtEvent** 和 **nms:BatchEvent** 資料模式。

的 **`<ctx>`** 元素包含消息資料。 其XML內容是開啟的，這意味著可以根據要傳送的內容進行配置。

>[!NOTE]
>
>優化消息中包含的XML節點的數量和大小，以避免在傳遞過程中使伺服器超負荷，這一點非常重要。

資料示例：

```
   <ctx>
               <client>
                        <firstname>John</firstname>
                        <lastname>Doe</lastname>
               </client>
               <action>
                         <type>Order confirmation</type>
                          <number>CN23453</number>
               </action>
               <orderdetails>
                          <article num="1">
                                   <name>Generic USB key</name>
                                   <price>20</price>
                           </article>
               </orderdetails>
    </ctx>
```

## SOAP調用返回的資訊 {#information-returned-by-the-soap-call}

當它收到事件時，Adobe Campaign會生成唯一的返回ID。 這是事件存檔版本的ID。

>[!IMPORTANT]
>
>Adobe Campaign在接收SOAP呼叫時驗證電子郵件地址格式。 如果電子郵件地址格式不正確，則返回錯誤。

* 事件處理成功時由方法返回的標識符示例：

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">72057594037935966</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

如果返回標識符的值嚴格大於零，則表示事件已在Adobe Campaign成功存檔。

但是，如果該事件未能處理，則該方法返回錯誤消息或等於零的值。

* 處理查詢不包含登錄名或指定運算子沒有所需權限時失敗的事件示例：

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">Error while reading parameters of method 'PushEvent' of service 'nms:rtEvent'.</faultstring>
            <detail xsi:type="xsd:string">Invalid login or password. Connection denied.</detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* 由於查詢錯誤而失敗的事件示例（未遵守XML分類）:

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <SOAP-ENV:Fault>
            <faultcode>SOAP-ENV:Client</faultcode>
            <faultstring xsi:type="xsd:string">The XML SOAP message is invalid (service 'PushEvent', method 'nms:rtEvent').</faultstring>
            <detail xsi:type="xsd:string"><![CDATA[(16:8) : Expected end of tag 'rtevent'
   Error while parsing XML string '<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
      <soapenv:Header/>
      <soapenv:Body>
         <urn:PushEvent>
            <urn:sessiontoken>mc/</urn:sessiontoken>
            <urn:domEvent>
   <rtevent type="create_account" email="esther.hall@adobe.com" origin="eCommerce" wishedChannel="email" 
         externalId="1596" language="english" country="EN" emailFormat="2"
         mobilePhone="+447700123123">
     <ctx>
      <website name="eCommerce" url="http://www.eCo']]></detail>
         </SOAP-ENV:Fault>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

* 失敗並返回零標識符（錯誤的方法名稱）的事件示例：

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">0</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```
