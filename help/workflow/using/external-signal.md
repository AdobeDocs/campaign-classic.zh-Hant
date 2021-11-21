---
product: campaign
title: 外部訊號
description: 深入了解外部訊號工作流程活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# 外部訊號{#external-signal}

![](../../assets/common.svg)

此 **外部信號** 活動可讓您觸發在工作流程中對排程執行一組任務。

「外部信號」任務激活後，將無限期暫停，或直到指定時段結束。 其轉變由SOAP呼叫啟動 **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete)。** 此 **[!UICONTROL complete]** 參數可讓任務完成，因此不會對後續呼叫做出反應。

有關PostEvent函式的詳細資訊，請參閱有關SOAP呼叫的線上檔案。

您可以設定此活動，以便在未收到任何訊號時定義事件。 若要這麼做，請編輯活動並按一下 **[!UICONTROL Expiration]** 標籤。 按一下 **[!UICONTROL Insert]** 按鈕來建立和設定事件。

![](assets/edit_signal.png)

到期日的設定在 [過期](defining-approvals.md).

此 **延遲** 欄位可讓您以選擇的單位指定到期延遲。 請參閱 [等待](wait.md).

每行代表過期類型，並與轉變一致。

![](assets/external_sign_diag.png)
