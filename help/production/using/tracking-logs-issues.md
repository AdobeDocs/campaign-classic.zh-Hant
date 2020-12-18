---
solution: Campaign Classic
product: campaign
title: 追蹤記錄問題
description: 追蹤記錄問題
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---


# 追蹤記錄問題{#tracking-logs-issues}

追蹤記錄無法轉送的原因可能有多種。 建議您檢查下列資訊：

* **追蹤**&#x200B;工作流程是否有錯誤？

   請參閱[監控技術工作流](../../workflow/using/monitoring-technical-workflows.md)。

   ![](assets/tracking_scheduled_task.png)

* 伺服器上是否運行模組&#x200B;**trackinglogd**?

   請參閱[日誌檔案](../../production/using/log-files.md)。

* 是否進行了更改？ 它們可以使用追蹤別名觸發與伺服器的連線中斷。

