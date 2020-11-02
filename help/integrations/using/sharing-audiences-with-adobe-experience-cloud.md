---
title: 使用Adobe Experience Cloud分享受眾
seo-title: 使用Adobe Experience Cloud分享受眾
description: 使用Adobe Experience Cloud分享受眾
seo-description: null
page-status-flag: never-activated
uuid: 24ac3463-69ab-48b4-85e0-4fe1948bf5ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 8f295058-5a78-4512-9bdf-d5f022457e10
translation-type: tm+mt
source-git-commit: 4b98c23f4120cbea6dd54cd68b61202e74bee3e1
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Sharing audiences with Adobe Experience Cloud{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>若要與Adobe Experience Cloud解決方案分享受眾，您必須實作Adobe Identity Management System。 [進一步瞭解IMS](../../integrations/using/about-adobe-id.md)。

有了Adobe Campaign，您就可以透過Adobe Experience Cloud解決方案和核心服務來分享受眾和細分。 有兩個選項可供使用：

1. 將Adobe Experience Platform區段資料傳送至Adobe Campaign。 若要實作此整合，您需要將即時客戶資料平台連結至Campaign(RTCDP)。 [在本節中進一步瞭解](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html)。


1. 將 **Adobe Campaign** 與People核心服務 **(又稱為Profiles &amp; Audiences核心服務******)或Adobe Audience Manager。 然後，您將能夠：

   * 從不同的Adobe Experience Cloud解決方案將共用的觀眾／區段匯入Adobe Campaign。 您可以透過Adobe Campaign中的清單匯入觀眾。

   * 以Adobe Experience Cloud共用觀眾的形式匯出清單。 這些受眾可用於您所使用的不同Adobe Experience Cloud解決方案。 在工作流程中，使用專屬活動進行定位後，即可匯出對象 **[!UICONTROL Update shared audience]** 。

此整合支援兩種Adobe Experience Cloud ID:

* **訪客ID**:此類識別碼可協調Adobe Experience Cloud訪客與Adobe Campaign收件者。
* **宣告的ID**:此類型的識別碼可協調所有類型的資料與Adobe Campaign資料庫的元素。 在Adobe Campaign中，它會以預先定義的協調金鑰呈現。
