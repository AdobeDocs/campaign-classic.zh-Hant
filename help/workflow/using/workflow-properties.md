---
product: campaign
title: 工作流程屬性
description: 深入了解Campaign工作流程屬性
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: c7bff902-4f5d-4783-aec4-13561fa7d242
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 38%

---

# 工作流程屬性{#workflow-properties}



## 「執行」頁簽 {#execution-tab}

此 **[!UICONTROL Execution]** 的 **[!UICONTROL Properties]** 視窗可劃分為3個區段：

![](assets/wf_execution_tab.png)

### 排程器 {#scheduler}

此區段只會顯示在行銷活動工作流程中。

* **[!UICONTROL Priority]**

   工作流程引擎根據此欄位中定義的優先順序准則來處理要執行的工作流程。 例如，所有包含 **[!UICONTROL Average]** 優先順序將在具有 **[!UICONTROL Low]** 優先順序。

* **[!UICONTROL Schedule execution for a time of low activity]**

   此選項會將工作流程開始延遲至較閒的時段。 就資料庫引擎的資源而言，某些工作流程可能成本高昂。 建議將執行時間排定在活動量較低的時間（例如在晚上）。 低活動期間定義於 **[!UICONTROL Processes on campaigns]** 技術工作流程。

### 執行 {#execution}

* **[!UICONTROL Default affinity]**

   如果您的安裝包括多個工作流程伺服器，請使用此欄位選擇工作流程將在其中執行的電腦。如果在此欄位定義的值不存在於任何伺服器，工作流程將保持待處理狀態。

   請參閱 [Campaign Classicv7安裝指南](../../installation/using/configuring-campaign-server.md#high-availability-workflows-and-affinities).

* **[!UICONTROL History in days]**

   資料庫的工作表保留執行的歷史記錄（任務、事件、日誌）。 您可以在此處定義此工作流程的封存天數：清除程序會每天刪除一次最舊的封存檔。如果此欄位的值為零，則永遠不會刪除封存檔。

* **[!UICONTROL Log SQL queries in the journal]**

   此功能保留給進階使用者使用。它涉及包含目標定位活動 (查詢、聯合、交集等) 的工作流程。勾選此選項後，在工作流程執行期間傳送到資料庫的 SQL 查詢將顯示在 Adobe Campaign 中：這表示您可以分析它們以最佳化查詢或診斷問題。

   查詢會顯示在 **[!UICONTROL SQL logs]** 標籤，此標籤會新增至工作流程（促銷活動工作流程除外）和 **[!UICONTROL Properties]** 活動。 此 **[!UICONTROL Audit]** 索引標籤也包含SQL查詢。

   ![](assets/wf_tab_log_sql.png)

* **[!UICONTROL Execute in the engine]**

   此選項只能用於除錯，絕不能用於生產。 啟用後，工作流程會優先處理，而所有其他工作流程會停止，直到完成此工作流程為止。

### 錯誤管理 {#error-management}

* **[!UICONTROL Troubleshooting]**

   此欄位可讓您定義工作流程的任務發生錯誤時要採取的動作。您有兩個選擇：

   * **[!UICONTROL Stop the process]**:工作流程會自動暫停。 工作流程狀態變更為 **[!UICONTROL Failed]**. 問題解決後，請使用 **[!UICONTROL Start]** 或 **[!UICONTROL Restart]** 按鈕。
   * **[!UICONTROL Ignore]**:觸發錯誤的任務的狀態更改為 **[!UICONTROL Failed]**，但工作流程會保留 **[!UICONTROL Started]** 狀態。 此設定與週期性任務相關：如果分支包含排程器，它將在下次工作流程執行時正常啟動。

* **[!UICONTROL Consecutive errors]**

   此欄位在 **[!UICONTROL Ignore]** 值 **[!UICONTROL In case of errors]** 欄位。 您可以指定程序停止之前可以忽略的錯誤數。達到此數字後，工作流程狀態會變更為 **[!UICONTROL Failed]**. 如果此欄位的值為 0，則無論錯誤數為何，工作流程都不會停止。

* **[!UICONTROL Template]**

   此欄位可讓您選取當工作流程主管的狀態變更為 **[!UICONTROL Failed]**.

   若相關營運人員的設定檔中有電子郵件地址，則會以電子郵件通知。 要定義工作流主管，請轉至 **[!UICONTROL Supervisor(s)]** 屬性欄位(**[!UICONTROL General]** 標籤)。

   ![](assets/wf-properties_select-supervisors.png)

   此 **[!UICONTROL Notification to a workflow supervisor]** 預設範本包含透過網頁存取Adobe Campaign主控台的連結，讓收件者在登入後即可處理問題。

   若要建立個人化範本，請前往 **[!UICONTROL Administration>Campaign management>Technical deliveries and templates]**.
