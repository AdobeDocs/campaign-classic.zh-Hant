---
product: campaign
title: 回復到以前的版本
description: 了解如何回復至舊版
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# 回復到以前的版本{#about-rollback}

![](../../assets/v7-only.svg)

移轉後，若有問題，您可能需要回復至舊版的Campaign。

回滾程式取決於您的Campaign初始版本。

## 還原至Campaign v6.1

以下是從v7還原v6.1的步驟。

1. 恢復資料庫的備份並恢復它。
1. 恢復 **Adobe Campaign v6.back** 資料夾(**nl6.back** 在Linux中)，將其重新命名為 **Adobe Campaign v6** (**nl6** 在Linux中)，並將其還原到原始位置。
1. 通過重新分配監聽埠重新配置IIS，以重新建立Adobe Campaign v6.1在IIS網站級別的整合。
1. 停止Adobe Campaign v7服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign v6.1服務。

## 還原至Campaign v6.02

以下是從v7還原v6.02的步驟。

1. 恢復資料庫的備份並恢復它。
1. 恢復 **Neolane v6.back** 資料夾(**nl6.back** 在Linux中)，將其重新命名為 **Neolane v6** (**nl6** 在Linux中)，並將其還原到原始位置。
1. 通過重新分配監聽埠來重新配置IIS，以重新建立Adobe Campaign v6.02在IIS網站級別的整合。
1. 停止Adobe Campaign v6.1服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign v6.02服務。

## 還原至Campaign v5.11

以下是從v7還原v5.11的過程。

1. 恢復資料庫的備份並恢復它。
1. 恢復 **Neolane v5.back** 資料夾(**nl5.back** 在Linux中)，將其重新命名為 **Neolane v5** (**nl5** 在Linux中)，並將其還原到原始位置。
1. 通過重新分配偵聽埠重新配置IIS，以在IIS網站級別重新建立Neolane v5的整合。
1. 停止Adobe Campaign v7服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign v5服務。
