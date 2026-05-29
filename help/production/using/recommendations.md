---
product: campaign
title: 建議
description: 建議
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
TQID: https://experienceleague.adobe.com/hz0wmjq8MEpmen-C30F0tHt5-sRXjQAJ6vaie3hjfAo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 136
ht-degree: 15%

---

# 建議{#recommendations}



Adobe Campaign是高度交易系統（OLTP資料庫）。 這表示基礎資料庫將經常更新，導致效能隨時間降低。 若要避免這類問題，需要定期維護資料庫。

>[!IMPORTANT]
>
>只有在定期維護資料庫時，資料庫才能以最佳方式執行。 某些RDBMS提供的自動維護功能是不夠的，無法取代任何關聯式資料庫異動管理系統的深入維護。
>  
>本檔案中說明的程式是建議。 維護計畫是資料庫管理員的責任，發生問題時，管理員必須是您的第一連絡人。
