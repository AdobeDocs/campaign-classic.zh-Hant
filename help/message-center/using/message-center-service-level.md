---
product: campaign
title: 訊息中心服務層級
description: 進一步瞭解訊息中心服務等級報告
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 6%

---

# 訊息中心服務層級 {#message-center-service-level}



此報表顯示與異動訊息相關的傳送統計資料以及錯誤劃分。 您可以按一下錯誤型別以顯示其詳細資料。

此報表是針對技術管理員，也可透過以下網址存取： **[!UICONTROL Monitoring]** 索引標籤上的控制項執行個體。

![](assets/mc_reports_1.png)

在此報表中，您可以選擇顯示整體統計資料，或顯示與特定執行例項相關的統計資料。 您也可以依管道和特定期間篩選資料。

顯示在以下位置的指示器： **[!UICONTROL Indicators over the period]** 區段會在所選的時段內計算：

* **[!UICONTROL Incoming (throughput event/h)]** ：在訊息中心佇列中輸入的平均每小時事件數。
* **[!UICONTROL Incoming (event vol)]** ：在訊息中心佇列中輸入的事件數。
* **[!UICONTROL Outgoing (throughput msg/h)]** ：每小時成功的傳出訊息中心事件平均數（由傳遞傳送）。
* **[!UICONTROL Outgoing (msg vol)]** ：成功的傳出訊息中心事件數（由傳遞傳送）。
* **[!UICONTROL Average sending time (seconds)]** ：成功處理事件的平均訊息中心逗留時間。 該計算會將處理時間和郵件傳送時間納入考量。
* **[!UICONTROL Error rate]** ：發生錯誤的事件數，與已進入訊息中心佇列的事件數比較。 考慮以下錯誤：路由錯誤、過期事件（佇列中的事件太長）、傳送錯誤、由傳送忽略（隔離等）。

>[!NOTE]
>
>可以在部署精靈中設定警告（橘色）和警示（紅色）指標臨界值。 請參閱 [監視臨界值](../../message-center/using/additional-configurations.md#monitoring-thresholds).
