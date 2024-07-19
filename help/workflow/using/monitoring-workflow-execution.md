---
product: campaign
title: 監視工作流程的執行
description: 監視工作流程的執行
feature: Workflows
exl-id: d589180b-8e1d-4149-9b16-3f541018a41f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '2018'
ht-degree: 2%

---

# 監視工作流程的執行 {#monitoring-workflow-execution}



本節提供如何監視工作流程執行的資訊。

[本節](supervising-workflows.md#supervising-workflows)也提供如何建立工作流程的使用案例，可讓您監視一組「已暫停」、「已停止」或「發生錯誤」的工作流程的狀態。

此外，執行個體的管理員可以使用&#x200B;**稽核軌跡**&#x200B;來檢查工作流程的活動和上次所做的修改，以及工作流程的狀態。 如需詳細資訊，請參閱[Campaign Classicv7生產指南](../../production/using/audit-trail.md)。

監視不同Campaign處理序的其他方法顯示在[Campaign Classic v7生產指南](../../production/using/monitoring-guidelines.md)中。

## 顯示進度 {#displaying-progress}

您可以使用工具列上的適當圖示來顯示進度，以監視執行。

**[!UICONTROL Display progress information]**&#x200B;圖示可讓您在執行畫面中顯示狀態和活動結果。

![](assets/s_user_segmentation_toolbar_progr.png)

選取此選項時，執行的活動會以藍色顯示，擱置的活動會閃爍，警告會以橘色顯示，而錯誤則以紅色顯示。 此選項也會顯示其出站轉變上的活動結果，其後是活動屬性中定義的結果標籤，如果超過一秒，則為工作的持續時間

![](assets/s_user_segmentation_results.png)

## 顯示記錄 {#displaying-logs}

記錄檔包含工作流程的歷史記錄或稽核軌跡。 它會註冊所有使用者動作、執行的所有作業以及遇到的錯誤。 您可以：

* 選取詳細資料中的&#x200B;**[!UICONTROL Tracking]**&#x200B;索引標籤。 此清單包含所有工作流程訊息。

  ![](assets/new-workflow-display-log-tab.png)

* 依活動篩選紀錄訊息。 若要這麼做，請按一下圖表上方工具列上的&#x200B;**[!UICONTROL Display the tasks and the log]**，以顯示圖表下方的&#x200B;**[!UICONTROL Log]**&#x200B;和&#x200B;**[!UICONTROL Tasks]**&#x200B;標籤。 選取活動以檢視所有相關訊息。 此清單包含未選取活動時的所有訊息。

  ![](assets/new-workflow-display-log-activity.png)

  >[!NOTE]
  >
  >按一下圖表的背景以取消選取所有元素。

* 僅檢視連結至指定任務的訊息。 若要這麼做，請選取&#x200B;**[!UICONTROL Tasks]**&#x200B;標籤，然後在圖表中選取活動以限制清單。 按兩下工作以顯示資訊；視窗中的最後一個標籤包含記錄。

  ![](assets/new-workflow-display-tasks-activity.png)

  **[!UICONTROL Details...]**&#x200B;按鈕可讓您顯示活動執行的所有其他資訊。 例如，您可以檢視驗證運運算元，以及核準時輸入的註解（如下列範例所示）（如適用）：

  ![](assets/new-workflow-display-tasks-activity-details.png)

>[!NOTE]
>
>重新啟動工作流程時不會清除記錄。 會保留所有訊息。 如果您要捨棄先前執行的訊息，則必須永久刪除歷史記錄。

記錄檔會顯示與定位工作流程活動相關之執行訊息的時間順序清單。

* 目標定位行銷活動的記錄

  目標定位行銷活動執行後，按一下&#x200B;**[!UICONTROL Tracking]**&#x200B;索引標籤以檢視執行追蹤。

  ![](assets/s_user_segmentation_journal.png)

  所有行銷活動訊息都會顯示：已執行的行銷活動以及警告或錯誤。

* 活動記錄

  您也可以檢視每個活動的執行記錄檔和詳細資訊。 有兩種方法可以達成此目的：

   1. 選取目標活動，然後按一下&#x200B;**[!UICONTROL Display the tasks and the log]**&#x200B;圖示。

      ![](assets/s_user_segmentation_show_logs.png)

      圖表的下半部分顯示兩個標籤：記錄檔和工作。

      在圖表中選取的活動在記錄和工作清單中作為篩選器。

      ![](assets/s_user_segmentation_logs.png)

   1. 以滑鼠右鍵按一下目標活動，然後選取&#x200B;**[!UICONTROL Display logs]**。

      ![](assets/s_user_segmentation_logs_menu.png)

      記錄會顯示在另一個視窗中。

## 清除記錄 {#purging-the-logs}

系統不會自動清除工作流程歷史記錄：預設會保留所有訊息。 您可以透過&#x200B;**[!UICONTROL File > Actions]**&#x200B;功能表或按一下位於清單上方工具列中的&#x200B;**[!UICONTROL Actions]**&#x200B;按鈕，清除歷史記錄。 選取 **[!UICONTROL Purge history]**。**[!UICONTROL Actions]**&#x200B;功能表中可用的選項在[動作工具列](starting-a-workflow.md)區段中詳細說明。

![](assets/purge_historique.png)

## 工作表和工作流程結構描述 {#worktables-and-workflow-schema}

工作流程會傳達可透過特定活動操作的工作表。 Adobe Campaign可讓您透過「資料管理」活動，修改、重新命名及擴充工作流程工作表格的欄，例如根據客戶需求調整其命名法，以收集合約共同受益人的其他資訊等。

您也可以建立不同工作維度之間的連結，並定義維度變更。 例如，針對資料庫中記錄的每份合約，指定主要持有者的位址，並在其他資訊中使用共同持有者資料。

當工作流程鈍化時，會自動刪除工作流程的工作表。 如果要保留工作表，請透過&#x200B;**[!UICONTROL List update]**&#x200B;活動將其儲存在清單中（請參閱[清單更新](list-update.md)）。

## 管理錯誤 {#managing-errors}

發生錯誤時，工作流程會暫停，而發生錯誤時所執行的活動會以紅色閃爍。 在工作流程概觀中，在&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤 — **[!UICONTROL Workflows]**&#x200B;連結下方，您只能顯示有錯誤的工作流程，如下所示。

![](assets/wf-global-view_filter_only_errors.png)

在Adobe Campaign Explorer中，工作流程清單預設會顯示&#x200B;**[!UICONTROL Failed]**&#x200B;欄。

![](assets/wf-explorer_errors_col.png)

當工作流程發生錯誤時，只要工作流程監督群組的操作員的電子郵件地址列在其設定檔中，該操作員就會收到電子郵件通知。 已在工作流程屬性的&#x200B;**[!UICONTROL Supervisor(s)]**&#x200B;欄位中選取此群組。

![](assets/wf-properties_select-supervisors.png)

已在&#x200B;**[!UICONTROL Workflow manager notification]**&#x200B;預設範本中設定通知內容：已在工作流程屬性的&#x200B;**[!UICONTROL Execution]**&#x200B;標籤中選取此範本。 通知會顯示錯誤工作流程和相關任務的名稱。

通知範例：

![](assets/wf-notification_error-msg.png)

連結可讓您在Web模式下存取Adobe Campaign主控台，並在您登入後處理錯誤工作流程。

![](assets/wf-notification_error-console.png)

您可以設定工作流程，使其在出現錯誤時不會暫停並繼續執行。若要這麼做，請編輯工作流程&#x200B;**[!UICONTROL Properties]**，並在&#x200B;**[!UICONTROL Error management]**&#x200B;區段中，選取&#x200B;**[!UICONTROL In case of error]**&#x200B;欄位中的&#x200B;**[!UICONTROL Ignore]**&#x200B;選項。 然後，您可以指定在程序暫停之前可以忽略的連續錯誤數。

在此情況下，錯誤工作會中止。 此模式特別適合用於設計為在稍後重新嘗試行銷活動（定期動作）的工作流程。

![](assets/wf_edit_properties_for_error_mgt.png)

>[!NOTE]
>
>您可以對每個活動個別套用此設定。 若要這麼做，請編輯活動屬性，並在&#x200B;**[!UICONTROL Advanced]**&#x200B;索引標籤中選取錯誤管理模式。

如需工作流程執行疑難排解的詳細資訊，請參閱[Campaign Classicv7生產指南](../../production/using/workflow-execution.md)。

## 正在處理錯誤 {#processing-errors}

關於活動，**[!UICONTROL Process errors]**&#x200B;選項會顯示特定轉變，如果產生錯誤，將會啟用此轉變。 在此情況下，工作流程不會進入錯誤模式並繼續執行。

考慮的錯誤是檔案系統錯誤（無法移動檔案、無法存取目錄等）。

此選項不會處理與活動設定相關的錯誤，即無效值。 與錯誤設定相關的錯誤將不會啟用此轉換（目錄不存在等）。

如果工作流程暫停（手動或在錯誤後自動暫停），**[!UICONTROL Start]**&#x200B;按鈕會在工作流程停止的地方重新啟動工作流程執行。 系統會重新執行錯誤的活動（或已暫停的活動）。 先前活動不會重新執行。

若要重新執行所有工作流程活動，請使用&#x200B;**[!UICONTROL Restart]**&#x200B;按鈕。

如果您修改已執行的活動，則重新啟動工作流程執行時不會考慮變更。

如果您修改未執行的活動，則會在重新啟動工作流程執行時考慮這些活動。

如果您修改暫停的活動，則當工作流程重新啟動時，無法正確考量變更。

如果可行，建議在執行修改後完全重新啟動工作流程。

## 執行個體監督 {#instance-supervision}

**[!UICONTROL Instance supervision]**&#x200B;頁面可讓您檢視Adobe Campaign伺服器活動，並顯示工作流程清單和含有錯誤的傳送。

若要存取此頁面，請移至&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL General view]**&#x200B;連結。

