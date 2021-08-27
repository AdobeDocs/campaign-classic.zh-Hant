---
product: campaign
title: 事件說明
description: 了解如何使用SOAP方法在Adobe Campaign Classic中管理交易式訊息事件。
audience: message-center
content-type: reference
topic-tags: introduction
exl-id: 9f7f4b6c-2ee8-4091-847d-f616d6abeb6b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---

# 事件說明 {#event-description}

![](../../assets/v7-only.svg)

## 交易式訊息資料模型 {#about-transactional-messaging-datamodel}

交易式訊息需仰賴Adobe Campaign資料模型，並使用其他兩個不同的表格。 這些[表](../../configuration/using/data-model-description.md#message-center-module)、**NmsRtEvent**&#x200B;和&#x200B;**NmsBatchEvent**&#x200B;包含相同的欄位，允許您管理即時事件和批次事件。

## SOAP方法 {#soap-methods}

本節詳細說明與交易式訊息模組結構相關聯的SOAP方法。

兩個&#x200B;**PushEvent**&#x200B;或&#x200B;**PushEvents** SOAP方法連結到兩個&#x200B;**nms:rtEvent**&#x200B;和&#x200B;**nms:BatchEvent**&#x200B;資料化學。 決定事件是「批次」還是「即時」類型的資訊系統。

* **** PushEvent可讓您將單一事件插入訊息中，
* **** PushEvent可讓您將一系列事件插入訊息中。

用於訪問這兩種方法的WSDL路徑為：

* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:** rtEvent以存取即時類型結構。
* **http://hostname/nl/jsp/schemawsdl.jsp?schema=nms:** batchEven以存取批次類型結構。

兩種方法都包含用於登入交易式訊息模組的&#x200B;**`<urn:sessiontoken>`**&#x200B;元素。 建議您透過信任的IP位址使用識別方法。 要檢索會話令牌，請執行登錄SOAP調用，然後執行獲取令牌，然後執行註銷。 對數個RT呼叫使用相同的Token。 本節包含的範例是使用工作階段代號方法，此為建議的方法。

如果您使用負載平衡伺服器，則可以使用「使用者/密碼」驗證（位於RT訊息的層級）。 範例:

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

**PushEvent**&#x200B;方法由包含事件的&#x200B;**`<urn:domevent>`**&#x200B;參陣列成。

**PushEvents**&#x200B;方法由包含事件的&#x200B;**`<urn:domeventcollection>`**&#x200B;參陣列成。

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
>若呼叫&#x200B;**PushEvents**&#x200B;方法，則需要新增父XML元素以符合標準XML。 此XML元素將框架事件中包含的各種&#x200B;**`<rtevent>`**&#x200B;元素。

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

**`<rtevent>`**&#x200B;和&#x200B;**`<batchevent>`**&#x200B;元素具有一組屬性以及強制子元素：**`<ctx>`**&#x200B;以整合訊息資料。

>[!NOTE]
>
>**`<batchevent>`**&#x200B;元素可讓您將事件新增至「batch」佇列。 **`<rtevent>`**&#x200B;會將事件新增至「即時」佇列。

**`<rtevent>`**&#x200B;和&#x200B;**`<batchevent>`**&#x200B;元素的強制屬性為@type和@email。 @type的值必須與設定執行例項時定義的項目清單值相同。 此值可讓您定義要在傳送期間連結至事件內容的範本。

`<rtevent> configuration example:`

```
<rtEvent type="order_confirmation" email="john.doe@domain.com" origin="eCommerce" wishedChannel="0" externalId="1242" mobilePhone="+33620202020"> 
```

在此範例中，提供兩個管道：電子郵件地址和行動電話號碼。 **wishedChannel**&#x200B;可讓您選取將事件轉換為訊息時要使用的管道。 「0」值對應至電子郵件通道、「1」值對應至行動通道等。

如果您想要延遲事件傳送，請新增&#x200B;**[!UICONTROL scheduled]**&#x200B;欄位，後面接著偏好的日期。 該事件將在此日期轉換為訊息。

建議您使用數值填@wishedChannel和@emailFormat屬性。 在資料架構描述中找到連結數值和標籤的函式表。

>[!NOTE]
>
>**nms:rtEvent**&#x200B;和&#x200B;**nms:BatchEvent**&#x200B;資料架構的說明中提供了所有授權屬性及其值的詳細說明。

**`<ctx>`**&#x200B;元素包含訊息資料。 其XML內容是開啟的，這表示可以根據要傳送的內容進行配置。

>[!NOTE]
>
>請務必最佳化訊息中包含的XML節點數目和大小，以避免傳送期間發生伺服器過載。

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

Adobe Campaign在收到事件時會產生唯一傳回ID。 這是封存版本的事件ID。

>[!IMPORTANT]
>
>Adobe Campaign收到SOAP呼叫時，會驗證電子郵件地址格式。 如果電子郵件地址的格式不正確，則會傳回錯誤。

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

不過，如果無法處理事件，方法會傳回錯誤訊息或等於零的值。

* 處理查詢不包含登入或指定運算子沒有必要權限時失敗的事件範例：

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

* 因查詢錯誤而失敗的事件範例（未遵循XML分類）:

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

* 失敗並傳回零識別碼（錯誤的方法名稱）的事件範例：

   ```
   <SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns="http://xml.apache.org/xml-soap" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
      <SOAP-ENV:Body>
         <urn:PushEventResponse SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" xmlns:urn="urn:nms:rtEvent">
            <plId xsi:type="xsd:long">0</plId>
         </urn:PushEventResponse>
      </SOAP-ENV:Body>
   </SOAP-ENV:Envelope>
   ```
