---
title: 工作流程屬性
seo-title: 工作流程屬性
description: 工作流程屬性
seo-description: null
page-status-flag: never-activated
uuid: bd576cc0-2db8-4519-bcb5-52bf5c811f42
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: 71969b30-cc01-4358-9597-f17939720684
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 工作流程屬性{#workflow-properties}

## 「執行」頁籤 {#execution-tab}

工作流 **[!UICONTROL Execution]** 中窗口的 **[!UICONTROL Properties]** 頁籤分為3個部分：

![](assets/wf_execution_tab.png)

### 排程器 {#scheduler}

此區段只會顯示在促銷活動工作流程中。

* **[!UICONTROL Priority]**

   工作流引擎根據此欄位中定義的優先順序標準處理要執行的工作流。 例如，所有具有優先順序的 **[!UICONTROL Average]** 工作流程都會先於具有優先順序的工 **[!UICONTROL Low]** 作流程。

* **[!UICONTROL Schedule execution for a time of low activity]**

   此選項會將工作流程開始時間推遲至較不繁忙的時段。 有些工作流程在資料庫引擎的資源方面可能十分昂貴。 我們建議將執行時間排定在低活動時間（例如晚上）。 低活動期限是在技術工作流程中 **[!UICONTROL Processes on campaigns]** 定義的。

### 執行 {#execution}

* **[!UICONTROL Default affinity]**

   如果您的安裝包含數個工作流程伺服器，請使用此欄位來選擇要執行工作流程的機器。 如果此欄位中定義的值不存在於任何伺服器上，工作流程將維持擱置狀態。

   請參閱本 [節](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)。

* **[!UICONTROL History in days]**

   資料庫的工作表保留執行的歷史記錄（任務、事件、日誌）。 您可以在此處定義要為此工作流存檔的天數：清理過程將每天刪除最舊的存檔一次。 如果此欄位中的值為零，則不會刪除封存檔。

* **[!UICONTROL Log SQL queries in the journal]**

   此功能保留給進階使用者。 它涉及包含定位活動（查詢、聯合、交叉點等）的工作流程。 勾選此選項時，在工作流程執行期間傳送至資料庫的SQL查詢會顯示在Adobe Campaign中：這表示您可以分析查詢或診斷問題。

   查詢會顯示在 **[!UICONTROL SQL logs]** 新增至工作流程（促銷活動工作流程除外）的標籤中，以及啟用選 **[!UICONTROL Properties]** 項時顯示至活動。 該選 **[!UICONTROL Audit]** 項卡還包括SQL查詢。

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   此選項只能用於除錯，絕不能用於生產。 啟用後，工作流將優先，所有其他工作流將停止，直到此工作流完成。

### 錯誤管理 {#error-management}

* **[!UICONTROL Troubleshooting]**

   此欄位可讓您定義在工作流程任務發生錯誤時要執行的動作。 有兩種可能的選項：

   * **[!UICONTROL Stop the process]**:工作流程會自動暫停。 工作流狀態將更改為 **[!UICONTROL Failed]**。 問題解決後，請使用或按鈕重新啟動工 **[!UICONTROL Start]** 作 **[!UICONTROL Restart]** 流程。
   * **[!UICONTROL Ignore]**:觸發錯誤的任務的狀態將更改為 **[!UICONTROL Failed]**，但工作流將保留狀 **[!UICONTROL Started]** 態。 此配置與循環任務相關：如果分支包含調度程式，則下次執行工作流時，它將正常啟動。

* **[!UICONTROL Consecutive errors]**

   當在欄位中選取值 **[!UICONTROL Ignore]** 時，此欄位就可 **[!UICONTROL In case of errors]** 用。 您可以指定在停止進程之前可以忽略的錯誤數。 到達此數字後，工作流狀態將更改為 **[!UICONTROL Failed]**。 如果此欄位的值為0，則無論錯誤數為何，工作流程都不會停止。

* **[!UICONTROL Template]**

   此欄位可讓您選擇通知範本，當其狀態變更為時，傳送給工作流主管 **[!UICONTROL Failed]**。

   如果相關營運商的個人檔案中有電子郵件地址，他們會收到電子郵件通知。 要定義工作流主管，請轉至屬 **[!UICONTROL Supervisor(s)]** 性（頁籤）的&#x200B;**[!UICONTROL General]** 欄位。

   ![](assets/wf-properties_select-supervisors.png)

   預 **[!UICONTROL Notification to a workflow supervisor]** 設範本包含透過網路存取Adobe Campaign主控台的連結，讓收件者在登入後即可處理問題。

   若要建立個人化範本，請前往 **[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**。

