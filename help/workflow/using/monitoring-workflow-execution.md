---
solution: Campaign Classic
product: campaign
title: 監控工作流程執行
description: 監控工作流程執行
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1998'
ht-degree: 0%

---


# 監控工作流程執行 {#monitoring-workflow-execution}

本節介紹如何監控工作流執行的資訊。

本節也提供如何建立工作流程的使用案例，讓您監視「暫停」、「停止」或「有錯誤」的一組工作流程 [狀態](../../workflow/using/supervising-workflows.md#supervising-workflows)。

此外，例項的管理員可使用 **Audit trail** ，來檢查活動和對工作流程所做的最後修改（工作流程的狀態）。 For more on this, refer to the [dedicated section](../../production/using/audit-trail.md).

本頁提供其他監控不同促銷活動程式 [的方法](../../production/using/monitoring-guidelines.md)。

## 顯示進度 {#displaying-progress}

您可以使用工具列上的適當圖示來顯示進度，以監控執行。

圖 **[!UICONTROL Display progress information]** 示可讓您顯示狀態，以及導致執行畫面的活動。

![](assets/s_user_segmentation_toolbar_progr.png)

選取此選項時，已執行的活動會以藍色顯示，待定活動會閃爍，警告會以橙色顯示，錯誤會以紅色顯示。 此選項還顯示活動在其出站轉移時的結果，後面是活動屬性中定義的結果標籤，如果超過一秒，則顯示作業的持續時間

![](assets/s_user_segmentation_results.png)

## 顯示日誌 {#displaying-logs}

記錄檔包含工作流程的歷史記錄或稽核記錄。 它註冊所有用戶操作、所有執行的操作和遇到的錯誤。 您可以：

* 在詳細資訊 **[!UICONTROL Tracking]** 中選擇該頁籤。 此清單包含所有工作流消息。

   ![](assets/new-workflow-display-log-tab.png)

* 按活動篩選日誌消息。 要執行此操作，請單 **[!UICONTROL Display the tasks and the log]** 擊圖上方的工具欄上的，以便在圖下 **[!UICONTROL Log]** 顯示 **[!UICONTROL Tasks]** 和頁籤。 選擇活動以查看所有相關消息。 此清單包含未選擇任何活動時的所有消息。

   ![](assets/new-workflow-display-log-activity.png)

   >[!NOTE]
   >
   >按一下圖的背景以取消選擇所有元素。

* 僅查看連結到給定任務的消息。 要執行此操作，請選 **[!UICONTROL Tasks]** 擇頁籤，然後在圖中選擇活動以限制清單。 連按兩下工作即可顯示資訊；窗口中的最後一個頁籤包含日誌。

   ![](assets/new-workflow-display-tasks-activity.png)

   此按 **[!UICONTROL Details...]** 鈕可讓您顯示活動執行的所有其他資訊。 例如，您可以檢視驗證運算子，以及在適用時，在核准期間輸入的註解，如下列範例所示：

   ![](assets/new-workflow-display-tasks-activity-details.png)

>[!NOTE]
>
>重新啟動工作流時，不會清除日誌。 保留所有留言。 如果要放棄先前執行中的消息，則必須清除歷史記錄。

日誌顯示與定位工作流活動相關的執行消息的時間清單。

* 定位促銷活動的記錄

   執行定位促銷活動後，按一下標 **[!UICONTROL Tracking]** 簽以檢視執行追蹤。

   ![](assets/s_user_segmentation_journal.png)

   所有促銷活動訊息皆顯示：促銷活動以及警告或錯誤。

* 活動記錄

   您也可以檢視執行記錄檔和每個活動的詳細資訊。 有兩種方法可以做到：

   1. 選取目標活動，然後按一下 **[!UICONTROL Display the tasks and the log]** 圖示。

      ![](assets/s_user_segmentation_show_logs.png)

      圖的下部分顯示兩個頁籤：日誌和任務。

      在圖中選擇的活動用作日誌和任務清單上的篩選器。

      ![](assets/s_user_segmentation_logs.png)

   1. 按一下右鍵目標活動並選擇 **[!UICONTROL Display logs]**。

      ![](assets/s_user_segmentation_logs_menu.png)

      記錄檔會顯示在個別視窗中。

## 清除日誌 {#purging-the-logs}

工作流歷史記錄不會自動清除：預設情況下會保留所有消息。 您可以透過選單或按一 **[!UICONTROL File > Actions]** 下清單上方工具列中 **[!UICONTROL Actions]** 的按鈕，來清除歷史記錄。 選取 **[!UICONTROL Purge history]**。功能表中可用的選 **[!UICONTROL Actions]** 項會在「動作」工具列區 [段中詳細說明](../../workflow/using/starting-a-workflow.md) 。

![](assets/purge_historique.png)

## 工作表和工作流模式 {#worktables-and-workflow-schema}

工作流程會傳達可透過特定活動處理的工作表。 Adobe Campaign可讓您透過「資料管理」活動修改、重新命名和豐富工作流程工作表的欄，例如，根據客戶的需求，將它們與名稱對齊，以收集合約共同受益人的其他資訊等。

還可以建立各種工作維之間的連結並定義維更改。 例如，對於資料庫中記錄的每個合同，請定址主持人，並在附加資訊中使用共同持有人資料。

當工作流被鈍化時，工作流的工作表將被自動刪除。 如果希望保留工作表，請通過活動將其保存在列 **[!UICONTROL List update]** 表中(請參 [閱清單更新](../../workflow/using/list-update.md))。

## 管理錯誤 {#managing-errors}

發生錯誤時，工作流程暫停，當發生錯誤時執行的活動閃爍紅色。 在工作流程概述(**[!UICONTROL Monitoring]** Universe > **[!UICONTROL Workflows]** link)中，您只能顯示有錯誤的工作流程，如下所示。

![](assets/wf-global-view_filter_only_errors.png)

在Adobe Campaign Explorer中，工作流程清單預設會 **[!UICONTROL Failed]** 顯示一欄。

![](assets/wf-explorer_errors_col.png)

當工作流出錯時，只要其電子郵件地址列在其配置檔案中，即會以電子郵件通知屬於工作流監督組的操作員。 此組在工作流屬性 **[!UICONTROL Supervisor(s)]** 的欄位中選擇。

![](assets/wf-properties_select-supervisors.png)

通知內容是在預設範本 **[!UICONTROL Workflow manager notification]** 中設定：此模板在工作流屬性 **[!UICONTROL Execution]** 的頁籤中選擇。 通知會顯示錯誤工作流程的名稱及相關任務。

通知範例：

![](assets/wf-notification_error-msg.png)

此連結可讓您以網頁模式存取Adobe Campaign主控台，並在您登入後，就能處理錯誤工作流程。

![](assets/wf-notification_error-console.png)

您可以設定工作流程，以免發生錯誤時暫停並繼續執行。 若要這麼做，請編輯工 **[!UICONTROL Properties]** 作流程，並在 **[!UICONTROL Error management]** 區段中選 **[!UICONTROL Ignore]** 取欄位中的選 **[!UICONTROL In case of error]** 項。 然後，您可以指定在暫停程式之前可忽略的連續錯誤數。

在這種情況下，錯誤任務將中止。 此模式特別適用於設計為稍後重新嘗試促銷活動（定期動作）的工作流程。

![](assets/wf_edit_properties_for_error_mgt.png)

>[!NOTE]
>
>您可以針對每個活動分別套用此設定。 若要這麼做，請編輯活動屬性，並在標籤中選取錯誤管理 **[!UICONTROL Advanced]** 模式。

有關工作流執行故障排除的詳細資訊，請參閱專 [用部分](../../production/using/workflow-execution.md)。

## 處理錯誤 {#processing-errors}

關於活動，選 **[!UICONTROL Process errors]** 項會顯示特定轉場，當產生錯誤時，此轉場將啟用。 在這種情況下，工作流不會進入錯誤模式並繼續執行。

考慮到的錯誤是檔案系統錯誤（無法移動檔案、無法訪問目錄等）。

此選項不處理與活動配置相關的錯誤，即無效值。 與故障配置相關的錯誤將不會啟用此轉換（目錄不存在等）。

如果暫停了工作流（手動或在發生錯誤後自動），則按 **[!UICONTROL Start]** 鈕會在停止工作流時重新啟動執行。 錯誤活動（或暫停的活動）將會重新執行。 不會重新執行先前的活動。

要重新執行所有工作流活動，請使用該 **[!UICONTROL Restart]** 按鈕。

如果修改已執行的活動，則在重新啟動工作流執行時不會考慮這些更改。

如果修改未執行的活動，則在重新啟動工作流執行時會考慮這些活動。

如果您修改暫停的活動，則在重新啟動工作流程時無法正確考慮這些變更。

如果可能，建議在進行修改後完全重新啟動工作流。

## 實例監督 {#instance-supervision}

此頁 **[!UICONTROL Instance supervision]** 面可讓您檢視Adobe Campaign伺服器活動，並顯示有錯誤的工作流程和傳送清單。

若要存取本頁，請前往宇宙， **[!UICONTROL Monitoring]** 然後按一下連 **[!UICONTROL General view]** 結。

![](assets/wf-monitoring_from-homepage.png)

若要顯示所有工作流程，請按一下 **[!UICONTROL Workflows]** 連結。 使用下拉式清單，根據工作流程的狀態來顯示平台中的工作流程。

![](assets/wf-monitoring_edit-wf.png)

按一下含有錯誤的工作流程上的連結，以開啟並檢視其記錄檔。

![](assets/wf-monitoring_edit-task-wf.png)

## 防止同時執行多個執行 {#preventing-simultaneous-multiple-executions}

單一工作流程可同時執行數個執行。 在某些情況下，您應該防止這種情況發生。

例如，您可以讓排程器每小時觸發工作流程執行，但有時整個工作流程的執行需要超過一小時。 如果工作流已運行，則可能希望跳過執行。

如果您在工作流程開始時有訊號活動，則在工作流程執行時，可能會想略過訊號。

一般原則是：

![](assets/workflow-reentrancy-protection-principle.png)

解決方案是使用例項變數。 執行個體變數會由工作流程的所有平行執行共用。

以下是簡單的測試工作流程：

![](assets/wkf_simultaneous_execution1.png)

每 **[!UICONTROL Scheduler]** 分鐘都會觸發事件。 下列 **[!UICONTROL Test]** 活動將測試 **isRunning** instance變數，以決定是否繼續執行：

![](assets/wkf_simultaneous_execution2.png)

>[!NOTE]
>
>**isRunning** 是本範例所選的變數名稱。 這不是內建變數。

緊接在yes分支中 **[!UICONTROL Test]** 的 **後續活動** ，必須在其 **Initialization指令碼中設定實例變數**:

```
instance.vars.isRunning = true
```

yes分支中最後一個活 **動** ，必須將其初始化指令碼中的變 **數還原為false**:

```
instance.vars.isRunning = false
```

請注意：

* 您可以透過工作流程「屬性」中的「變數」 **標籤** ，檢查例項變數的 **目前值**。
* 當您重新啟動工作流程時，會重設例項變數。
* 在JavaScript中，測試中未定義的值為false，允許在初始化執行個體變數之前先測試它。
* 通過向&quot;no&quot;結束的初始化指令碼添加日誌記錄指令，可以監視因此機制而未處理的活動。

   ```
   logInfo("Workflow already running, parallel execution not allowed.");
   ```

本節將介紹一個使用案例： [協調資料更新](../../workflow/using/coordinating-data-updates.md)。

## 資料庫維護 {#database-maintenance}

工作流程使用大量工作表，這些工作表會佔用空間，最終導致整個平台的速度變慢（如果不加以維護）。 有關資料庫維護的詳細資訊，請參 [閱](../../production/using/tables-to-maintain.md) 。

「數 **據庫清理** 」工作流可通過「管理」>「生產」>「技術工作流程 **** 」節點訪問，它允許您刪除過時的資料，以避免資料庫的指數級增長。 工作流程會自動觸發，使用者不需干預。 Refer to this [section](../../production/using/database-cleanup-workflow.md).

您也可以建立特定的技術工作流程，以清除不必要的資料佔用空間。 請參閱本 [節](../../production/using/application-objects.md) 和本 [頁](#purging-the-logs)。

## 處理暫停的工作流程 {#handling-of-paused-workflows}

預設情況下，如果某個工作流暫停，則不會清除其工作表。 從build 8880開始，暫停狀態太久的工作流程會自動停止，並清除其工作表。 觸發此行為的方式如下：

* 自7天以來暫停的工作流程會在監控控制面板（和監控API）中顯示為警告，並傳送通知給主管群組。
* 每週觸發技術工作流程時都 **[!UICONTROL cleanupPausedWorkflows]** 會發生相同的情況。 有關工作流的詳細資訊，請參 [閱本節](../../workflow/using/delivery.md)。
* 在4個通知後（亦即預設為一個月處於暫停狀態），工作流程會無條件停止。 日誌停止後，該日誌將出現在工作流中。 在下一個執行工作流時將清 **[!UICONTROL cleanup]** 除

這些句點可以通過NmsServer_PausedWorkflowPeriod選項進行配置。

工作流程主管會收到通知。 同時也會通知建立者和修改工作流程的最後使用者。 管理員不會收到通知。

## 根據工作流程的狀態篩選工作流程 {#filtering-workflows-status}

Campaign Classic介面可讓您使用預先定義的檢視，監控執行個體上所有工作流程的執行&#x200B;**狀態**。 要訪問這些視圖，請開啟&#x200B;**[!UICONTROL Administration]**/**[!UICONTROL Audit]**/**[!UICONTROL Workflows Status]**&#x200B;節點。

可使用下列檢視：

* **[!UICONTROL Running]**：列出所有執行中的工作流程。
* **[!UICONTROL Paused]**：列出所有暫停的工作流程。
* **[!UICONTROL Failed]**：列出所有失敗的工作流程。
* **[!UICONTROL Start Pending]**：列出等待operationMagt進程啟動的所有工作流。 此檢視僅適用於&#x200B;**Marketing促銷活動套件**(請參閱 [安裝促銷活動標準套件](../../installation/using/installing-campaign-standard-packages.md))。

![](assets/workflow-monitoring-views.png)

依預設，這些檢視可在資料夾中&#x200B;**[!UICONTROL Audit]**&#x200B;存取。 但是，您可以在資料夾樹中選擇的位置重新建立它們。 如此，就可讓不具管理權限的標準使用者使用。

要執行此操作：

1. 按一下右鍵要添加視圖的資料夾。
1. 在 **[!UICONTROL Add new folder]**/**[!UICONTROL Administration]**&#x200B;中，選擇要添加的視圖。
1. 將資料夾添加到樹中後，請確保將其配置為視圖，以便顯示所有工作流（無論其源資料夾是什麼）。有關如何配置視圖的詳細資訊，請參 [閱此部分](../../platform/using/access-management.md#adding-folders-and-creating-views)。

除了這些檢視外，您還可以設定篩選資料夾，讓您根據工作流程的執行狀態來篩選工作流程清單。 操作步驟：

1. 存取工作流程類型資料夾，然後選取 **[!UICONTROL Filters]** /功 **[!UICONTROL Advanced filter]** 能表。
1. 設定篩選，讓工作流程的 **[!UICONTROL @status]** 欄位等於您選擇的狀態。
1. 儲存並命名篩選。 然後，篩選器清單中就會直接提供它。

![](assets/workflow-monitoring-filter.png)

如需詳細資訊，請參閱下列章節：

* [建立進階篩選](../../platform/using/creating-filters.md#creating-an-advanced-filter)
* [儲存篩選](../../platform/using/creating-filters.md#saving-a-filter)
