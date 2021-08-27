---
product: campaign
title: 工作流程屬性
description: 深入了解Campaign工作流程屬性
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: c7bff902-4f5d-4783-aec4-13561fa7d242
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 1%

---

# 工作流程屬性{#workflow-properties}

![](../../assets/common.svg)

## 「執行」頁簽 {#execution-tab}

工作流程中&#x200B;**[!UICONTROL Properties]**&#x200B;視窗的&#x200B;**[!UICONTROL Execution]**&#x200B;標籤分為3個區段：

![](assets/wf_execution_tab.png)

### 排程器 {#scheduler}

此區段只會顯示在行銷活動工作流程中。

* **[!UICONTROL Priority]**

   工作流程引擎根據此欄位中定義的優先順序准則來處理要執行的工作流程。 例如，所有具有&#x200B;**[!UICONTROL Average]**&#x200B;優先順序的工作流程將在具有&#x200B;**[!UICONTROL Low]**&#x200B;優先順序的工作流程之前執行。

* **[!UICONTROL Schedule execution for a time of low activity]**

   此選項會將工作流程開始延遲至較閒的時段。 就資料庫引擎的資源而言，某些工作流程可能成本高昂。 建議將執行時間排定在活動量較低的時間（例如在晚上）。 在&#x200B;**[!UICONTROL Processes on campaigns]**&#x200B;技術工作流程中定義低活動期間。

### 執行 {#execution}

* **[!UICONTROL Default affinity]**

   如果您的安裝包含數個工作流程伺服器，請使用此欄位來選擇要執行工作流程的電腦。 如果此欄位中定義的值在任何伺服器上都不存在，工作流程將保持擱置狀態。

   請參閱本[Campaign Classicv7安裝指南](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)。

* **[!UICONTROL History in days]**

   資料庫的工作表保留執行的歷史記錄（任務、事件、日誌）。 您可以在此處定義要為此工作流程封存的天數：清除程式會每天刪除最舊的封存一次。 如果此欄位中的值為零，則不會刪除封存。

* **[!UICONTROL Log SQL queries in the journal]**

   此功能已保留給進階使用者。 它與包含定位活動（查詢、聯合、交集等）的工作流程有關。 核取此選項時，工作流程執行期間傳送至資料庫的SQL查詢會顯示在Adobe Campaign中：這表示您可以分析查詢，以最佳化查詢或診斷問題。

   查詢會顯示在&#x200B;**[!UICONTROL SQL logs]**&#x200B;索引標籤中，當選項啟用時，該索引標籤會新增至工作流程（促銷活動工作流程除外）和&#x200B;**[!UICONTROL Properties]**&#x200B;活動。 **[!UICONTROL Audit]**&#x200B;標籤還包含SQL查詢。

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   此選項只能用於除錯，絕不能用於生產。 啟用後，工作流程會優先處理，而所有其他工作流程會停止，直到完成此工作流程為止。

### 錯誤管理 {#error-management}

* **[!UICONTROL Troubleshooting]**

   此欄位可讓您定義在工作流程任務發生錯誤時要採取的動作。 有兩種可能的選項：

   * **[!UICONTROL Stop the process]**:工作流程會自動暫停。工作流狀態將更改為&#x200B;**[!UICONTROL Failed]**。 問題解決後，使用&#x200B;**[!UICONTROL Start]**&#x200B;或&#x200B;**[!UICONTROL Restart]**&#x200B;按鈕重新啟動工作流。
   * **[!UICONTROL Ignore]**:觸發錯誤的任務的狀態將更改為， **[!UICONTROL Failed]**&#x200B;但工作流將保留 **[!UICONTROL Started]** 狀態。此設定與循環任務相關：如果分支包含排程器，則下次執行工作流程時，該分支將正常啟動。

* **[!UICONTROL Consecutive errors]**

   在&#x200B;**[!UICONTROL In case of errors]**&#x200B;欄位中選取&#x200B;**[!UICONTROL Ignore]**&#x200B;值時，此欄位便可用。 您可以指定在停止進程之前可忽略的錯誤數。 達到此數字後，工作流程狀態會變更為&#x200B;**[!UICONTROL Failed]**。 如果此欄位的值為0，則無論錯誤數量多寡，工作流程都將永不停止。

* **[!UICONTROL Template]**

   此欄位可讓您選取當工作流程主管的狀態變更為&#x200B;**[!UICONTROL Failed]**&#x200B;時要傳送給其的通知範本。

   若相關營運人員的設定檔中有電子郵件地址，則會以電子郵件通知。 要定義工作流監管程式，請轉至屬性的&#x200B;**[!UICONTROL Supervisor(s)]**&#x200B;欄位（**[!UICONTROL General]**&#x200B;標籤）。

   ![](assets/wf-properties_select-supervisors.png)

   **[!UICONTROL Notification to a workflow supervisor]**&#x200B;預設範本包含可透過Web存取Adobe Campaign主控台的連結，讓收件者在登入後即可處理問題。

   若要建立個人化範本，請前往&#x200B;**[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**。
