---
solution: Campaign Classic
product: campaign
title: 訊息中心處理時間
description: 訊息中心處理時間
audience: message-center
content-type: reference
topic-tags: reports
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%

---


# 訊息中心處理時間{#message-center-processing-time}

此報告會顯示與即時佇列相關的主要指標。 此報告針對技術管理員，也可透過控制例項的&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤存取。

![](assets/mc_reports_2.png)

就像&#x200B;**[!UICONTROL Message Center service level]**&#x200B;報表一樣，您可以選擇顯示整體統計資料或與特定執行例項相關的統計資料。 您也可以依頻道及特定時段來篩選資料。 在&#x200B;**[!UICONTROL Indicators over the period]**&#x200B;區段中顯示的指示符會在選定期間計算：

* **[!UICONTROL Average queuing time]** :成功處理事件在「訊息中心」中逗留的平均時間。只考慮處理時間。
* **[!UICONTROL Average message sending time (s)]** :成功處理事件在「訊息中心」中逗留的平均時間。只會考量到mta傳送時間。
* **[!UICONTROL Average processing time (s)]** :成功處理事件在「訊息中心」中逗留的平均時間。計算會考慮處理時間和mta傳送時間。
* **[!UICONTROL Maximum number of queued events]** :消息中心隊列中任意給定時刻存在的最大事件數。
* **[!UICONTROL Minimum number of queued events]** :消息中心隊列中任意給定時刻存在的最小事件數。
* **[!UICONTROL Average number of queued events]** :消息中心隊列中任意給定時刻的事件平均數。

>[!NOTE]
>
>警告（橘色）和警報（紅色）指示符閾值可在Adobe Campaign部署嚮導中配置。 請參閱[監視閾值](../../message-center/using/monitoring-thresholds.md)。