![](assets/wf-monitoring_from-homepage.png)

若要顯示所有工作流程，請按一下&#x200B;**[!UICONTROL Workflows]**&#x200B;連結。 使用下拉式清單，根據工作流程的狀態顯示平台中的工作流程。

![](assets/wf-monitoring_edit-wf.png)

按一下發生錯誤的工作流程上的連結，以開啟並檢視其記錄。

![](assets/wf-monitoring_edit-task-wf.png)

## 防止同時執行多個專案 {#preventing-simultaneous-multiple-executions}

單一工作流程可以同時執行數個執行。 在某些情況下，您應該防止此情況發生。

例如，您可以讓排程器每小時觸發一次工作流程執行，但有時整個工作流程的執行需要超過一小時。 如果工作流程已在執行中，您可能會想要略過執行。

如果您在工作流程開始時有訊號活動，則在工作流程正在執行時，您可能想要略過訊號。

一般原則如下：

![](assets/workflow-reentrancy-protection-principle.png)

解決方案是使用例項變數。 執行個體變數會由工作流程的所有平行執行共用。

以下是簡單的測試工作流程：

![](assets/wkf_simultaneous_execution1.png)

**[!UICONTROL Scheduler]**&#x200B;每分鐘都會觸發一個事件。 下列&#x200B;**[!UICONTROL Test]**&#x200B;活動即將測試&#x200B;**isRunning**&#x200B;執行個體變數，以決定是否繼續執行：

