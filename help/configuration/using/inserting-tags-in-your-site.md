---
product: campaign
title: 在您的網站中插入標籤
description: 在您的網站中插入標籤
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: e7fcec75-82fe-45ff-8d45-7d6e95baeb14
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 5%

---

# 在您的網站中插入標籤{#inserting-tags-in-your-site}

## 簡單方法{#simple-method}

此方法包括透過在您要追蹤之網頁的HTML原始碼中插入&#x200B;**`<img>`** HTML標籤，將HTTP呼叫傳送至重新導向伺服器。

>[!IMPORTANT]
>
>此方法會使用網頁瀏覽器傳送的Cookie來識別收件者，且不能100%可靠。

**範例**:

```
<img height='0' width='0' alt='' src='https://localhost/r/12343?tagid=home'
```

插入的標籤與重定向伺服器聯繫。

![](assets/d_ncs_integration_webtracking_structure2.png)

當您在主控台中定義要追蹤的頁面時，可以產生範例網頁追蹤標籤，以複製並貼到網頁的原始碼中。

但是，使用TRANSACTION類型標籤時，必須使用JavaScript修改示例標籤，以插入事務資訊（金額、項目數）和擴展架構定義的任何資訊。

### 標籤{#static-insertion-of-tags}的靜態插入

若要執行靜態標籤插入，只需將主控台產生或手動建構的標籤複製並貼到網頁來源即可。

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

在確認頁面(「amount.md」)中插入TRANSACTION類型的Web追蹤標籤。

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

### 動態產生網頁追蹤標籤{#dynamic-generation-of-web-tracking-tags}

動態產生網頁時，您可以在頁面產生時新增網頁追蹤標籤。

**範例**:JSP中添加了Web跟蹤。

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

## 最佳方法{#optimum-method-}

如果您希望控制發送到重定向伺服器的資訊，最可靠的方法是使用頁面生成語言自行同步執行HTTP查詢。

您建構的URL必須遵循[Web追蹤標籤中定義的語法規則：definition](../../configuration/using/web-tracking-tag--definition.md)。

![](assets/d_ncs_integration_webtracking_structure3.png)

>[!NOTE]
>
>重定向和Web跟蹤使用Cookie，執行同步HTTP調用的Web伺服器必須與重定向伺服器位於同一域中。 各種HTTP交換必須傳達「id」、「uuid」和「uuid230」Cookie。

**範例**:以Java動態產生，收件者使用其帳號進行驗證。

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
