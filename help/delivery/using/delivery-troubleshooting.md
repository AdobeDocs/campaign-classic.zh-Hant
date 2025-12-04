---
product: campaign
title: 傳遞傳送疑難排解
description: 進一步瞭解傳遞效能，以及如何疑難排解與傳遞監視相關的問題
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 1%

---

# 傳遞傳送疑難排解 {#delivery-troubleshooting}

>[!NOTE]
>
>Campaign v8檔案中已記錄傳遞疑難排解的全面指引，適用於Campaign Classic v7和Campaign v8使用者：
>
>* 常見傳遞失敗與解決方案： [瞭解傳遞失敗](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* 傳送診斷緩慢： [在Campaign UI中監視傳送](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* 傳遞最佳實務：[傳遞最佳實務](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>此頁面記錄針對混合式部署和內部部署的&#x200B;**Campaign Classic v7專屬疑難排解**。

## 疑難排解 {#v7-specific}

針對&#x200B;**Campaign Classic v7混合/內部部署**，下列疑難排解步驟是您管理的基礎建設專用：

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
