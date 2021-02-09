---
solution: Campaign Classic
product: campaign
title: 傳遞執行
description: 傳遞執行
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: fd6195ca447fa0345189f3153f44ad2f9a067210
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 7%

---


# 傳遞執行{#delivery-execution}

## 事務性消息發送{#transactional-message-send}

在執行例項上，一旦濃縮階段完成且傳送範本已連結至事件，傳送。

>[!NOTE]
>
>MTA會優先處理交易訊息，而非其他傳送。

所有傳送都會分組在&#x200B;**[!UICONTROL Administration > Production > Message Center > Default > Deliveries]**&#x200B;資料夾中。

![](assets/messagecenter_deliveries_execinstances_001.png)

依預設，會依傳送月份將它們排序為子資料夾。 可以在消息模板屬性中更改此排序，如下所示。

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>對於代管或混合式安裝，如果您已升級至[增強型MTA](../../delivery/using/sending-with-enhanced-mta.md)，所有交易訊息也可隨Adobe Campaign增強型MTA傳送，以改善傳遞能力、總處理能力和彈回處理。 所有影響與標準行銷訊息的影響相同。

## 事務性消息監視{#transactional-message-monitoring}

要監視事務性消息，請檢查發送日誌。 存取傳送記錄檔的方式見[本節](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)。

從執行實例發送的事務傳送通過每小時運行的技術工作流(**[!UICONTROL Message Center execution instance]**)同步回控制實例。

>[!NOTE]
>
>每週傳送會根據最新事件更新累積事件，而非根據事件建立日期。 因此，當從控制實例提取事務性消息傳送日誌時，與每個傳送日誌ID相關聯的傳送ID可隨著日誌更新而隨時間變化（例如，當接收到事件的傳入彈回數時）。

<!--The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

Let's take a [delivery template](../../message-center/using/introduction.md) labelled *Template_1*.

1. An event corresponding to *Template_1* is received on the execution instance.
1. The **Processing real time events** (rtEventsProcessing) workflow processes the event and searches for an existing delivery for the current month.

    >[!NOTE]
    >
    >If not found, a new delivery is created and the event is assigned to the new delivery.

1. The transactional email is sent and the delivery status changes to **[!UICONTROL Sent]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and updates the delivery logs on the control instance.
1. The control instance searches for an existing delivery for week 40 (2020-09-28_Template_1).

    >[!NOTE]
    >
    >If not found, a new delivery is created.

1. The week after, an inbound bounce is received for the event.
1. The status of the event changes to **[!UICONTROL Delivery failed]**.
1. The **Message Center execution instance** (mcSync_mcExec) workflow retrieves the delivery logs from the execution instance and searches for a delivery for week 41 (2020-10-05_Template_1) to update the delivery logs. The delivery logs are then linked to a new delivery for the current week.

To summarize, the deliveries weekly accumulate the events based on the latest event update, and not on the event creation date.

Therefore, when extracting transactional messaging delivery logs from the control instance, the delivery ID associated with each delivery log ID changes every week.-->