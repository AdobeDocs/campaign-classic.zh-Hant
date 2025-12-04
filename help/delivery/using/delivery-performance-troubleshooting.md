---
product: campaign
title: 傳遞效能與疑難排解
description: 瞭解如何最佳化傳遞效能和疑難排解Campaign Classic v7中的問題
feature: Monitoring, Deliverability, Troubleshooting
role: User, Developer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# 傳遞效能與疑難排解 {#delivery-performance-troubleshooting}

>[!NOTE]
>
>有關傳遞效能和最佳實務的完整指引記錄在[Campaign v8傳遞最佳實務](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices)頁面中。 此內容適用於Campaign Classic v7和Campaign v8使用者。
>
>此頁面記錄了&#x200B;**Campaign Classic v7的特定設定**，用於混合部署和內部部署中的效能最佳化和疑難排解。

如需傳遞效能、平台最佳化、隔離管理、資料庫維護和排程建議的完整最佳實務，請參閱[Campaign v8傳遞最佳實作檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}。

## 效能最佳化 {#performance-optimization}

針對&#x200B;**Campaign Classic v7混合/內部部署**，下列資料庫和基礎架構最佳化可以改善傳遞效能。

### 資料庫最佳化

**索引位址**&#x200B;以最佳化應用程式中使用的SQL查詢效能。 可以從資料結構描述的主要元素宣告索引。 此最佳化需要直接存取資料庫，以及可在內部部署中使用的結構描述自訂。

### 基礎架構調整

**大型傳遞設定**：傳送給超過一百萬位收件者的傳遞在傳送佇列中需要空間。 對於內部部署安裝，可以將MTA子項設定為處理自訂批次大小。 請聯絡您的系統管理員，以根據您的基礎架構容量調整這些設定。

>[!NOTE]
>
>對於Campaign v8受管理的Cloud Services使用者，基礎架構最佳化和MTA設定由Adobe管理。 如需適用於您部署的效能建議，請參閱[Campaign v8傳遞最佳實務](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}。

### 維護資料庫 {#database-maintenance}

對於&#x200B;**Campaign Classic v7混合/內部部署**，平台和資料庫維護會直接影響傳遞傳送效能。

定期維護任務包括：

**資料庫清理**：使用資料庫清理工作流程移除舊的傳遞記錄、追蹤資料和暫存表格。 不良的資料庫維護可能會減慢傳遞準備和傳送的速度。

**資料庫效能監視**：監視查詢效能、索引片段和資料表統計資料。 如需詳細指引，請參閱[此頁面](../../production/using/database-performances.md)。

**技術工作流程監控**：確認所有技術工作流程（尤其是清除、追蹤及傳遞能力更新工作流程）皆正確執行且沒有錯誤。

>[!NOTE]
>
>對於Campaign v8受管理的Cloud Services使用者，資料庫維護和技術工作流程會由Adobe監控和管理。 如[Campaign v8監視器傳遞檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitoring-deliverability){target="_blank"}中所述，專注於傳遞特定的監視。

## 疑難排解傳送問題 {#troubleshooting}

>[!NOTE]
>
>Campaign v8檔案中已記錄傳遞疑難排解的全面指引，適用於Campaign Classic v7和Campaign v8使用者：
>
>* 常見傳遞失敗與解決方案： [瞭解傳遞失敗](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* 傳送診斷緩慢： [在Campaign UI中監視傳送](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* 傳遞最佳實務：[傳遞最佳實務](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>本節記錄針對混合式部署和內部部署的&#x200B;**Campaign Classic v7專屬疑難排解**。

對於&#x200B;**Campaign Classic v7混合/內部部署**，下列疑難排解步驟是您管理的基礎結構所特有的。

### MX規則設定

如果您遇到特定ISP的節流問題，您可能需要檢閱並調整您的MX規則設定。 如需MX規則和配額的詳細資訊，請參閱[本節](../../installation/using/email-deliverability.md#about-mx-rules)。

### 傳遞效能的資料庫維護

如果您在中間來源部署中遇到以下錯誤：

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

原因與效能問題有關，行銷執行個體在將資料傳送到中間來源伺服器之前花費太多時間建置資料。

**對於內部部署安裝**，請在資料庫上執行真空並重新索引。 如需資料庫維護的詳細資訊，請參閱[本節](../../production/using/recommendations.md)。

您也應該重新啟動所有具有已排程活動的工作流程，以及所有處於失敗狀態的工作流程。 請參閱[本節](../../workflow/using/scheduler.md)。

### 技術工作流程監視

對於內部部署安裝，請確定與傳遞能力相關的所有技術工作流程皆順利執行，且沒有錯誤：

**傳遞能力更新工作流程**：更新退回郵件資格規則和傳遞能力指標。

**追蹤工作流程**：處理已傳送傳遞的追蹤資料。

**資料庫清理工作流程**：定期清除舊的傳遞記錄檔和暫存資料表以維持效能。

在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**&#x200B;中檢查工作流程狀態。

>[!NOTE]
>
>對於Campaign v8受管理的Cloud Services使用者，技術工作流程和基礎架構監控由Adobe管理。 如[Campaign v8檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}所述，著重於傳遞內容和目標定位。

## 相關主題

* [瞭解傳遞失敗](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} （Campaign v8檔案）
* [傳遞最佳實務](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} （Campaign v8檔案）
* [在Campaign UI中監視傳遞](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} （Campaign v8檔案）
* [資料庫維護](../../production/using/recommendations.md) （v7混合/內部部署）
* [電子郵件傳遞能力](../../installation/using/email-deliverability.md) （v7混合/內部部署）
* [資料庫效能](../../production/using/database-performances.md) （v7混合/內部部署）

