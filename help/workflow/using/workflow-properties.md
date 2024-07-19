---
product: campaign
title: 工作流程屬性
description: 進一步瞭解Campaign工作流程屬性
feature: Workflows
exl-id: c7bff902-4f5d-4783-aec4-13561fa7d242
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 38%

---

# 工作流程屬性{#workflow-properties}



## 執行標籤 {#execution-tab}

工作流程中&#x200B;**[!UICONTROL Properties]**&#x200B;視窗的&#x200B;**[!UICONTROL Execution]**&#x200B;標籤分為3個區段：

![](assets/wf_execution_tab.png)

### 排程器 {#scheduler}

此區段僅會顯示在行銷活動工作流程中。

* **[!UICONTROL Priority]**

  工作流程引擎會根據此欄位中定義的優先順序條件，處理要執行的工作流程。 例如，所有優先順序為&#x200B;**[!UICONTROL Average]**&#x200B;的工作流程都會在優先順序為&#x200B;**[!UICONTROL Low]**&#x200B;的工作流程之前執行。

* **[!UICONTROL Schedule execution for a time of low activity]**

  此選項會將工作流程開始延遲到較不繁忙的期間。 有些工作流程可能會耗費資料庫引擎的資源。 我們建議將執行排程定於活動較少的時間（例如，在晚上）。 已在&#x200B;**[!UICONTROL Processes on campaigns]**&#x200B;技術工作流程中定義低活動期間。

### 執行 {#execution}

* **[!UICONTROL Default affinity]**

  如果您的安裝包括多個工作流程伺服器，請使用此欄位選擇工作流程將在其中執行的電腦。如果在此欄位定義的值不存在於任何伺服器，工作流程將保持待處理狀態。

  請參閱此[Campaign Classicv7安裝指南](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)。

* **[!UICONTROL History in days]**

  資料庫的工作表會保留執行專案的歷史記錄（工作、事件、記錄）。 您可以在此處定義此工作流程的封存天數：清除程序會每天刪除一次最舊的封存檔。如果此欄位的值為零，則永遠不會刪除封存檔。

* **[!UICONTROL Log SQL queries in the journal]**

  此功能保留給進階使用者使用。它涉及包含目標定位活動 (查詢、聯合、交集等) 的工作流程。勾選此選項後，在工作流程執行期間傳送到資料庫的 SQL 查詢將顯示在 Adobe Campaign 中：這表示您可以分析它們以最佳化查詢或診斷問題。

  當選項啟用時，查詢會顯示在&#x200B;**[!UICONTROL SQL logs]**&#x200B;索引標籤中，該索引標籤已新增至工作流程（行銷活動工作流程除外）和&#x200B;**[!UICONTROL Properties]**&#x200B;活動。 **[!UICONTROL Audit]**&#x200B;索引標籤也包含SQL查詢。

  ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

  此選項只能用於除錯，絕不可用於生產。 啟用時，工作流程會獲得優先順序，而所有其他工作流程會一直停止，直到此工作流程完成。

### 錯誤管理 {#error-management}

* **[!UICONTROL Troubleshooting]**

  此欄位可讓您定義工作流程的任務發生錯誤時要採取的動作。您有兩個選擇：

   * **[!UICONTROL Stop the process]**：工作流程已自動暫停。 工作流程狀態變更為&#x200B;**[!UICONTROL Failed]**。 問題解決後，使用&#x200B;**[!UICONTROL Start]**&#x200B;或&#x200B;**[!UICONTROL Restart]**&#x200B;按鈕重新啟動工作流程。
   * **[!UICONTROL Ignore]**：觸發錯誤的工作狀態變更為&#x200B;**[!UICONTROL Failed]**，但工作流程會保留&#x200B;**[!UICONTROL Started]**&#x200B;狀態。 此設定與週期性任務相關：如果分支包含排程器，它將在下次工作流程執行時正常啟動。

* **[!UICONTROL Consecutive errors]**

  在&#x200B;**[!UICONTROL In case of errors]**&#x200B;欄位中選取&#x200B;**[!UICONTROL Ignore]**&#x200B;值時，此欄位將變為可用。 您可以指定程序停止之前可以忽略的錯誤數。一旦達到此數目，工作流程狀態就會變更為&#x200B;**[!UICONTROL Failed]**。 如果此欄位的值為 0，則無論錯誤數為何，工作流程都不會停止。

* **[!UICONTROL Template]**

  此欄位可讓您選取當工作流程主管的狀態變更為&#x200B;**[!UICONTROL Failed]**&#x200B;時，要傳送給其的通知範本。

  如果相關操作員的設定檔中有電子郵件地址，則會以電子郵件通知相關操作員。 若要定義工作流程監督員，請移至屬性（**[!UICONTROL General]**&#x200B;標籤）的&#x200B;**[!UICONTROL Supervisor(s)]**&#x200B;欄位。

  ![](assets/wf-properties_select-supervisors.png)

  **[!UICONTROL Notification to a workflow supervisor]**&#x200B;預設範本包含透過網頁存取Adobe Campaign主控台的連結，讓收件者可以在登入後處理問題。

  若要建立個人化範本，請移至&#x200B;**[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**。
