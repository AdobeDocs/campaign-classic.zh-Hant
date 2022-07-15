---
product: campaign
title: 關於 Campaign 整合
description: 使用其他 Adobe 解決方案，並將其不同的功能與 Campaign 結合。
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 開始使用Adobe Campaign整合 {#about-campaign-integrations}

![](../../assets/common.svg)

Adobe Experience Cloud是一套綜合性的同類最佳整合解決方案，構建在一個具有一套共同強大核心服務的通用資料平台上。

瞭解Adobe Campaign和 [Adobe Experience Cloud解決方案](https://experienceleague.adobe.com/docs/core-services/interface/marketing-cloud-integrations.html) 和 [核心服務](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html)。 然後，您就可以實現解決方案實施的現代化並實施Experience Cloud，這樣您就可以使用客戶屬性和受眾等功能。

![](assets/ExCloud-solutions.png)

可與Adobe Campaign整合的Adobe解決方案和核心服務的完整清單以及相關文檔，可在 [此部分](#experience-cloud-integrations)。

>[!CAUTION]
>
>這些整合大多需要實施AdobeIdentity Management系統(IMS)，通過Adobe ID登錄。 [在本頁中深入瞭解](../../integrations/using/about-adobe-id.md)。

## 連結解決方案 {#working-with-experience-cloud-solutions}

多個解決方案可以與Adobe Experience Cloud聯繫。 的 **組織** 是使管理員能夠配置組和用戶以及控制Adobe Experience Cloud的單點登錄(SSO)的客戶實體。 該組織就像一個登錄公司，涵蓋所有Experience Cloud產品和解決方案。 通常，組織就是您的公司名稱。但是，一個公司可以有許多組織。

Adobe Experience Cloud賬戶的組織管理和連結詳見 [Adobe Experience Cloud幫助門戶](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)。

## 身份和cookie管理 {#id-and-cookies}

安裝Adobe Campaign或與Adobe Experience Cloud整合現有安裝時， [Adobe Experience Cloud身份服務](https://experienceleague.adobe.com/docs/id-service/using/home.html) 的子菜單。 這項服務取代了Adobe Campaign首先用於跟蹤功能的永久cookie。

Adobe Experience Cloud身份服務（ID服務）提供通用、持久的ID，用於識別Experience Cloud中所有解決方案的訪問者。

將為生成跟蹤日誌的收件人分配唯一訪問者ID。 此ID將保存在 **[!UICONTROL Requester UUID (@sourceID)]** 的 **[!UICONTROL nms:trackingLogRcp]** 的子菜單。 **因此，在實施訪問者ID服務之前存在的收件人的跟蹤資料將不再可用**。

然後，ID將由具有相同CNAME的其他Adobe Experience Cloud解決方案識別。 [了解更多](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/cname.html)

## Experience Cloud 整合 {#experience-cloud-integrations}

下表提供了對可用Experience Cloud整合文檔的訪問。

<table> 
 <thead> 
  <tr> 
   <th> 解決方案和核心服務<br /> </th> 
   <th> 使用案例<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform</strong><br /> </td> 
   <td> Adobe Campaign與Adobe Real-time Customer Data Platform(RTCDP)的整合使您可以共用段資料並將受眾導入Adobe Campaign。<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">瞭解更多資訊</a> 關於競選 — Adobe Real-time Customer Data Platform整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AdobeIdentity Management系統公司 — Adobe ID</strong><br /> </td> 
   <td> 允許您與其他Adobe Campaign解決方案使用相同的Adobe ID連接到Adobe Experience Cloud。<br /> 必須使用Adobe ID登錄，以便使用與Adobe Experience Cloud整合、特別是核心服務相關的某些功能。<br /> <p><a href="../../integrations/using/about-adobe-id.md">瞭解更多資訊</a> 和Adobe Campaign一起實施Adobe ID。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> 允許您直接在中建立映射到Adobe Campaign資料庫的電子郵件內容或表單 <strong>Adobe Experience Manager</strong>。<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">瞭解更多資訊</a> Adobe Campaign-Adobe Experience Manager一體化。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> 允許您插入由 <strong>Adobe Target</strong> 開啟Adobe Campaign建立和發送的電子郵件時。<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">瞭解更多資訊</a> Adobe Campaign-Adobe Target一體化。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>人員核心服務</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> 允許您在您使用的Adobe Experience Cloud解決方案和核心解決方案之間共用受眾。<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">瞭解更多資訊</a> Adobe Campaign — 人員核心服務和Adobe Audience Manager整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>資產核心服務</strong><br /> </td> 
   <td> 可讓您將 Adobe Experience Cloud 資料庫中的資產插入到 Adobe Campaign 中建立的電子郵件和登錄頁中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">瞭解更多資訊</a> 關於Adobe Campaign — 資產核心服務整合</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> 允許您從 <strong>AEM Assets</strong> 在Adobe Campaign建立的電子郵件和登錄頁。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">瞭解更多資訊</a> Adobe Campaign-AEM Assets一體化。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> 整合於 <strong>觸發核心服務</strong> 而Adobe Campaign允許您向客戶發送個性化的電子郵件，作為對Adobe Analytics在您的網站上跟蹤的特定行為的反應。<br /> <p><a href="https://helpx.adobe.com/tw/campaign/kb/triggers-and-campaign.html">瞭解更多資訊</a> 關於Adobe Campaign—Experience Cloud觸發整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics 連接器</strong><br /> </td> 
   <td> <strong>Adobe Analytics連接器</strong> 允許Adobe Campaign和Adobe Analytics在電子郵件活動後通過用戶行為的部分進行交互。 相反地，它會將 Adobe Campaign 所傳送電子郵件行銷活動的指標和屬性傳送至 Adobe Analytics。<br /> <p><a href="../../platform/using/adobe-analytics-connector.md">瞭解更多資訊</a> 關於Campaign - Analytics Connectors整合。</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
