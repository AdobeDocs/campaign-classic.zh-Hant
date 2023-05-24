---
product: campaign
title: 架構
description: 工作流程由特定模組處理，該模組可在多個伺服器上啟動，以共用處理負載
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---

# 架構 {#architecture}



工作流程由特定模組處理。 此模組可在多個伺服器上啟動，以共用處理負載。

![](assets/architecture.png)

* 「工作流程例項執行器」(runwf)程式會執行指定工作流程例項的所有工作。 當目前沒有要執行的作業時，它會變成「被動」，也就是說，它會先將狀態儲存在資料庫中，然後停止。
* 「工作流程伺服器」(wfserver)模組會監視目前的工作流程執行個體。 當有任務要執行時，此模組會建立流程以啟動（或重新啟動）對應的執行個體。
