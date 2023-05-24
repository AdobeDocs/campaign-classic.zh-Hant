---
product: campaign
title: 工作流程最佳實務
description: 瞭解行銷活動工作流程最佳實務
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 39c57f61-2629-4214-91e4-cb97dc039deb
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1687'
ht-degree: 12%

---

# 工作流程最佳實務{#workflow-best-practices}



## 執行與效能 {#execution-and-performance}

以下列出最佳化Campaign效能的一般准則，包括套用至工作流程的最佳實務。

與工作流程執行相關的疑難排解指南也可在以下網址取得： [Campaign Classic v7生產指南](../../production/using/workflow-execution.md).

### 記錄 {#logs}

JavaScript方法 **[!UICONTROL logInfo()]** 是工作流程除錯的絕佳解決方案。 它很有用，但必須謹慎使用，尤其是經常執行的活動：它可能會讓記錄超載，並顯著增加記錄表格的大小。 但您可能還需要 **[!UICONTROL logInfo()]**.

另外兩種解決方案可提供協助：

* **保留兩次執行之間的中期族群結果**

   此選項會保留工作流程兩個執行之間的臨時表格。 它可在工作流程屬性中使用 **[!UICONTROL General]** 標籤，和可用於開發和測試目的，以監控資料及檢查結果。 您可以在開發環境中使用此選項，但切勿在生產環境中使用它。保留臨時表能會導致資料庫顯著變大，最終會達到上限。此外，它會減慢備份速度。

   只保留最後一次執行工作流程的工作表。先前執行的工作表會由清除 **[!UICONTROL cleanup]** 工作流程，每日執行。

   >[!CAUTION]
   >
   >在生產工作流程中，請勿勾選此選項。 此選項用於分析結果，且僅供用於測試目的，因此只能在開發或中繼環境中使用。

* **在日誌中記錄 SQL 查詢**

   可在以下位置取得： **[!UICONTROL Execution]** 標籤中，此選項會記錄工具從不同活動產生的所有SQL查詢。 這是檢視平台實際執行動作的好方法。 不過，此選項只應在開發期間暫時使用，而不應在生產環境中啟用。

當不再需要記錄時，請清除這些記錄。 系統不會自動清除工作流程歷史記錄：所有訊息都會依預設保留。 您可以透過以下方式清除歷史記錄 **[!UICONTROL File > Actions]** 功能表，或按一下位於清單上方工具列中的「動作」按鈕。 選取清除歷史記錄。
若要瞭解如何清除記錄檔，請參閱此 [檔案](starting-a-workflow.md).

### 工作流程規劃 {#workflow-planning}

* 請試著在一天內維持穩定的活動水準，並避免尖峰，以防止執行個體過載。 若要這麼做，請在一天中平均分配工作流程開始時間。
* 排程資料載入隔夜以減少資源爭用。
* 長的工作流程可能會對伺服器和資料庫資源造成影響。 分割最長的工作流程，以減少處理時間。
* 為縮短整體執行時間，請以簡化且更快的活動來取代耗時的活動。
* 避免同時執行超過20個工作流程。 如果同時執行太多工作流程，系統可能會耗盡資源並變得不穩定。 有關工作流程可能未啟動原因的詳細資訊，請參閱此 [文章](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html).

### 工作流程執行 {#workflow-execution}

**請勿將工作流程排程為超過每15分鐘執行一次** 因為它可能會阻礙整體系統效能，並在資料庫中建立區塊。

**避免讓工作流程處於暫停狀態**. 如果您建立臨時工作流程，請確定它能夠正確完成並且不會停留在 **[!UICONTROL paused]** 州別。 如果暫停，則表示您需要保留臨時表格，因此會增加資料庫的大小。 在「工作流程屬性」下指定「工作流程主管」，以便在工作流程失敗或系統暫停時傳送警報。

若要避免工作流程處於暫停狀態：

