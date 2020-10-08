---
title: 關於 Campaign 整合
description: 使用其他Adobe解決方案，並將其不同的功能與Campaign結合。
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 10%

---


# 關於 Campaign 整合 {#about-campaign-integrations}

Adobe Experience Cloud是一套全方位的同級最佳整合解決方案，以通用資料平台為基礎，並提供一組功能強大的核心服務。

瞭解Adobe Campaign與 [Adobe Experience Cloud解決方案與核心服務之間的功](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) 能整合 [](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)。 然後，您就可以最新化解決方案實作並實作Experience Cloud，以便使用客戶屬性和受眾等功能。

本節提供可與Adobe Campaign整合的Adobe解決方案和核心服務以及相關檔案的完整 [清單](#experience-cloud-integrations)。

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>這些整合大部分都需要透過Adobe ID(IMS)登入。 For more on this implementation, refer to [this page](../../integrations/using/about-adobe-id.md).
>
>請注意，IMS實作是一個複雜的程式，可能會很長。 嚴格保留給Adobe技術管理員。

## 連結您的解決方案 {#working-with-experience-cloud-solutions}

根據您的環境，數種解決方案可以連結至Adobe Experience Cloud。 它們以「組織」的形式連結。 An **organization** is the entity that enables an administrator to configure groups and users, and to control single sign-on in the Experience Cloud. 組織的運作方式類似登入公司，其涵蓋所有 Experience Cloud 產品和解決方案。通常，組織就是您的公司名稱。但是，一個公司可以有許多組織。

Adobe Experience Cloud說明入口網站會詳細說明組織管 [理和連結Adobe Experience Cloud帳戶](https://docs.adobe.com/content/help/zh-Hant/core-services/interface/manage-users-and-products/organizations.html)。

>[!CAUTION]
>
>新安裝Adobe Campaign或將現有安裝與Adobe Experience Cloud整合時， [Experience Cloud ID服務即會啟用](https://docs.adobe.com/content/help/en/id-service/using/home.html) 。 此服務會取代Adobe Campaign首先用於追蹤功能的永久Cookie。
>
>接著，系統會將唯一訪客ID指派給產生追蹤記錄的收件者。 此ID將保存在表 **[!UICONTROL Requester UUID (@sourceID)]** 的字 **[!UICONTROL nms:trackingLogRcp]** 段中。 因此，在訪客ID服務實作前已存在的收件者追蹤資料將不再可用。
>
>然後，具有相同CNAME的其他Adobe Experience Cloud解決方案將會識別該 [ID](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html)。

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
   <td> <strong>Adobe即時客戶資料平台</strong><br /> </td> 
   <td> Adobe Campaign與Adobe即時客戶資料平台的整合可讓您共用區段資料，並將觀眾匯入Adobe Campaign。<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">進一步瞭解</a> Campaign - Adobe即時客戶資料平台整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
   <td> 可讓您使用與其他Adobe Experience Cloud解決方案相同的Adobe ID連線至Adobe Campaign。<br /> 必須使用Adobe ID才能登入，才能使用與Adobe Experience Cloud整合相關的特定功能，尤其是核心服務。<br /> <p><a href="../../integrations/using/about-adobe-id.md">進一步瞭解</a> 「使用Adobe Campaign實作Adobe ID」。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Allows you to create email contents or forms mapped to the Adobe Campaign database directly in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">進一步瞭解</a> Adobe Campaign - Adobe Experience Manager整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Allows you to insert images that are dynamically computed by <strong>Adobe Target</strong> when the email created and sent by Adobe Campaign is opened.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">進一步瞭解</a> Adobe Campaign - Adobe Target整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>人員核心服務</strong><br /><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> 可讓您在Adobe Experience Cloud解決方案和您使用的核心之間共用受眾。<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">進一步瞭解</a> Adobe Campaign - People核心服務與Adobe Audience Manager整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>資產核心服務</strong><br /> </td> 
   <td> 可讓您將 Adobe Experience Cloud 資料庫中的資產插入到 Adobe Campaign 中建立的電子郵件和登錄頁中。<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">進一步瞭解</a> Adobe Campaign —— 資產核心服務整合</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Allows you to insert assets from your <strong>AEM Assets</strong> library into emails and landing pages created in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">進一步瞭解</a> Adobe Campaign - AEM Assets整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> Integration between <strong>Triggers core service</strong> and Adobe Campaign allows you to send personalized emails to your customers as a reaction to specific behaviors that are tracked on your website by Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/tw/campaign/kb/triggers-and-campaign.html">進一步瞭解</a> Adobe Campaign - Experience Cloud觸發器整合。</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics —— 資料連接器</strong><br /> </td> 
   <td> <strong>資料連接器</strong> （先前稱為Adobe Genesis）可讓Adobe Campaign和Adobe Analytics透過與電子郵件促銷活動後使用者行為相關的區段進行互動。 相反地，它會將Adobe Campaign傳送的電子郵件促銷活動指標和屬性傳送至Adobe Analytics —— 資料連接器。<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">進一步瞭解</a> 「促銷活動——資料連接器」整合。</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

