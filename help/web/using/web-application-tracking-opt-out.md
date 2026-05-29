---
product: campaign
title: 網站應用程式追蹤選擇退出
description: 網站應用程式追蹤選擇退出
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Web Apps
exl-id: 4bff6b55-3335-433e-a2ff-5d8c83e8f0d3
TQID: https://experienceleague.adobe.com/-5Bp8qdxH8DTEJ0-NASuorQrjwDMUmvuhBNbW1alqyc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
subfeature_v2:
  - id: f391046b-0cf3-4e76-bd3b-97fe06654506
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
  - id: d7be2b01-dc9c-40f7-aace-a151707504ed
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 719
ht-degree: 2%

---

# 網站應用程式追蹤選擇退出{#web-application-tracking-opt-out}



Adobe Campaign可讓您停止追蹤選擇退出透過Cookie或網路信標進行行為追蹤之一般使用者的網路行為。 此功能包括顯示橫幅以向使用者呈現該選項的功能；您可以將這些橫幅新增到網頁應用程式或登入頁面中。

如果終端使用者選擇退出透過Cookie或網路信標的行為追蹤，該資訊會透過JavaScript API傳輸至Adobe Campaign追蹤伺服器。 請注意，某些管轄區可能要求客戶在提供選擇退出之前，提供使用者選擇加入（或具有其他法律要求），且客戶有責任遵守適用法律。

>[!NOTE]
>
>當指令碼一律遵循[安全性與隱私權檢查清單](https://helpx.adobe.com/campaign/kb/acc-security.html#dev)中說明的准則時。

## 設定橫幅 {#configuring-the-banner-}

橫幅必須設定才能顯示在網頁應用程式或登入頁面中。

Adobe Campaign隨附範例橫幅，您必須根據自己的需求進行調整。 此橫幅版本會在內容模型資料夾中顯示為個人化區塊。 請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalization-blocks.html){target="_blank"}。

>[!IMPORTANT]
>
>若要建立自己的橫幅，您必須個人化現成的橫幅。

若要啟用橫幅，您必須設定Web應用程式屬性。 請參閱[設計Web應用程式](designing-a-web-application.md)區段。

如果網路追蹤已啟用，您可以：

* 沒有橫幅。
* 在每個頁面上手動設定橫幅：核取此選項，並在頁面屬性中選取每個頁面中的橫幅。

  ![](assets/pageproperties.png)

* 自動將橫幅新增至所有頁面：直接在網頁應用程式屬性中選取橫幅。

  ![](assets/optoutconfig.png)

>[!NOTE]
>
>相容性模式適用於具有相同行為的v5 Web應用程式。

預設橫幅的結構如下：

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

您必須將&#x200B;**請在此插入您的訊息**，並以包含追蹤資訊的區塊取代。 此取代應在與選擇退出橫幅相關的新個人化區塊中執行。

橫幅會以特定CSS傳遞。 不過，您可在建立和設定網頁時覆寫樣式。 請參見[此頁面](content-editor-interface.md)。

## 使用API設定選擇退出Cookie {#setting-the-opt-out-cookie-using-api}

Adobe Campaign隨附的API可讓您管理Cookie值並擷取使用者偏好設定。

Cookie名稱為&#x200B;**apottout**。 常見的值包括：

* 0：使用者已允許網頁追蹤（預設值）
* 1：使用者已禁止網路追蹤
* null：使用者尚未選擇，但允許網路追蹤，因為這是預設值

自訂橫幅的可用使用者端API為：

* **NL.ClientWebTracking.allow()**：設定選擇退出Cookie值以允許網頁追蹤。 預設允許網頁追蹤。
* **NL.ClientWebTracking.forbid()**：設定選擇退出Cookie值以禁止Web追蹤。 網路追蹤需要禁止使用者輸入。
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**：在使用者按一下[接受]或[拒絕]按鈕後，關閉選擇退出Cookie橫幅。 （在點按事件反升階段期間）

  bannerDomElt {DOMElement}需要移除之Cookie橫幅的根DOM元素

* **NL.ClientWebTracking.hasUserPrefs()**：如果使用者已選擇其網頁追蹤的偏好設定，則傳回true。
* **NL.ClientWebTracking.getUserPrefs()**：傳回定義使用者偏好設定的選擇退出Cookie值。

如果您必須撰寫JSSP，則可使用伺服器端API：

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**：產生選擇退出橫幅的標籤，以插入JSSP頁面

  **escapeJs{Boolean}**：當產生的標籤需要逸出才能在JavaScript中使用時，會傳回true。

  它會傳回需要在頁面中列印的選擇退出橫幅標籤的HTML。

* **NL.ServerWebTracking._displayOptOutBanner()**

  如果選擇退出橫幅在管理員選取選擇退出橫幅後應該顯示，則傳回「true」

  當管理員已選擇使用網頁追蹤選擇退出橫幅時，就會呼叫此程式碼。

  如果使用者尚未選擇是否追蹤，則應顯示橫幅。

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

  將選擇退出橫幅插入至JSSP頁面，以轉譯該橫幅的標籤。 其呼叫方式與Jssp中的呼叫方式相同，介於&lt;% %>之間

  **escapeJs{Boolean}**：當產生的標籤需要逸出才能在JavaScript中使用時，會傳回true

JSSP範例：

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
