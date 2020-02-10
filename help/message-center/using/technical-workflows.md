---
title: 技術工作流程
seo-title: 技術工作流程
description: 技術工作流程
seo-description: null
page-status-flag: never-activated
uuid: dfd1b180-86b5-4740-9bad-a0e210f433c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2e648e63-06d2-4e8f-9934-066a41d18eac
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 技術工作流程{#technical-workflows}

在部署任何事務性消息模板之前，您必須確保已建立並啟動控制實例和不同執行實例的技術工作流。

與事務性消息傳遞（消息中心）相關的各種技術工作流在控制實例和執行實例之間被劃分。

## 控制例項工作流程 {#control-instance-workflows}

在控制實例上，每個執行實例必須建立一個歸檔工作流。 然後，您可從「管理>生產>訊息中 **心」資料夾存取封存工作流程** 。 建立後，封存工作流程就會自動啟動。

**分佈式體系結構**

如果您註冊了一個或多個執行實例，則必須在控制實例上為每個外部帳戶建立一個歸 **[!UICONTROL Message Center execution instance]** 檔工作流。 按一下 **[!UICONTROL Create the archiving workflow]** 按鈕以建立並啟動工作流程。

![](assets/messagecenter_archiving_002.png)

**最低架構**

在將控制和執行模組安裝在同一實例上後，您必須使用部署嚮導建立歸檔工作流。 按一下 **[!UICONTROL Create the archiving workflow]** 按鈕以建立並啟動工作流程。

![](assets/messagecenter_archiving_001.png)

## 執行例項工作流程 {#execution-instance-workflows}

在執行實例上，可從「管理」>「生產」>「消息中心」資料夾訪問事務 **性消息傳遞的技術工作流** 。 你只需要開始。 清單中的工作流程包括：

* **[!UICONTROL Processing batch events]** (內部名稱： **[!UICONTROL batchEventsProcessing]** ):此工作流程可讓您在將批次事件連結至訊息範本之前，先在佇列中加以劃分。
* **[!UICONTROL Processing real time events]** (內部名稱： **[!UICONTROL rtEventsProcessing]** ):此工作流程可讓您在將即時事件連結至訊息範本之前，先在佇列中加以劃分。
* **[!UICONTROL Update event status]** (內部名稱： **[!UICONTROL updateEventStatus]** ):此工作流程可讓您將狀態歸因於事件。

   可使用下列事件狀態：

   * **[!UICONTROL Pending]** :事件在隊列中。 尚未為其指派消息模板。
   * **[!UICONTROL Pending delivery]** :事件在佇列中，已指派訊息範本給該事件，且傳送正在處理該事件。
   * **[!UICONTROL Sent]** :此狀態會從傳送記錄複製。 這表示傳送已傳送。
   * **[!UICONTROL Ignored by the delivery]** :此狀態會從傳送記錄複製。 這表示傳送被忽略。
   * **[!UICONTROL Delivery failed]** :此狀態會從傳送記錄複製。 這意味著交付失敗。
   * **[!UICONTROL Event not taken into account]** :事件無法連結至訊息範本。 不會處理事件。

