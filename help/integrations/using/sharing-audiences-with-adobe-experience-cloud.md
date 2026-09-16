---
product: campaign
title: 與Adobe Experience Cloud共用受眾
description: 與Adobe Experience Cloud共用受眾
feature: Audiences
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
TQID: https://experienceleague.adobe.com/MGzMyGtmzaVGZy6oWHcirPPdSSpu9YYcuR30KIVZ9bc
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Adobe Analytics integration
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
    internal-label: Adobe Experience Manager integration
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Adobe Experience Platform integration
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
    internal-label: Adobe Target integration
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 51%
---
# 與Adobe Experience Cloud共用受眾 {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>若要與Adobe Experience Cloud解決方案共用閱聽眾，您必須實作Adobe Identity Management系統。 [進一步瞭解IMS](../../integrations/using/about-adobe-id.md)。

透過Adobe Campaign，您可以與Adobe Experience Cloud服務共用受眾和區段。 有兩個可用選項：

1. 將Adobe Experience Platform區段資料傳送至Adobe Campaign。 若要實作此整合，您必須將Real-Time Customer Data Platform連結至Campaign (RTCDP)。 [在本章節了解更多資訊](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=zh-Hant){target="_blank"}。

1. 將&#x200B;**Adobe Campaign**&#x200B;與&#x200B;**Experience Cloud Audiences**&#x200B;或&#x200B;**Adobe Audience Manager**&#x200B;整合。 之後，您將能夠：

   * 從不同的 Adobe Experience Cloud 解決方案匯入共用的客群/區段至 Adobe Campaign。 您可以透過 Adobe Campaign 中的清單匯入客群。

   * 以 Adobe Experience Cloud 共用客群的形式匯出清單。 這些客群可用於您所使用的不同 Adobe Experience Cloud 解決方案。 在工作流程中目標定位後，可使用專用的 **[!UICONTROL Update shared audience]** 活動匯出客群。

此整合支援兩種類型的 Adobe Experience Cloud ID：

* **訪客 ID**：此類型的識別碼可協調 Adobe Experience Cloud 訪客與 Adobe Campaign 收件者。
* **宣告 ID**：此類型的識別碼可協調所有類型的資料與 Adobe Campaign 資料庫中的元素。 在 Adobe Campaign 中以預先定義的調解金鑰呈現。

  >[!NOTE]
  >
  > 已宣告的ID資料來源現在也可搭配Experience Cloud Assets整合使用。
  >
