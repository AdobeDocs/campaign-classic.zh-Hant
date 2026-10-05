---
product: campaign
title: 追蹤記錄檔問題
description: 追蹤記錄檔問題
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 58656aa1-aa95-451f-80b8-9e2d28223056
TQID: 'https://experienceleague.adobe.com/9u8xqAINLPKmeptZOZf94Ms-GiEciCL4nFBaw7SjRss'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 24%
---
# 追蹤記錄檔問題{#tracking-logs-issues}



未轉送追蹤記錄的原因有好幾種。 建議您檢視下列資訊：

* **&#x200B;**&#x200B;追蹤&#x200B;**工作流程是否有錯誤？**

請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=zh-Hant){target="_blank"}。

![](assets/tracking_scheduled_task.png)

* **模組** trackinglogd **是否正在伺服器上執行？**

  請參閱[記錄檔](../../production/using/log-files.md)。

* **已進行變更嗎？**

  使用追蹤別名時，它們可能會觸發與伺服器的連線中斷。
