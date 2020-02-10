---
title: 恢復v6.02
seo-title: 恢復v6.02
description: 恢復v6.02
seo-description: null
page-status-flag: never-activated
uuid: df21209b-4825-42fa-a303-f383f872abb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 4f65ba19-e9f0-4425-b640-f27c61394859
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# 恢復v6.02{#restoring-v}

以下是從v7恢復v6.02的步驟。

1. 恢復資料庫的備份並恢復它。
1. 恢復 **Neolane v6.back** (**Linux中為nl6.back** )資料夾，將其更名為 **Neolane v6(Linux中為****** nl6)，並將其恢復到其原始位置。
1. 重新指派監聽埠，以重新建立IIS網站層級的Adobe Campaign 6.02整合，重新設定IIS。
1. 停止Adobe Campaign 6.1版服務。
1. 重新啟動IIS。
1. 重新啟動Adobe Campaign 6.02版服務。

