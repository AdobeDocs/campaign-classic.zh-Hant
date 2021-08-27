---
product: campaign
title: 透過 SOAP 整合 (伺服器端)
description: 透過 SOAP 整合 (伺服器端)
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 3%

---

# 透過SOAP整合（伺服器端）{#integration-via-soap-server-side}

![](../../assets/v7-only.svg)

為選件管理提供的SOAP Web服務與Adobe Campaign中通常使用的服務不同。 您可以透過前一節所述的互動URL來存取這些選件，並讓您為特定連絡人呈現或更新選件。

## 優惠方案主張 {#offer-proposition}

如需透過SOAP的優惠方案主張，請新增&#x200B;**nms:composition#Propose**&#x200B;命令，後面接著下列參數：

* **targetId**:收件者的主要金鑰（可以是複合金鑰）。
* **maxCount**:指定聯繫人的優惠方案數。
* **內容**:可讓您在空間架構中新增內容資訊。如果使用的架構為&#x200B;**nms:interaction**，則應新增&#x200B;**`<empty>`**。
* **類別**:指定選件必須屬於的類別。
* **主題**:指定選件必須屬於的主題。
* **uuid**:Adobe Campaign永久cookie的值(「uuid230」)。
* **nli**:Adobe Campaign工作階段cookie的值(「nlid」)。
* **noProp**:使用&quot;true&quot;值停用建議插入。

>[!NOTE]
>
>**targetId**&#x200B;和&#x200B;**maxCount**&#x200B;設定是強制性的。 其他則為選用。

響應查詢，SOAP服務將返回以下參數：

* **interactionId**:互動的ID。
* **主張**:XML元素，包含命題的清單，每個命題都有自己的ID和HTML表示。

## 選件更新 {#offer-update}

將&#x200B;**nms:interaction#UpdateStatus**&#x200B;命令添加到URL，然後添加以下參數：

* **主張**:字元字串，其中包含在優惠方案主張期間以輸出形式提供的主張ID。請參閱[優惠方案主張](#offer-proposition)。
* **狀態**:字串類型，它會指定選件的新狀態。可能的值列在&#x200B;**命題狀態**&#x200B;枚舉中，位於&#x200B;**nms:common**&#x200B;方案中。 例如，現成可用，數字3對應於&#x200B;**接受**&#x200B;狀態。
* **內容**:XML元素，可讓您在空間架構中添加上下文資訊。如果使用的架構為&#x200B;**nms:interaction**，則應新增&#x200B;**`<empty>`**。

## 使用SOAP呼叫的範例 {#example-using-a-soap-call}

以下是SOAP呼叫的程式碼範例：

```
<%
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
      for each( var propHtml in props.proposition.*.mdSource )
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
