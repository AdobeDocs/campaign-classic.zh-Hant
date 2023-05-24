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



追蹤記錄檔未轉送可能有多種原因。 建議您檢視下列資訊：

* **此**&#x200B;追蹤&#x200B;**工作流程有錯誤？**

   請參閱 [監控技術工作流程](../../workflow/using/monitoring-technical-workflows.md).

   ![](assets/tracking_scheduled_task.png)

* **為模組** trackinglogd **是否正在伺服器上執行？**

   請參閱 [記錄檔](../../production/using/log-files.md).

* **有變更嗎？**

   使用追蹤別名時，它們可能會觸發與伺服器的連線中斷。
