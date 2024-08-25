---
product: campaign
title: 與Adobe Experience Cloud共用對象
description: 與Adobe Experience Cloud共用對象
feature: Audiences
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: b11185da8236d6100d98eabcc9dc1cf2cffa70af
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 50%

---

# 與Adobe Experience Cloud共用對象 {#sharing-audiences-with-adobe-experience-cloud}


>[!CAUTION]
>
>若要與Adobe Experience Cloud解決方案共用閱聽眾，您必須實作AdobeIdentity Management系統。 [進一步瞭解IMS](../../integrations/using/about-adobe-id.md)。

透過Adobe Campaign，您可以與Adobe Experience Cloud服務共用受眾和區段。 有兩個可用選項：

1. 將Adobe Experience Platform區段資料傳送至Adobe Campaign。 若要實作此整合，您需要將Real-time Customer Data Platform連結至Campaign (RTCDP)。 [在本節瞭解更多資訊](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html){target="_blank"}。

1. 將&#x200B;**Adobe Campaign**&#x200B;與&#x200B;**Experience Cloud對象**&#x200B;或&#x200B;**Adobe Audience Manager**&#x200B;整合。 之後，您將能夠：

   * 從不同的 Adobe Experience Cloud 解決方案匯入共用的客群/區段至 Adobe Campaign。 您可以透過 Adobe Campaign 中的清單匯入客群。

   * 以 Adobe Experience Cloud 共用客群的形式匯出清單。 這些客群可用於您所使用的不同 Adobe Experience Cloud 解決方案。 在工作流程中目標定位後，可使用專用的 **[!UICONTROL Update shared audience]** 活動匯出客群。

此整合支援兩種類型的 Adobe Experience Cloud ID：

* **訪客 ID**：此類型的識別碼可協調 Adobe Experience Cloud 訪客與 Adobe Campaign 收件者。
* **宣告 ID**：此類型的識別碼可協調所有類型的資料與 Adobe Campaign 資料庫中的元素。 在 Adobe Campaign 中以預先定義的調解金鑰呈現。

  >[!NOTE]
  >
  > 已宣告的ID資料來源現在也可搭配Experience Cloud Assets整合使用。
  >
