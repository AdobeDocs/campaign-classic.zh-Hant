---
product: campaign
title: 透過 SOAP 整合 (伺服器端)
description: 透過 SOAP 整合 (伺服器端)
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 3%

---

# 透過SOAP整合（伺服器端）{#integration-via-soap-server-side}



為Offer Management提供的SOAP Web服務與Adobe Campaign中通常使用的服務不同。 可透過上一節所述的互動URL存取優惠方案，並讓您提供或更新指定聯絡人的優惠方案。

## 產品建議提議 {#offer-proposition}

若要透過SOAP提出優惠方案，請新增&#x200B;**nms：proposition#Propose**&#x200B;命令，後面接著下列引數：

* **targetId**：收件者的主索引鍵（可以是複合索引鍵）。
* **maxCount**：指定連絡人的優惠方案主張數目。
* **內容**：可讓您在空間結構描述中新增內容資訊。 如果使用的結構描述是&#x200B;**nms：interaction**，則應新增&#x200B;**`<empty>`**。
* **類別**：指定優惠必須屬於的類別。
* **主題**：指定選件必須屬於的主題。
* **uuid**： Adobe Campaign永久cookie的值(「uuid230」)。
* **nli**： Adobe Campaign工作階段Cookie的值(「nlid」)。
* **noProp**：使用「true」值停用提案插入。

>[!NOTE]
>
>**targetId**&#x200B;和&#x200B;**maxCount**&#x200B;設定是強制性的。 其他則是選擇性的。

為回應查詢，SOAP服務將傳回下列引數：

* **interactionId**：互動識別碼。
* **主張**： XML元素，包含主張清單，每個都具有自己的ID和HTML表示法。

## 優惠更新 {#offer-update}

將&#x200B;**nms：interaction#UpdateStatus**&#x200B;命令新增至URL，後面接著這些引數：

* **主張**：字元字串，它包含在優惠方案主張期間作為輸出提供的主張ID。 請參閱[優惠方案主張](#offer-proposition)。
* **狀態**：字串型別，它指定選件的新狀態。 可能的值列在&#x200B;**nms：common**&#x200B;結構描述的&#x200B;**propositionStatus**&#x200B;列舉中。 例如，數字3是現成可用的，對應至&#x200B;**已接受**&#x200B;狀態。
* **context**： XML元素，可讓您在空間結構描述中新增內容資訊。 如果使用的結構描述是&#x200B;**nms：interaction**，則應新增&#x200B;**`<empty>`**。

## 使用SOAP呼叫的範例 {#example-using-a-soap-call}

您會在下方找到SOAP呼叫的程式碼範例。

以下是URL的範例：

```
http://<urlOfYourJSSP>?env=liveRcp&sp=<nameSpaceOfferSpace>&t=<targetID>
```

```
<%
  var env = request.getUTF8Parameter("env");
  var space = request.parameters.sp
  var cnx = new HttpSoapConnection(
    "https://" + request.serverName + ":" + request.serverPort + "/interaction/" + env + "/" + space,
    "utf-8",
    HttpSoapConnection.SOAP_12)
  var session = new SoapService(cnx, "nms:interaction")
  var action = request.parameters.a
  if( action == undefined )
    action = 'propose'

  try
  {
    switch( action )
    {
    case "update":
      var proposition = request.parameters.p
      var status      = request.parameters.st
      session.addMethod("UpdateStatus", "nms:interaction#UpdateStatus",
       ["proposition", "string",
        "status",      "string",
        "context",     "NLElement"],
       [])
      session.UpdateStatus(proposition, status, <undef/>)
      var redirect = request.parameters.r
      if( redirect != undefined )
        response.sendRedirect(redirect)
      break;

    case "propose":
      var count = request.parameters.n
      var target = request.parameters.t
      var categorie = request.parameters.c
      var theme = request.parameters.th
      var layout = request.parameters.l
      if( count == undefined )
        count = 1
      session.addMethod("Propose", "nms:proposition#Propose",
       ["targetId",      "string",
        "maxCount",      "string",
         "categories",    "string",
         "themes",        "string",
        "context",       "NLElement"],
       ["interactionId", "string",
        "propositions",  "NLElement"])
      response.setContentType("text/html")
      var result = session.Propose(target, count, category, theme, <empty/>)
      var props = result[1]
  %><table><tr><%
      for each( var propHtml in props.proposition.*.htmlSource )
      {
        %><td><%=propHtml%></td><%
      }
  %></tr></table><%
      break;
    }
  }
  catch( e )
  {
  }
  %>
```
