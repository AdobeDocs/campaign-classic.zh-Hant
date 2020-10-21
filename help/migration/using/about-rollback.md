---
title: 回滾到舊版
description: 瞭解如何回滾至舊版
page-status-flag: never-activated
uuid: 9d404ca5-e38c-48ba-b5e0-8e70a40482c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 0e17abea-5e86-43b5-8bca-ee39d9b24c90
translation-type: tm+mt
source-git-commit: 7a3cdf40da579fc3c4c7fc26b10c160543cc45d7
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
1. 將 **Adobe Campaign v6.back** (**nl6.back)資料夾復原(在Linux中為** nl6.back **)，將它重新命名為** Adobe Campaign v6(在Linux中為&#x200B;**** nl6)，並將它還原至原始位置。
1. 重新指派監聽埠以重新建立IIS網站層級的Adobe Campaign 6.1整合，以重新設定IIS。
1. 停止Adobe Campaign v7服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign 6.1版服務。

## 復原至Campaign 6.02版

以下是從v7恢復v6.02的過程。

1. 恢復資料庫的備份並恢復它。
1. 恢復 **Neolane v6.back** (**Linux中為nl6.back** )資料夾，將其更名為 **Neolane v6(Linux中為****** nl6)，並將其恢復到其原始位置。
1. 重新指派監聽埠，以重新建立IIS網站層級的Adobe Campaign 6.02整合，重新設定IIS。
1. 停止Adobe Campaign 6.1版服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign 6.02版服務。

## 復原至Campaign v5.11

以下是從v7恢復v5.11的步驟。

1. 恢復資料庫的備份並恢復它。
1. 恢復 **Neolane v5.back** (**Linux中為nl5.back** )資料夾，將其更名為 **Neolane v5** nl5(Linux中為&#x200B;**** nl5)，並將其恢復到其原始位置。
1. 通過重新分配偵聽埠重新配置IIS ，以重新建立IIS網站級別的Neolane v5整合。
1. 停止Adobe Campaign v7服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign v5服務。
