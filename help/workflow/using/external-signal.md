---
product: campaign
title: 外部訊號
description: 進一步瞭解外部訊號工作流程活動
feature: Workflows
hide: true
hidefromtoc: true
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# 外部訊號{#external-signal}



**外部訊號**&#x200B;活動可讓您觸發執行工作流程中的一組工作至排程。

「外部訊號」任務啟動時，會無限期暫停或直到指定時段結束。 其轉變由SOAP呼叫&#x200B;**PostEvent(sessionToken， workflowId， activity， transition， parameters， complete)啟動。** **[!UICONTROL complete]**&#x200B;引數允許工作完成，因此不會回應後續的呼叫。

如需有關PostEvent函式的進一步資訊，請參閱有關SOAP呼叫的線上檔案。

您可以設定此活動，以便在未收到訊號時定義事件。 若要這麼做，請編輯活動並按一下&#x200B;**[!UICONTROL Expiration]**&#x200B;標籤。 按一下&#x200B;**[!UICONTROL Insert]**&#x200B;按鈕以建立及設定事件。

![](assets/edit_signal.png)

有效期的設定在[有效期](defining-approvals.md)中詳細說明。

**延遲**&#x200B;欄位可讓您以您選擇的單位指定到期延遲。 請參閱[等待](wait.md)。

每行代表一種到期型別，並與轉換重合。

![](assets/external_sign_diag.png)
