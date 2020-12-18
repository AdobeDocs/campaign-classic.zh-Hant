---
solution: Campaign Classic
product: campaign
title: 外部訊號
description: 進一步瞭解外部信號工作流程活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---


# 外部訊號{#external-signal}

**外部信號**&#x200B;活動可讓您觸發工作流中一組任務的執行到調度。

當「外部信號」任務被激活時，它將被無限期暫停，或直到指定時段結束。 其轉場是由SOAP呼叫&#x200B;**PostEvent(sessionToken, workflowId, activity, transition, parameters, complete)所啟動。** 此參 **[!UICONTROL complete]** 數允許任務完成，因此不會對後續呼叫做出反應。

如需PostEvent函式的詳細資訊，請參閱有關SOAP呼叫的線上檔案。

您可以設定此活動，以在未收到任何訊號時定義事件。 若要這麼做，請編輯活動，然後按一下&#x200B;**[!UICONTROL Expiration]**&#x200B;標籤。 按一下&#x200B;**[!UICONTROL Insert]**&#x200B;按鈕以建立和配置事件。

![](assets/edit_signal.png)

過期的配置詳見[過期](../../workflow/using/defining-approvals.md)。

**延遲**&#x200B;欄位可讓您以選擇的單位指定到期延遲。 請參閱[等待](../../workflow/using/wait.md)。

每一行代表過期類型，並與轉換一致。

![](assets/external_sign_diag.png)

