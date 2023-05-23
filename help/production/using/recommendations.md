---
product: campaign
title: 建議
description: 建議
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# 建議{#recommendations}



Adobe Campaign是一個高度事務性系統（OLTP資料庫）。 這意味著基礎資料庫將經常更新，導致效能隨時間而降低。 為避免此類問題，需要定期維護資料庫。

>[!IMPORTANT]
>
>只有在定期維護資料庫時，資料庫才會以最佳方式運行。 某些RDBMS提供的自動維護不夠，並且不會像任何關係資料庫事務管理系統那樣替代深入維護。
>  
>本文中介紹的步驟是建議。 維護計畫由資料庫管理員負責，在出現問題時，管理員必須是您的第一個聯繫人。