* 請定期檢查您的工作流程，以確保沒有未預期的錯誤。
* 儘可能簡化工作流程，例如將大型工作流程分割為數個不同的工作流程。 您可以使用 **[!UICONTROL External signal]** 活動會根據其他工作流程的執行來觸發其執行。
* 請避免在工作流程中停用流程的活動，讓執行緒保持開啟狀態，並導致許多可能會佔用大量空間的臨時表格。 不要將活動保留在 **[!UICONTROL Do not enable]** 或 **[!UICONTROL Enable but do not execute]** 工作流程中的狀態。

**停止未使用的工作流程**. 持續執行的工作流程會維護與資料庫的連線。

**僅在極少數情況下使用無條件停止**. 請勿定期使用此動作。 在工作流程產生到資料庫的連線上不執行乾淨的關閉，會影響效能。

**不要在同一工作流程上執行多個停止請求**. 停止工作流程為非同步程式：要求已註冊，然後工作流程伺服器取消正在進行的操作。 因此，停止工作流程例項可能需要一些時間，尤其是當工作流程正在多個伺服器上執行時，每個伺服器都必須取得控制權，才能取消進行中的工作。 若要避免發生任何問題，請等候停止作業完成，並避免多次停止工作流程。

### 在引擎選項中執行 {#execute-in-the-engine-option}

在 **[!UICONTROL Workflow properties]** 視窗，請勿勾選 **[!UICONTROL Execute in the engine]** 選項。 啟用此選項後，工作流程會獲得優先權，而所有其他工作流程會由工作流程引擎停止，直到完成此工作流程為止。

![](assets/wf-execute-in-engine.png)

## 工作流程屬性 {#workflow-properties}

### 工作流程資料夾 {#workflow-folders}

Adobe建議您在專用資料夾中建立工作流程。

如果工作流程會影響整個平台（例如清除程式），您可以考慮在內建中新增子資料夾 **[!UICONTROL Technical Workflows]** 資料夾。

### 工作流程命名 {#workflow-naming}

由於若未以預期方式執行，可讓工作流程更容易找到並疑難排解，Adobe建議您為工作流程指定適當的名稱和標籤：填寫工作流程的說明欄位，彙總要執行的程式，讓運算子輕鬆瞭解。

如果工作流程是涉及多個工作流程的流程的一部分，您可以明確輸入標籤；使用數字是排序工作流程的絕佳方式（依標籤）。

例如：

* 001 — 匯入 — 匯入收件者
* 002 — 匯入 — 匯入銷售
* 003 — 匯入 — 匯入銷售詳細資料
* 010 — 匯出 — 匯出傳遞記錄
* 011 — 匯出 — 匯出追蹤記錄

### 工作流程嚴重性 {#workflow-severity}

您可以在工作流程屬性中設定工作流程的嚴重性，位置如下： **[!UICONTROL Execution]** 標籤：

* 正常
* 生產
* 關鍵

在建立工作流程時提供此資訊可協助您瞭解所設定程式的嚴重性。

此選項對行銷活動工作流程以外的工作流程沒有功能影響。

如果行銷活動有多個應同時執行的流程，系統會優先執行嚴重性較高的行銷活動工作流程（作為行銷活動/作業的一部分建立的工作流程）。 根據選項NmsOperation_LimitConcurrency，預設情況下，行銷活動中只能同時執行10個處理。 例如，如果行銷活動包含25個工作流程，則具有較高嚴重性的工作流程將在第一個10個流程的集區中執行。

### 監視工作流程 {#workflow-monitoring}

應監控在生產環境中執行的所有已排程工作流程，以便在發生錯誤時收到警報。

在工作流程屬性中，選取監督員群組（預設值之一） **[!UICONTROL Workflow supervisors]** 或自訂群組。 請確定至少有一個運運算元屬於此群組，並設定了電子郵件。

