---
product: campaign
title: 訊息中心處理時間
description: 進一步瞭解訊息中心處理時間報告
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 6%

---

# 訊息中心處理時間 {#message-center-processing-time}



此報表顯示與即時佇列相關的主要指標。

此報表是針對技術管理員，也可透過以下網址存取： **[!UICONTROL Monitoring]** 索引標籤上的控制項執行個體。

![](assets/mc_reports_2.png)

就像的 **[!UICONTROL Message Center service level]** 報表，您可以選擇顯示整體統計資料或特定執行例項的相關統計資料。 您也可以依管道和特定期間篩選資料。

顯示在以下位置的指示器： **[!UICONTROL Indicators over the period]** 區段會在所選的時段內計算：

* **[!UICONTROL Average queuing time]** ：成功處理在訊息中心所花費之事件的平均時間。 僅考慮處理時間。
* **[!UICONTROL Average message sending time (s)]** ：成功處理在訊息中心所花費之事件的平均時間。 只考慮MTA傳送時間。
* **[!UICONTROL Average processing time (s)]** ：成功處理在訊息中心所花費之事件的平均時間。 該計算會將處理時間和郵件傳送時間納入考量。
* **[!UICONTROL Maximum number of queued events]** ：在任何指定時刻存在於訊息中心佇列中的最大事件數。
* **[!UICONTROL Minimum number of queued events]** ：在任何指定時刻出現在訊息中心佇列中的最小事件數。
* **[!UICONTROL Average number of queued events]** ：在任何指定時刻出現在訊息中心佇列中的平均事件數。

>[!NOTE]
>
>可以在Adobe Campaign部署精靈中設定警告（橘色）和警示（紅色）指標臨界值。 請參閱 [監視臨界值](../../message-center/using/additional-configurations.md#monitoring-thresholds).
