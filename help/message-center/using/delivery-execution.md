---
solution: Campaign Classic
product: campaign
title: 傳遞執行
description: 傳遞執行
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 5bc6c8a824929c6a61cf562fc961e5bdd1867837
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 8%

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
>若是代管或混合式安裝，如果您已升級至「增強MTA」，所有交易訊息也可能會隨Adobe Campaign Enhanced MTA一起傳送，以改善傳遞能力、吞吐量和彈回處理。 所有影響與標準行銷訊息的影響相同，並詳見[Adobe Campaign Enhanced MTA](https://helpx.adobe.com/tw/campaign/kb/acc-campaign-enhanced-mta.html)檔案。

<!--## Transactional message monitoring {#transactional-message-monitoring}

To monitor your transactional messages, check the delivery logs. Accessing the delivery logs is presented in [this section](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history).

The transactional deliveries sent from the execution instance are synchronized back to the control instance as follows.

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