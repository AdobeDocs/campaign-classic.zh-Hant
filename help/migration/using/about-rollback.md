---
solution: Campaign Classic
product: campaign
title: 回滾到舊版
description: 瞭解如何回滾至舊版
audience: migration
content-type: reference
topic-tags: rollback
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# 回滾到舊版{#about-rollback}

在移轉後，若有問題，您可能需要回滾至舊版的Campaign。

回滾過程取決於您的Campaign初始版本。

## 回復 v6.1

以下是從v7恢復v6.1的過程。

1. 恢復資料庫的備份並恢復它。
1. 恢復&#x200B;**Adobe Campaign v6.back**&#x200B;資料夾（Linux中為&#x200B;**nl6.back**），將其重新命名為&#x200B;**Adobe Campaign v6**（Linux中為&#x200B;**nl6**），並將其還原至其原始位置。
1. 重新指派監聽埠以重新建立IIS網站層級的Adobe Campaign 6.1整合，以重新設定IIS。
1. 停止Adobe Campaign v7服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign 6.1版服務。

## 復原至Campaign 6.02版

以下是從v7恢復v6.02的過程。

1. 恢復資料庫的備份並恢復它。
1. 恢復&#x200B;**Neolane v6.back**&#x200B;資料夾（Linux中為&#x200B;**nl6.back**），將其更名為&#x200B;**Neolane v6**（Linux中為&#x200B;**nl6**），並將其恢復到其原始位置。
1. 重新指派監聽埠，以重新建立IIS網站層級的Adobe Campaign 6.02整合，重新設定IIS。
1. 停止Adobe Campaign 6.1版服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign 6.02版服務。

## 復原至Campaign v5.11

以下是從v7恢復v5.11的步驟。

1. 恢復資料庫的備份並恢復它。
1. 恢復&#x200B;**Neolane v5.back**&#x200B;資料夾（Linux中為&#x200B;**nl5.back**），將其更名為&#x200B;**Neolane v5**（Linux中為&#x200B;**nl5**），並將其恢復到其原始位置。
1. 通過重新分配偵聽埠重新配置IIS ，以重新建立IIS網站級別的Neolane v5整合。
1. 停止Adobe Campaign v7服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign v5服務。
