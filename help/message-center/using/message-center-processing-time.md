---
product: campaign
title: 訊息中心處理時間
description: 進一步了解訊息中心處理時間報表。
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: e86350cf12db37e3f2c227563057b97922601729
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# 訊息中心處理時間 {#message-center-processing-time}

此報表顯示與即時佇列相關的主要指標。

此報告針對技術管理員，也可透過控制執行個體的&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤來存取。

![](assets/mc_reports_2.png)

與&#x200B;**[!UICONTROL Message Center service level]**&#x200B;報表一樣，您可以選擇顯示整體統計資料或與特定執行例項相關的統計資料。 您也可以依管道和特定期間來篩選資料。

**[!UICONTROL Indicators over the period]**&#x200B;區段中顯示的指標會在選取的期間內計算：

* **[!UICONTROL Average queuing time]** :成功處理事件在訊息中心逗留的平均時間。只考慮處理時間。
* **[!UICONTROL Average message sending time (s)]** :成功處理事件在訊息中心逗留的平均時間。只考慮mta傳送時間。
* **[!UICONTROL Average processing time (s)]** :成功處理事件在訊息中心逗留的平均時間。計算會考量處理時間和mta傳送時間。
* **[!UICONTROL Maximum number of queued events]** :在任何給定時刻消息中心隊列中存在的事件數上限。
* **[!UICONTROL Minimum number of queued events]** :在任何給定時刻消息中心隊列中存在的事件的最小數量。
* **[!UICONTROL Average number of queued events]** :在任何給定時刻消息中心隊列中存在的事件平均數。

>[!NOTE]
>
>警告（橙色）和警報（紅色）指標臨界值可在Adobe Campaign部署精靈中設定。 請參閱[監視閾值](../../message-center/using/additional-configurations.md#monitoring-thresholds)。
