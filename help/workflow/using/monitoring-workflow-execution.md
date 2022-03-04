---
product: campaign
title: 監視工作流程的執行
description: 監視工作流程的執行
feature: Workflows
exl-id: d589180b-8e1d-4149-9b16-3f541018a41f
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '2016'
ht-degree: 0%

---

# 監視工作流程的執行 {#monitoring-workflow-execution}

![](../../assets/common.svg)

本節介紹如何監視工作流的執行。

有關如何建立工作流的使用案例，也可在中找到一組「已暫停」、「已停止」或「有錯誤」的工作流的狀態 [此部分](supervising-workflows.md#supervising-workflows)。

此外，實例的管理員可以使用 **審核跟蹤** 要檢查活動和對工作流所做的最後修改，請查看工作流的狀態。 有關此內容的詳細資訊，請參閱 [Campaign Classicv7生產指南](../../production/using/audit-trail.md)。

下面介紹了監測不同市場活動流程的其他方法 [Campaign Classicv7生產指南](../../production/using/monitoring-guidelines.md)。

## 顯示進度 {#displaying-progress}

可以使用工具欄上的相應表徵圖顯示進度來監視執行。

的 **[!UICONTROL Display progress information]** 表徵圖用於在執行螢幕中顯示狀態和活動結果。

![](assets/s_user_segmentation_toolbar_progr.png)

選中此選項後，已執行的活動以藍色顯示，掛起的活動閃爍，警告以橙色顯示，錯誤以紅色顯示。 此選項還顯示活動在其出站轉移時的結果，後面是活動屬性中定義的結果標籤以及作業持續時間（如果超過一秒）

![](assets/s_user_segmentation_results.png)

## 顯示日誌 {#displaying-logs}

日誌包含工作流的歷史記錄或審核跟蹤。 它註冊所有用戶操作、執行的所有操作和遇到的錯誤。 您可以：

* 選擇 **[!UICONTROL Tracking]** 的子菜單。 此清單包含所有工作流消息。

   ![](assets/new-workflow-display-log-tab.png)

* 按活動篩選日誌消息。 要執行此操作，請按一下 **[!UICONTROL Display the tasks and the log]** 在圖上方的工具欄上，以顯示 **[!UICONTROL Log]** 和 **[!UICONTROL Tasks]** 頁籤。 選擇活動以查看所有相關消息。 未選擇活動時，此清單包含所有消息。

   ![](assets/new-workflow-display-log-activity.png)

   >[!NOTE]
   >
   >按一下圖的背景以取消選擇所有元素。

* 僅查看連結到給定任務的那些消息。 要執行此操作，請選擇 **[!UICONTROL Tasks]** ，然後在圖中選擇活動以限制清單。 按兩下任務顯示資訊；窗口中的最後一個頁籤包含日誌。

   ![](assets/new-workflow-display-tasks-activity.png)

   的 **[!UICONTROL Details...]** 按鈕，顯示有關活動執行的所有附加資訊。 例如，您可以查看驗證運算子，並在適用時查看它們在審批期間輸入的注釋，如下例所示：

   ![](assets/new-workflow-display-tasks-activity-details.png)

>[!NOTE]
>
>重新啟動工作流時，不會清除日誌。 所有消息都保留。 如果要放棄上次執行中的消息，必須清除歷史記錄。

日誌顯示與目標工作流活動相關的執行消息的時間清單。

* 目標市場活動的日誌

   執行目標市場活動後，按一下 **[!UICONTROL Tracking]** 頁籤。

   ![](assets/s_user_segmentation_journal.png)

   將顯示所有市場活動消息：進行的活動以及警告或錯誤。

* 活動日誌

   您還可以查看執行日誌和每個活動的詳細資訊。 有兩種方法：

   1. 選擇目標活動，然後按一下 **[!UICONTROL Display the tasks and the log]** 表徵圖

      ![](assets/s_user_segmentation_show_logs.png)

      圖的下部顯示兩個頁籤：日誌和任務。

      在圖中選擇的活動將作為日誌和任務清單的篩選器。

      ![](assets/s_user_segmentation_logs.png)

   1. 按一下右鍵目標活動並選擇 **[!UICONTROL Display logs]**。

      ![](assets/s_user_segmentation_logs_menu.png)

      日誌顯示在單獨的窗口中。

## 清除日誌 {#purging-the-logs}

工作流歷史記錄不會自動清除：預設情況下，所有消息都會保留。 歷史記錄可通過 **[!UICONTROL File > Actions]** 或 **[!UICONTROL Actions]** 按鈕。 選取 **[!UICONTROL Purge history]**。中的可用選項 **[!UICONTROL Actions]** 中 [操作工具欄](starting-a-workflow.md) 的子菜單。

![](assets/purge_historique.png)

## 工作表和工作流架構 {#worktables-and-workflow-schema}

該工作流傳送可通過某些活動操縱的工作表。 Adobe Campaign允許您通過資料管理活動修改、更名和豐富工作流工作表的列，例如，根據客戶的需要，使它們與術語相一致，以便收集有關合同共同受益人的附加資訊，等等。

還可以在各種工作維之間建立連結並定義維更改。 例如，對於資料庫中記錄的每份合同，向主持人地址並在附加資訊中使用共同持有人資料。

當工作流被鈍化時，工作流的工作表將自動被刪除。 如果希望保留工作表，請通過 **[!UICONTROL List update]** 活動(請參閱 [清單更新](list-update.md))。

## 管理錯誤 {#managing-errors}

出現錯誤時，工作流暫停，發生錯誤時正在執行的活動閃爍紅色。 在工作流概述中，在 **[!UICONTROL Monitoring]** 頁籤  **[!UICONTROL Workflows]** 連結，您只能顯示有錯誤的工作流，如下所示。

![](assets/wf-global-view_filter_only_errors.png)

在Adobe Campaign資源管理器中，工作流清單顯示 **[!UICONTROL Failed]** 列。

![](assets/wf-explorer_errors_col.png)

當工作流出錯時，只要其電子郵件地址列在其配置檔案中，就通過電子郵件通知屬於工作流監督組的操作員。 此組在 **[!UICONTROL Supervisor(s)]** 的子菜單。

![](assets/wf-properties_select-supervisors.png)

通知內容在 **[!UICONTROL Workflow manager notification]** 預設模板：此模板在 **[!UICONTROL Execution]** 頁籤。 通知顯示錯誤工作流的名稱和相關任務。

通知示例：

![](assets/wf-notification_error-msg.png)

該連結允許您以Web模式訪問Adobe Campaign控制台，並在登錄後處理錯誤工作流。

![](assets/wf-notification_error-console.png)

您可以配置工作流，以便在出現錯誤時不暫停並繼續執行。 為此，請編輯工作流 **[!UICONTROL Properties]** 在 **[!UICONTROL Error management]** 的 **[!UICONTROL Ignore]** 的上界 **[!UICONTROL In case of error]** 的子菜單。 然後，可以指定進程暫停前可忽略的連續錯誤數。

在這種情況下，錯誤任務被中止。 此模式特別適用於設計為稍後重新嘗試市場活動（定期操作）的工作流。

![](assets/wf_edit_properties_for_error_mgt.png)

>[!NOTE]
>
>您可以針對每個活動單獨應用此配置。 要執行此操作，請編輯活動屬性並在 **[!UICONTROL Advanced]** 頁籤。

有關工作流執行故障排除的詳細資訊，請參閱 [Campaign Classicv7生產指南](../../production/using/workflow-execution.md)。

## 處理錯誤 {#processing-errors}

關於活動， **[!UICONTROL Process errors]** 選項顯示在生成錯誤時將啟用的特定轉換。 在這種情況下，工作流不會進入錯誤模式並繼續執行。

考慮的錯誤包括檔案系統錯誤（無法移動檔案、無法訪問目錄等）。

此選項不處理與活動配置相關的錯誤，即無效值。 與錯誤配置相關的錯誤將不會啟用此轉換（目錄不存在等）。

如果暫停了工作流（在出錯後手動或自動）, **[!UICONTROL Start]** 按鈕將在停止工作流的位置重新啟動工作流執行。 將重新執行錯誤的活動（或暫停的活動）。 不會重新執行以前的活動。

要重新執行所有工作流活動，請使用 **[!UICONTROL Restart]** 按鈕

如果修改已執行的活動，則在重新啟動工作流執行時不會考慮這些更改。

如果修改未執行的活動，則在重新啟動工作流執行時會考慮這些活動。

如果修改暫停的活動，則在重新啟動工作流時無法正確考慮更改。

如果可能，建議在進行修改後完全重新啟動工作流。

## 實例監督 {#instance-supervision}

的 **[!UICONTROL Instance supervision]** 頁面，您可以查看Adobe Campaign伺服器活動並顯示工作流和交貨的清單，但有錯誤。

要訪問此頁，請轉到 **[!UICONTROL Monitoring]** ，然後按一下 **[!UICONTROL General view]** 的子菜單。

![](assets/wf-monitoring_from-homepage.png)

要顯示所有工作流，請按一下 **[!UICONTROL Workflows]** 的子菜單。 使用下拉清單根據工作流的狀態顯示平台中的工作流。

![](assets/wf-monitoring_edit-wf.png)

按一下工作流上出現錯誤的連結，以開啟該工作流並查看其日誌。

![](assets/wf-monitoring_edit-task-wf.png)

## 防止同時執行多個執行 {#preventing-simultaneous-multiple-executions}

單個工作流可以同時運行多個執行。 在某些情況下，你應該防止這種情況發生。

例如，您可以讓調度程式每小時觸發工作流執行，但有時整個工作流的執行需要超過一小時。 如果工作流已在運行，則可能要跳過執行。

如果在工作流的開始處有信號活動，則如果工作流正在運行，則可能要跳過該信號。

一般原則是：

![](assets/workflow-reentrancy-protection-principle.png)

解決方案是使用實例變數。 實例變數由工作流的所有並行執行共用。

下面是一個簡單的test工作流：

![](assets/wkf_simultaneous_execution1.png)

的 **[!UICONTROL Scheduler]** 每分鐘都會觸發一個事件。 以下 **[!UICONTROL Test]** 活動將test **正在運行** 用於決定是否繼續執行的實例變數：

![](assets/wkf_simultaneous_execution2.png)

>[!NOTE]
>
>**正在運行** 是為此示例選擇的變數名稱。 這不是內置變數。

緊跟於 **[!UICONTROL Test]** 的 **是** 分支必須在其中設定實例變數 **初始化指令碼**:

```
instance.vars.isRunning = true
```

中的最後一個活動 **是** 分支必須將變數在其中還原為false **初始化指令碼**:

```
instance.vars.isRunning = false
```

請注意：

* 可通過 **變數** 頁籤 **屬性**。
* 重新啟動工作流時，實例變數將被重置。
* 在JavaScript中，未定義的值在test中為false，允許在初始化實例變數之前對其進行test。
* 通過向「否」結束的初始化指令碼添加日誌記錄指令，可以監視因此機制而未處理的活動。

   ```
   logInfo("Workflow already running, parallel execution not allowed.");
   ```

本節將介紹一個使用案例： [協調資料更新](coordinating-data-updates.md)。

## 資料庫維護 {#database-maintenance}

工作流使用大量工作表，這些工作表佔用空間，如果不進行維護，最終會減慢整個平台的速度。 有關資料庫維護的詳細資訊，請參閱 [節](../../production/using/tables-to-maintain.md) 。

的 **資料庫清理** 可通過 **管理>生產>技術工作流** 節點，用於刪除過時的資料以避免資料庫的指數增長。 工作流自動觸發，無需用戶干預。 請參閱 [Campaign Classicv7生產指南](../../production/using/database-cleanup-workflow.md)。

您還可以建立特定的技術工作流來清除不必要的資料佔用空間。 請參閱 [Campaign Classicv7生產指南](../../production/using/application-objects.md) 和 [節](#purging-the-logs)。

## 處理暫停的工作流 {#handling-of-paused-workflows}

預設情況下，如果某個工作流已暫停，則其工作表將從不清除。 從build 8880中，處於暫停狀態太長的工作流將自動停止，並清除其工作表。 此行為觸發方式如下：

* 自超過7天以來已暫停的工作流在監視儀表板（和監視API）中顯示為警告，並將通知發送到監視組。
* 每週，當 **[!UICONTROL cleanupPausedWorkflows]** 技術工作流被觸發。 有關工作流的詳細資訊，請參閱 [此部分](delivery.md)。
* 在4個通知（即預設處於暫停狀態一個月）後，將無條件停止工作流。 停止工作流後，將在工作流中顯示日誌。 在下次執行時清除這些表 **[!UICONTROL cleanup]** 工作流

可通過NmsServer_PausedWorkflowPeriod選項配置這些期間。

將通知工作流主管。 還會通知建立者和修改工作流的最後用戶。 管理員不接收通知。

## 根據工作流的狀態篩選工作流 {#filtering-workflows-status}

Campaign Classic介面允許您使用預定義的介面監視實例上所有工作流的執行狀態 **視圖**。 要訪問這些視圖，請開啟 **[!UICONTROL Administration]** / **[!UICONTROL Audit]** / **[!UICONTROL Workflows Status]** 的下界。

以下視圖可用：

* **[!UICONTROL Running]**：列出所有正在運行的工作流。
* **[!UICONTROL Paused]**：列出所有暫停的工作流。
* **[!UICONTROL Failed]**：列出所有失敗的工作流。
* **[!UICONTROL Start Pending]**：列出操作管理進程正在等待啟動的所有工作流。 此視圖可用於 **市場營銷活動** 僅包。 瞭解詳情 [Campaign Classicv7安裝指南](../../installation/using/installing-campaign-standard-packages.md))。

![](assets/workflow-monitoring-views.png)

預設情況下，在 **[!UICONTROL Audit]** 的子菜單。 但是，可以在資料夾樹中所選的位置重新建立它們。 這樣，它們就可供沒有管理權限的標準用戶使用。

要執行此操作：

1. 按一下右鍵要添加視圖的資料夾。
1. 在 **[!UICONTROL Add new folder]** / **[!UICONTROL Administration]**，選擇要添加的視圖。
1. 將資料夾添加到樹後，請確保將其配置為視圖，以便它顯示所有工作流，無論其來源資料夾是什麼。有關如何配置視圖的詳細資訊，請參閱 [此部分](../../platform/using/access-management-folders.md)。

除了這些視圖外，您還可以設定篩選器資料夾，以便根據工作流的執行狀態篩選工作流清單。 操作步驟：

1. 訪問工作流類型資料夾，然後選擇 **[!UICONTROL Filters]** / **[!UICONTROL Advanced filter]** 的子菜單。
1. 配置篩選器，以便工作流 **[!UICONTROL @status]** 欄位等於您選擇的狀態。
1. 保存並命名篩選器。 然後，它將直接從篩選器清單中可用。

![](assets/workflow-monitoring-filter.png)

有關詳細資訊，請參閱以下各節：

* [建立高級篩選器](../../platform/using/creating-filters.md#creating-an-advanced-filter)
* [保存篩選器](../../platform/using/creating-filters.md#saving-a-filter)
