---
product: campaign
title: 在您的網站中插入網頁追蹤標籤
description: 瞭解如何在您的網站中插入網頁追蹤標籤
feature: Configuration
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
exl-id: e7fcec75-82fe-45ff-8d45-7d6e95baeb14
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 2%

---

# 在您的網站中插入網頁追蹤標籤{#inserting-tags-in-your-site}

## 簡單方法 {#simple-method}

此方法包含透過插入「 」將HTTP呼叫傳送至重新導向伺服器 **`<img>`** HTML標籤，該標籤位於您要追蹤之網頁的HTML原始碼中。

>[!IMPORTANT]
>
>此方法會使用網頁瀏覽器傳送的Cookie來識別收件者，而且並非100%可靠。

**範例**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

插入的標籤會連絡重新導向伺服器。

![](assets/d_ncs_integration_webtracking_structure2.png)

當您定義要在主控台中追蹤的頁面時，可以產生範例網頁追蹤標籤，以複製並貼到網頁的原始程式碼中。

但是，當您使用TRANSACTION型別標籤時，必須使用JavaScript修改範例標籤，以便插入交易資訊（金額、專案數）和擴充功能架構定義的任何資訊。

### 靜態插入標籤 {#static-insertion-of-tags}

若要執行靜態標籤插入，只需複製並貼上主控台產生的標籤或手動建構到網頁的來源中即可。

**範例**：在顯示表單的頁面上插入網頁追蹤標籤。

```
<html>
  <...>
  <body>
  <script>
      document.write("<img height='0' width='0' alt='' src='https://localhost/r/" + Math.random().toString() + "?tagid=home'>");
    </script>
    <noscript>
     <img height='0' width='0' alt='' src='https://localhost/r/?tagid=home'>
    </noscript>
    <h1>My site</h1>
    <form action="http://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

在確認頁面(「amount.md」)中插入TRANSACTION型別的網頁追蹤標籤。

```
<html>
  <body>
    <script>
      function getURLparam(name) 
      {
        var m = location.search.match new RegExp("[?&]" + name + "=([^&]+)"));
        return m ? unescape(m[1]) : "";
      }
 
       var params = "https://localhost/r/" + Math.random().toString() + "?tagid=amount&amount="
                      +getURLparam("amount")+"&article="+getURLparam("quantity");
       document.write("<img height='0' width='0' src='"+params+"'/>");
    </script>

    <h1>Approval confirmation</h1>
  </body>
</html>
```

### 動態產生網頁追蹤標籤 {#dynamic-generation-of-web-tracking-tags}

如果網頁是以動態方式產生，您可以在產生頁面時新增網頁追蹤標籤。

**範例**：網頁追蹤已新增到JSP。

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <img height='0' width='0' alt='' src='https://localhost/r/<%=new Random().nextInt()%>?tagid=home'>
    <h1>My site</h1>
    <form action="https://localhost/amount.md">
      Quantity: <input type="text" name="quantity"/><br/><br/>
      Amount: <input type="text" name="amount"/><br/><br/>
      <input value="Save" type="submit">
    </form>
  </body>
</html>
```

```
<%@page import="java.util.Random" %>
<html>
  <body>
    <%  
      String strParams = new Random().nextInt() + "?tagid=amount";
      strParams += "&amount="+request.getParameter("amount");
      strParams += "&article="+request.getParameter("quantity");
    %>
    <img height='0' width='0' alt=''
     src='http://localhost/r/<%=strParams%>'>
    <h1>Approval confirmation</h1>
    </body>
</html>
```

## 最佳方法 {#optimum-method-}

如果您希望控制傳送至重新導向伺服器的資訊，最可靠的方式是使用頁面產生語言自行同步執行HTTP查詢。

您建構的URL必須符合中定義的語法規則。 [網路追蹤標籤：定義](../../configuration/using/web-tracking-tag--definition.md).

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>重新導向和網頁追蹤使用Cookie，執行同步HTTP呼叫的網頁伺服器務必要與重新導向伺服器位在相同網域中。 各種HTTP交換必須傳遞「id」、「uuid」和「uuid230」Cookie。

**範例**：在Java中動態產生，收件者使用其帳號進行驗證。

```
[...]
  // Recipient account, amount and articles
  String strAccount = request.getParameter("account");
  String strAmount = request.getParameter("amount");
  String strArticle = request.getParameter("article");

  StringBuffer strCookies = new StringBuffer();
  String strSetCookie = null;

  // Get cookies from client request
  Cookie[] cookies = request.getCookies();
  for(int i=0; i< cookies.length; i++ )
  {
    Cookie c = cookies[i];
    String strName = c.getName();
    if( strName.equals("id") || strName.equals("uuid") || strName.equals("uuid230") )
      // Helper function to add cookies in string
      AddCookie(strCookies, c);
  }
  // Now perform a synchronous HTTP request to inform redirection server
  // Add a tagid in auto-discover mode, and a default jobId to use (in hexa)
  StringBuffer strURL = new StringBuffer("https://www.adobe.com/r/a?tagid=cmd_page%7Ct&jobid=27EE");
  if( strAccount != null )
    AddParameter(strURL, "rcpid", "saccount="+strAccount);
  if( strAmount != null )
    AddParameter(strURL, "amount", strAmount);
  if( strArticle != null )
    AddParameter(strURL, "article", strArticle);
  
  URL url = new URL(strURL.toString());
  HttpURLConnection connection = (HttpURLConnection)url.openConnection();
  // Add the client cookies
  if( strCookies.length() > 0 )
    connection.setRequestProperty("Cookie", strCookies.toString());

  int errcode = connection.getResponseCode();

  // Now add the Adobe Campaign cookies if the server returned one :
  if( errcode == 200 )
  {
    strSetCookie = connection.getHeaderField("Set-Cookie");
    if( strSetCookie != null && strSetCookie.length() > 0 )
      response.addHeader("Set-Cookie", strSetCookie);
  }
  [...]
```
