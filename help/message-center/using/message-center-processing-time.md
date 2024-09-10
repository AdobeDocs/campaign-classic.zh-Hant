---
product: campaign
title: 訊息中心處理時間
description: 進一步瞭解訊息中心處理時間報告
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# 訊息中心處理時間 {#message-center-processing-time}



此報表顯示與即時佇列相關的主要指標。

此報表是針對技術管理員，也可透過控制執行個體上的&#x200B;**[!UICONTROL Monitoring]**&#x200B;索引標籤進行存取。

![](assets/mc_reports_2.png)

就像&#x200B;**[!UICONTROL Message Center service level]**&#x200B;報告一樣，您可以選擇顯示整體統計資料，或相對於特定執行例項的統計資料。 您也可以依管道和特定期間篩選資料。

**[!UICONTROL Indicators over the period]**&#x200B;區段中所顯示的指標是在選取的時段內計算：

* **[!UICONTROL Average queuing time]** ：成功處理在訊息中心所花費之事件的平均時間。 僅考慮處理時間。
* **[!UICONTROL Average message sending time (s)]** ：成功處理在訊息中心所花費之事件的平均時間。 只考慮MTA傳送時間。
* **[!UICONTROL Average processing time (s)]** ：成功處理在訊息中心所花費之事件的平均時間。 該計算會將處理時間和郵件傳送時間納入考量。
* **[!UICONTROL Maximum number of queued events]** ：在任何指定時刻存在於訊息中心佇列中的最大事件數。
* **[!UICONTROL Minimum number of queued events]** ：在任何指定時刻出現在訊息中心佇列中的最小事件數。
* **[!UICONTROL Average number of queued events]** ：在任何指定時刻出現在訊息中心佇列中的平均事件數。

>[!NOTE]
>
>可以在Adobe Campaign部署精靈中設定警告（橘色）和警示（紅色）指標臨界值。 請參閱[監視臨界值](../../message-center/using/additional-configurations.md#monitoring-thresholds)。
