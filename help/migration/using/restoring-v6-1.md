---
title: 恢復v6.1
seo-title: 恢復v6.1
description: 恢復v6.1
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# 恢復v6.1{#restoring-v}

以下是從v7恢復v6.1的過程。

1. 恢復資料庫的備份並恢復它。
1. 將 **Adobe Campaign v6.back** (**nl6.back)資料夾復原(在Linux中為** nl6.back **)，將它重新命名為** Adobe Campaign v6(在Linux中為&#x200B;**** nl6)，並將它還原至原始位置。
1. 重新指派監聽埠以重新建立IIS網站層級的Adobe Campaign 6.1整合，以重新設定IIS。
1. 停止Adobe Campaign v7服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign 6.1版服務。

