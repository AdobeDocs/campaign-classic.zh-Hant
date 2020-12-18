---
solution: Campaign Classic
product: campaign
title: 關於 Campaign 整合
description: 使用其他 Adobe 解決方案，並將其不同的功能與 Campaign 結合。
audience: integrations
content-type: reference
topic-tags: campaign-integrations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 9%

---


# 開始使用Adobe Campaign整合{#about-campaign-integrations}

Adobe Experience Cloud是一套全方位的同級最佳整合解決方案，以通用資料平台為基礎，並提供一組功能強大的核心服務。

瞭解Adobe Campaign與[Adobe Experience Cloud解決方案](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html)和[核心服務](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)之間的功能整合。 然後，您就可以最新化解決方案實作並實作Experience Cloud，以便使用客戶屬性和受眾等功能。

![](assets/ExCloud-solutions.png)

您可在[本節](#experience-cloud-integrations)中取得可與Adobe Campaign整合的Adobe解決方案和核心服務以及相關檔案的完整清單。

>[!CAUTION]
>
>這些整合大部分都需要實作Adobe Identity Management System(IMS)，才能透過Adobe ID登入。 [在本頁中進一步瞭解](../../integrations/using/about-adobe-id.md)。


## 連結您的解決方案{#working-with-experience-cloud-solutions}

多個解決方案可以連結至Adobe Experience Cloud。 **organization**&#x200B;是客戶實體，可讓管理員在Adobe Experience Cloud中設定群組和使用者，以及控制單一登入(SSO)。 該組織的運作方式類似登入公司，涵蓋所有Experience Cloud產品和解決方案。 通常，組織就是您的公司名稱。但是，一個公司可以有許多組織。

組織管理和連結Adobe Experience Cloud帳戶的詳細資訊請見[Adobe Experience Cloud說明入口網站](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html)。

## 身分與Cookie管理{#id-and-cookies}

當安裝Adobe Campaign或將現有安裝與Adobe Experience Cloud整合時，[Adobe Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/id-service/using/home.html)已啟用。 此服務會取代Adobe Campaign首先用於追蹤功能的永久Cookie。

Adobe Experience Cloud Identity Service（ID服務）提供通用、永久的ID，可識別Experience Cloud所有解決方案中的訪客。

系統會為產生追蹤記錄的收件者指派唯一訪客ID。 此ID將保存在&#x200B;**[!UICONTROL nms:trackingLogRcp]**&#x200B;表的&#x200B;**[!UICONTROL Requester UUID (@sourceID)]**&#x200B;欄位中。 **因此，在訪客ID服務實作前已存在的收件者追蹤資料將不再可用**。

然後，具有相同[CNAME](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html)的其他Adobe Experience Cloud解決方案將會識別該ID。

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
   <td> <strong>Adobe即時客戶資料平台(RTCDP)</strong><br /> </td> 
   <td> Adobe Campaign與Adobe即時客戶資料平台(RTCDP)的整合可讓您共用區段資料，並將觀眾匯入Adobe Campaign。<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">進一</a> 步瞭解Campaign - Adobe即時客戶資料平台整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System(IMS)- Adobe ID</strong><br /> </td> 
   <td> 可讓您使用與其他Adobe Experience Cloud解決方案相同的Adobe ID連線至Adobe Campaign。<br /> 必須使用Adobe ID才能登入，才能使用與Adobe Experience Cloud整合相關的特定功能，尤其是核心服務。<br /> <p><a href="../../integrations/using/about-adobe-id.md">進一</a> 步瞭解如何使用Adobe Campaign實作Adobe ID。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> 可讓您直接在<strong>Adobe Experience Manager</strong>中建立對應至Adobe Campaign資料庫的電子郵件內容或表單。<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">進一</a> 步瞭解Adobe Campaign - Adobe Experience Manager整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> 可讓您插入在開啟由Adobe Campaign建立和傳送的電子郵件時，由<strong>Adobe Target</strong>動態計算的影像。<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">進一</a> 步瞭解Adobe Campaign - Adobe Target整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>人員核心</strong><br /> <strong>服務Adobe Audience Manager</strong><br /> </td> 
   <td> 可讓您在Adobe Experience Cloud解決方案和您使用的核心之間共用受眾。<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">進一</a> 步瞭解Adobe Campaign —— 人員核心服務與Adobe Audience Manager整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>資產核心服務</strong><br /> </td> 
   <td> 可讓您將 Adobe Experience Cloud 資料庫中的資產插入到 Adobe Campaign 中建立的電子郵件和登錄頁中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">進一</a> 步瞭解Adobe Campaign —— 資產核心服務整合</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> 可讓您將<strong>AEM Assets</strong>資料庫中的資產插入在Adobe Campaign中建立的電子郵件和登陸頁面。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">進一</a> 步瞭解Adobe Campaign - AEM Assets整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> <strong>Triggers core service</strong>與Adobe Campaign的整合可讓您傳送個人化電子郵件給客戶，以回應Adobe Analytics在您網站上追蹤的特定行為。<br /> <p><a href="https://helpx.adobe.com/tw/campaign/kb/triggers-and-campaign.html">進一</a> 步瞭解Adobe Campaign - Experience Cloud觸發器整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics —— 資料連接器</strong><br /> </td> 
   <td> <strong>資料連接器</strong> （先前稱為Adobe Genesis）可讓Adobe Campaign和Adobe Analytics透過與電子郵件促銷活動後使用者行為相關的區段進行互動。相反地，它會將Adobe Campaign所傳送之電子郵件促銷活動的指標和屬性傳送至Adobe Analytics —— 資料連接器。<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">進一步</a> 瞭解促銷活動——資料連接器整合。</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

