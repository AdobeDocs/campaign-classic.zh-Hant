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
TQID: 'https://experienceleague.adobe.com/MGzMyGtmzaVGZy6oWHcirPPdSSpu9YYcuR30KIVZ9bc'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
  - id: afa4204e-6d08-4e29-bc35-26aafb656d48
    internal-label: Profiles and audiences
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
    internal-label: Experience Manager integration
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Experience Platform integration
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
    internal-label: Target integration
  - id: d6330382-c886-4f7a-a4f7-74e3f36c0d9c
    internal-label: Audiences
source-git-commit: 1b8805ac952da110858c88fc2c252aece69ad2bf
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 38%
---
# 與[!DNL Adobe CX Enterprise]共用對象 {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>若要與[!DNL CX Enterprise]解決方案共用對象，您必須實作Adobe Identity Management System。 [進一步瞭解IMS](../../integrations/using/about-adobe-id.md)。

透過Adobe Campaign，您可以與[!DNL CX Enterprise]服務共用對象和區段。 有兩個可用選項：

1. 將Adobe Experience Platform區段資料傳送至Adobe Campaign。 若要實作此整合，您必須將Real-Time Customer Data Platform連結至Campaign (RTCDP)。 [在本章節了解更多資訊](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=zh-Hant){target="_blank"}。

1. 將&#x200B;**Adobe Campaign**&#x200B;與&#x200B;**Experience Cloud Audiences**&#x200B;或&#x200B;**Adobe Audience Manager**&#x200B;整合。 之後，您將能夠：

   * 從不同的[!DNL CX Enterprise]解決方案匯入共用的對象/區段至Adobe Campaign。 您可以透過 Adobe Campaign 中的清單匯入客群。

   * 以[!DNL CX Enterprise]個共用對象的形式匯出清單。 這些對象可用於您所使用的不同[!DNL CX Enterprise]解決方案。 在工作流程中目標定位後，可使用專用的 **[!UICONTROL Update shared audience]** 活動匯出客群。

此整合支援兩種類型的 Adobe Experience Cloud ID：

* **訪客 ID**：此類型的識別碼可協調 Adobe Experience Cloud 訪客與 Adobe Campaign 收件者。
* **宣告 ID**：此類型的識別碼可協調所有類型的資料與 Adobe Campaign 資料庫中的元素。 在 Adobe Campaign 中以預先定義的調解金鑰呈現。

  >[!NOTE]
  >
  > 已宣告的ID資料來源現在也可搭配Experience Cloud Assets整合使用。
  >
