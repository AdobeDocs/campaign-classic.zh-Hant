---
product: campaign
title: 架構
description: 工作流程由特定模組處理，可在多個伺服器上啟動以共用處理負載
feature: Workflows
hide: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
TQID: 'https://experienceleague.adobe.com/lQLXeSTFhKRCNhA9SdShd9Nyd1mbNt-KPa-XJw-6wAs'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%
---
# 架構 {#architecture}



工作流程由特定模組處理。 此模組可以在多個伺服器上啟動，以共用處理負載。

![](assets/architecture.png)

* 「工作流程執行個體執行器」(runwf)流程會執行指定工作流程執行個體的所有工作。 當目前沒有要執行的工作時，它會變成「被動」，也就是說，它會先將狀態儲存到資料庫中，然後停止。
* 「工作流程伺服器」(wfserver)模組會監視目前的工作流程執行個體。 當有任務要執行時，此模組會建立流程以啟動（或重新啟動）對應的執行個體。
