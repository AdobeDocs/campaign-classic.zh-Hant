---
solution: Campaign Classic
product: campaign
title: 訊息中心服務層級
description: 訊息中心服務層級
audience: message-center
content-type: reference
topic-tags: reports
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 5%

---


# 訊息中心服務層級{#message-center-service-level}

此報告會顯示與交易訊息相關的傳送統計資料以及錯誤劃分。 您可以按一下錯誤類型以顯示其詳細資訊。 此報告針對技術管理員，也可透過控制例項的&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤存取。

![](assets/mc_reports_1.png)

在此報表中，您可以選擇顯示整體統計資料或與特定執行例項相關的統計資料。 您也可以依頻道及特定時段來篩選資料。 在&#x200B;**[!UICONTROL Indicators over the period]**&#x200B;區段中顯示的指示符會在選定期間計算：

* **[!UICONTROL Incoming (throughput event/h)]** :在「消息中心」隊列中輸入的事件的平均每小時數。
* **[!UICONTROL Incoming (event vol)]** :在「消息中心」隊列中輸入的事件數。
* **[!UICONTROL Outgoing (throughput msg/h)]** :成功傳出消息中心事件的平均每小時數（由傳送傳送）。
* **[!UICONTROL Outgoing (msg vol)]** :成功傳出消息中心事件的數量（由傳送發送）。
* **[!UICONTROL Average sending time (seconds)]** :成功處理事件的訊息中心平均逗留時間。計算會考慮處理時間和mta傳送時間。
* **[!UICONTROL Error rate]** :與已進入「消息中心」隊列的事件數相比，錯誤的事件數。會考量到下列錯誤：路由錯誤、過期事件（佇列中的事件過長）、傳送錯誤，被傳送忽略（隔離等）。

>[!NOTE]
>
>可以在部署嚮導中配置警告（橙色）和警報（紅色）指示器閾值。 請參閱[監視閾值](../../message-center/using/monitoring-thresholds.md)。

