---
product: campaign
title: 與Adobe Experience Cloud共用受眾
description: 與Adobe Experience Cloud共用受眾
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: c929557ee9f5467f9c3b8eb1ed25fae5399820ba
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 6%

---

# 與Adobe Experience Cloud共用受眾{#sharing-audiences-with-adobe-experience-cloud}

![](../../assets/common.svg)

>[!CAUTION]
>
>若要與Adobe Experience Cloud解決方案共用閱聽眾，您需要實作AdobeIdentity Management系統。 [深入了解IMS](../../integrations/using/about-adobe-id.md).

透過Adobe Campaign，您可以與Adobe Experience Cloud解決方案及核心服務共用受眾和區段。 有兩個選項可用：

1. 將Adobe Experience Platform區段資料傳送至Adobe Campaign。 若要實作此整合，您需要將Real-time Customer Data Platform連線至Campaign(RTCDP)。 [在本節了解更多資訊](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

1. 整合 **Adobe Campaign** with **人員核心服務** (也稱為 **設定檔與受眾核心服務**)或Adobe Audience Manager。 之後，您將能夠：

   * 從不同的Adobe Experience Cloud解決方案匯入共用的受眾/區段至Adobe Campaign。 您可以透過Adobe Campaign中的清單匯入對象。

   * 以Adobe Experience Cloud共用對象的形式匯出清單。 這些對象可用於您所使用的不同Adobe Experience Cloud解決方案。 在工作流程中鎖定目標後，可使用專用的 **[!UICONTROL Update shared audience]** 活動。

此整合支援兩種類型的Adobe Experience Cloud ID:

* **訪客ID**:此類型的識別碼可協調Adobe Experience Cloud訪客與Adobe Campaign收件者。
* **宣告ID**:此類型的識別碼可協調所有類型的資料與Adobe Campaign資料庫中的元素。 在Adobe Campaign中以預先定義的調解金鑰呈現。

   >[!NOTE]
   >
   > 已宣告的 ID 資料來源現在也可搭配 People 核心服務整合使用。
   >
   >如果您使用People核心服務整合，且想要新增Audience Manager整合，則需要Adobe Audience Manager顧問的協助，以避免在Adobe Audience Manager內容中轉換為使用此宣告ID資料來源時，所收集的所有ID同步都遺失。
