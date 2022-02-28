---
product: campaign
title: 關於 Adobe Experience Cloud 觸發程式
description: 開始實施Adobe Experience Cloud Triggers
audience: integrations
content-type: reference
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 0a59b0dbdbe70cf8993ce7153b8f3c049c1f1108
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 8%

---

# 使用市場活動和Experience Cloud觸發器{#about-adobe-experience-triggers}

![](../../assets/common.svg)

[!DNL Triggers] 是Adobe Campaign和Adobe Analytics利用管道的整合。 管道從您的網站檢索用戶的操作或觸發器。 放棄購物車是一個觸發器的例子。 觸發器在Adobe Campaign處理，以便近乎即時地發送電子郵件。

>[!CAUTION]
>
>這項功能無法立即在產品中使用。對於此實施，您首先需要開啟一個具有Adobe支援的票證。 然後，您將能夠執行本中詳述的步驟 [頁](../../integrations/using/configuring-pipeline.md#prerequisites)。

[!DNL Triggers] 在用戶操作後的短時間內運行市場營銷操作。 典型響應時間不到1小時。

它允許更靈活的整合，因為配置最小，不涉及第三方。
它還支援大量流量，而不影響營銷活動的效能。 例如，整合每小時可處理100萬個觸發器。

## [!DNL Triggers] 體系結構 {#triggers-architecture}

的 [!DNL pipelined] 流程始終在Adobe Campaign營銷伺服器上運行。 它連接到管線，檢索事件並立即處理它們。

![](assets/triggers_2.png)

的 [!DNL pipelined] 進程使用身份驗證服務登錄到Experience Cloud併發送私鑰。 驗證服務返回令牌。 檢索事件時，令牌用於進行身份驗證。

有關身份驗證的詳細資訊，請參閱 [頁](../../integrations/using/configuring-adobe-io.md)。
