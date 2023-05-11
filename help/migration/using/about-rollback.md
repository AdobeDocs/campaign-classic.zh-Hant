---
product: campaign
title: 回復到以前的版本
description: 了解如何回復至舊版
audience: migration
content-type: reference
topic-tags: rollback
hide: true
hidefromtoc: true
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 80cf56e330731237d5e7b394381b737f30f8b350
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# 回復到以前的版本{#about-rollback}

![](../../assets/v7-only.svg)

移轉後，若有問題，您可能需要回復至舊版的Campaign。

回滾程式取決於您的Campaign初始版本。

以下是從v7還原v6.1的步驟。

1. 恢復資料庫的備份並恢復它。
1. 恢復 **Adobe Campaign v6.back** 資料夾(**nl6.back** 在Linux中)，將其重新命名為 **Adobe Campaign v6** (**nl6** 在Linux中)，並將其還原到原始位置。
1. 通過重新分配監聽埠重新配置IIS，以重新建立Adobe Campaign v6.1在IIS網站級別的整合。
1. 停止Adobe Campaign v7服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign v6.1服務。

<!--
	
## Restore to Campaign v6.02

Here is the procedure to restore a v6.02 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v6.back** folder (**nl6.back** in Linux), rename it to **Neolane v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.02 at IIS Website level.
1. Stop the Adobe Campaign v6.1 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.02 service.

## Restore to Campaign v5.11

Here is the procedure to restore a v5.11 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v5.back** folder (**nl5.back** in Linux), rename it to **Neolane v5** (**nl5** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Neolane v5 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Re-start the Adobe Campaign v5 service.

-->