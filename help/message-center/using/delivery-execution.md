---
product: campaign
title: 傳遞執行
description: 深入瞭解異動訊息傳遞執行與監控
feature: Transactional Messaging, Message Center, Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 930c6395-0c00-40ee-a925-3e0cae67c55f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 6%

---

# 傳遞執行 {#delivery-execution}



## 異動訊息傳送 {#transactional-message-send}

在執行例項上，當擴充階段完成並將傳遞範本連結至事件後，就會傳送傳遞。

>[!NOTE]
>
>MTA會優先處理交易式訊息，而非其他傳送。

所有傳遞都會分組在 **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** 資料夾。

![](assets/messagecenter_deliveries_execinstances_001.png)

依預設，它們會依傳送月份排序為子資料夾。 您可以在訊息範本屬性中變更此排序，如下所示。

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>對於託管或混合安裝，如果您已升級至 [增強的MTA](../../delivery/using/sending-with-enhanced-mta.md)，所有異動訊息也可隨Adobe Campaign Enhanced MTA傳送，以改善傳遞能力、吞吐量和退信處理。 所有影響與標準行銷訊息的影響相同。

## 異動訊息監視 {#transactional-message-monitoring}

若要監視異動訊息，請檢查 [傳遞記錄](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

從執行例項傳送的交易式傳遞會透過技術工作流程(**[!UICONTROL Message Center execution instance]**)每小時執行一次。

>[!NOTE]
>
>傳遞每週會根據最新的事件更新累積事件，而不是根據事件建立日期累積事件。 因此，從控制執行個體擷取異動訊息傳送記錄時，與每個傳送記錄ID相關聯的傳送ID可能會隨著記錄更新的時間（例如，當收到事件的入站退回時）而變更。

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

若要監視執行例項的活動和執行中，請參閱 [異動訊息傳送報告](../../message-center/using/about-transactional-messaging-reports.md).
