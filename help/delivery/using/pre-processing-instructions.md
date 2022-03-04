---
product: campaign
title: 跟蹤的URL的預處理指令
description: 瞭解有關用於編寫電子郵件URL指令碼的預處理說明的詳細資訊，並且仍要對其進行跟蹤
feature: Monitoring
exl-id: 9d3f5c74-377a-4e24-81e5-bb605f69cf8a
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# 預處理指令 {#pre-processing-instructions}

![](../../assets/common.svg)

您可以在傳遞內容中使用特定語法來添加說明並編寫跟蹤的電子郵件的URL指令碼。 &lt;%@說明不是JavaScript:此語法是特定於Adobe Campaign的。

它們只適用於傳遞內容的上下文。 它是編寫電子郵件URL指令碼並仍對其進行跟蹤（除URL參數外）的唯一方法。 在檢測要跟蹤的連結之前，這些連結可視為在傳遞分析期間應用的自動複製/貼上。

有三種說明類型：

* **[!DNL include]**:主要是將選項、個性化塊、外部檔案或頁面中的某些代碼分解。 [了解更多](#include)
* **[!DNL value]**:以授予對傳遞中載入的傳遞、傳遞變數和自定義對象的欄位的訪問權限。 [了解更多](#value)
* **[!DNL foreach]**:循環作為自定義對象載入的陣列。 [了解更多](#foreach)

可以直接從交付嚮導中測試它們。 它們應用於內容預覽，當您按一下跟蹤按鈕查看URL清單時。

## [!DNL include] {#include}

以下示例是最常用的示例：

* 包括鏡像頁連結：

   ```
   <%@ include view="MirrorPage" %>  
   ```

* 鏡像頁URL:

   ```
   View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
   ```

* 現成取消訂閱URL:

   ```
   <%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>
   ```

* 其他示例：

   ```
   <%@ include file='http://www.google.com' %>
   <%@ include file='file:///X:/france/service/test.html' %>
   <%@ include option='NmsServer_URL' %>
   ```

   使用傳遞嚮導中的個性化按鈕獲取正確的語法。

## [!DNL value] {#value}

本說明允許訪問所有收件人的傳遞參數不變。

語法:

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

位置：

* **[!DNL object]**:對象的名稱(示例：交付、提供商等)。
對象可以是：
   * **[!DNL delivery]**:當前交貨（請參閱下文子節中的詳細資訊和限制）。
   * **[!DNL provider]**:當前傳遞提供方/路由(nms:externalAccount)。
   * 額外的指令碼對象：如果對象通過以下方式載入到上下文： **屬性** > **個性化** > **在執行上下文中添加對象**。
   * 每個循環的項：見 [福阿赫](#foreach) 的下界。
* **[!DNL xpath]**:欄位的xpath。
* **[!DNL index]** （可選）:如果 **[!DNL object]** 是陣列（對於額外指令碼對象），陣列中的項索引（從0開始）。

### [!DNL delivery] 對象 {#delivery-object}

對於電子郵件個性化設定，可以通過兩種方式訪問傳遞對象：

* 使用JavaScript:

   ```
   <%= delivery.myField %>`.
   ```

   在JavaScript對象傳遞自定義欄位中不受支援。 它們在預覽版中工作，但在MTA中不工作，因為MTA只能訪問出廠預裝交付架構。

* 使用預處理：

   ```
   <%@ value object="delivery"
   ```


**警告**

如果您對通過中間來源補充發送的交貨使用以下說明，則自定義欄位 **@myCustomField** 必須在營銷平台和中間採購平台上添加到nms:delivery架構：

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

對於傳遞參數/變數，請使用以下語法（使用傳遞對象）:

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] 在Javascript節中 {#value-in-javascript}

要允許在Javascript節中使用&lt;%@值，請將兩個特殊對象替換為&lt;%和%>:

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

此指令允許在傳遞中載入的對象陣列上進行迭代，以跟蹤與對象相關的各個連結。

語法:

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

位置：

* **[!DNL object]**:要開始的對象的名稱，通常是額外的指令碼對象，但它可以是傳遞。
* **[!DNL xpath]** （可選）:要循環的集合的xpath。 預設值為&quot;。&quot;，表示對象是要循環的陣列。
* **[!DNL index]** （可選）:如果xpath不是「」。 對象是陣列本身，對象的項索引（從0開始）。
* **[!DNL item]** （可選）:foreach循環內&lt;%@值可訪問的新對象的名稱。 預設為架構中的連結名稱。

範例:

在遞送屬性/個性化中，載入物品陣列和接收者和物品之間的關係表。

只需使用Javascript即可顯示指向這些文章的連結，如下所示：

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

通過該解決方案，可以不加區分地跟蹤所有物品的連結。 您可以知道收件人已按一下了文章連結，但您無法知道在哪篇文章上。

解決方案是：

1. 將所有可能的文章預載入到遞送的額外指令碼陣列 — articleList[]  — 這意味著可能的條款數量必須有限。
1. 在內容的開頭編寫JavaScript函式。

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

1. 通過調用函式來顯示文章。

   ```
   <%
   for(var i=0; i<recipient.rcpArticle.length; i++ )
   {
    displayArticle(recipient.rcpArticle[i].article.@id)
   }
   %>
   ```
