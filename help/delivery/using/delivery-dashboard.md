---
product: campaign
title: 傳遞儀表板
description: 進一步瞭解如何使用傳送儀表板來監視您的傳送
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Monitoring
role: User, Data Engineer
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 5%

---

# 傳遞儀表板 {#delivery-dashboard}


此 **傳遞儀表板** 是監視傳遞內容以及在傳送訊息期間遇到的最終問題的關鍵。

它可讓您擷取傳送的相關資訊，並在必要時加以編輯。 請注意，傳送後，索引標籤內容可能不會再變更。

以下是使用控制面板中提供的數個標籤來監視的資訊：

* [傳遞摘要](#delivery-summary)
* [傳遞報告](#delivery-reports)
* [傳遞記錄、映象頁面、排除專案](#delivery-logs-and-history)
* [傳遞追蹤記錄和歷史記錄](#tracking-logs)
* [傳遞呈現](#delivery-rendering)
* [傳遞稽核](#delivery-audit-)

![](assets/s_ncs_user_del_details.png)

**相關主題：**

* [瞭解傳遞故障](understanding-delivery-failures.md)
* [瞭解隔離管理](understanding-quarantine-management.md)
* [關於傳遞的最佳實務](delivery-best-practices.md)
* [管理傳遞能力](about-deliverability.md)

## 傳遞摘要 {#delivery-summary}

此 **[!UICONTROL Summary]** 索引標籤包含傳遞的特性：傳遞狀態、使用的管道、有關寄件者的資訊、主題、有關執行的資訊。

## 傳遞報告 {#delivery-reports}

此 **[!UICONTROL Reports]** 連結，可從存取 **[!UICONTROL Summary]** 索引標籤中，可讓您檢視與傳送動作相關的一組報告：一般傳送報告、詳細報告、傳送報告、失敗訊息的分佈、年初匯率、點按和交易等。

您可以根據自己的需求設定此標籤的內容。 如需傳送報告的詳細資訊，請參閱 [本節](../../reporting/using/delivery-reports.md).

![](assets/delivery-report.png)

## 傳遞記錄、記錄和排除 {#delivery-logs-and-history}

此 **[!UICONTROL Delivery]** 索引標籤會提供此傳送中發生的記錄。 它包含傳遞記錄，即已傳送的訊息清單及其狀態和相關聯的訊息。

對於傳遞，您可以（例如）僅顯示傳送失敗或在隔離中的地址的收件者。 若要這麼做，請按一下 **[!UICONTROL Filters]** 按鈕並選取 **[!UICONTROL By state]**. 然後在下拉式清單中選取狀態。 中列出各種狀態 [此頁面](delivery-statuses.md).

>[!NOTE]
>
>顯示傳送記錄的清單可與Campaign Classic中的任何清單一樣自訂。 例如，您可以新增欄，以瞭解在傳送中每封電子郵件傳送了哪個IP位址。 如需詳細資訊，請參閱中的使用案例，詳情 [本節](#use-case).

![](assets/s_ncs_user_delivery_delivery_tab.png)

此 **[!UICONTROL Display the mirror page for this message...]** 連結可讓您在新視窗中檢視從清單中選取之傳遞內容的映象頁面。

映象頁面僅適用於已定義HTML內容的傳送。 有關詳細資訊，請參閱 [產生映象頁面](sending-messages.md#generating-the-mirror-page).

![](assets/s_ncs_user_wizard_miror_page_link.png)

## 傳遞追蹤記錄和歷史記錄 {#tracking-logs}

此 **[!UICONTROL Tracking]** 索引標籤會列出此傳送的追蹤記錄。 此標籤會顯示已傳送訊息的追蹤資料，例如，所有受Adobe Campaign追蹤的URL。 追蹤資料會每小時更新。

>[!NOTE]
>
>如果未啟用傳遞追蹤，則不會顯示此索引標籤。

追蹤設定會在傳遞精靈的適當階段執行。 另請參閱 [如何設定追蹤的連結](how-to-configure-tracked-links.md).

**[!UICONTROL Tracking]** 資料會在傳遞報表中解譯。 請參閱[本節](../../reporting/using/delivery-reports.md)。

![](assets/s_ncs_user_delivery_tracking_tab.png)

## 收件匣轉譯 {#delivery-rendering}

此 **[!UICONTROL Inbox rendering]** 標籤可讓您在可能接收訊息的不同內容中預覽訊息，並檢查主要案頭和應用程式中的相容性。

如此一來，您就可以確保以最佳方式在各種Web使用者端、網頁郵件與裝置上向收件者顯示您的訊息。

有關收件匣轉譯的詳細資訊，請參閱 [此頁面](inbox-rendering.md)

![](assets/s_tn_inbox_rendering_tokens.png)

## 傳遞稽核 {#delivery-audit-}

此 **[!UICONTROL Audit]** 索引標籤包含傳遞記錄及與校樣相關的所有訊息。

此 **[!UICONTROL Refresh]** 按鈕可讓您更新資料。 使用 **[!UICONTROL Filters]** 按鈕來定義資料的篩選器。

特殊圖示可讓您識別錯誤或警告。 另請參閱 [分析傳遞](steps-validating-the-delivery.md#analyzing-the-delivery).

此 **[!UICONTROL Proofs]** 子索引標籤可讓您檢視已傳送的校樣清單。

![](assets/s_ncs_user_delivery_log_tab.png)

您可以修改此視窗中顯示的資訊(以及 **[!UICONTROL Delivery]** 和 **[!UICONTROL Tracking]** 標籤)，方法是選取要顯示的欄。 若要這麼做，請按一下 **[!UICONTROL Configure list]** 圖示位於右下角。 有關設定清單顯示的詳細資訊，請參閱 [本節](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## 傳遞控制面板同步 {#delivery-dashboard-synchronization}

從您的傳送控制面板，檢查已處理的訊息和傳送記錄檔，確定傳送成功。

有些指標或狀態可能錯誤或不是最新的，此問題可能由下列解決方案解決：

* 如果您的傳送狀態不正確，請檢查此傳送的所有必要核准是否已完成，或 **[!UICONTROL operationMgt]** 和 **[!UICONTROL deliveryMgt]** 工作流程正在執行中且沒有錯誤。 這也可能是因為傳送使用未在傳送執行個體上設定的相似性。

* 如果您的傳遞指標仍然為零，並且如果您在中間來源設定，請檢視 **[!UICONTROL Mid-sourcing (delivery counters)]** 技術工作流程。 如果狀態不是，則啟動它 **[!UICONTROL Started]**. 接著，您可以在Adobe Campaign總管中的相關傳送上按一下滑鼠右鍵，然後選取「 」，嘗試重新計算指標 **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. 如需追蹤指標的詳細資訊，請參閱本節 [區段](../../reporting/using/delivery-reports.md#tracking-indicators).

* 如果傳送計數器與您的傳送不符，請嘗試在Adobe Campaign總管中的相關傳送上按一下右鍵，然後選取「 」，以重新計算指標 **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** 以重新同步。 如需追蹤指標的詳細資訊，請參閱本節 [區段](../../reporting/using/delivery-reports.md#tracking-indicators).

* 如果您的傳送計數器不是中間來源部署的最新計數器，請檢查 **[!UICONTROL Mid-Sourcing (Delivery counters)]** 技術工作流程正在執行中。 如需關於此項目的詳細資訊，請參閱此[頁面](../../installation/using/mid-sourcing-deployment.md)。

您也可以透過傳送控制面板，使用不同的報告追蹤您的傳送內容。 如需詳細資訊，請參閱本[區段](../../reporting/using/delivery-reports.md)。

## 使用案例：將傳送者的IP位址新增至記錄檔 {#use-case}

在本節中，您將瞭解如何將有關在傳送中傳送每封電子郵件的IP位址的資訊新增到傳送記錄中。

>[!NOTE]
>
>如果您使用單一執行個體或中間來源執行個體，則此修改會不同。 進行修改之前，請確定您已連線至電子郵件傳送執行個體。

### 步驟1：擴充結構

新增 **publicID** 在傳遞記錄中，您需要先擴充方案。 您可以依照以下步驟繼續操作。

1. 建立方案擴充功能，在 **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**.

   有關架構擴充功能的詳細資訊，請參閱 [此頁面](../../configuration/using/extending-a-schema.md).

1. 選取 **[!UICONTROL broadLogRcp]** 擴充收件者傳遞記錄(nms)並定義自訂名稱空間。 在此案例中會是「cus」：

   ![](assets/schema-parameters.png)

   >[!NOTE]
   >
   >如果您的執行個體位於中間來源，則需使用broadLogMid結構描述。

1. 在擴充功能中新增欄位。 在此範例中，您需要取代：

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp"/>
   ```

   作者：

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp">
   <attribute desc="Outbound IP identifier" label="IP identifier"
   name="publicId" type="long"/>
   </element>
   ```

   ![](assets/edit-schema.png)

### 步驟2：更新資料庫結構

完成修改後，您需要更新資料庫結構，使其與其邏輯說明一致。

要執行此操作，請遵循下列步驟：

1. 按一下 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]** 功能表。

   ![](assets/update-database-structure.png)

1. 在 **[!UICONTROL Edit tables]** 視窗， **[!UICONTROL NmsBroadLogRcp]** 已核取表格(或 **[!UICONTROL broadLogMid]** 表格（如果您在中間來源環境中），如下所示：

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >請一律確認沒有其他修改，但 **[!UICONTROL NmsBroadLoGRcp]** 表格(或 **[!UICONTROL broadLogMid]** 表格（如果您的是在中間來源環境中）。 如果是，請取消核取其他表格。

1. 按一下 **[!UICONTROL Next]** 以進行驗證。 接著會顯示下列畫面：

   ![](assets/update-script.png)

1. 按一下 **[!UICONTROL Next]**，然後 **[!UICONTROL Start]** 以開始更新資料庫結構。 正在開始建立索引。 此步驟可能很長，視中的列數而定 **[!UICONTROL NmsBroadLogRcp]** 表格。

   ![](assets/start-database-update.png)

>[!NOTE]
>
>成功更新資料庫的實體結構後，您需要中斷連線並重新連線，以便考慮您的修改。

### 步驟3：驗證修改

若要確認一切都正常運作，您需要更新傳送記錄畫面。

若要這麼做，請存取傳遞記錄並新增「IP識別碼」欄。

![](assets/list-config.png)

>[!NOTE]
>
>若要瞭解如何在Campaign Classic介面中設定清單，請參閱 [此頁面](../../platform/using/adobe-campaign-workspace.md).

以下是您應在 **[!UICONTROL Delivery]** 標籤進行修改後：

![](assets/logs-with-ip.png)
