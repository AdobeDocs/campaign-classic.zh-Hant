---
product: campaign
title: 管理報告
description: 管理報告
feature: Reporting, Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 68908664-3cf6-4a6c-a327-c7f059c27aa3
TQID: 'https://experienceleague.adobe.com/LA4v5oODC9n5K2Ttox9SF7lwcGQOU7IDEvL1P4Sls-4'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c309ee4e-82e4-4f7e-b608-ef345678c34e
    internal-label: Dynamic reporting
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: b3a4149f-2b3a-44d1-894e-e3ac4c77fb47
    internal-label: Reporting interface
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 4%
---
# 管理報告{#managing-reports}



必須重新開發以預設Adobe Campaign收件者（nm:recipient或連結的結構描述）專屬的結構描述為基礎的報表，以便考慮來自自訂表格及其透過目標對應連結之表格的資料（請參閱[目標對應](../../configuration/using/target-mapping.md)區段）。

若要建立新報告，請參閱[本節](../../reporting/using/about-reports-creation-in-campaign.md)。

某些情況下，您也必須放置這些表格專屬的新立方結構。 在[此區段](../../reporting/using/ac-cubes.md)中詳細說明立方體。

以下是相關報表：

* **[!UICONTROL Recent proposition tracking]** (recentPropositions)：即時主張追蹤。
* **[!UICONTROL Breakdown of opens]** (opensByUserAgent)：開啟根據使用者軟體劃分的檔案。
* **[!UICONTROL Statistics of the sharing activities]** (forwardActivities)：分析每個時段的共用活動、開啟和訂閱。
* **[!UICONTROL Tracking indicators]** (mobileAppDeliveryFeedback)：追蹤行動應用程式上傳送的指標。
* **[!UICONTROL Offer analysis]** (offerAnalysis)：依日期和管道的優惠方案分析。
* **[!UICONTROL Reactivity rate]** (mobileAppDistribution)：最新傳遞的反應率。
* **[!UICONTROL Breakdown of subscriptions]** (mobileAppDistribution)：每個行動應用程式的作用中訂閱劃分。
