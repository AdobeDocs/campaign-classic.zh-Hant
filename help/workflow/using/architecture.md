---
product: campaign
title: 架構
description: 工作流程由特定模組處理，可在多個伺服器上啟動以共用處理負載
feature: Workflows
hide: true
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
TQID: https://experienceleague.adobe.com/lQLXeSTFhKRCNhA9SdShd9Nyd1mbNt-KPa-XJw-6wAs
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 116
ht-degree: 1%

---

# 架構 {#architecture}



工作流程由特定模組處理。 此模組可以在多個伺服器上啟動，以共用處理負載。

![](assets/architecture.png)

* 「工作流程執行個體執行器」(runwf)流程會執行指定工作流程執行個體的所有工作。 當目前沒有要執行的工作時，它會變成「被動」，也就是說，它會先將狀態儲存到資料庫中，然後停止。
* 「工作流程伺服器」(wfserver)模組會監視目前的工作流程執行個體。 當有任務要執行時，此模組會建立流程以啟動（或重新啟動）對應的執行個體。
