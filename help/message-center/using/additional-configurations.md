---
product: campaign
title: 其他設定
description: 了解如何在Adobe Campaign Classic中為交易式訊息設定其他設定
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 7%

---

# 其他設定 {#mc-additional-configurations}



## 監視臨界值 {#monitoring-thresholds}

您可以設定顯示在 **訊息中心服務層級** 和 **訊息中心處理時間** 報表(請參閱 [存取交易式訊息報表](../../message-center/using/about-transactional-messaging-reports.md))。

要執行此操作，請遵循下列步驟：

1. 在 **執行實例**.

1. 前往 **[!UICONTROL Message Center]** 頁面。

1. 使用箭頭更改閾值。

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>佇列中待處理的事件數會顯示在 [系統指標](../../production/using/monitoring-processes.md#system-indicators) 區段(位於「Adobe Campaign程式監控」頁面)。 有關部署嚮導的詳細資訊，請參閱 [本節](../../installation/using/deploying-an-instance.md#deployment-wizard).

## 清除事件 {#purging-events}

您可以使用 [部署精靈](../../production/using/database-cleanup-workflow.md#deployment-wizard) 配置資料儲存在資料庫中的時間。

事件清除會由 [資料庫清理工作流程](../../production/using/database-cleanup-workflow.md). 此工作流程會清除在執行執行個體上收到和儲存的事件，以及封存在控制執行個體上的事件。

視需要使用箭頭來更改清除設定。

控制實例上的事件清除設定：

![](assets/messagecenter_delete_events_001.png)

執行實例上的事件清除設定：

![](assets/messagecenter_delete_events_002.png)

如需資料庫清理工作流程的詳細資訊，請參閱 [本節](../../production/using/database-cleanup-workflow.md).


## 技術工作流程 {#technical-workflows}

部署任何交易式訊息範本之前，您必須確定已建立並啟動控制執行個體和不同執行例項的技術工作流程。

與交易式訊息傳送（訊息中心）相關的各種技術工作流程會在控制執行個體和執行執行個體之間劃分。

### 控制執行個體工作流程 {#control-instance-workflows}

在控制實例上，無論您註冊了一個或多個執行實例，都必須為每個實例建立一個存檔工作流 **[!UICONTROL Message Center execution instance]** 外部帳戶。 按一下 **[!UICONTROL Create the archiving workflow]** 按鈕來建立和啟動工作流。

![](assets/messagecenter_archiving_002.png)

然後，您就可以從 **管理>生產>訊息中心** 檔案夾。 建立後，會自動啟動封存工作流程。

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

### 執行執行個體工作流程 {#execution-instance-workflows}

在執行例項上，交易式訊息的技術工作流程可從 **管理>生產>訊息中心** 檔案夾。 你只需要開始。 清單中的工作流程為：

* **[!UICONTROL Processing batch events]** (內部名稱： **[!UICONTROL batchEventsProcessing]** ):此工作流程可讓您在將批次事件連結至訊息範本之前，先劃分佇列中的批次事件。
* **[!UICONTROL Processing real time events]** (內部名稱： **[!UICONTROL rtEventsProcessing]** ):此工作流程可讓您在將佇列中的即時事件連結至訊息範本之前，先加以劃分。
* **[!UICONTROL Update event status]** (內部名稱： **[!UICONTROL updateEventStatus]** ):此工作流程可讓您將狀態歸因於事件。

   可使用下列事件狀態：

   * **[!UICONTROL Pending]** :事件在佇列中。 尚未為其指派訊息範本。
   * **[!UICONTROL Pending delivery]** :事件在佇列中，已指派訊息範本給該事件，並由傳送處理。
   * **[!UICONTROL Sent]** :此狀態是從傳送記錄檔複製而來。 這表示已傳送傳遞。
   * **[!UICONTROL Ignored by the delivery]** :此狀態是從傳送記錄檔複製而來。 這表示會由傳送忽略。
   * **[!UICONTROL Delivery failed]** :此狀態是從傳送記錄檔複製而來。 這表示傳送失敗。
   * **[!UICONTROL Event not taken into account]** :無法將事件連結到消息模板。 將不會處理事件。

## 設定多品牌 {#configuring-multibranding}

本節說明一個解決方案，可針對Adobe Campaign中的交易式訊息，依品牌設定追蹤和鏡像頁面URL。

### 必要條件 {#prerequisites}

* 必須將所有主機新增至執行個體的設定檔案(`config-<instance>.xml`)。
* 必須為每個品牌指派子網域。
* 如果已在HTTPS頁面上完成網頁追蹤，則所有品牌都必須具備HTTPS憑證。

若要設定多品牌，您需要同時設定執行例項和控制例項。

### 執行實例 {#execution-instance}

在執行例項上，請遵循下列步驟：

1. 為每個品牌建立一個外部帳戶。

   >[!NOTE]
   >
   >了解如何在中建立執行執行執行個體類型外部帳戶 [本節](../../message-center/using/configuring-instances.md#control-instance).

1. 擴充nms:extAccount架構以新增追蹤URL:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >了解如何在 [擴充結構](../../configuration/using/extending-a-schema.md) 區段。

1. 修改nms:extAccount表單：

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. 修改NmsTracking_OpenFormul和NmsTracking_ClickFormula選項以使用外部帳戶而非全域選項。

   若要這麼做，請取代：

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   包含：

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >這些變更在升級時可能會導致衝突。 您可能需要手動將這些公式與其新版本合併。

### 控制實例 {#control-instance}

在控制執行個體上，您需要連結傳遞範本和外部帳戶。

要執行此操作，請遵循下列步驟：

1. 以與上定義的相同內部名稱，為每個品牌建立一個外部帳戶 [執行實例](#execution-instance) （步驟1）。

1. 為每個品牌建立一個預設傳送範本。

   >[!NOTE]
   >
   >    了解如何在 [本節](../../delivery/using/creating-a-delivery-template.md#creating-a-new-template).

1. 在傳送範本的 **[!UICONTROL Properties]**，設定品牌外部帳戶的路由。
