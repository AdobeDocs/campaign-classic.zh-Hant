---
product: campaign
title: 追蹤記錄檔問題
description: 追蹤記錄檔問題
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 14%

---

# 追蹤記錄檔問題{#tracking-logs-issues}



未轉送追蹤記錄的原因有好幾種。 建議您檢視下列資訊：

* ****&#x200B;追蹤&#x200B;**工作流程是否有錯誤？**

請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=zh-Hant){target="_blank"}。

![](assets/tracking_scheduled_task.png)

* **模組** trackinglogd **是否正在伺服器上執行？**

  請參閱[記錄檔](../../production/using/log-files.md)。

* **已進行變更嗎？**

  使用追蹤別名時，它們可能會觸發與伺服器的連線中斷。
