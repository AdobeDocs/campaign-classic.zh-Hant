---
product: campaign
title: 追蹤記錄檔問題
description: 追蹤記錄檔問題
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 13%

---

# 追蹤記錄檔問題{#tracking-logs-issues}



追蹤記錄檔無法轉送的原因有多種。 建議您檢查下列資訊：

* **是否**&#x200B;追蹤&#x200B;**工作流程有錯誤？**

   請參閱 [監控技術工作流程](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **是模組** trackinglogd **在伺服器上執行？**

   請參閱 [記錄檔](../../production/using/log-files.md).

* **是否已進行變更？**

   它們可以使用追蹤別名觸發與伺服器的連線遺失。
