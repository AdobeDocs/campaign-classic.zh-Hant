---
solution: Campaign Classic
product: campaign
title: 事件回收
description: 事件回收
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# 事件回收{#event-recycling}

如果特定渠道上的訊息傳送失敗，Adobe Campaign可以使用不同的渠道重新傳送訊息。 例如，如果SMS頻道上的傳送失敗，則會使用電子郵件頻道重新傳送訊息。

為此，您需要設定工作流程，重新建立所有具有&#x200B;**傳送錯誤**&#x200B;狀態的事件，並為其指派不同的頻道。

>[!CAUTION]
>
>此步驟只能使用工作流程執行，因此保留給專家用戶。 如需詳細資訊，請聯絡Adobe銷售代表。

