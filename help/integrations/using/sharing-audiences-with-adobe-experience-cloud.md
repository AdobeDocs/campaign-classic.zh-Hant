---
solution: Campaign Classic
product: campaign
title: 使用Adobe Experience Cloud分享受眾
description: 使用Adobe Experience Cloud分享受眾
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# 與Adobe Experience Cloud共用觀眾{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>若要與Adobe Experience Cloud解決方案分享受眾，您必須實作Adobe Identity Management System。 [進一步瞭解IMS](../../integrations/using/about-adobe-id.md)。

有了Adobe Campaign，您就可以透過Adobe Experience Cloud解決方案和核心服務來分享受眾和細分。 有兩個選項可供使用：

1. 將Adobe Experience Platform區段資料傳送至Adobe Campaign。 若要實作此整合，您需要將即時客戶資料平台連結至Campaign(RTCDP)。 [在本節中進一步瞭解](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html)。


1. 將&#x200B;**Adobe Campaign**&#x200B;與&#x200B;**People core service**（又稱為&#x200B;**Profiles &amp; Audiences core service**）或Adobe Audience Manager整合。 然後，您將能夠：

   * 從不同的Adobe Experience Cloud解決方案將共用的觀眾／區段匯入Adobe Campaign。 您可以透過Adobe Campaign中的清單匯入觀眾。

   * 以Adobe Experience Cloud共用觀眾的形式匯出清單。 這些受眾可用於您所使用的不同Adobe Experience Cloud解決方案。 在工作流程中，使用專屬的&#x200B;**[!UICONTROL Update shared audience]**&#x200B;活動進行定位後，即可匯出觀眾。

此整合支援兩種Adobe Experience Cloud ID:

* **訪客ID**:此類識別碼可協調Adobe Experience Cloud訪客與Adobe Campaign收件者。
* **宣告的ID**:此類型的識別碼可協調所有類型的資料與Adobe Campaign資料庫的元素。在Adobe Campaign中，它會以預先定義的協調金鑰呈現。
