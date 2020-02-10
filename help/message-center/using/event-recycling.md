---
title: 事件回收
seo-title: 事件回收
description: 事件回收
seo-description: null
page-status-flag: never-activated
uuid: 55624a41-65a1-4759-8087-6e5d2c5c5b62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 568a9dec-5818-4666-b858-aa41fe827b92
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 事件回收{#event-recycling}

如果特定渠道上的訊息傳送失敗，Adobe Campaign可以使用不同的渠道重新傳送訊息。 例如，如果SMS頻道上的傳送失敗，則會使用電子郵件頻道重新傳送訊息。

若要這麼做，您必須設定工作流程，以重新建立具有「傳送錯誤」狀態的所有 **事件** ，並指派不同的渠道給這些事件。

>[!CAUTION]
>
>此步驟只能使用工作流程執行，因此保留給專家用戶。 如需詳細資訊，請聯絡Adobe銷售代表。

