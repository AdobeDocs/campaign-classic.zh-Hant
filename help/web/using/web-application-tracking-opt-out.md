---
title: 選擇退出的網路應用程式追蹤
seo-title: 選擇退出的網路應用程式追蹤
description: 選擇退出的網路應用程式追蹤
seo-description: null
page-status-flag: never-activated
uuid: c9b9eee2-a5be-4378-b2d7-53ed7121eae8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 8f413002-bd32-426f-88b9-44cefae68593
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 選擇退出的網路應用程式追蹤{#web-application-tracking-opt-out}

Adobe Campaign可讓您停止追蹤透過Cookie或網站信標選擇退出行為追蹤的使用者的網路行為。 該功能包括能夠顯示橫幅，向最終用戶顯示該選項；您可以將這些橫幅加入網頁應用程式或登陸頁面。

如果使用者透過Cookie或網站信標選擇退出行為追蹤，則該資訊會以JavaScript API傳送至Adobe Campaign追蹤伺服器。 請注意，有些司法轄區可能要求客戶在提供選擇退出之前向使用者出示選擇加入的資訊（或有其他法律要求），而客戶有責任遵守適用法律。

## 設定橫幅 {#configuring-the-banner-}

若要在Web應用程式或著陸頁面中顯示，必須設定橫幅。

Adobe Campaign會隨附範例橫幅，您必須依需求調整。 此橫幅版本會顯示為位於內容模型檔案夾中的個人化區塊。 請參見[此頁面](../../delivery/using/personalization-blocks.md)。

>[!CAUTION]
>
>若要建立您自己的橫幅，您必須個人化現成可用的橫幅。

若要啟用橫幅，您必須設定Web應用程式屬性。 請參閱「設 [計Web應用程式](../../web/using/designing-a-web-application.md) 」一節。

如果網頁追蹤已啟動，您可以：

* 沒有橫幅。
* 在每個頁面上手動設定橫幅：勾選此選項，並選取頁面屬性中每個頁面的橫幅。

   ![](assets/pageproperties.png)

* 自動將橫幅新增至所有頁面：直接在Web應用程式屬性中選取橫幅。

   ![](assets/optoutconfig.png)

>[!NOTE]
>
>v5 web應用程式具有相同行為時，可使用相容模式。

預設橫幅的結構如下：

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

您必須將「請 **在此處插入訊息** 」取代為包含追蹤資訊的區塊。 此項取代應在您與「退出」橫幅相關的新個人化區塊中執行。

橫幅會以特定的CSS傳送。 不過，您可以在建立和設定網頁時覆寫樣式。 請參見[此頁面](../../web/using/content-editor-interface.md)。

## 使用API設定選擇退出Cookie {#setting-the-opt-out-cookie-using-api}

Adobe Campaign會隨附API，可讓您管理Cookie值並擷取使用者偏好設定。

Cookie名稱為 **Acoptout**。 常見值有：

* 0:使用者已允許網頁追蹤（預設值）
* 1:使用者已禁止網頁追蹤
* null:使用者尚未選擇，但允許進行網頁追蹤，因為它是預設值

自訂橫幅的可用用戶端API包括：

* **NL.ClientWebTracking.allow()**:設定退出Cookie值以允許網頁追蹤。 預設允許網頁追蹤。
* **NL.ClientWebTracking.bord()**:設定選擇退出Cookie值以禁止網頁追蹤。 網頁追蹤需要禁止使用者輸入。
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**:在使用者按一下「接受」或「拒絕」按鈕後，關閉選擇退出Cookie橫幅。 （在點按事件反升階段）

   bannerDomElt {DOMElement}需要移除之Cookie橫幅的根DOM元素

* **NL.ClientWebTracking.hasUserPrefs()**:如果使用者已選擇他的網頁追蹤偏好設定，則傳回true。
* **NL.ClientWebTracking.getUserPrefs()**:傳回定義使用者偏好設定的退出Cookie值。

如果您必須編寫JSSP，則可使用伺服器端API:

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**:生成要插入JSSP頁的退出橫幅的標籤

   **escapeJs {Boolean}**:true，當產生的標籤需要逸出才能用於JavaScript中。

   它會傳回需要在頁面中列印的退出橫幅標籤的HTML。

* **NL.ServerWebTracking。_displayOptOutBanner()**

   如果管理員在選取退出橫幅後應顯示退出橫幅，則傳回true

   當管理員已選擇使用網頁追蹤退出橫幅時，就會呼叫此程式碼。

   如果使用者尚未選擇要追蹤或不要追蹤，應顯示橫幅。

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

   將退出橫幅插入JSSP頁面，以呈現該橫幅的標籤。 在Jssp中，它被調用為&lt;% %>之間的狀態

   **escapeJs {Boolean}**:true：當產生的標籤需要逸出以用於JavaScript中時

JSSP示例：

```
<%@ page import="/nl/core/shared/nl.js" %>
<!doctype html>
<%
NL.require('/nl/core/shared/webTracking.js');
NL.client.require('/nl/core/shared/webTracking.js');
%>
<html>
<head>
<%==NL.client.deps()%>
</head>

<body>

<!-- TEST USING SERVER API IN JSSP -->
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
webTracking.renderOptOutBanner();
%>

<!-- TEST USING SERVER API IN A SCRIPT -->
<!--
<% 
var webTracking = new NL.ServerWebTracking(request, 'optOutBanner');
%>
<script>var el = document.createElement('div'); el.innerHTML =  "<% webTracking.renderOptOutBanner(true); %>";document.body.appendChild(el);</script>
-->

<!-- TEST OF THE CLIENT API -->
<!--
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
-->
</body>
</html>
```