![](assets/wkf_simultaneous_execution2.png)

>[!NOTE]
>
>**isRunning**&#x200B;是為這個範例選擇的變數名稱。 這不是內建變數。

在&#x200B;**是**&#x200B;分支中緊接在&#x200B;**[!UICONTROL Test]**&#x200B;之後的活動，必須在其&#x200B;**初始化指令碼**&#x200B;中設定執行個體變數：

```
instance.vars.isRunning = true
```

**是**&#x200B;分支中的最後一個活動必須在其&#x200B;**初始化指令碼**&#x200B;中將變數還原為false：

```
instance.vars.isRunning = false
```

請注意：

* 您可以透過工作流程&#x200B;**屬性**&#x200B;中的&#x200B;**變數**&#x200B;索引標籤，檢查執行個體變數的目前值。
* 當您重新啟動工作流程時，執行個體變數會重設。
* 在JavaScript中，未定義的值在測試中為false，可讓您在初始化執行個體變數之前對其進行測試。
* 您可以將記錄指示新增至「no」結尾的初始化指令碼，以監視因此機制而未處理的活動。

  ```
  logInfo("Workflow already running, parallel execution not allowed.");
  ```

此章節中會顯示使用案例： [協調資料更新](coordinating-data-updates.md)。

## 資料庫維護 {#database-maintenance}

工作流程會使用許多工作表格，消耗空間，如果不進行維護，最終會導致整個平台速度變慢。 如需資料庫維護的詳細資訊，請參閱此[區段](../../production/using/tables-to-maintain.md)。

