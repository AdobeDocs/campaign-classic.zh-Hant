---
solution: Campaign Classic
product: campaign
title: 指令碼和編碼准則
description: 進一步瞭解在Adobe Campaign進行開發時應遵循的准則（工作流程、Javascript、JSSP等）。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 4%

---


# 指令碼和編碼准則{#scripting-coding-guidelines}

## 指令碼

如需詳細資訊，請參閱[促銷活動JSAPI檔案](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

如果您使用工作流程、Web應用程式、工作階段編寫指令碼，請遵循下列最佳實務：

* 盡量避免使用SQL陳述式。

* 如果需要，請使用參數化（prepare語句）函式，而不是字串串連。

   壞做法：

   ```
   sqlGetInt( "select iRecipientId from NmsRecipient where sEmail ='" + request.getParameter('email') +  "'  limit 1" )
   ```

   良好做法：

   ```
   sqlGetInt( "select iRecipientId from NmsRecipient where sEmail = $(sz) limit 1", request.getParameter('email'));
   ```

   >[!IMPORTANT]
   >
   >sqlSelect不支援此功能，因此您必須使用DBEngine類的查詢函式：

   ```
   var cnx = application.getConnection()
   var stmt = cnx.query("SELECT sFirstName, sLastName FROM NmsRecipient where sEmail = $(sz)", request.getParameter('email'))
   for each(var row in stmt) logInfo(row[0] + " : " + row[1])
   cnx.dispose()
   ```

為避免插入SQL，必須將SQL函式添加到允許清單中，以便在Adobe Campaign使用。 將它們新增至允許清單後，運算式編輯器中的運算子就會看到它們。 請參見[此頁面](../../configuration/using/adding-additional-sql-functions.md)。

>[!IMPORTANT]
>
>如果您使用的內部版本早於8140,**XtkPassUnknownSQLFunctionsToRDBMS**&#x200B;選項可能會設為&#39;1&#39;。 如果要保護資料庫，請刪除此選項（或將其設定為&#39;0&#39;）。

如果您使用使用者輸入來建立查詢或SQL陳述式中的篩選器，則必須一律加以逸出(請參閱[Campaign JSAPI檔案](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html) —— 資料保護：逸出函式)。 這些函式包括：

* NL.XML.escape(data)
* NL.SQL.escape(data)
* NL.JS.escape(data)
* NL.XML.escapeAttribute(data)

## 保護新資料模型的安全

### 資料夾庫

請參閱以下頁面：

* [資料夾訪問屬性](../../platform/using/access-management.md)
* [連結的資料夾](../../configuration/using/configuration.md#linked-folder)

### 命名權限

除了資料夾型安全性模型外，您也可以使用命名權限來限制運算元動作：

* 您可以添加一些系統篩選器(sysFilter)來防止對資料的讀／寫（請參見[本頁](../../configuration/using/filtering-schemas.md)）。

   ```
   <sysFilter name="writeAccess">    
       <condition enabledIf="hasNamedRight('myNewRole')=false" expr="FALSE"/>  
   </sysFilter>
   ```

* 您也可以保護在結構描述中定義的某些操作（SOAP方法）。 只需將具有相應命名權限的訪問屬性設定為值即可。

   ```
   <method name="grantVIPAccess" access="myNewRole">
       <parameters>
   ...
       </parameters>
   </method>
   ```

   有關詳細資訊，請參見[此頁面](../../configuration/using/implementing-soap-methods.md)。

>[!IMPORTANT]
>
>您可以在navtree的命令節點中使用命名權限。 它提供更佳的使用者體驗，但不提供任何保護（僅使用用戶端來隱藏／停用它們）。 您必須使用access屬性。

### 溢位表

如果您需要根據運算子存取層級來保護機密資料（架構的一部分），請勿在表單定義（enabledIf/visibleIf條件）中隱藏機密資料。

全圖元由畫面載入，您也可以在欄定義中顯示。 為此，必須建立溢出表。 請參閱[本頁](../../configuration/using/examples-of-schemas-edition.md#overflow-table)。

## 在Web應用程式中新增擷取功能

在公開的登陸頁面／訂閱頁面中新增驗證碼是個很好的做法。 很遺憾，在DCE（數字內容編輯器）頁面中添加驗證碼並不容易。 我們將示範如何新增v5 captcha或Google reCAPTCHA。

在DCE中添加驗證碼的一般方法是建立個性化塊，以便輕鬆將其包含在頁面內容中。 您必須新增&#x200B;**Script**&#x200B;活動和&#x200B;**Test**。

### 個人化區塊

1. 前往&#x200B;**[!UICONTROL Resources]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Personalization blocks]**&#x200B;並建立新的。

1. 使用&#x200B;**[!UICONTROL Web application]**&#x200B;內容類型並檢查&#x200B;**[!UICONTROL Visible in the customization menus]**。

   如需詳細資訊，請參閱[本頁面](../../delivery/using/personalization-blocks.md)。

   以下是&#x200B;**促銷活動captcha**&#x200B;的範例：

   ```javascript
   <%
   var captchaID = CaptchaIDGen();
   %>
   <img src="/nms/jsp/captcha.jsp?captchaID=<%=captchaID%>&width=200&height=50&minWordSize=8&maxWordSize=8"/>
   <input id="captchaValue" name="captchaValue" <%= String(ctx.vars.captchaValid) === "false" ? class="ui-state-error" : "" %>>
   <input type="hidden" name="captchaID" value="<%=captchaID%>"/>
   <%
   if( serverForm.isInputErroneous("captchaValue") ) {
   %>
   <script type="text/javascript"> 
   $("#captchaValue").addClass("ui-state-error")
   </script>
   <%
   }
   %>
   ```

   * 第1至6行產生所有需要的輸入。
   * 行7到末端手柄錯誤。
   * 第4行可讓您變更驗證碼灰色方塊大小（寬度／高度）和產生的字詞長度(minWordSize/maxWordSize)。
   * 在使用Google reCAPTCHA之前，您必須在Google上註冊並建立新的reCAPTCHA網站。

      `<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>`
   您應該可以停用驗證按鈕，但是由於我們沒有任何標準按鈕／連結，所以最好在HTML本身中執行。 要瞭解如何執行，請參閱[本頁](https://developers.google.com/recaptcha/)。

### 更新您的Web應用程式

1. 存取Web應用程式的屬性，以新增名為&#x200B;**captchaValid**&#x200B;的布林變數。

   ![](assets/scripting-captcha.png)

1. 在最後一頁和&#x200B;**[!UICONTROL Storage]**&#x200B;活動之間，添加&#x200B;**[!UICONTROL Script]**&#x200B;和&#x200B;**[!UICONTROL Test]**。

   將分支&#x200B;**[!UICONTROL True]**&#x200B;插入&#x200B;**[!UICONTROL Storage]**，將另一個分支插入具有captcha的頁面。

   ![](assets/scripting-captcha2.png)

1. 編輯分支True的條件，`"[vars/captchaValid]"`等於True。

   ![](assets/scripting-captcha3.png)

1. 編輯&#x200B;**[!UICONTROL Script]**&#x200B;活動。 內容將視所選的captcha引擎而定。

1. 最後，您可以在頁面中新增個人化區塊：請參閱[本頁](../../web/using/editing-content.md)。

   ![](assets/scripting-captcha4.png)

   ![](assets/scripting-captcha5.png)

>[!IMPORTANT]
>
>若要進行reCAPTCHA整合，您必須在HTML（在`<head>...</head>`中）中新增用戶端JavaScript:
>
>`<script src="https://www.google.com/recaptcha/api.js" async defer></script>`

### 促銷活動captcha

```javascript
var captchaID = request.getParameter("captchaID");
var captchaValue = request.getParameter("captchaValue");
  
if( !CaptchaValidate(captchaID, captchaValue) ) {
  serverForm.logInputError("captchaValue",
                           "The characters you typed for the captcha must match the image ones.",
                           "captchaValue")
  ctx.vars.captchaValid = false
}
else
  ctx.vars.captchaValid = true
```

第6行：您可以放置任何類型的錯誤訊息。

### Google recaptcha

請參閱[官方檔案](https://developers.google.com/recaptcha/docs/verify)。

```javascript
ctx.vars.captchaValid = false
var gReCaptchaResponse = request.getParameter("g-recaptcha-response");
  
// Call reCaptcha API to validate it
var req = new HttpClientRequest("https://www.google.com/recaptcha/api/siteverify")
req.method = "POST"
req.header["Content-Type"] = "application/x-www-form-urlencoded"
req.body = "secret=YOUR_SECRET_HERE&response=" + encodeURIComponent(gReCaptchaResponse)
req.execute()
var response = req.response
if( response.code == 200 ) {
  captchaRes = JSON.parse(response.body.toString(response.codePage));
  ctx.vars.captchaValid = captchaRes.success
}
  
if( ctx.vars.captchaValid == false ) {
  serverForm.logInputError("reCaptcha",
                           "Please validate the captcha",
                           "reCaptcha")
  logInfo("reCaptcha not validated")
}
```

若要使用JSON.parse，您必須在webApp中加入「shared/json2.js」:

![](assets/scripting-captcha6.png)

自建置8797以來，為了使用驗證API URL，您必須將它新增至urlPermission節點中的serverConf檔案中的allow清單：

`<url dnsSuffix="www.google.com" urlRegEx="https://www.google.com/recaptcha/api/siteverify"/>`
