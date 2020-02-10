---
title: 消息中心服務級別
seo-title: 消息中心服務級別
description: 消息中心服務級別
seo-description: null
page-status-flag: never-activated
uuid: 8e363706-292b-40db-97bc-d41b41910556
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: e46a4e87-6c02-4b9c-bf6d-bb4e785e78fa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 消息中心服務級別{#message-center-service-level}

此報告會顯示與交易訊息相關的傳送統計資料以及錯誤劃分。 您可以按一下錯誤類型以顯示其詳細資訊。 此報告針對技術管理員，也可透過控制例項中 **[!UICONTROL Monitoring]** 的宇宙存取。

![](assets/mc_reports_1.png)

在此報表中，您可以選擇顯示整體統計資料或與特定執行例項相關的統計資料。 您也可以依頻道及特定時段來篩選資料。 區段中顯示的指 **[!UICONTROL Indicators over the period]** 標會在選取的期間內計算：

* **[!UICONTROL Incoming (throughput event/h)]** :在「消息中心」隊列中輸入的事件的平均每小時數。
* **[!UICONTROL Incoming (event vol)]** :在「消息中心」隊列中輸入的事件數。
* **[!UICONTROL Outgoing (throughput msg/h)]** :成功傳出消息中心事件的平均每小時數（由傳送傳送）。
* **[!UICONTROL Outgoing (msg vol)]** :成功傳出消息中心事件的數量（由傳送發送）。
* **[!UICONTROL Average sending time (seconds)]** :成功處理事件的訊息中心平均逗留時間。 計算會考慮處理時間和mta傳送時間。
* **[!UICONTROL Error rate]** :與已進入「消息中心」隊列的事件數相比，錯誤的事件數。 會考量到下列錯誤：路由錯誤、過期事件（佇列中的事件過長）、傳送錯誤，被傳送忽略（隔離等）。

>[!NOTE]
>
>可以在部署嚮導中配置警告（橙色）和警報（紅色）指示器閾值。 請參閱監 [控閾值](../../message-center/using/monitoring-thresholds.md)。