可透過&#x200B;**管理>生產>技術工作流程**&#x200B;節點存取的&#x200B;**資料庫清理**&#x200B;工作流程，可讓您刪除過時的資料，以避免資料庫呈指數增長。 工作流程會自動觸發，使用者無需另行干預。 請參閱[Campaign Classicv7生產指南](../../production/using/database-cleanup-workflow.md)。

您也可以建立特定的技術工作流程，以清除不必要的資料佔用空間。 請參閱[Campaign Classicv7生產指南](../../production/using/application-objects.md)和此[區段](#purging-the-logs)。

## 處理暫停的工作流程 {#handling-of-paused-workflows}

根據預設，如果暫停工作流程，則不會永久刪除其工作表。 從Build 8880開始，已處於暫停狀態太久的工作流程會自動停止，並清除其工作表。 此行為的觸發方式如下：

* 在超過7天後暫停的工作流程會在監控儀表板（和監控API）中顯示為警告，並傳送通知給主管群組。
* 每週觸發&#x200B;**[!UICONTROL cleanupPausedWorkflows]**&#x200B;技術工作流程時也會發生相同情況。 如需工作流程的詳細資訊，請參閱[本區段](delivery.md)。
* 在4個通知後（即預設為暫停狀態一個月），工作流程會無條件停止。 記錄停止後，即會顯示在工作流程中。 在下次執行&#x200B;**[!UICONTROL cleanup]**&#x200B;工作流程時清除表格

這些期間可透過NmsServer_PausedWorkflowPeriod選項設定。

通知工作流程主管。 也會通知建立者和上次修改工作流程的使用者。 管理員不會收到通知。

## 根據工作流程的狀態進行篩選 {#filtering-workflows-status}

Campaign Classic介面可讓您使用預先定義的&#x200B;**檢視**&#x200B;來監視執行個體上所有工作流程的執行狀態。 若要存取這些檢視，請開啟&#x200B;**[!UICONTROL Administration]** / **[!UICONTROL Audit]** / **[!UICONTROL Workflows Status]**&#x200B;節點。

可使用下列檢視：

* **[!UICONTROL Running]**：列出所有執行中的工作流程。
* **[!UICONTROL Paused]**：列出所有暫停的工作流程。
* **[!UICONTROL Failed]**：列出所有失敗的工作流程。
* **[!UICONTROL Start Pending]**：列出所有等待由operationMgt處理序啟動的工作流程。 此檢視僅適用於&#x200B;**行銷活動**&#x200B;套件。 請參閱[Campaign Classicv7安裝指南](../../installation/using/installing-campaign-standard-packages.md)以瞭解更多資訊。

![](assets/workflow-monitoring-views.png)

預設可在&#x200B;**[!UICONTROL Audit]**&#x200B;資料夾中存取這些檢視。 不過，您可以在資料夾樹狀結構中所選擇的位置重新建立它們。 如此一來，便可供沒有管理許可權的標準使用者使用。

若要這麼做：

1. 在您要新增檢視的資料夾上按一下滑鼠右鍵。
1. 在&#x200B;**[!UICONTROL Add new folder]** / **[!UICONTROL Administration]**&#x200B;中，選取您要新增的檢視。
1. 資料夾新增至樹狀結構後，請確定將其設定為檢視，以便顯示所有工作流程，無論其原始資料夾為何。如需如何設定檢視的詳細資訊，請參閱[本節](../../platform/using/access-management-folders.md)。

除了這些檢視之外，您還可以設定篩選資料夾，讓您根據工作流程的執行狀態來篩選工作流程清單。 操作步驟：

1. 存取工作流程型別資料夾，然後選取&#x200B;**[!UICONTROL Filters]** / **[!UICONTROL Advanced filter]**&#x200B;功能表。
1. 設定篩選器，使工作流程的&#x200B;**[!UICONTROL @status]**&#x200B;欄位等於您選擇的狀態。
1. 儲存並命名篩選器。 然後，您就可以直接從篩選器清單中取得該篩選。

![](assets/workflow-monitoring-filter.png)

如需詳細資訊，請參閱下列章節：

* [建立進階篩選](../../platform/using/creating-filters.md#creating-an-advanced-filter)
* [儲存篩選器](../../platform/using/creating-filters.md#saving-a-filter)
