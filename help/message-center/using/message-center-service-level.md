---
product: campaign
title: 訊息中心服務層級
description: 進一步瞭解訊息中心服務等級報告
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 3%

---

# 訊息中心服務層級 {#message-center-service-level}



此報表顯示與異動訊息相關的傳遞統計資料以及錯誤劃分。 您可以按一下錯誤型別以顯示其詳細資料。

此報表是針對技術管理員，也可透過以下網址存取： **[!UICONTROL Monitoring]** 索引標籤上的控制例項。

![](assets/mc_reports_1.png)

在此報表中，您可以選擇顯示整體統計資料，或相對於特定執行執行處理的統計資料。 您也可以依管道和特定期間篩選資料。

顯示在中的指示器 **[!UICONTROL Indicators over the period]** 區段會在選取的期間內計算：

* **[!UICONTROL Incoming (throughput event/h)]** ：在Message Center佇列中輸入的平均每小時事件數。
* **[!UICONTROL Incoming (event vol)]** ：在Message Center佇列中輸入的事件數。
* **[!UICONTROL Outgoing (throughput msg/h)]** ：成功外寄訊息中心事件的平均每小時數量（由傳遞傳送）。
* **[!UICONTROL Outgoing (msg vol)]** ：成功的傳出訊息中心事件數（由傳遞傳送）。
* **[!UICONTROL Average sending time (seconds)]** ：成功處理事件的平均訊息中心逗留時間。 該計算會將處理時間和mta傳送時間納入考量。
* **[!UICONTROL Error rate]** ：發生錯誤的事件數目，與已進入Message Center佇列的事件數目比較。 考慮以下錯誤：路由錯誤、過期事件（在佇列中的事件過長）、傳送錯誤、被傳送忽略（隔離等）。

>[!NOTE]
>
>可以在部署精靈中設定警告（橘色）和警示（紅色）指標臨界值。 請參閱 [監視臨界值](../../message-center/using/additional-configurations.md#monitoring-thresholds).