開始建立工作流程之前，請記得定義工作流程主管。 如果發生錯誤，他們會收到電子郵件通知。 有關詳細資訊，請參閱 [管理錯誤](monitoring-workflow-execution.md#managing-errors).

定期檢查 **[!UICONTROL Monitoring]** 標籤來檢視作用中工作流程的整體狀態。 有關詳細資訊，請參閱 [執行個體監督](monitoring-workflow-execution.md#instance-supervision).

工作流程熱度圖可讓Adobe Campaign平台管理員監控執行個體的負載，並據此規劃工作流程。 有關詳細資訊，請參閱 [工作流程監視](heatmap.md).

## 使用活動 {#using-activities}

>[!CAUTION]
>
>您可以在同一個工作流程中複製和貼上活動。 不過，我們不建議跨不同的工作流程複製貼上活動。 附加至傳送和排程器等活動的某些設定，在執行目標工作流程時可能會導致衝突和錯誤。 我們建議您  **複製** 工作流程。 如需詳細資訊，請參閱 [複製工作流程](building-a-workflow.md#duplicating-workflows).

### 活動名稱 {#name-of-the-activity}

在開發工作流程時，所有活動都會有名稱，所有Adobe Campaign物件亦然。 雖然該名稱是由工具產生的，但我們建議您在設定時，以明確名稱來重新命名它。 稍後執行此動作的風險在於，它可能會使用另一個先前活動的名稱來中斷工作流程。 因此，後續更新名稱會相當困難。

活動名稱可在以下網址找到： **[!UICONTROL Advanced]** 標籤。 不要保留名稱 **[!UICONTROL query]**， **[!UICONTROL query1]**， **[!UICONTROL query11]**，但請為它們指定明確名稱，例如 **[!UICONTROL querySubscribedRecipients]**. 此名稱將顯示在日誌中，如果適用，也會顯示在SQL記錄中，這有助於在設定工作流程時對其進行偵錯。

### 第一個和最後一個活動 {#first-and-last-activities}

* 一律以開始您的工作流程 **[!UICONTROL Start]** 活動或 **[!UICONTROL Scheduler]** 活動。 如有需要，您也可以使用 **[!UICONTROL External signal]** 活動。
* 在建立工作流程時，請只使用一個 **[!UICONTROL Scheduler]** 每個分支的活動。 如果工作流程的同一分支有多個排程器（相互連結），則要執行的任務數量將呈指數倍增，這將使得資料庫大幅超載。此規則也適用所有具有的活動 **[!UICONTROL Scheduling & History]** 標籤。 進一步瞭解 [排程](scheduler.md).

   ![](assets/wf-scheduler.png)

* 使用 **[!UICONTROL End]** 每個工作流程的活動。 這可讓Adobe Campaign釋出用於工作流程中計算的暫存空間。 有關詳細資訊，請參閱： [開始和結束](start-and-end.md).

### 活動中的Javascript {#javascript-within-an-activity}

初始化工作流程活動時，您可能想要新增JavaScript。 這可以在活動的中完成 **[!UICONTROL Advanced]** 活動索引標籤中的變數。

若要更輕鬆找到工作流程，我們建議在活動標籤的開始和結束位置使用雙破折號，如下所示： — 我的標籤 — 。

### 訊號 {#signal}

在大多數情況下，您不會知道從何處呼叫訊號。 為避免此問題，請使用 **[!UICONTROL Comment]** 內的欄位 **[!UICONTROL Advanced]** 訊號活動的索引標籤，以記錄此活動的訊號預期來源。

![](assets/workflow-signal-bp.png)

## 工作流程更新 {#workflow-update}

不應直接更新生產工作流程。 除非流程包含使用範本工作流程建立行銷活動，否則應先在開發環境中測試流程。 完成此驗證後，工作流程即可部署並在生產環境中啟動。

在開發或中繼環境（而非生產環境）中執行所有測試。 在此情況下，無法確保效能。

封存的工作流程可能會保留在開發或測試平台上的封存資料夾中，但生產環境應儘可能保持乾淨。 如果舊的工作流程處於非使用中狀態，則應將其從生產環境中移除。
