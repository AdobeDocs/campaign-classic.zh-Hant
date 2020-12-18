---
solution: Campaign Classic
product: campaign
title: 管理報表
description: 管理報表
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---


# 管理報表{#managing-reports}

必須重新開發預設Adobe Campaign收件者（nm:recipient或schema linked）專屬的架構報表，以考慮自訂表格及其透過目標對應連結的表格的資料（請參閱[Target對應](../../configuration/using/target-mapping.md)區段）。

若要建立新報表，請參閱[本節](../../reporting/using/about-reports-creation-in-campaign.md)。

在某些情況下，還必須放置這些表專用的新立方。 Cubes詳見[本節](../../reporting/using/about-cubes.md)。

以下報告涉及：

* **[!UICONTROL Recent proposition tracking]** （最近的建議）:即時提案追蹤。
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent):開啟時，會依使用者軟體劃分。
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivitys):分析共用活動、每個時段的開啟和訂閱。
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback):在行動應用程式上傳送的追蹤指標。
* **[!UICONTROL Offer analysis]** (offerAnalysis):選件分析。
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution):最新交付的反應性率。
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution):每個行動應用程式的作用中訂閱劃分。

