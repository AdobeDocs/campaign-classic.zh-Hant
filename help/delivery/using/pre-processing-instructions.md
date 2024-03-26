---
product: campaign
title: 追蹤的URL的預處理指示
description: 深入瞭解用於編寫電子郵件URL指令碼以及仍進行追蹤的預處理指示
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Monitoring
role: User, Data Engineer, Developer
exl-id: 9d3f5c74-377a-4e24-81e5-bb605f69cf8a
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 1%

---

# 前置處理指示 {#pre-processing-instructions}

您可以在傳送內容中使用特定語法，新增指示並編寫追蹤電子郵件URL的指令碼。 &lt;%@指示不是JavaScript：此語法特定於Adobe Campaign。

附註僅適用於傳遞內容的內容。 這是編寫電子郵件URL的指令碼且仍對其進行追蹤的唯一方法（除了URL引數以外）。 在偵測要追蹤的連結之前，可將連結視為在傳遞分析期間套用的自動複製/貼上。

有三種型別的指示：

* **[!DNL include]**：主要用於分解選項、個人化區塊、外部檔案或頁面中的部分程式碼。 [了解更多](#include)
* **[!DNL value]**：為傳送的欄位、傳送變數以及載入傳送的自訂物件授予存取權。 [了解更多](#value)
* **[!DNL foreach]**：循環載入為自訂物件的陣列。 [了解更多](#foreach)

可直接從傳遞精靈中測試這些變數。 註解會套用於內容預覽，以及當您按一下追蹤按鈕以檢視URL清單時。

## [!DNL include] {#include}

最常使用的範例如下：

* 包含映象頁面連結：

  ```
  <%@ include view="MirrorPage" %>  
  ```

* 映象頁面URL：

  ```
  View as a <a href="<%@ include view='MirrorPageUrl' %>" _label="Mirror Page" _type="mirrorPage">web page.
  ```

* 現成可用的取消訂閱URL：

  ```
  <%@ include option='NmsServer_URL' %>/webApp/unsub?id=<%= escapeUrl(recipient.cryptedId)%>
  ```

* 其他範例：

  ```
  <%@ include file='http://www.google.com' %>
  <%@ include file='file:///X:/france/service/test.html' %>
  <%@ include option='NmsServer_URL' %>
  ```

  使用傳送精靈中的個人化按鈕來取得正確的語法。

## [!DNL value] {#value}

此指示可讓您存取所有收件者均恆定的傳遞引數。

語法：

```
<%@ value object="myObject" xpath="@myField" index="1" %>
```

其中：

* **[!DNL object]**：物件的名稱（例如：傳送、提供者等）。
物件可以是：
   * **[!DNL delivery]**：針對目前的傳送（請參閱以下子區段中的詳細資訊和限制）。
   * **[!DNL provider]**：適用於目前的傳送提供者/路由(nms：externalAccount)。
   * 額外的指令碼物件：如果物件是透過載入到內容中： **屬性** > **個人化** > **在執行內容中新增物件**.
   * foreach回圈的專案：請參閱 [Foreach](#foreach) 一節。
* **[!DNL xpath]**：欄位的xpath。
* **[!DNL index]** （選用）：若為 **[!DNL object]** 是一個陣列（用於額外的指令碼物件），陣列中的專案索引（從0開始）。

### [!DNL delivery] 物件 {#delivery-object}

針對電子郵件個人化，傳遞物件提供兩種存取方式：

* 使用JavaScript：

  ```
  <%= delivery.myField %>`.
  ```

  JavaScript物件傳送不支援自訂欄位。 它們可在預覽中運作，但無法在MTA中運作，因為MTA只能存取現成的傳遞結構描述。

* 使用預先處理：

  ```
  <%@ value object="delivery"
  ```


**注意**

如果您對透過中間來源傳送的傳遞使用以下指示，自訂欄位 **@myCustomField** 必須新增至行銷和中間來源平台上的nms：delivery綱要：

```
<%@ value object="delivery" xpath="@myCustomField" %>
```

對於傳送引數/變數，請使用下列語法（使用傳送物件）：

```
<%@ value object="delivery" xpath="variables/var[@name='myVar']/@stringValue" %>
```

### [!DNL value] 在Javascript區段中 {#value-in-javascript}

若要允許在Javascript區段中使用&lt;%@值，兩個特殊物件會取代為&lt;%和%>：

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

此指示允許載入傳遞中的物件陣列上的反複專案追蹤與物件相關的個別連結。

語法：

```
<%@ foreach object="myObject" xpath="myLink" index="3" item="myItem" %> <%@ end %>
```

其中：

* **[!DNL object]**：要開始的物件名稱，通常是額外的指令碼物件，但可以是傳送。
* **[!DNL xpath]** （選用）：要重複播放之集合的xpath。 預設值為「。」，表示物件是要重複播放的陣列。
* **[!DNL index]** （選用）：如果xpath不是「。」 而且物件本身是一個陣列，物件的專案索引（從0開始）。
* **[!DNL item]** （選用）：可在foreach回圈內使用&lt;%@值存取的新物件名稱。 在架構中具有連結名稱的預設值。

例如：

在傳遞屬性/個人化中，載入一系列文章以及收件者和文章之間的關係表。

顯示這些文章的連結可透過Javascript輕鬆完成，如下所示：

```
<%
  for(var i=0; i<recipient.rcpArticle.length; i++ )
  {
    %><a href="http://nl.net?a.jsp?article=<%=recipient.rcpArticle[i].article.@id%>">article</a><%
  }
%>
```

使用該解決方案，可毫無區別地追蹤所有文章的連結。 您可以知道收件者已按一下文章連結，但您無法知道是哪篇文章。

解決方案是：

1. 在額外的傳遞指令碼陣列中預先載入所有可能的文章 — articleList[]  — 表示可能的文章數量必須是有限的。
1. 在內容的開頭撰寫JavaScript函式。

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
