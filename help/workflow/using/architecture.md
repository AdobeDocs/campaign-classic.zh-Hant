---
product: campaign
title: 架構
description: 工作流程由特定模組處理，可在多個伺服器上啟動，以共用處理負載
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

* 「工作流實例運行程式」(runwf)進程會執行給定工作流實例的所有任務。 當暫時沒有要執行的任務時，它就會變成「被動」，即它將其狀態保存在資料庫中，然後停止。
* 「工作流伺服器」(wfserver)模組會監控目前的工作流程例項。 當有要執行的任務時，此模組會建立一個程式以啟動（或重新啟用）對應的執行個體。
