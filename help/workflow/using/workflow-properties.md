---
product: campaign
title: 工作流程屬性
description: 瞭解有關市場活動工作流屬性的詳細資訊
feature: Workflows
exl-id: c7bff902-4f5d-4783-aec4-13561fa7d242
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 1%

---

# 工作流程屬性{#workflow-properties}

![](../../assets/v7-only.svg)

## 「執行」頁籤 {#execution-tab}

的 **[!UICONTROL Execution]** 頁籤 **[!UICONTROL Properties]** 將工作流中的窗口分為3個部分：

![](assets/wf_execution_tab.png)

### 排程器 {#scheduler}

此部分僅顯示在市場活動工作流中。

* **[!UICONTROL Priority]**

   工作流引擎根據此欄位中定義的優先順序標準處理要執行的工作流。 例如，所有具有 **[!UICONTROL Average]** 優先順序將先於 **[!UICONTROL Low]** 優先順序。

* **[!UICONTROL Schedule execution for a time of low activity]**

   此選項將工作流開始時間推遲到較少的忙時間。 某些工作流在資料庫引擎的資源方面可能成本高昂。 我們建議將執行時間安排在低活動時間（例如晚上）。 低活動期間在 **[!UICONTROL Processes on campaigns]** 技術工作流。

### 執行 {#execution}

* **[!UICONTROL Default affinity]**

   如果您的安裝包括多個工作流伺服器，請使用此欄位選擇將在其上執行工作流的電腦。 如果此欄位中定義的值在任何伺服器上都不存在，則工作流將保持掛起狀態。

   請參閱此 [Campaign Classicv7安裝指南](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)。

* **[!UICONTROL History in days]**

   資料庫的工作表保留執行的歷史記錄（任務、事件、日誌）。 在此，您可以定義要存檔此工作流的天數：清除過程將每天刪除最舊的存檔一次。 如果此欄位中的值為零，則將永遠不刪除存檔。

* **[!UICONTROL Log SQL queries in the journal]**

   此功能保留給高級用戶。 它涉及包含目標活動（查詢、聯合、交叉點等）的工作流。 選中此選項後，工作流執行期間發送到資料庫的SQL查詢將顯示在Adobe Campaign:這意味著您可以分析查詢或診斷問題。

   查詢顯示在 **[!UICONTROL SQL logs]** 頁籤，添加到工作流（市場活動工作流除外）和 **[!UICONTROL Properties]** 選項時執行。 的 **[!UICONTROL Audit]** 頁籤還包括SQL查詢。

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   此選項只能用於卸貨，不能用於生產。 啟用後，工作流將優先，並且所有其他工作流將停止，直到此工作流完成。

### 錯誤管理 {#error-management}

* **[!UICONTROL Troubleshooting]**

   此欄位用於定義在工作流任務有錯誤時要執行的操作。 有兩種可能的選擇：

   * **[!UICONTROL Stop the process]**:工作流將自動暫停。 工作流狀態更改為 **[!UICONTROL Failed]**。 問題解決後，使用 **[!UICONTROL Start]** 或 **[!UICONTROL Restart]** 按鈕。
   * **[!UICONTROL Ignore]**:觸發錯誤更改的任務的狀態 **[!UICONTROL Failed]**，但工作流保留 **[!UICONTROL Started]** 狀態。 此配置與循環任務相關：如果分支包含調度程式，則在下次執行工作流時，它將正常啟動。

* **[!UICONTROL Consecutive errors]**

   當 **[!UICONTROL Ignore]** 值 **[!UICONTROL In case of errors]** 的子菜單。 您可以指定在進程停止之前可以忽略的錯誤數。 一旦達到此數字，工作流狀態將更改為 **[!UICONTROL Failed]**。 如果此欄位的值為0，則無論錯誤數如何，都不會停止工作流。

* **[!UICONTROL Template]**

   此欄位允許您選擇在工作流主管的狀態更改為 **[!UICONTROL Failed]**。

   如果其個人資料中有電子郵件地址，將通過電子郵件通知有關操作員。 要定義工作流主管，請轉到 **[!UICONTROL Supervisor(s)]** 欄位(**[!UICONTROL General]** )的正平方根。

   ![](assets/wf-properties_select-supervisors.png)

   的 **[!UICONTROL Notification to a workflow supervisor]** 預設模板包括通過Web訪問Adobe Campaign控制台的連結，以便收件人登錄後可以處理此問題。

   要建立個性化模板，請轉到 **[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**。
