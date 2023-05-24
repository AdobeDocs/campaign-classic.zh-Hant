---
product: campaign
title: 回覆至上一個版本
description: 瞭解如何回覆至先前的版本
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: migration
content-type: reference
topic-tags: rollback
hide: true
hidefromtoc: true
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# 回覆至上一個版本{#about-rollback}



移轉後，如果發生問題，您可能需要復原至舊版Campaign。

復原程式取決於您的Campaign初始版本。

以下是從v7還原v6.1的程式。

1. 復原資料庫備份並還原。
1. 復原 **Adobe Campaign v6.back** 資料夾(**nl6.back** （在Linux中），將其重新命名為 **Adobe Campaign v6** (**nl6** （在Linux中）並將它還原至其原始位置。
1. 透過重新指派監聽連線埠來重新設定IIS，以便在IIS網站層級重新建立Adobe Campaign v6.1的整合。
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