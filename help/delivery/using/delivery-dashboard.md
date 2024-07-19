---
product: campaign
title: 傳遞儀表板
description: 進一步瞭解如何使用傳送儀表板來監視您的傳送
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Monitoring
role: User, Data Engineer
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1186'
ht-degree: 5%

---

# 傳遞儀表板 {#delivery-dashboard}


**傳遞儀表板**&#x200B;是監視您的傳遞以及在傳送訊息期間遇到的最終問題的關鍵。

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

**[!UICONTROL Summary]**&#x200B;索引標籤包含傳遞的特性：傳遞狀態、使用的管道、寄件者的相關資訊、主旨、執行的相關資訊。

## 傳遞報告 {#delivery-reports}

可從&#x200B;**[!UICONTROL Summary]**&#x200B;標籤存取的&#x200B;**[!UICONTROL Reports]**&#x200B;連結可讓您檢視與傳遞動作相關的一組報告：一般傳遞報告、詳細報告、傳遞報告、失敗訊息的分發、年初匯率、點按和交易等。

您可以根據自己的需求設定此標籤的內容。 如需傳遞報告的詳細資訊，請參閱[本節](../../reporting/using/delivery-reports.md)。

![](assets/delivery-report.png)

## 傳遞記錄、記錄和排除 {#delivery-logs-and-history}

**[!UICONTROL Delivery]**&#x200B;索引標籤會提供此傳遞中發生的記錄。 它包含傳遞記錄，即已傳送的訊息清單及其狀態和相關聯的訊息。

對於傳遞，您可以（例如）僅顯示傳送失敗或在隔離中的地址的收件者。 若要這麼做，請按一下&#x200B;**[!UICONTROL Filters]**&#x200B;按鈕並選取&#x200B;**[!UICONTROL By state]**。 然後在下拉式清單中選取狀態。 [此頁面](delivery-statuses.md)中列出各種狀態。

