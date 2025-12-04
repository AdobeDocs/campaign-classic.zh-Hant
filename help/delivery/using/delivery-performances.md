---
product: campaign
title: 傳遞效能最佳實務
description: 進一步瞭解傳遞效能和最佳實務
feature: Deliverability
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 3%

---

# 傳遞效能最佳實務 {#delivery-performances}

>[!NOTE]
>
>有關傳遞效能和最佳實務的完整指引記錄在[Campaign v8傳遞最佳實務](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices)頁面中。 此內容適用於Campaign Classic v7和Campaign v8使用者。
>
>此頁面記錄混合式部署和內部部署專用於&#x200B;**Campaign Classic v7的效能組態**。

如需傳遞效能、平台最佳化、隔離管理、資料庫維護和排程建議的完整最佳實務，請參閱[Campaign v8傳遞最佳實作檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}。

## 效能調整 {#best-practices-performance}

針對&#x200B;**Campaign Classic v7混合/內部部署**，下列資料庫和基礎架構最佳化可以改善傳遞效能：

### 資料庫最佳化

**索引位址**&#x200B;以最佳化應用程式中使用的SQL查詢效能。 可以從資料結構描述的主要元素宣告索引。 此最佳化需要直接存取資料庫，以及可在內部部署中使用的結構描述自訂。

### 基礎架構調整

**大型傳遞設定**：傳送給超過一百萬位收件者的傳遞在傳送佇列中需要空間。 對於內部部署安裝，可以將MTA子項設定為處理自訂批次大小。 請聯絡您的系統管理員，以根據您的基礎架構容量調整這些設定。

>[!NOTE]
>
>對於Campaign v8受管理的Cloud Services使用者，基礎架構最佳化和MTA設定由Adobe管理。 如需適用於您部署的效能建議，請參閱[Campaign v8傳遞最佳實務](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}。

## 維護資料庫 {#performance-issues}

對於&#x200B;**Campaign Classic v7混合/內部部署**，平台和資料庫維護會直接影響傳遞傳送效能。

定期維護任務包括：

**資料庫清理**：使用資料庫清理工作流程移除舊的傳遞記錄、追蹤資料和暫存表格。 不良的資料庫維護可能會減慢傳遞準備和傳送的速度。

**資料庫效能監視**：監視查詢效能、索引片段和資料表統計資料。 如需詳細指引，請參閱[此頁面](../../production/using/database-performances.md)。

**技術工作流程監控**：確認所有技術工作流程（尤其是清除、追蹤及傳遞能力更新工作流程）皆正確執行且沒有錯誤。

>[!NOTE]
>
>對於Campaign v8受管理的Cloud Services使用者，資料庫維護和技術工作流程會由Adobe監控和管理。 如[Campaign v8監視器傳遞檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}中所述，專注於傳遞特定的監視。

## 相關主題

* [傳遞最佳實務](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} （Campaign v8檔案）
* [監視您的傳遞能力](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"} （Campaign v8檔案）
* [傳遞疑難排解](delivery-troubleshooting.md)
* [資料庫效能](../../production/using/database-performances.md) （v7混合/內部部署）
