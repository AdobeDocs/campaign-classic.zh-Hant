---
product: campaign
title: 傳遞儀表板
description: 瞭解有關如何使用交貨控制板監控交貨的更多資訊
feature: Monitoring
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 4%

---

# 傳遞儀表板 {#delivery-dashboard}

![](../../assets/common.svg)

的 **交貨儀表板** 是監控您的交貨以及在發送郵件時遇到的最終問題的關鍵。

它允許您檢索有關交貨的資訊，並在必要時對其進行編輯。 請注意，一旦發送了交貨，標籤內容就不能再更改。

以下是可以使用儀表板中提供的幾個頁籤監視的資訊：

* [傳遞摘要](#delivery-summary)
* [傳遞報告](#delivery-reports)
* [交付日誌、鏡像頁、排除](#delivery-logs-and-history)
* [傳遞跟蹤日誌和歷史記錄](#tracking-logs)
* [交付呈現](#delivery-rendering)
* [交貨審核](#delivery-audit-)

![](assets/s_ncs_user_del_details.png)

**相關主題：**

* [瞭解傳遞故障](understanding-delivery-failures.md)
* [瞭解隔離管理](understanding-quarantine-management.md)
* [關於傳遞的最佳實務](delivery-best-practices.md)
* [管理傳遞能力](about-deliverability.md)

## 傳遞摘要 {#delivery-summary}

的 **[!UICONTROL Summary]** 頁籤包含交貨的特徵：傳送狀態、使用的渠道、有關發送方的資訊、主題、有關執行的資訊。

## 傳遞報告 {#delivery-reports}

的 **[!UICONTROL Reports]** 連結，可從 **[!UICONTROL Summary]** 頁籤中，您可以查看與交貨操作相關的一組報告：一般傳遞報告、詳細報告、傳遞報告、失敗消息的分發、開機率、點擊和事務等。

此頁籤的內容可以根據您的要求進行配置。 有關交付報告的詳細資訊，請參閱 [此部分](../../reporting/using/delivery-reports.md)。

![](assets/delivery-report.png)

## 交貨日誌、歷史記錄和排除 {#delivery-logs-and-history}

的 **[!UICONTROL Delivery]** 頁籤提供此交貨中出現的事件的歷史記錄。 它包含傳遞日誌，即發送的消息清單及其狀態和關聯的消息。

對於交貨，您只能顯示（例如）交貨失敗或隔離地址為收件人。 要執行此操作，請按一下 **[!UICONTROL Filters]** 按鈕 **[!UICONTROL By state]**。 然後在下拉清單中選擇狀態。 列出了各種狀態 [此頁](delivery-statuses.md)。

>[!NOTE]
>
>可以定制顯示交貨日誌的清單，如同Campaign Classic中的任何清單。 例如，您可以添加一列，以瞭解在傳遞中發送的每封電子郵件的IP地址。 有關詳情，請參閱中詳細說明的使用案例 [此部分](#use-case)。

![](assets/s_ncs_user_delivery_delivery_tab.png)

的 **[!UICONTROL Display the mirror page for this message...]** 連結允許您在新窗口中查看從清單中選擇的傳遞內容的鏡像頁。

鏡像頁面僅可用於已定義HTML內容的遞送。 有關此內容的詳細資訊，請參閱 [生成鏡像頁](sending-messages.md#generating-the-mirror-page)。

![](assets/s_ncs_user_wizard_miror_page_link.png)

## 傳遞跟蹤日誌和歷史記錄 {#tracking-logs}

的 **[!UICONTROL Tracking]** 頁籤列出此交貨的跟蹤歷史記錄。 此頁籤顯示所發送消息的跟蹤資料，即受Adobe Campaign跟蹤的所有URL。 跟蹤資料按小時更新。

>[!NOTE]
>
>如果未為交貨啟用跟蹤，則不顯示此標籤。

跟蹤配置在傳遞嚮導的適當階段執行。 請參閱 [如何配置跟蹤的連結](how-to-configure-tracked-links.md)。

**[!UICONTROL Tracking]** 資料在交付報告中進行解釋。 請參閱[本節](../../reporting/using/delivery-reports.md)。

![](assets/s_ncs_user_delivery_tracking_tab.png)

## 收件匣轉譯 {#delivery-rendering}

的 **[!UICONTROL Inbox rendering]** 頁籤允許您在接收消息的不同上下文中預覽消息，並檢查主案頭和應用程式的相容性。

這樣，您就可以確保以最佳方式在各種Web客戶端、 Web郵件和設備上向收件人顯示您的郵件。

有關收件箱呈現的詳細資訊，請參閱 [此頁](inbox-rendering.md)

![](assets/s_tn_inbox_rendering_tokens.png)

## 交貨審核 {#delivery-audit-}

的 **[!UICONTROL Audit]** 頁籤包含傳遞日誌和有關校樣的所有消息。

的 **[!UICONTROL Refresh]** 按鈕來更新資料。 使用 **[!UICONTROL Filters]** 按鈕。

使用特殊表徵圖可以識別錯誤或警告。 請參閱 [分析交貨](steps-validating-the-delivery.md#analyzing-the-delivery)。

的 **[!UICONTROL Proofs]** 頁籤，用於查看已發送的校樣清單。

![](assets/s_ncs_user_delivery_log_tab.png)

您可以修改此窗口中顯示的資訊(以及 **[!UICONTROL Delivery]** 和 **[!UICONTROL Tracking]** 頁籤)。 要執行此操作，請按一下 **[!UICONTROL Configure list]** 表徵圖。 有關配置清單顯示的詳細資訊，請參閱 [此部分](../../platform/using/adobe-campaign-workspace.md#configuring-lists)。

## 交貨儀表板同步 {#delivery-dashboard-synchronization}

在傳遞儀表板中，您要檢查已處理的郵件和傳遞日誌，以確保已成功發送傳遞。

某些指標或狀態可能不正確或不是最新，這可以通過以下解決方案解決：

* 如果您的交貨狀態不正確，請檢查是否已對此交貨執行了所有必要的審批，或者 **[!UICONTROL operationMgt]** 和 **[!UICONTROL deliveryMgt]** 工作流正在運行，但沒有錯誤。 這也可能是因為使用發送實例上未配置的關聯進行傳遞。

* 如果您的交貨指標仍為零，並且您處於中間採購配置中，請檢查 **[!UICONTROL Mid-sourcing (delivery counters)]** 技術工作流。 如果狀態不是，請啟動它 **[!UICONTROL Started]**。 然後，您可以嘗試通過在Adobe Campaign瀏覽器中按一下右鍵相關傳遞並選擇 **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**。 有關跟蹤指標的詳細資訊，請參閱此 [節](../../reporting/using/delivery-reports.md#tracking-indicators)。

* 如果您的交貨計數器與您的交貨不匹配，請嘗試通過在Adobe Campaign瀏覽器中按一下右鍵相關交貨並選擇 **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** 重新同步。 有關跟蹤指標的詳細資訊，請參閱此 [節](../../reporting/using/delivery-reports.md#tracking-indicators)。

* 如果您的交貨計數器不是中間採購部署的最新，請檢查 **[!UICONTROL Mid-Sourcing (Delivery counters)]** 技術工作流正在運行。 如需關於此項目的詳細資訊，請參閱此[頁面](../../installation/using/mid-sourcing-deployment.md)。

您還可以通過交貨控制面板使用不同的報表跟蹤交貨。 如需詳細資訊，請參閱本[區段](../../reporting/using/delivery-reports.md)。

## 用例：將發件人的IP地址添加到日誌 {#use-case}

在本節中，您將瞭解如何向傳遞日誌中添加有關在傳遞中發送每封電子郵件的IP地址的資訊。

>[!NOTE]
>
>如果您使用的是單個實例或中間採購實例，則此修改會有所不同。 在進行修改之前，請確保您已連接到電子郵件發送實例。

### 步驟1:擴展架構

添加 **公共ID** 在交付日誌中，您需要先擴展架構。 您可以按如下步驟進行。

1. 建立架構擴展，在 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**。

   有關架構擴展的詳細資訊，請參閱 [此頁](../../configuration/using/extending-a-schema.md)。

1. 選擇 **[!UICONTROL broadLogRcp]** 擴展收件人傳遞日誌(nms)並定義自定義命名空間。 在這種情況下，它將是「關注」：

   ![](assets/schema-parameters.png)

   >[!NOTE]
   >
   >如果實例在中間採購中，則需要使用broadLogMid架構。

1. 在分機中添加新欄位。 在此示例中，您需要替換：

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp"/>
   ```

   按：

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp">
   <attribute desc="Outbound IP identifier" label="IP identifier"
   name="publicId" type="long"/>
   </element>
   ```

   ![](assets/edit-schema.png)

### 步驟2:更新資料庫結構

修改完成後，需要更新資料庫結構，使其與其邏輯說明對齊。

要執行此操作，請遵循下列步驟：

1. 按一下 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]** 的子菜單。

   ![](assets/update-database-structure.png)

1. 在 **[!UICONTROL Edit tables]** 的 **[!UICONTROL NmsBroadLogRcp]** 表被選中(或 **[!UICONTROL broadLogMid]** 中)，如下所示：

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >請始終確保除以下項之外沒有其他修改 **[!UICONTROL NmsBroadLoGRcp]** 表(或 **[!UICONTROL broadLogMid]** 的下界)。 如果是，則取消選中其他表。

1. 按一下 **[!UICONTROL Next]** 驗證。 將顯示以下螢幕：

   ![](assets/update-script.png)

1. 按一下 **[!UICONTROL Next]**，則 **[!UICONTROL Start]** 開始更新資料庫結構。 索引生成正在啟動。 此步驟可能很長，具體取決於 **[!UICONTROL NmsBroadLogRcp]** 的子菜單。

   ![](assets/start-database-update.png)

>[!NOTE]
>
>資料庫物理結構的更新成功完成後，您需要斷開連接並重新連接，以便將您的修改考慮在內。

### 第3步：驗證修改

要確認所有操作都正常，您需要更新交貨日誌螢幕。

為此，請訪問傳遞日誌並添加「IP標識符」列。

![](assets/list-config.png)

>[!NOTE]
>
>要瞭解如何在Campaign Classic介面中配置清單，請參閱 [此頁](../../platform/using/adobe-campaign-workspace.md)。

下面是您在 **[!UICONTROL Delivery]** 頁籤：

![](assets/logs-with-ip.png)
