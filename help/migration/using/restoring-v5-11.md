---
title: 回復 v5.11
seo-title: 回復 v5.11
description: 回復 v5.11
seo-description: null
page-status-flag: never-activated
uuid: 4480c97c-5845-483c-a17b-644f05783b4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: ef778333-8e50-402b-9a69-78ac94497c67
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 9%

---


# 回復 v5.11{#restoring-v}

以下是從v7恢復v5.11的步驟。

1. 恢復資料庫的備份並恢復它。
1. 恢復 **Neolane v5.back** (**Linux中為nl5.back** )資料夾，將其更名為 **Neolane v5** nl5(Linux中為&#x200B;**** nl5)，並將其恢復到其原始位置。
1. 通過重新分配偵聽埠重新配置IIS ，以重新建立IIS網站級別的Neolane v5整合。
1. 停止Adobe Campaign v7服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign v5服務。

