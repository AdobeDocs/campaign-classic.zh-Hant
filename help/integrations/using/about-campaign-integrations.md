---
solution: Campaign Classic
product: campaign
title: 關於 Campaign 整合
description: 使用其他 Adobe 解決方案，並將其不同的功能與 Campaign 結合。
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 9%

---

# 開始使用Adobe Campaign整合{#about-campaign-integrations}

Adobe Experience Cloud是一組同級最佳的全方位整合式解決方案，建置於具有功能強大的通用核心服務集的通用資料平台上。

了解Adobe Campaign與[Adobe Experience Cloud解決方案](https://experienceleague.adobe.com/docs/core-services/interface/marketing-cloud-integrations.html)和[核心服務](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html)之間可用的功能整合。 接著，您可以導入最新的解決方案實作並實作Experience Cloud，以便使用客戶屬性和受眾等功能。

![](assets/ExCloud-solutions.png)

可與Adobe Campaign整合的Adobe解決方案和核心服務以及相關檔案的完整清單，可在[本節](#experience-cloud-integrations)中取得。

>[!CAUTION]
>
>大部分的整合需要實作AdobeIdentity Management系統(IMS)，才能透過Adobe ID登入。 [了解更多資訊](../../integrations/using/about-adobe-id.md)。


## 連結您的解決方案{#working-with-experience-cloud-solutions}

多個解決方案可連結至Adobe Experience Cloud。 **organization**&#x200B;是客戶實體，可讓管理員設定群組和使用者，以及控制Adobe Experience Cloud中的單一登入(SSO)。 組織的作用就像登入公司，涵蓋所有Experience Cloud產品和解決方案。 通常，組織就是您的公司名稱。但是，一個公司可以有許多組織。

[Adobe Experience Cloud說明入口網站](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)中會詳細說明組織管理和連結Adobe Experience Cloud帳戶。

## 身分和Cookie管理{#id-and-cookies}

安裝Adobe Campaign或將現有安裝與Adobe Experience Cloud整合時，會啟用[Adobe Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html)。 此服務會取代Adobe Campaign在追蹤功能中首先使用的永久Cookie。

Adobe Experience Cloud Identity Service（ID服務）提供永續性的通用ID，可識別Experience Cloud中所有解決方案的訪客。

系統會為產生追蹤記錄的收件者指派唯一訪客ID。 此ID將保存在&#x200B;**[!UICONTROL nms:trackingLogRcp]**&#x200B;表的&#x200B;**[!UICONTROL Requester UUID (@sourceID)]**&#x200B;欄位中。 **因此，在訪客ID服務實作前已存在的收件者追蹤資料將無法使用**。

接著，具有相同CNAME的其他Adobe Experience Cloud解決方案便會識別ID。 [了解更多](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/cname.html)

## Experience Cloud 整合 {#experience-cloud-integrations}

下表提供對可用Experience Cloud整合檔案的存取。

<table> 
 <thead> 
  <tr> 
   <th> 解決方案與核心服務<br /> </th> 
   <th> 使用案例<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>AdobeReal-time Customer Data Platform(RTCDP)</strong><br /> </td> 
   <td> Adobe Campaign與Adobe即時客戶資料平台(RTCDP)的整合可讓您共用區段資料，並將對象匯入Adobe Campaign。<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">進一</a> 步了解Campaign -Adobe即時客戶資料平台整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AdobeIdentity Management系統(IMS)- Adobe ID</strong><br /> </td> 
   <td> 可讓您連線至Adobe Campaign，其Adobe ID與其他Adobe Experience Cloud解決方案相同。<br /> 必須使用Adobe ID登入，才能使用連結至Adobe Experience Cloud整合的特定功能，尤其是核心服務。<br /> <p><a href="../../integrations/using/about-adobe-id.md">進</a> 一步了解如何使用Adobe Campaign實作Adobe ID。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> 可讓您直接在<strong>Adobe Experience Manager</strong>中建立對應至Adobe Campaign資料庫的電子郵件內容或表單。<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">進一</a> 步了解Adobe Campaign - Adobe Experience Manager整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> 可讓您在開啟由Adobe Campaign建立和傳送的電子郵件時插入由<strong>Adobe Target</strong>動態計算的影像。<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">進一</a> 步了解Adobe Campaign - Adobe Target整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People核心服</strong><br /> <strong>務AdobeAudience Manager</strong><br /> </td> 
   <td> 可讓您在使用的Adobe Experience Cloud解決方案與核心之間共用閱聽眾。<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">進一</a> 步了解Adobe Campaign — 人員核心服務和Adobe Audience Manager整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>資產核心服務</strong><br /> </td> 
   <td> 可讓您將 Adobe Experience Cloud 資料庫中的資產插入到 Adobe Campaign 中建立的電子郵件和登錄頁中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">進一</a> 步了解Adobe Campaign - Assets核心服務整合</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> 可讓您將<strong>AEM Assets</strong>資料庫中的資產插入在Adobe Campaign中建立的電子郵件和登錄頁面中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">進一</a> 步了解Adobe Campaign - AEM Assets整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> <strong>觸發器核心服務</strong>與Adobe Campaign的整合可讓您傳送個人化電子郵件給客戶，以回應Adobe Analytics在您網站上追蹤的特定行為。<br /> <p><a href="https://helpx.adobe.com/tw/campaign/kb/triggers-and-campaign.html">深入</a> 了解Adobe Campaign -Experience Cloud觸發器整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Data Connectors</strong><br /> </td> 
   <td> <strong>Data Connectors</strong> (先前稱為Adobe Genesis)可讓Adobe Campaign和Adobe Analytics透過關於電子郵件行銷活動後使用者行為的區段進行互動。相反地，它會將Adobe Campaign傳送之電子郵件促銷活動的指標和屬性傳送至Adobe Analytics - Data connector。<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">進一</a> 步了解Campaign - Data Connectors整合。</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
