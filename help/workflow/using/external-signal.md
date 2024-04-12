---
product: campaign
title: 外部訊號
description: 進一步瞭解外部訊號工作流程活動
feature: Workflows
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# 外部訊號{#external-signal}



此 **外部訊號** 活動可讓您在工作流程中觸發執行排程的一組任務。

「外部訊號」任務啟動時，會無限期暫停或直到指定時段結束。 其轉變會由SOAP呼叫啟動 **PostEvent(sessionToken， workflowId， activity， transition， parameters， complete)。** 此 **[!UICONTROL complete]** 引數可讓工作完成，使其不會回應後續呼叫。

如需有關PostEvent函式的進一步資訊，請參閱有關SOAP呼叫的線上檔案。

您可以設定此活動，以便在未收到訊號時定義事件。 若要這麼做，請編輯活動並按一下 **[!UICONTROL Expiration]** 標籤。 按一下 **[!UICONTROL Insert]** 按鈕以建立和設定事件。

![](assets/edit_signal.png)

有關過期的設定詳情，請參閱 [有效期](defining-approvals.md).

此 **延遲** 欄位可讓您以所選擇的單位指定到期延遲。 另請參閱 [等待](wait.md).

每行代表一種到期型別，並與轉換重合。

![](assets/external_sign_diag.png)
