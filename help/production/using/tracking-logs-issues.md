---
product: campaign
title: 追蹤記錄檔問題
description: 追蹤記錄檔問題
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# 追蹤記錄檔問題{#tracking-logs-issues}



未轉送追蹤記錄的原因有好幾種。 建議您檢視下列資訊：

* ****&#x200B;追蹤&#x200B;**工作流程是否有錯誤？**

  請參閱[監視技術工作流程](../../workflow/using/monitoring-technical-workflows.md)。

  ![](assets/tracking_scheduled_task.png)

* **模組** trackinglogd **是否正在伺服器上執行？**

  請參閱[記錄檔](../../production/using/log-files.md)。

* **已進行變更嗎？**

  使用追蹤別名時，它們可能會觸發與伺服器的連線中斷。
