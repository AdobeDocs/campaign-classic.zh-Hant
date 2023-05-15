---
product: campaign
title: 建議
description: 建議
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# 建議{#recommendations}



Adobe Campaign是高度事務性系統（OLTP資料庫）。 這表示基礎資料庫將經常更新，導致效能隨時間而降低。 為避免此類問題，需要定期維護資料庫。

>[!IMPORTANT]
>
>只有定期維護資料庫，資料庫才能最佳執行。 某些RDBMS提供的自動維護不夠充分，而且不會取代任何關係資料庫事務管理系統的深入維護。
>  
>本檔案所述的程式為建議。 維護計畫是資料庫管理員的責任，在發生問題時，必須由他們作為您的第一個聯繫人。
