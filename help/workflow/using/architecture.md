---
title: 架構
description: 工作流程由特定模組處理，可在多部伺服器上啟動，以共用處理負載。
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---


# 架構 {#architecture}

工作流由特定模組處理。 此模組可在多台伺服器上啟動，以共用處理負載。

![](assets/architecture.png)

* 「工作流實例運行者」(runwf)進程執行給定工作流實例的所有任務。 當目前沒有任務需要執行時，它會變成「被動」，即它將狀態保存在資料庫中，然後停止。
* 「Workflow Server」(wfserver)模組會監控目前的工作流程例項。 當有要執行的任務時，此模組將建立一個過程以激活（或重新激活）相應實例。