>[!NOTE]
>
>顯示傳送記錄的清單可與Campaign Classic中的任何清單一樣自訂。 例如，您可以新增欄，以瞭解在傳送中每封電子郵件傳送了哪個IP位址。 如需詳細資訊，請參閱[本節](#use-case)中詳細的使用案例。

![](assets/s_ncs_user_delivery_delivery_tab.png)

**[!UICONTROL Display the mirror page for this message...]**&#x200B;連結可讓您在新視窗中檢視從清單選取之傳遞內容的映象頁面。

映象頁面僅適用於已定義HTML內容的傳送。 如需詳細資訊，請參閱[產生映象頁面](sending-messages.md#generating-the-mirror-page)。

![](assets/s_ncs_user_wizard_miror_page_link.png)

## 傳遞追蹤記錄和歷史記錄 {#tracking-logs}

**[!UICONTROL Tracking]**&#x200B;索引標籤會列出此傳遞的追蹤記錄。 此標籤會顯示已傳送訊息的追蹤資料，例如，所有受Adobe Campaign追蹤的URL。 追蹤資料會每小時更新。

>[!NOTE]
>
>如果未啟用傳遞追蹤，則不會顯示此索引標籤。

追蹤設定會在傳遞精靈的適當階段執行。 請參閱[如何設定追蹤的連結](how-to-configure-tracked-links.md)。

在傳遞報告中解譯&#x200B;**[!UICONTROL Tracking]**&#x200B;資料。 請參閱[本節](../../reporting/using/delivery-reports.md)。

![](assets/s_ncs_user_delivery_tracking_tab.png)

## 收件匣轉譯 {#delivery-rendering}

**[!UICONTROL Inbox rendering]**&#x200B;索引標籤可讓您在可能接收訊息的不同內容中預覽訊息，並檢查主要案頭和應用程式中的相容性。

如此一來，您就可以確保以最佳方式在各種Web使用者端、網頁郵件與裝置上向收件者顯示您的訊息。

如需收件匣轉譯的詳細資訊，請參閱[此頁面](inbox-rendering.md)

![](assets/s_tn_inbox_rendering_tokens.png)

## 傳遞稽核 {#delivery-audit-}

**[!UICONTROL Audit]**&#x200B;索引標籤包含傳遞記錄檔及與校樣相關的所有訊息。

**[!UICONTROL Refresh]**&#x200B;按鈕可讓您更新資料。 使用&#x200B;**[!UICONTROL Filters]**&#x200B;按鈕來定義資料的篩選器。

特殊圖示可讓您識別錯誤或警告。 請參閱[分析傳遞](steps-validating-the-delivery.md#analyzing-the-delivery)。

**[!UICONTROL Proofs]**&#x200B;子索引標籤可讓您檢視已傳送的校樣清單。

![](assets/s_ncs_user_delivery_log_tab.png)

您可以修改此視窗中顯示的資訊（以及&#x200B;**[!UICONTROL Delivery]**&#x200B;和&#x200B;**[!UICONTROL Tracking]**&#x200B;索引標籤的資訊），方法是選取要顯示的欄。 若要這麼做，請按一下右下角的&#x200B;**[!UICONTROL Configure list]**&#x200B;圖示。 如需設定清單顯示的詳細資訊，請參閱[本節](../../platform/using/adobe-campaign-workspace.md#configuring-lists)。

## 傳遞控制面板同步 {#delivery-dashboard-synchronization}

從您的傳送控制面板，檢查已處理的訊息和傳送記錄檔，確定傳送成功。

有些指標或狀態可能錯誤或不是最新的，此問題可能由下列解決方案解決：

* 如果您的傳遞狀態不正確，請檢查此傳遞的所有必要核准是否已完成，或&#x200B;**[!UICONTROL operationMgt]**&#x200B;和&#x200B;**[!UICONTROL deliveryMgt]**&#x200B;工作流程是否正在執行且沒有錯誤。 這也可能是因為傳送使用未在傳送執行個體上設定的相似性。

* 如果您的傳遞指標仍然為零，並且如果您在中間來源組態，請檢查&#x200B;**[!UICONTROL Mid-sourcing (delivery counters)]**&#x200B;技術工作流程。 若其狀態不是&#x200B;**[!UICONTROL Started]**，請啟動它。 然後，您可以在Adobe Campaign總管中的相關傳遞上按一下滑鼠右鍵，並選取&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**，以嘗試重新計算指標。 如需追蹤指標的詳細資訊，請參閱此[區段](../../reporting/using/delivery-reports.md#tracking-indicators)。

* 如果您的傳遞計數器不符合您的傳遞，請在Adobe Campaign總管中的相關傳遞上按一下滑鼠右鍵，並選取&#x200B;**[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**&#x200B;以重新同步處理，藉此嘗試重新計算指標。 如需追蹤指標的詳細資訊，請參閱此[區段](../../reporting/using/delivery-reports.md#tracking-indicators)。

* 如果您的傳遞計數器不是最新中間來源部署，請檢查&#x200B;**[!UICONTROL Mid-Sourcing (Delivery counters)]**&#x200B;技術工作流程是否正在執行。 如需關於此項目的詳細資訊，請參閱此[頁面](../../installation/using/mid-sourcing-deployment.md)。

您也可以透過傳送控制面板，使用不同的報告追蹤您的傳送內容。 如需詳細資訊，請參閱本[區段](../../reporting/using/delivery-reports.md)。

## 使用案例：將傳送者的IP位址新增至記錄檔 {#use-case}

在本節中，您將瞭解如何將有關在傳送中傳送每封電子郵件的IP位址的資訊新增到傳送記錄中。

>[!NOTE]
>
>如果您使用單一執行個體或中間來源執行個體，則此修改會不同。 進行修改之前，請確定您已連線至電子郵件傳送執行個體。

### 步驟1：擴充結構

若要在傳遞記錄中新增&#x200B;**publicID**，您必須先擴充結構描述。 您可以依照以下步驟繼續操作。

1. 在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**&#x200B;下建立結構描述延伸。

   如需結構描述擴充功能的詳細資訊，請參閱[此頁面](../../configuration/using/extending-a-schema.md)。

1. 選取&#x200B;**[!UICONTROL broadLogRcp]**&#x200B;以擴充收件者傳遞記錄(nms)並定義自訂名稱空間。 在此案例中會是「cus」：

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

1. 按一下&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]**&#x200B;功能表。

   ![](assets/update-database-structure.png)

1. 在&#x200B;**[!UICONTROL Edit tables]**&#x200B;視窗中，已檢查&#x200B;**[!UICONTROL NmsBroadLogRcp]**&#x200B;表格(或者&#x200B;**[!UICONTROL broadLogMid]**&#x200B;表格（如果您在中間來源環境中），如下所示：

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >請一律確認沒有其他修改，除了&#x200B;**[!UICONTROL NmsBroadLoGRcp]**&#x200B;資料表（或如果您在中間來源環境中，則為&#x200B;**[!UICONTROL broadLogMid]**&#x200B;資料表）。 如果是，請取消核取其他表格。

1. 按一下&#x200B;**[!UICONTROL Next]**&#x200B;進行驗證。 接著會顯示下列畫面：

   ![](assets/update-script.png)

1. 按一下&#x200B;**[!UICONTROL Next]**，然後按&#x200B;**[!UICONTROL Start]**&#x200B;開始更新資料庫結構。 正在開始建立索引。 此步驟可能很長，取決於&#x200B;**[!UICONTROL NmsBroadLogRcp]**&#x200B;表格中的列數。

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
>若要瞭解如何在Campaign Classic介面中設定清單，請參閱[此頁面](../../platform/using/adobe-campaign-workspace.md)。

以下是修改後您在&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤中應該看到的內容：

![](assets/logs-with-ip.png)
