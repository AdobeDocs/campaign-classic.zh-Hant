---
title: 使用Adobe Experience cloud分享受眾
seo-title: 使用Adobe Experience cloud分享受眾
description: 使用Adobe Experience cloud分享受眾
seo-description: null
page-status-flag: never-activated
uuid: 24ac3463-69ab-48b4-85e0-4fe1948bf5ed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: 8f295058-5a78-4512-9bdf-d5f022457e10
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 418a36cd51106dae2b4201c8b5abda9b05285a18

---


# 使用Adobe Experience cloud分享受眾{#sharing-audiences-with-adobe-experience-cloud}

>[!NOTE]
>
>使用此整合需要實作IMS。 請參閱 [IMS相關章節](../../integrations/using/about-adobe-id.md)。

Adobe Campaign可讓您使用Adobe Experience cloud解決方案和核心服務來交換和分享受眾／細分。 若要這麼做，您必須將 **Adobe Campaign** 與 **People核心服務** (又稱為 **Profiles &amp; Audiences核心服務**)或Adobe Audience Manager整合。 然後，您將能夠：

* 從不同的Adobe Experience cloud解決方案將共用的觀眾／區段匯入Adobe Campaign。 您可以透過Adobe Campaign中的清單匯入觀眾。
* 以Adobe Experience cloud共用觀眾的形式匯出清單。 這些受眾可用於您所使用的不同Adobe Experience cloud解決方案。 在工作流程中，使用專屬活動進行定位後，即可匯出對 **[!UICONTROL Update shared audience]** 像。

>[!CAUTION]
>
>根據資料類型，匯入Adobe Campaign中的觀眾可能會受到法律限制。

此整合支援兩種Adobe Experience Cloud ID:

* **訪客ID**:此類識別碼可協調Adobe Experience cloud訪客與Adobe Campaign收件者。
* **宣告的ID**:此類型的識別碼可協調所有類型的資料與Adobe Campaign資料庫的元素。 在Adobe Campaign中，它會以預先定義的協調金鑰呈現。
