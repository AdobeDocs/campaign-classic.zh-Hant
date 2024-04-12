---
product: campaign
title: 架構
description: 工作流程由特定模組處理，可在多個伺服器上啟動以共用處理負載
feature: Workflows
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---

# 架構 {#architecture}



工作流程由特定模組處理。 此模組可以在多個伺服器上啟動，以共用處理負載。

![](assets/architecture.png)

* 「工作流程執行個體執行器」(runwf)流程會執行指定工作流程執行個體的所有工作。 當目前沒有要執行的工作時，它會變成「被動」，也就是說，它會先將狀態儲存到資料庫中，然後停止。
* 「工作流程伺服器」(wfserver)模組會監視目前的工作流程執行個體。 當有任務要執行時，此模組會建立流程以啟動（或重新啟動）對應的執行個體。
