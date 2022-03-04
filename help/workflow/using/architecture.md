---
product: campaign
title: 架構
description: 工作流由特定模組處理，該模組可以在多個伺服器上啟動，以共用處理負載。
feature: Workflows
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---

# 架構 {#architecture}

![](../../assets/common.svg)

工作流由特定模組處理。 此模組可以在多個伺服器上啟動，以共用處理負載。

![](assets/architecture.png)

* 「工作流實例運行程式」(runwf)進程執行給定工作流實例的所有任務。 當暫時沒有要執行的任務時，它就變為「被動」，即它將其狀態保存在資料庫中，然後停止。
* 「工作流伺服器」(wfserver)模組監視當前工作流實例。 當有要執行的任務時，此模組將建立一個過程以激活（或重新激活）相應實例。
