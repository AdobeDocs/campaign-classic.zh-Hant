---
product: campaign
title: 關於 Campaign 整合
description: 使用其他 Adobe 解決方案，並將其不同的功能與 Campaign 結合
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 12%

---

# 開始使用Adobe Campaign整合 {#about-campaign-integrations}



Adobe Experience Cloud是一組同級最佳的全方位整合式解決方案，建置於具有功能強大的通用核心服務集的通用資料平台上。

了解Adobe Campaign與 [Adobe Experience Cloud解決方案](https://experienceleague.adobe.com/docs/core-services/interface/marketing-cloud-integrations.html) 和 [核心服務](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html). 接著，您可以導入最新的解決方案實作並實作Experience Cloud，以便使用客戶屬性和受眾等功能。

![](assets/ExCloud-solutions.png)

可與Adobe Campaign整合的Adobe解決方案和核心服務完整清單，以及相關檔案，請參閱 [本節](#experience-cloud-integrations).

>[!CAUTION]
>
>大部分的整合需要實作AdobeIdentity Management系統(IMS)，才能透過Adobe ID登入。 [在本頁中深入瞭解](../../integrations/using/about-adobe-id.md)。

## 連結您的解決方案 {#working-with-experience-cloud-solutions}

多個解決方案可連結至Adobe Experience Cloud。 此 **組織** 是客戶實體，可讓管理員設定群組和使用者，以及控制Adobe Experience Cloud中的單一登入(SSO)。 組織的作用就像登入公司，涵蓋所有Experience Cloud產品和解決方案。 通常，組織就是您的公司名稱。但是，一個公司可以有許多組織。

組織管理和連結Adobe Experience Cloud帳戶在 [Adobe Experience Cloud說明入口網站](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html).

## 身分與Cookie管理 {#id-and-cookies}

安裝Adobe Campaign或將現有安裝與Adobe Experience Cloud整合時， [Adobe Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html) 啟用。 此服務會取代Adobe Campaign在追蹤功能中首先使用的永久Cookie。

Adobe Experience Cloud Identity Service（ID服務）提供永續性的通用ID，可識別Experience Cloud中所有解決方案的訪客。

系統會為產生追蹤記錄的收件者指派唯一訪客ID。 此ID會儲存在 **[!UICONTROL Requester UUID (@sourceID)]** 欄位 **[!UICONTROL nms:trackingLogRcp]** 表格。 **因此，在訪客ID服務實作前已存在的收件者追蹤資料將無法使用**.

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
   <td> <strong>Adobe Real-time Customer Data Platform(RTCDP)</strong><br /> </td> 
   <td> Adobe Campaign與Adobe Real-time Customer Data Platform(RTCDP)的整合可讓您共用區段資料，並將對象匯入Adobe Campaign。<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">深入了解</a> 關於Campaign - Adobe Real-time Customer Data Platform整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AdobeIdentity Management系統(IMS)- Adobe ID</strong><br /> </td> 
   <td> 可讓您連線至Adobe Campaign，其Adobe ID與其他Adobe Experience Cloud解決方案相同。<br /> 必須使用Adobe ID登入，才能使用連結至Adobe Experience Cloud整合的特定功能，尤其是核心服務。<br /> <p><a href="../../integrations/using/about-adobe-id.md">深入了解</a> 關於使用Adobe Campaign實作Adobe ID。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> 可讓您直接在中建立對應至Adobe Campaign資料庫的電子郵件內容或表單 <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">深入了解</a> 關於Adobe Campaign - Adobe Experience Manager整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> 可讓您插入以 <strong>Adobe Target</strong> 開啟Adobe Campaign建立和傳送的電子郵件時。<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">深入了解</a> 關於Adobe Campaign - Adobe Target整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>人員核心服務</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> 可讓您在使用的Adobe Experience Cloud解決方案和核心之間共用受眾。<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">深入了解</a> 關於Adobe Campaign — 人員核心服務與Adobe Audience Manager整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>資產核心服務</strong><br /> </td> 
   <td> 可讓您將 Adobe Experience Cloud 資料庫中的資產插入到 Adobe Campaign 中建立的電子郵件和登錄頁中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">深入了解</a> 關於Adobe Campaign - Assets核心服務整合</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> 可讓您從 <strong>AEM Assets</strong> 程式庫放入Adobe Campaign中建立的電子郵件和登錄頁面。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">深入了解</a> 關於Adobe Campaign - AEM Assets整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> 整合 <strong>觸發核心服務</strong> 而Adobe Campaign可讓您傳送個人化電子郵件給客戶，以回應Adobe Analytics在您網站上追蹤的特定行為。<br /> <p><a href="https://helpx.adobe.com/tw/campaign/kb/triggers-and-campaign.html">深入了解</a> 關於Adobe Campaign -Experience Cloud觸發器整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics 連接器</strong><br /> </td> 
   <td> <strong>Adobe Analytics Connector</strong> 可讓Adobe Campaign和Adobe Analytics透過關於電子郵件促銷活動後使用者行為的區段互動。 相反地，它會將 Adobe Campaign 所傳送電子郵件行銷活動的指標和屬性傳送至 Adobe Analytics。<br /> <p><a href="../../platform/using/adobe-analytics-connector.md">深入了解</a> 關於Campaign - Analytics連接器整合。</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
