---
product: campaign
title: 指令碼和程式碼指南
description: 進一步瞭解在Adobe Campaign中進行開發時應遵循的准則（工作流程、Javascript、JSSP等）
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 1f96c3df-0ef2-4f5f-9c36-988cbcc0769f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 5%

---

# 指令碼和程式碼指南 {#scripting-coding-guidelines}



## 指令碼

如需詳細資訊，請參閱 [Campaign JSAPI檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant).

如果您使用工作流程、網頁應用程式、jssp編寫指令碼，請遵循以下最佳實務：

* 儘可能避免使用SQL敘述句。

* 如果需要，請使用引數化（準備陳述式）函式，而非字串串串連。

  不當做法：

  ```
  sqlGetInt( "select iRecipientId from NmsRecipient where sEmail ='" + request.getParameter('email') +  "'  limit 1" )
  ```

  良好實務：

  ```
  sqlGetInt( "select iRecipientId from NmsRecipient where sEmail = $(sz) limit 1", request.getParameter('email'));
  ```

  >[!IMPORTANT]
  >
  >sqlSelect不支援此功能，因此您必須使用DBEngine類別的查詢函式：

  ```
  var cnx = application.getConnection()
  var stmt = cnx.query("SELECT sFirstName, sLastName FROM NmsRecipient where sEmail = $(sz)", request.getParameter('email'))
  for each(var row in stmt) logInfo(row[0] + " : " + row[1])
  cnx.dispose()
  ```

若要避免SQL插入，必須將SQL函式新增至允許清單，才能在Adobe Campaign中使用。 將變數新增至允許清單後，運運算元就會在運算式編輯器中看見該變數。 請參見[此頁面](../../configuration/using/adding-additional-sql-functions.md)。

>[!IMPORTANT]
>
>如果您使用的組建版本早於8140，則 **xtkpassunknowledsqlfunctionsToRDBMS** 選項可設為&#39;1&#39;。 如果要保護資料庫的安全，請刪除此選項（或將它設定為&#39;0&#39;）。

如果您使用使用者輸入在查詢或SQL陳述式中建置篩選器，您必須一律將其逸出(請參閱 [Campaign JSAPI檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant)  — 資料保護：逸出功能)。 這些函式包括：

* NL.XML.escape(data)
* NL.SQL.escape(data)
* NL.JS.escape(data)
* NL.XML.escapeAttribute(data)

## 保護您的新資料模型

### 資料夾基底

請參閱下列頁面：

* [資料夾存取屬性](../../platform/using/access-management.md)
* [連結的資料夾](../../configuration/using/configuration.md#linked-folder)

### 已命名的權限

除了資料夾式安全性模型之外，您還可以使用已命名的許可權來限制操作員動作：

* 您可以新增一些系統篩選器(sysFilter)，以防止讀取/寫入您的資料(請參閱 [此頁面](../../configuration/using/filtering-schemas.md))。

  ```
  <sysFilter name="writeAccess">    
      <condition enabledIf="hasNamedRight('myNewRole')=false" expr="FALSE"/>  
  </sysFilter>
  ```

* 您也可以保護結構描述中定義的某些動作（SOAP方法）。 只需設定存取屬性，並將對應的已命名許可權設為值即可。

  ```
  <method name="grantVIPAccess" access="myNewRole">
      <parameters>
  ...
      </parameters>
  </method>
  ```

  如需詳細資訊，請參閱[此頁面](../../configuration/using/implementing-soap-methods.md)。

>[!IMPORTANT]
>
>您可以在導覽樹狀結構的命令節點中使用已命名的許可權。 它提供更佳的使用者體驗，但不提供任何保護（僅使用使用者端隱藏/停用它們）。 您必須使用access屬性。

### 溢位表格

如果您需要根據運運算元存取層級保護機密資料（結構描述的一部分），請勿在表單定義（enabledIf/visibleIf條件）中隱藏這些資料。

熒幕會載入完整圖元，您也可以在欄定義中顯示它們。 要執行此操作，您必須建立溢位表格。 參考 [此頁面](../../configuration/using/examples-of-schemas-edition.md#overflow-table).

## 在網頁應用程式中新增字幕

在公開登陸頁面/訂閱頁面中新增驗證碼是建議的做法。 不幸的是，在DCE （數位內容編輯器）頁面中新增驗證碼並不容易。 我們將說明如何新增v5驗證碼或Google reCAPTCHA。

在DCE中新增驗證碼的一般方法是建立個人化區塊，以便輕鬆將其納入頁面內容中。 您必須新增 **指令碼** 活動和 **測試**.

### 個人化區塊

1. 前往 **[!UICONTROL Resources]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Personalization blocks]** 並建立一個新的。

1. 使用 **[!UICONTROL Web application]** 內容型別和檢查 **[!UICONTROL Visible in the customization menus]**.

   如需詳細資訊，請參閱[本頁面](../../delivery/using/personalization-blocks.md)。

   以下是的範例 **Campaign驗證碼**：

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

   * 第1行至第6行會產生所有需要的輸入。
   * 第7行到結尾控制代碼錯誤。
   * 第4行可讓您變更驗證碼灰色方塊大小（寬度/高度）和產生的文字長度(minWordSize/maxWordSize)。
   * 在使用Google reCAPTCHA之前，您必須在Google上註冊並建立新的reCAPTCHA網站。

     `<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>`

   您應該能夠停用驗證按鈕，但由於我們沒有任何標準按鈕/連結，所以最好在HTML中自行操作。 若要瞭解其操作方式，請參閱 [此頁面](https://developers.google.com/recaptcha/).

### 更新您的Web應用程式

1. 存取網頁應用程式的屬性，以新增名為的布林值變數 **驗證碼有效**.

   ![](assets/scripting-captcha.png)

1. 最後一頁和之間 **[!UICONTROL Storage]** 活動，新增 **[!UICONTROL Script]** 和 **[!UICONTROL Test]**.

   插入分支 **[!UICONTROL True]** 至 **[!UICONTROL Storage]** 另一個連線至將具有驗證碼的頁面。

   ![](assets/scripting-captcha2.png)

1. 使用編輯分支的條件True `"[vars/captchaValid]"` 等於True。

   ![](assets/scripting-captcha3.png)

1. 編輯 **[!UICONTROL Script]** 活動。 內容將取決於所選的驗證碼引擎。

1. 最後，您可以在頁面中新增個人化區塊：請參閱 [此頁面](../../web/using/editing-content.md).

   ![](assets/scripting-captcha4.png)

   ![](assets/scripting-captcha5.png)

>[!IMPORTANT]
>
>若為reCAPTCHA整合，您必須在HTML中新增使用者端JavaScript (在 `<head>...</head>`)：
>
>`<script src="https://www.google.com/recaptcha/api.js" async defer></script>`

### Campaign驗證碼

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

第6行：您可以輸入任何型別的錯誤訊息。

### Google recaptcha

請參閱 [正式檔案](https://developers.google.com/recaptcha/docs/verify).

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

若要使用JSON.parse，您必須在webApp中加入「shared/json2.js」：

![](assets/scripting-captcha6.png)

從建置8797開始，若要使用驗證API URL，您必須透過在urlPermission節點中新增來將它新增到serverConf檔案的允許清單中：

`<url dnsSuffix="www.google.com" urlRegEx="https://www.google.com/recaptcha/api/siteverify"/>`
