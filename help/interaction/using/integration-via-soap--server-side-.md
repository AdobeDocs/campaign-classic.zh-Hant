---
product: campaign
title: 透過 SOAP 整合 (伺服器端)
description: 透過 SOAP 整合 (伺服器端)
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: unitary-interactions
exl-id: 3eaef689-44fa-41b3-ade8-9fe447e165ec
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 3%

---

# 透過SOAP整合（伺服器端）{#integration-via-soap-server-side}



為選件管理提供的SOAP Web服務與Adobe Campaign中常用的不同。 可透過上一節所述的互動URL存取優惠方案，並讓您提供或更新指定連絡人的優惠方案。

## 優惠方案主張 {#offer-proposition}

針對透過SOAP的優惠方案主張，新增 **nms：proposition#Propose** 命令後接下列引數：

* **targetId**：收件者的主鍵（可以是複合鍵）。
* **maxCount**：指定聯絡人的優惠方案主張數量。
* **內容**：可讓您在空間結構描述中新增內容資訊。 如果使用的結構描述是 **nms：interaction**， **`<empty>`** 應已新增。
* **類別**：指定優惠方案必須所屬的類別。
* **主題**：指定選件必須屬於的主題。
* **uuid**：Adobe Campaign永久cookie的值(「uuid230」)。
* **nli**：Adobe Campaign工作階段Cookie的值(「nlid」)。
* **noProp**：使用「true」值來停用提案插入。

>[!NOTE]
>
>此 **targetId** 和 **maxCount** 設定是強制性的。 其他則是選擇性的。

為回應查詢，SOAP服務將傳回下列引數：

* **interactionId**：互動的ID。
* **主張**： XML元素，包含主張清單，每個主張都有自己的ID和HTML表示。

## 優惠更新 {#offer-update}

新增 **nms：interaction#UpdateStatus** 命令前往URL，接著執行下列引數：

* **主張**：字元字串，其中包含優惠方案主張期間作為輸出提供的主張ID。 請參閱 [優惠方案主張](#offer-proposition).
* **狀態**：字串型別，它指定選件的新狀態。 可能的值會列在 **propositionStatus** 分項清單，在 **nms：common** 結構描述。 例如，數字3是現成可用的，會對應至 **已接受** 狀態。
* **內容**：XML元素，可讓您在空間結構描述中新增內容資訊。 如果使用的結構描述是 **nms：interaction**， **`<empty>`** 應已新增。

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
