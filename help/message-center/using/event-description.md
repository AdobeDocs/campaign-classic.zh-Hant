---
title: 事件說明
seo-title: 事件說明
description: 事件說明
seo-description: null
page-status-flag: never-activated
uuid: 7b174ffd-28b2-4147-b992-e17b0b2cf733
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 3c8388d8-1a91-4d16-a8ac-016f643c6009
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc227c2da2e8b1a78714748809ad40bbcefe0458

---


# 事件說明{#event-description}

## 關於事務性消息傳遞資料模型 {#about-transactional-messaging-datamodel}

交易式傳訊需仰賴Adobe Campaign資料模型，並使用另外兩個不同的表格。 這 [些表](../../configuration/using/data-model-description.md#message-center-module)( **NmsRtEvent** 和 **** NmsBatchEvent)包含相同的欄位，允許您管理即時事件和批處理事件。

## SOAP方法 {#soap-methods}

本節詳細介紹與事務性消息模組結構描述關聯的SOAP方法。

兩個 **PushEvent** 或 **PushEvents** SOAP方法會連結至兩個 **nms:rtEvent** 和 **** nms:BatchEventDataschemas。 決定事件是「批次」或「即時」類型的資訊系統。

* **PushEvent** 可讓您將單一事件插入訊息中，
* **PushEvents** 可讓您在訊息中插入一連串事件。

用於訪問兩種方法的WSDL路徑為：

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:rtEvent** ，以存取即時類型結構。
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:batchEvent** ，以存取批次類型結構。

這兩種方法都包 **`<urn:sessiontoken>`** 含用於登入事務性訊息模組的元素。 我們建議透過受信任的IP位址使用識別方法。 若要擷取工作階段Token，請執行登入SOAP呼叫，然後執行取得Token，再執行註銷。 對數個RT呼叫使用相同的Token。 本節中包含的範例是使用建議的作業Token方法。

如果您使用負載平衡伺服器，則可使用使用者／密碼驗證（位於RT訊息的層級）。 例如：

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

PushEvent **方法由包****`<urn:domevent>`** 含事件的參陣列成。

PushEvents **方法** ，由包含事件 **`<urn:domeventcollection>`** 的參陣列成。

使用PushEvent的範例：

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
>在呼叫 **PushEvents方法時** ，我們需要新增父XML元素以符合標準XML。 此XML元素將框架化事件中 **`<rtevent>`** 包含的各種元素。

使用PushEvents的範例：

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

和 **`<rtevent>`** 元 **`<batchevent>`** 素具有一組屬性和強制子元素：用 **`<ctx>`** 於整合消息資料。

>[!NOTE]
>
>元素 **`<batchevent>`** 可讓您將事件新增至「批次」佇列。 將 **`<rtevent>`** 事件新增至「即時」佇列。

和元素的必 **`<rtevent>`** 備屬 **`<batchevent>`** 性是@type和@email。 @type的值必須與配置執行實例時定義的項目化清單值相同。 此值可讓您定義要連結至傳送期間事件內容的範本。

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

在此範例中，提供兩個頻道：電子郵件地址和行動電話號碼。 The **wishedChannel** gots you select the channel you wisht to use when the event into a message. 「0」值對應於電子郵件渠道、「1」值對應於行動渠道等。

如果您想要延遲事件傳送，請新增欄 **[!UICONTROL scheduled]** 位，後面接著偏好的日期。 該事件將在此日期轉換為消息。

我們建議以數值填入@wishedChannel和@emailFormat屬性。 連結數值和標籤的函式表位於資料方案說明中。

>[!NOTE]
>
>在 **nms:rtEvent和** nms:BatchEvent資料架構的說明中，提供了所有授權屬性及其值的詳 **** 細說明。

元素 **`<ctx>`** 包含訊息資料。 其XML內容是開啟的，這表示您可以根據要傳送的內容來設定它。

>[!NOTE]
>
>請務必最佳化訊息中包含的XML節點數目和大小，以避免傳送期間伺服器超載。

資料範例：

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

## SOAP呼叫傳回的資訊 {#information-returned-by-the-soap-call}

當Adobe Campaign收到事件時，會產生唯一的傳回ID。 這是事件封存版本的ID。

>[!CAUTION]
>
>當收到SOAP呼叫時，Adobe Campaign會驗證電子郵件地址格式。 如果電子郵件地址格式錯誤，則會傳回錯誤。

* 事件處理成功時，方法傳回的識別碼範例：

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">72057594037935966</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

如果傳回識別碼的值嚴格大於零，表示事件已在Adobe Campaign中成功封存。

但是，如果事件無法處理，方法會傳回錯誤訊息或等於零的值。

* 處理在查詢不包含登入或指定運算子沒有必要權限時失敗的事件範例：

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

* 因查詢錯誤而失敗的事件範例（XML分類未符合）:

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

* 失敗並傳回零識別碼（錯誤方法名稱）的事件範例：

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">0</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```

