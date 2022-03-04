---
product: campaign
title: 網站應用程式追蹤選擇退出
description: 網站應用程式追蹤選擇退出
feature: Web Apps
exl-id: 4bff6b55-3335-433e-a2ff-5d8c83e8f0d3
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 2%

---

# 網站應用程式追蹤選擇退出{#web-application-tracking-opt-out}

![](../../assets/common.svg)

Adobe Campaign使您可以停止跟蹤通過cookie或Web信標選擇不進行行為跟蹤的最終用戶的Web行為。 該功能包括顯示橫幅以向最終用戶顯示該選項的功能；您可以將這些橫幅添加到Web應用程式或登錄頁中。

如果最終用戶通過cookie或Web信標選擇不進行行為跟蹤，則該資訊將通過JavaScript API發送到Adobe Campaign跟蹤伺服器。 請注意，某些管轄區可能要求客戶在提供選擇退出服務之前向選擇加入的最終用戶演示（或有其他法律要求），並且客戶有責任遵守適用的法律。

>[!NOTE]
>
>指令碼編寫時始終遵循中介紹的准則 [安全和隱私檢查表](https://helpx.adobe.com/campaign/kb/acc-security.html#dev)。

## 配置標題 {#configuring-the-banner-}

要在Web應用程式或登錄頁中顯示，需要配置標題。

Adobe Campaign的贈品標語樣樣本，您必須適應自己的需要。 此橫幅版本顯示為位於內容模型資料夾中的個性化塊。 請參見[此頁面](../../delivery/using/personalization-blocks.md)。

>[!IMPORTANT]
>
>要建立您自己的橫幅，您必須個性化現成的橫幅。

要激活橫幅廣告，必須配置Web應用程式屬性。 請參閱 [設計Web應用程式](designing-a-web-application.md) 的子菜單。

如果Web跟蹤被激活，則可以：

* 沒有橫幅。
* 在每頁上手動配置標題：選中此選項，然後在頁面屬性的每頁中選擇標題。

   ![](assets/pageproperties.png)

* 自動將標題添加到所有頁面：直接在Web應用程式屬性中選擇標題。

   ![](assets/optoutconfig.png)

>[!NOTE]
>
>v5 Web應用程式具有相同的行為，可使用相容模式。

預設橫幅具有以下結構：

```
<div onClick="NL.ClientWebTracking.closeOptOutBanner(this);" id="defaultOptOutBanner">
  <p>Please insert your message here
   <a onClick="NL.ClientWebTracking.allow();" class="optout-accept">Accept</a>
   <a onClick="NL.ClientWebTracking.forbid();" class="optout-decline">Refuse</a>
  </p>
</div>
      
```

必須替換 **請在此處插入您的郵件** 你的跟蹤資訊。 此替換應在與「退出」標題相關的新個性化塊中執行。

標語使用特定的CSS傳遞。 但是，在建立和配置網頁時可以覆蓋樣式。 請參見[此頁面](content-editor-interface.md)。

## 使用API設定opt-outcookie {#setting-the-opt-out-cookie-using-api}

Adobe Campaign提供的API允許您管理cookie值和檢索用戶首選項。

Cookie名稱為 **卡**。 通用值為：

* 0:用戶允許Web跟蹤（預設值）
* 1:用戶已禁止Web跟蹤
* 空：用戶尚未選擇，但允許Web跟蹤，因為它是預設值

可用的客戶端API用於自定義標語：

* **NL.ClientWebTracking.allow()**:設定opt-outcookie值以允許Web跟蹤。 預設情況下允許Web跟蹤。
* **NL.ClientWebTracking.briol()**:設定opt-outcookie值以禁止Web跟蹤。 Web跟蹤需要禁止用戶輸入。
* **NL.ClientWebTracking.closeOptOutBanner(bannerDomElt)**:在用戶按一下「接受」或「拒絕」按鈕後，關閉opt-out cookie標語。 （在按一下事件泡泡階段）

   bannerDomElt {DOMElement}需要刪除的cookie標語的根DOM元素

* **NL.ClientWebTracking.hasUserPrefs()**:如果用戶已選擇其Web跟蹤首選項，則返回true。
* **NL.ClientWebTracking.getUserPrefs()**:返回定義用戶首選項的opt-out Cookie值。

如果必須編寫JSSP，則伺服器端API可用：

* **NL.ServerWebTracking.generateOptOutBanner(escapeJs)**:生成要插入到JSSP頁的退出標題的標籤

   **escapeJs {Boolean}**:當需要轉義以在JavaScript中使用時為true。

   它返回需要在頁面中打印的opt-out標題的HTML。

* **NL.ServerWebTracking。_displayOptOutBanner()**

   如果管理員選擇退出標題後應顯示退出標題，則返回「true」

   當管理員已選擇使用Web跟蹤退出標題時，將調用此代碼。

   如果用戶尚未選擇跟蹤或未選擇跟蹤，則應顯示標題。

* **NL.ServerWebTracking.renderOptOutBanner(escapeJs)**

   通過將選擇退出標題插入JSSP頁來呈現該標注。 在Jssp中，它被調用為介於&lt;% %>之間

   **escapeJs {Boolean}**:當生成的標籤需要轉義以在JavaScript中使用時為true

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
