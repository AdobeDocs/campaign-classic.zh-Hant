---
solution: Campaign Classic
product: campaign
title: 透過 SOAP 整合 (伺服器端)
description: 透過 SOAP 整合 (伺服器端)
audience: interaction
content-type: reference
topic-tags: unitary-interactions
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 3%

---


# 透過SOAP（伺服器端）進行整合{#integration-via-soap-server-side}

為選件管理提供的SOAP網站服務與Adobe Campaign中通常使用的服務不同。 您可透過上一節所述的互動URL來存取這些選件，並讓您為特定連絡人呈現或更新選件。

## 優惠提案{#offer-proposition}

如需透過SOAP的選件提案，請新增&#x200B;**nms:competion#Phonde**&#x200B;命令，後面接著下列參數：

* **targetId**:收件者的主要金鑰（可以是複合金鑰）。
* **maxCount**:指定聯繫人的選件建議數。
* **內容**:可讓您在空間架構中添加上下文資訊。如果使用的模式為&#x200B;**nms:interaction**，則應添加&#x200B;**`<empty>`**。
* **類別**:指定選件必須屬於的類別。
* **主題**:指定選件必須屬於的主題。
* **uuid**:值(「uuid230」)。
* **nli**:值(「nlid」)。
* **noProp**:使用「true」值停用提案插入。

>[!NOTE]
>
>**targetId**&#x200B;和&#x200B;**maxCount**&#x200B;設定是強制性的。 其他則是選擇性的。

響應查詢，SOAP服務將返回以下參數：

* **interactionId**:互動的ID。
* **主張**:XML元素，包含命題的清單，每個命題都有其專屬的ID和HTML表示法。

## 選件更新{#offer-update}

將&#x200B;**nms:interaction#UpdateStatus**&#x200B;命令添加到URL中，後跟以下參數：

* **主張**:字元字串中，它包含選件提案期間輸出的提案ID。請參閱[優惠提案](#offer-proposition)。
* **狀態**:字串類型，它會指定選件的新狀態。可能的值列在&#x200B;**命題狀態**&#x200B;枚舉中，在&#x200B;**nms:common**&#x200B;模式中。 例如，現成可用的數字3與&#x200B;**Accepted**&#x200B;狀態相對應。
* **內容**:XML元素，可讓您在空間架構中新增上下文資訊。如果使用的模式為&#x200B;**nms:interaction**，則應添加&#x200B;**`<empty>`**。

## 使用SOAP呼叫{#example-using-a-soap-call}的範例

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
