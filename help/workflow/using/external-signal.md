---
title: 外部訊號
description: 進一步瞭解外部信號工作流程活動
page-status-flag: never-activated
uuid: dbe6624a-70cf-4ac4-adfd-bc72db9bb3f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 3739593f-056c-4165-87ef-63c812bd3c43
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---


# 外部訊號{#external-signal}

「外 **部信號** 」活動可讓您觸發工作流中一組任務的執行到調度。

當「外部信號」任務被激活時，它將被無限期暫停，或直到指定時段結束。 其轉場是由SOAP呼叫 **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete)來啟動。** 此參 **[!UICONTROL complete]** 數允許任務完成，因此不會對後續呼叫做出反應。

如需PostEvent函式的詳細資訊，請參閱有關SOAP呼叫的線上檔案。

您可以設定此活動，以在未收到任何訊號時定義事件。 若要這麼做，請編輯活動，然後按一下標 **[!UICONTROL Expiration]** 簽。 按一下 **[!UICONTROL Insert]** 按鈕以建立和設定事件。

![](assets/edit_signal.png)

到期日的設定在到期日中詳 [細說明](../../workflow/using/defining-approvals.md)。

「延 **遲** 」欄位可讓您以選擇的單位指定到期延遲。 請參 [閱等待](../../workflow/using/wait.md)。

每一行代表過期類型，並與轉換一致。

![](assets/external_sign_diag.png)

