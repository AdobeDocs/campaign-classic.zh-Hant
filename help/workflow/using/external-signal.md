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

**外部訊號**&#x200B;活動可讓您觸發在工作流程中對排程執行一組任務。

「外部信號」任務激活後，將無限期暫停，或直到指定時段結束。 其轉變是由SOAP呼叫&#x200B;**PostEvent(sessionToken, workflowId, activity, transition, parameters, complete)啟動。** 參 **[!UICONTROL complete]** 數可讓任務完成，因此不會對後續呼叫做出反應。

有關PostEvent函式的詳細資訊，請參閱有關SOAP呼叫的線上檔案。

您可以設定此活動，以便在未收到任何訊號時定義事件。 要執行此操作，請編輯活動，然後按一下&#x200B;**[!UICONTROL Expiration]**&#x200B;標籤。 按一下&#x200B;**[!UICONTROL Insert]**&#x200B;按鈕以建立和配置事件。

![](assets/edit_signal.png)

有效期的設定在[有效期](defining-approvals.md)中詳細說明。

**Delay**&#x200B;欄位可讓您以所選單位指定到期延遲。 請參閱[Wait](wait.md)。

每行代表過期類型，並與轉變一致。

![](assets/external_sign_diag.png)
