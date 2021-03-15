---
solution: Campaign Classic
product: campaign
title: 追蹤URL的預處理指示
description: 進一步瞭解使用來編寫電子郵件URL的指令碼，並仍會加以追蹤的預先處理指示。
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 8aab4bc23d688aa225cfc636936cf2835840e410
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---


# 預處理指令{#pre-processing-instructions}

您可以在傳送內容中使用特定語法來新增指示，並為追蹤之電子郵件的URL編寫指令碼。 &lt;%@指示不是JavaScript:此語法是Adobe Campaign特有的。

它們僅適用於傳送內容的內容。 這是為電子郵件的URL編寫指令碼並仍然追蹤（除了URL參數外）的唯一方法。 在偵測要追蹤的連結之前，這些連結可視為在傳送分析期間套用的自動複製／貼上。

說明有三種類型：

* **[!DNL include]**:主要用來將選項、個人化區塊、外部檔案或頁面中的某些程式碼分解。[進一步了解](#include)
* **[!DNL value]**:可存取傳送、傳送變數和傳送中載入的自訂物件欄位。[進一步了解](#value)
* **[!DNL foreach]**:以循環載入為自定義對象的陣列。[進一步了解](#foreach)

您可直接從傳送精靈中測試。 它們會套用在內容預覽中，當您按一下追蹤按鈕以查看URL清單時。

## [!DNL include] {#include}

下列範例是最常使用的範例：

* 包括鏡像頁連結：

   ```
   <%@ include view="MirrorPage" %>  
   ```

* 鏡像頁面URL:

   ```
   View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
   ```

* 立即可用的取消訂閱URL:

   ```
   <%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>
   ```

* 其他範例：

   ```
   <%@ include file='http://www.google.com' %>
   <%@ include file='file:///X:/france/service/test.html' %>
   <%@ include option='NmsServer_URL' %>
   ```

   使用傳送精靈中的個人化按鈕，取得正確的語法。

## [!DNL value] {#value}

本說明提供對所有收件者都恆定的傳送參數的存取。

語法:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

其中：

* **[!DNL object]**:對象的名稱(示例：傳送、提供者等)。對象可以是：
   * **[!DNL delivery]**:（請參閱下方子節中的詳細資訊和限制）。
   * **[!DNL provider]**:(nms:externalAccount)。
   * 額外的指令碼物件：如果對象通過以下方式載入到上下文：**屬性** > **個人化** > **在執行上下文中添加對象**。
   * 前循環項：請參閱下面的[Foreach](#foreach)一節。
* **[!DNL xpath]**:xpath。
* **[!DNL index]** （可選）:如 **[!DNL object]** 果是陣列（對於額外指令碼對象），則陣列中的項目索引（從0開始）。

### [!DNL delivery] 物件 {#delivery-object}

對於電子郵件個人化，傳送物件可透過兩種方式存取：

* 使用JavaScript:

   ```
   <%= delivery.myField %>`.
   ```

   在JavaScript物件傳送中不支援自訂欄位。 它們可在預覽中運作，但在MTA中無法運作，因為MTA只能存取現成可用的傳送架構。

* 使用預處理：

   ```
   <%@ value object="delivery"
   ```


**警告**

如果您使用下列指示來傳送經由中部來源補充傳送，則必須將自訂欄位&#x200B;**@myCustomField**&#x200B;新增至行銷和中部來源補充平台的nms:delivery架構：

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

對於傳送參數／變數，請使用下列語法（使用傳送物件）:

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] 在Javascript區段中  {#value-in-javascript}

若要允許在Javascript區段中使用&lt;%@值，請以&lt;%和%>取代兩個特殊物件：

```
<%@ value object='startScript' %>
<%@ value object='endScript' %>
```

例如：

```
<%@ value object='startScript' %> var iMode = <%@ value object="delivery" xpath="@deliveryMode" %> if(iMode == 1) { ... } else { ... }`
`<%@ value object='endScript' %> is expanded in something like <% var iMode = 1 if(iMode == 1) { ... } else { ... } %>.
```

## [!DNL foreach] {#foreach}

此指令允許在傳送中載入的物件陣列上進行小版本，以追蹤與物件相關的個別連結。

語法:

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

其中：

* **[!DNL object]**:要開始的對象的名稱，通常是額外的指令碼對象，但它可以是交付。
* **[!DNL xpath]** （可選）:xpath of the collection to loop on.預設值為&quot;。&quot;，表示物件是要循環播放的陣列。
* **[!DNL index]** （可選）:如果xpath不是&quot;&quot;對象是陣列本身，對象的項索引（從0開始）。
* **[!DNL item]** （可選）:可訪問的新對象的名稱  &lt;>預設為架構中的連結名稱。

範例:

在傳送屬性／個人化中，載入文章陣列以及收件者與文章之間的關係表。

只要使用Javascript即可顯示這些文章的連結，如下所示：

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

透過該解決方案，所有文章的連結都會不加區分地受到追蹤。 您可以知道收件者已點按文章連結，但您無法知道哪篇文章。

解決方案是：

1. 將所有可能的文章預先載入傳送的額外指令碼陣列- articleList[] —— 這表示可能的文章數目必須有限。
1. 在內容開頭編寫JavaScript函式。

   ```
   <%@ value object='startScript' %>
   function displayArticle(articleId)
   {
     <%@ foreach object="articleList" item="article" %>
       if( articleId == <% value object="article" xpath="@id" %> ) 
       {
         <%@ value object='endScript' %>
           <a href="http://nl.net?a.jsp?article=<%@ value object="article" xpath="@id" %>">article</a>
         <%@ value object='startScript' %>
       } 
     <%@ end @%>
   }
   <%@ value object='endScript' %>
   ```
1. 呼叫函式以顯示文章。

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```

