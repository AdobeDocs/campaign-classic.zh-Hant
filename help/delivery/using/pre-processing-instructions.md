---
product: campaign
title: 追蹤URL的預先處理指示
description: 進一步了解預先處理指示，以用於指令碼化電子郵件的URL，但仍可加以追蹤。
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: 9d3f5c74-377a-4e24-81e5-bb605f69cf8a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# 預處理指令 {#pre-processing-instructions}

![](../../assets/common.svg)

您可以在傳送內容中使用特定語法，以新增指示並編寫追蹤電子郵件的URL指令碼。 &lt;%@指示不是JavaScript:此語法是Adobe Campaign專屬的。

它們只適用於傳送內容的內容。 這是指令碼編寫電子郵件URL且仍會加以追蹤（除了URL參數以外）的唯一方法。 在偵測要追蹤的連結之前，它們可視為在傳送分析期間套用的自動複製/貼上。

指示有三種類型：

* **[!DNL include]**:主要用於將選項、個人化區塊、外部檔案或頁面中的某些程式碼分成因素。[深入瞭解](#include)
* **[!DNL value]**:提供傳送、傳送變數和傳送中載入之自訂物件的欄位存取權。[深入瞭解](#value)
* **[!DNL foreach]**:以循環載入為自訂物件的陣列。[深入瞭解](#foreach)

可直接從傳遞精靈測試。 它們會套用在內容預覽中，當您按一下追蹤按鈕以查看URL清單時。

## [!DNL include] {#include}

下列範例是最常使用的範例之一：

* 包括鏡像頁面連結：

   ```
   <%@ include view="MirrorPage" %>  
   ```

* 鏡像頁面URL:

   ```
   View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
   ```

* 現成可用的取消訂閱url:

   ```
   <%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>
   ```

* 其他範例：

   ```
   <%@ include file='http://www.google.com' %>
   <%@ include file='file:///X:/france/service/test.html' %>
   <%@ include option='NmsServer_URL' %>
   ```

   使用傳遞精靈中的個人化按鈕來取得正確語法。

## [!DNL value] {#value}

此指示可讓所有收件者存取固定的傳送參數。

語法:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

其中：

* **[!DNL object]**:物件名稱(範例：傳送、提供者等)。物件可以是：
   * **[!DNL delivery]**:（請參閱下文小節中的詳細資訊和限制）。
   * **[!DNL provider]**:(nms:externalAccount)。
   * 額外的指令碼物件：如果物件是透過以下項目載入內容：**屬性** > **個人化** > **在執行上下文中添加對象**。
   * 前循環項：請參閱下方的[前行](#foreach)一節。
* **[!DNL xpath]**:欄位的xpath。
* **[!DNL index]** （可選）:如 **[!DNL object]** 果是陣列（用於其他指令碼對象），則陣列中的項目索引（從0開始）。

### [!DNL delivery] 物件 {#delivery-object}

對於電子郵件個人化，可透過兩種方式存取傳送物件：

* 使用JavaScript:

   ```
   <%= delivery.myField %>`.
   ```

   在JavaScript物件傳送自訂欄位中不受支援。 它們可在預覽中運作，但在MTA中則無法運作，因為MTA只能存取現成可用的傳送結構。

* 使用預先處理：

   ```
   <%@ value object="delivery"
   ```


**注意**

如果您對透過中間來源傳送的傳送使用下列指示，則必須將自訂欄位&#x200B;**@myCustomField**&#x200B;新增至行銷和中間來源平台的nms:delivery結構中：

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

若是傳送參數/變數，請使用下列語法（使用傳送物件）:

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] 在Javascript區段中 {#value-in-javascript}

若要允許在Javascript區段中使用&lt;%@值，兩個特殊物件會取代為&lt;%和%>:

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

此指示允許在傳送中載入的物件陣列上進行迭代，以追蹤與物件相關的個別連結。

語法:

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

其中：

* **[!DNL object]**:要開始的物件名稱，通常是額外的指令碼物件，但可以是傳送。
* **[!DNL xpath]** （可選）:要循環的集合的xpath。預設值為「。」，表示物件是要循環的陣列。
* **[!DNL index]** （可選）:如果xpath不是&quot;&quot;而對象是陣列本身，是對象的項索引（從0開始）。
* **[!DNL item]** （可選）:新對象的名稱，可訪問  &lt;>預設為架構中的連結名稱。

範例:

在傳送屬性/個人化中，載入一系列文章以及收件者與文章之間的關係表格。

只要使用Javascript即可顯示這些文章的連結，如下所示：

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

透過該解決方案，所有文章的連結都可不受區分地受到追蹤。 您可以知道收件者已點按文章連結，但您無法知道要點擊哪篇文章。

解決方案是：

1. 將所有可能的文章預先載入至傳送的額外指令碼陣列 — articleList[] — 這表示可能的文章數量必須有限。
1. 在內容開頭撰寫JavaScript函式。

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
