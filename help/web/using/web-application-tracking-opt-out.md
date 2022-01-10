---
product: campaign
title: 網站應用程式追蹤選擇退出
description: 網站應用程式追蹤選擇退出
audience: web
content-type: reference
topic-tags: web-applications
exl-id: 4bff6b55-3335-433e-a2ff-5d8c83e8f0d3
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 2%

---

# 網站應用程式追蹤選擇退出{#web-application-tracking-opt-out}

![](../../assets/common.svg)

Adobe Campaign可讓您停止追蹤透過cookie或網站信標選擇退出行為追蹤之使用者的網站行為。 此功能包括顯示橫幅以向使用者呈現該選項的功能；您可以將這些橫幅新增至網頁應用程式或登陸頁面。

若使用者透過Cookie或網站信標選擇退出行為追蹤，則該資訊會透過JavaScript API傳輸至Adobe Campaign追蹤伺服器。 請注意，某些管轄區可能會要求客戶在可提供選擇退出（或有其他法律要求）之前，向最終使用者呈現選擇加入，而客戶有責任遵守適用法律。

>[!NOTE]
>
>指令碼執行時一律遵循 [安全性與隱私權檢查清單](https://helpx.adobe.com/campaign/kb/acc-security.html#dev).

## 設定橫幅 {#configuring-the-banner-}

若要在Web應用程式或登陸頁面中顯示橫幅，必須進行設定。

Adobe Campaign會隨範例橫幅提供，您必須加以調整以符合自己的需求。 此橫幅版本會顯示為位於內容模型資料夾中的個人化區塊。 請參見[此頁面](../../delivery/using/personalization-blocks.md)。

>[!IMPORTANT]
>
>若要建立您自己的橫幅，您必須個人化現成可用的橫幅。

要激活橫幅，必須配置Web應用程式屬性。 請參閱 [設計Web應用程式](designing-a-web-application.md) 區段。

如果已啟用網頁追蹤，您可以：

* 沒有橫幅。
* 在每個頁面上手動設定橫幅：核取此選項，然後在頁面屬性的每個頁面中選取橫幅。

   ![](assets/pageproperties.png)

* 自動將橫幅新增至所有頁面：直接在Web應用程式屬性中選擇橫幅。

   ![](assets/optoutconfig.png)

>[!NOTE]
>
>v5 Web應用程式具有相同行為時，可使用相容模式。

預設橫幅的結構如下：

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

您必須取代 **請在此處插入您的郵件** 包含追蹤資訊的區塊。 此取代應在與選擇退出橫幅相關的新個人化區塊中執行。

橫幅會與特定CSS一起傳送。 不過，建立和設定網頁時，您可以覆寫樣式。 請參見[此頁面](content-editor-interface.md)。

## 使用API設定選擇退出Cookie {#setting-the-opt-out-cookie-using-api}

Adobe Campaign隨API提供，可讓您管理Cookie值並擷取使用者偏好設定。

Cookie名稱為 **acoptout**. 常見值為：

* 0:使用者已允許Web追蹤（預設值）
* 1:使用者已禁止網頁追蹤
* null:使用者尚未選擇，但允許使用網頁追蹤，因為它是預設值

自訂橫幅的可用用戶端API為：

* **NL.ClientWebTracking.allow()**:設定選擇退出Cookie值以允許網頁追蹤。 預設允許進行網頁追蹤。
* **NL.ClientWebTracking.bord()**:設定選擇退出Cookie值以禁止網頁追蹤。 網路追蹤需要禁止使用者輸入。
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**:在使用者按一下「接受」或「拒絕」按鈕後，關閉選擇退出Cookie橫幅。 （在點擊事件反升階段期間）

   bannerDomElt {DOMElement}需要移除之Cookie橫幅的根DOM元素

* **NL.ClientWebTracking.hasUserPrefs()**:如果使用者已選擇其偏好設定進行網頁追蹤，則傳回true。
* **NL.ClientWebTracking.getUserPrefs()**:傳回定義使用者偏好設定的選擇退出Cookie值。

如果您必須撰寫JSSP，則可使用伺服器端API:

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**:為要插入JSSP頁面的退出橫幅產生標籤

   **escapeJs {Boolean}**:true，而產生的標籤需要逸出以在JavaScript內使用。

   它會傳回需要在頁面中列印的退出橫幅標籤HTML。

* **NL.ServerWebTracking。_displayOptOutBanner()**

   如果管理員選取退出橫幅後應顯示退出橫幅，則傳回「true」

   當管理員已選擇使用網頁追蹤選擇退出橫幅時，就會呼叫此程式碼。

   如果使用者尚未選擇進行追蹤或未選擇，應顯示橫幅。

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

   在JSSP頁面中插入退出橫幅來轉譯該標籤。 在&lt;% %>之間的Jssp中，就是這樣呼叫的

   **escapeJs {Boolean}**:true，而此時產生的標籤需要逸出以用於JavaScript內

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
