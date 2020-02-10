---
title: 追蹤記錄檔問題
seo-title: 追蹤記錄檔問題
description: 追蹤記錄檔問題
seo-description: null
page-status-flag: never-activated
uuid: 996869c4-7ffe-4fcc-9555-1d8b65e93e87
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 1b9ff479-4847-408d-a5c2-9a164805081f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# 追蹤記錄檔問題{#tracking-logs-issues}

追蹤記錄無法轉送的原因可能有多種。 建議您檢查下列資訊：

* 追蹤工 **作流程** 是否有錯誤？

   請參閱「監 [控技術工作流程](../../workflow/using/monitoring-technical-workflows.md)」。

   ![](assets/tracking_scheduled_task.png)

* 在伺服器上 **運行的模組** trackinglogd是否正在運行？

   請參閱 [記錄檔](../../production/using/log-files.md)。

* 是否進行了更改？ 它們可以使用追蹤別名觸發與伺服器的連線中斷。

