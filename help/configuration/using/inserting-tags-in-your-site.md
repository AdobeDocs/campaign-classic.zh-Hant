---
title: 在您的網站中插入標籤
seo-title: 在您的網站中插入標籤
description: 在您的網站中插入標籤
seo-description: null
page-status-flag: never-activated
uuid: e5e4a431-2093-4d5a-acd2-0040b6ce3519
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 57988b00-62cc-43d3-a2eb-bfed5bff7dc1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# 在您的網站中插入標籤{#inserting-tags-in-your-site}

## 簡單方法 {#simple-method}

此方法包括透過在您要追蹤之網頁的HTML原始碼中插入 **`<img>`** HTML標籤，將HTTP呼叫傳送至重新導向伺服器。

>[!CAUTION]
>
>此方法使用網頁瀏覽器傳送的Cookie來識別收件者，且不能100%可靠。

**範例**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

插入的標籤與重定向伺服器聯繫。

![](assets/d_ncs_integration_webtracking_structure2.png)

當您定義要在主控台中追蹤的頁面時，可以產生範例網頁追蹤標籤，以複製並貼至網頁的原始碼中。

但是，在使用TRANSACTION-type標籤時，必須使用JavaScript修改示例標籤，以插入事務資訊（金額、項目數）和擴展架構定義的任何資訊。

### 標籤的靜態插入 {#static-insertion-of-tags}

若要執行靜態標籤插入，只需將主控台產生或手動建構的標籤複製並貼入網頁來源即可。

**範例**:在顯示表單的頁面上插入網頁追蹤標籤。

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

在確認頁面(&quot;amount.md&quot;)中插入TRANSACTION類型的Web追蹤標籤。

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

動態產生網頁時，您可以在頁面產生時新增網頁追蹤標籤。

**範例**:已新增網路追蹤至JSP。

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

## 最佳化方法 {#optimum-method-}

如果您想要控制傳送至重新導向伺服器的資訊，最可靠的方式是使用頁面產生語言自行同步執行HTTP查詢。

您建構的URL必須遵循Web追蹤標籤中定義的 [語法規則：定義](../../configuration/using/web-tracking-tag--definition.md)。

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>重新導向和網路追蹤使用Cookie，而且執行同步HTTP呼叫的網頁伺服器必須與重新導向伺服器位於相同的網域中。 各種HTTP交換必須傳達&#39;id&#39;、&#39;uuid&#39;和&#39;uuid230&#39; Cookie。

**範例**:在Java中動態產生，並使用收件者的帳號進行驗證。

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

