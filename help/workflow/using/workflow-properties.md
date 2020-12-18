---
solution: Campaign Classic
product: campaign
title: 工作流程屬性
description: 進一步瞭解促銷活動工作流程屬性
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 1%

---


# 工作流程屬性{#workflow-properties}

## 執行頁籤{#execution-tab}

工作流中&#x200B;**[!UICONTROL Properties]**&#x200B;窗口的&#x200B;**[!UICONTROL Execution]**&#x200B;頁籤分為3個部分：

![](assets/wf_execution_tab.png)

### 排程器 {#scheduler}

此區段只會顯示在促銷活動工作流程中。

* **[!UICONTROL Priority]**

   工作流引擎根據此欄位中定義的優先順序標準處理要執行的工作流。 例如，所有具有&#x200B;**[!UICONTROL Average]**&#x200B;優先順序的工作流將在具有&#x200B;**[!UICONTROL Low]**&#x200B;優先順序的工作流之前執行。

* **[!UICONTROL Schedule execution for a time of low activity]**

   此選項會將工作流程開始時間推遲至較不繁忙的時段。 有些工作流程在資料庫引擎的資源方面可能十分昂貴。 我們建議將執行時間排定在低活動時間（例如晚上）。 低活動期限在&#x200B;**[!UICONTROL Processes on campaigns]**&#x200B;技術工作流程中定義。

### 執行 {#execution}

* **[!UICONTROL Default affinity]**

   如果您的安裝包含數個工作流程伺服器，請使用此欄位來選擇要執行工作流程的機器。 如果此欄位中定義的值不存在於任何伺服器上，工作流程將維持擱置狀態。

   請參閱此[節](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities)。

* **[!UICONTROL History in days]**

   資料庫的工作表保留執行的歷史記錄（任務、事件、日誌）。 您可以在此處定義要為此工作流存檔的天數：清理過程將每天刪除最舊的存檔一次。 如果此欄位中的值為零，則不會刪除封存檔。

* **[!UICONTROL Log SQL queries in the journal]**

   此功能保留給進階使用者。 它涉及包含定位活動（查詢、聯合、交叉點等）的工作流程。 勾選此選項時，在工作流程執行期間傳送至資料庫的SQL查詢會顯示在Adobe Campaign中：這表示您可以分析查詢或診斷問題。

   查詢會顯示在&#x200B;**[!UICONTROL SQL logs]**&#x200B;標籤中，此標籤會新增至工作流程（促銷活動工作流程除外）和&#x200B;**[!UICONTROL Properties]**&#x200B;活動（啟用選項時）。 **[!UICONTROL Audit]**&#x200B;頁籤還包括SQL查詢。

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   此選項只能用於除錯，絕不能用於生產。 啟用後，工作流將優先，所有其他工作流將停止，直到此工作流完成。

### 錯誤管理{#error-management}

* **[!UICONTROL Troubleshooting]**

   此欄位可讓您定義在工作流程任務發生錯誤時要執行的動作。 有兩種可能的選項：

   * **[!UICONTROL Stop the process]**:工作流程會自動暫停。工作流狀態更改為&#x200B;**[!UICONTROL Failed]**。 問題解決後，請使用&#x200B;**[!UICONTROL Start]**&#x200B;或&#x200B;**[!UICONTROL Restart]**&#x200B;按鈕重新啟動工作流程。
   * **[!UICONTROL Ignore]**:觸發錯誤的任務的狀態將更改為 **[!UICONTROL Failed]**，但工作流將保留 **[!UICONTROL Started]** 狀態。此配置與循環任務相關：如果分支包含調度程式，則下次執行工作流時，它將正常啟動。

* **[!UICONTROL Consecutive errors]**

   當在&#x200B;**[!UICONTROL In case of errors]**&#x200B;欄位中選取&#x200B;**[!UICONTROL Ignore]**&#x200B;值時，此欄位便可使用。 您可以指定在停止進程之前可以忽略的錯誤數。 到達此編號後，工作流狀態將更改為&#x200B;**[!UICONTROL Failed]**。 如果此欄位的值為0，則無論錯誤數為何，工作流程都不會停止。

* **[!UICONTROL Template]**

   此欄位允許您選擇當工作流主管的狀態更改為&#x200B;**[!UICONTROL Failed]**&#x200B;時要發送給其的通知模板。

   如果相關營運商的個人檔案中有電子郵件地址，他們會收到電子郵件通知。 要定義工作流主管，請轉至屬性的&#x200B;**[!UICONTROL Supervisor(s)]**&#x200B;欄位（**[!UICONTROL General]**&#x200B;頁籤）。

   ![](assets/wf-properties_select-supervisors.png)

   **[!UICONTROL Notification to a workflow supervisor]**&#x200B;預設範本包含透過網路存取Adobe Campaign主控台的連結，讓收件者在登入後即可處理問題。

   若要建立個人化範本，請前往&#x200B;**[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**。

