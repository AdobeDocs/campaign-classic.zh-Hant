---
solution: Campaign Classic
product: campaign
title: 與Adobe Experience Cloud分享受眾
description: 與Adobe Experience Cloud分享受眾
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 40abbf1f981331b8a19d3607c57624aac22c91f2
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# 與Adobe Experience Cloud分享觀眾{#sharing-audiences-with-adobe-experience-cloud}

>[!CAUTION]
>
>若要與Adobe Experience Cloud解決方案分享受眾，您必須實作AdobeIdentity Management系統。 [進一步瞭解IMS](../../integrations/using/about-adobe-id.md)。

有了Adobe Campaign，您就可以與Adobe Experience Cloud解決方案和核心服務分享受眾和細分。 有兩個選項可供使用：

1. 傳送Adobe Experience Platform區段資料至Adobe Campaign。 若要實作此整合，您需要將即時客戶資料平台連結至Campaign(RTCDP)。 [在本節中進一步瞭解](https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html)。


1. 將&#x200B;**Adobe Campaign**&#x200B;與&#x200B;**人員核心服務**（亦稱&#x200B;**設定檔與觀眾核心服務**）或Adobe Audience Manager整合。 然後，您將能夠：

   * 從不同的Adobe Experience Cloud解決方案將共用的觀眾／區段匯入Adobe Campaign。 您可以透過Adobe Campaign的清單匯入觀眾。

   * 以Adobe Experience Cloud共用受眾形式列出的出口清單。 這些受眾可用於您使用的不同Adobe Experience Cloud解決方案。 在工作流程中，使用專屬的&#x200B;**[!UICONTROL Update shared audience]**&#x200B;活動進行定位後，即可匯出觀眾。

此整合支援兩種類型的Adobe Experience CloudID:

* **訪客ID**:此類識別碼可協調Adobe Experience Cloud訪客與Adobe Campaign收件者。
* **宣告的ID**:這種類型的標識符將所有類型的資料與Adobe Campaign資料庫中的元素進行協調。它在Adobe Campaign被表示為預先定義的和解密鑰。

   >[!NOTE]
   >
   > 宣告的ID資料來源現在也可與People核心服務整合搭配使用。
   >
   >如果您使用「人員」核心服務整合併想要新增Audience Manager整合，您將需要Adobe Audience Manager顧問的協助，以避免在轉換至Adobe Audience Manager上下文中使用此Declared ID資料來源時遺失所有收集到的ID同步。
