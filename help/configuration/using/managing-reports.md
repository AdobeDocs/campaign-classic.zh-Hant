---
product: campaign
title: 管理報告
description: 管理報告
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---

# 管理報告{#managing-reports}

![](../../assets/v7-only.svg)

必須重新開發以預設Adobe Campaign收件者（nm:recipient或schema linked）特定結構為基礎的報表，以考慮自訂表格及其透過目標對應連結的表格的資料（請參閱[Target對應](../../configuration/using/target-mapping.md)區段）。

若要建立新報表，請參閱[此區段](../../reporting/using/about-reports-creation-in-campaign.md)。

在某些情況下，您還必須放置這些表格專用的新立方體。 在[此部分](../../reporting/using/about-cubes.md)中詳細介紹多維資料集。

有關報告如下：

* **[!UICONTROL Recent proposition tracking]** （最近的建議）:即時命題追蹤。
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent):開啟，依使用者軟體劃分。
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities):分析每個時段的共用活動、開啟和訂閱。
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback):在行動應用程式上傳送的追蹤指標。
* **[!UICONTROL Offer analysis]** (offerAnalysis):根據日期和管道進行優惠方案分析。
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution):最新傳送的再活動率。
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution):每個行動應用程式的作用中訂閱劃分。
