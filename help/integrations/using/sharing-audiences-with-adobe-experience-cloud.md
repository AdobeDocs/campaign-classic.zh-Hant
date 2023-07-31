---
product: campaign
title: 與Adobe Experience Cloud共用對象
description: 與Adobe Experience Cloud共用對象
feature: Audiences, People Core Service Integration
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 1c90e913-3375-476c-ab60-89f20239eb0d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 61%

---

# 與Adobe Experience Cloud共用對象{#sharing-audiences-with-adobe-experience-cloud}



>[!CAUTION]
>
>若要與Adobe Experience Cloud解決方案共用閱聽眾，您必須實作AdobeIdentity Management系統。 [進一步瞭解IMS](../../integrations/using/about-adobe-id.md).

透過Adobe Campaign，您可以與Adobe Experience Cloud解決方案和核心服務共用受眾和區段。 有兩個可用選項：

1. 將Adobe Experience Platform區段資料傳送至Adobe Campaign。 若要實作此整合，您需要將Real-time Customer Data Platform連結至Campaign (RTCDP)。 [在本章節了解更多資訊](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html)。

1. 整合 **Adobe Campaign** 替換為 **People核心服務** (也稱為 **設定檔與受眾核心服務**)或Adobe Audience Manager。 之後，您將能夠：

   * 從不同的 Adobe Experience Cloud 解決方案匯入共用的對象/區段至 Adobe Campaign。 您可以透過 Adobe Campaign 中的清單匯入對象。

   * 以 Adobe Experience Cloud 共用對象的形式匯出清單。 這些對象可用於您所使用的不同 Adobe Experience Cloud 解決方案。 在工作流程中目標定位後，可使用專用的 **[!UICONTROL Update shared audience]** 活動匯出對象。

此整合支援兩種類型的 Adobe Experience Cloud ID：

* **訪客 ID**：此類型的識別碼可協調 Adobe Experience Cloud 訪客與 Adobe Campaign 收件者。
* **宣告 ID**：此類型的識別碼可協調所有類型的資料與 Adobe Campaign 資料庫中的元素。 在 Adobe Campaign 中以預先定義的調解金鑰呈現。

  >[!NOTE]
  >
  > 已宣告的 ID 資料來源現在也可搭配 People 核心服務整合使用。
  >
  >如果您使用 People 核心服務整合，且想要新增 Audience Manager 整合，則需要 Adobe Audience Manager 顧問的協助，以避免在 Adobe Audience Manager 內容中轉換為使用此宣告 ID 資料來源時，所收集的 ID 同步全部遺失。
