---
solution: Campaign Classic
product: campaign
title: 技術工作流程
description: 技術工作流程
audience: message-center
content-type: reference
topic-tags: instance-configuration
translation-type: tm+mt
source-git-commit: d1130691e40c0cac183db37a4c0b410d00bb696a
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 11%

---


# 技術工作流程{#technical-workflows}

在部署任何事務性消息模板之前，您必須確保已建立並啟動控制實例和不同執行實例的技術工作流。

與事務性消息傳遞（消息中心）相關的各種技術工作流在控制實例和執行實例之間被劃分。

## 控制例項工作流程{#control-instance-workflows}

在控制實例上，無論您註冊了一個或多個執行實例，都必須為每個&#x200B;**[!UICONTROL Message Center execution instance]**&#x200B;外部帳戶建立一個歸檔工作流。 按一下&#x200B;**[!UICONTROL Create the archiving workflow]**&#x200B;按鈕以建立並啟動工作流。

![](assets/messagecenter_archiving_002.png)

然後，可從&#x200B;**管理>生產>消息中心**&#x200B;資料夾訪問這些工作流。 建立後，封存工作流程就會自動啟動。

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

## 執行例項工作流{#execution-instance-workflows}

在執行實例上，可從&#x200B;**管理>生產>消息中心**&#x200B;資料夾訪問事務性消息傳遞的技術工作流。 你只需要開始。 清單中的工作流程包括：

* **[!UICONTROL Processing batch events]** (內部名稱： **[!UICONTROL batchEventsProcessing]** ):此工作流程可讓您在將批次事件連結至訊息範本之前，先在佇列中加以劃分。
* **[!UICONTROL Processing real time events]** (內部名稱： **[!UICONTROL rtEventsProcessing]** ):此工作流程可讓您在將即時事件連結至訊息範本之前，先在佇列中加以劃分。
* **[!UICONTROL Update event status]** (內部名稱： **[!UICONTROL updateEventStatus]** ):此工作流程可讓您將狀態歸因於事件。

   可使用下列事件狀態：

   * **[!UICONTROL Pending]** :事件在隊列中。尚未為其指派訊息範本。
   * **[!UICONTROL Pending delivery]** :事件在佇列中，已指派訊息範本給該事件，且傳送正在處理該事件。
   * **[!UICONTROL Sent]** :此狀態會從傳送記錄複製。這表示傳送已傳送。
   * **[!UICONTROL Ignored by the delivery]** :此狀態會從傳送記錄複製。這表示會由傳送忽略。
   * **[!UICONTROL Delivery failed]** :此狀態會從傳送記錄複製。這表示傳送失敗。
   * **[!UICONTROL Event not taken into account]** :事件無法連結至訊息範本。將不會處理事件。
