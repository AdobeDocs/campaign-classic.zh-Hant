---
product: campaign
title: 建議
description: 建議
feature: Monitoring
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%

---

# 建議{#recommendations}



Adobe Campaign是高度交易系統（OLTP資料庫）。 這表示基礎資料庫將經常更新，導致效能隨時間降低。 若要避免這類問題，需要定期維護資料庫。

>[!IMPORTANT]
>
>只有在定期維護資料庫時，資料庫才能以最佳方式執行。 某些RDBMS提供的自動維護功能是不夠的，無法取代任何關聯式資料庫異動管理系統的深入維護。
>  
>本檔案中說明的程式是建議。 維護計畫是資料庫管理員的責任，發生問題時，管理員必須是您的第一連絡人。
