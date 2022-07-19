---
product: campaign
title: 外部訊號
description: 瞭解有關外部信號工作流活動的詳細資訊
feature: Workflows
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# 外部訊號{#external-signal}

![](../../assets/v7-only.svg)

的 **外部信號** 「活動」(Activity)，用於觸發工作流中一組任務的執行到調度。

激活「外部信號」任務時，該任務將無限期地暫停或直到指定時間段結束。 其轉換由SOAP調用激活 **PostEvent（sessionToken、workflowId、activity、transition、參數、完成）。** 的 **[!UICONTROL complete]** 參數允許任務完成，因此不會對後續調用做出反應。

有關PostEvent函式的詳細資訊，請參閱有關SOAP調用的聯機文檔。

您可以配置此活動，以便在未收到任何信號時定義事件。 為此，請編輯活動，然後按一下 **[!UICONTROL Expiration]** 頁籤。 按一下 **[!UICONTROL Insert]** 按鈕來建立和配置事件。

![](assets/edit_signal.png)

過期的配置在 [過期](defining-approvals.md)。

的 **延遲** 欄位中，您可以以所選單位指定過期延遲。 請參閱 [等待](wait.md)。

每行表示到期類型，並與過渡一致。

![](assets/external_sign_diag.png)
