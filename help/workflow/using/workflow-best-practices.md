---
product: campaign
title: 工作流程最佳實務
description: 了解Campaign工作流程最佳實務
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 39c57f61-2629-4214-91e4-cb97dc039deb
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 6%

---

# 工作流程最佳實務{#workflow-best-practices}

## 執行和效能{#execution-and-performance}

以下列出關於最佳化Campaign效能的一般准則，包括套用至工作流程的最佳實務。

[本節](../../production/using/workflow-execution.md)也提供與工作流程執行相關的疑難排解准則。

### 記錄檔 {#logs}

JavaScript方法&#x200B;**[!UICONTROL logInfo()]**&#x200B;是偵錯工作流程的絕佳解決方案。 它很實用，但必須謹慎使用，尤其是針對經常執行的活動：它可能會使記錄檔過載，並大幅增加記錄表的大小。 但您可能還需要更多&#x200B;**[!UICONTROL logInfo()]**。

另外兩個解決方案可提供協助：

* **在兩次處決之間保留臨時人口的結果**

   此選項可保留工作流的兩個執行之間的臨時表。 它可在工作流屬性的&#x200B;**[!UICONTROL General]**&#x200B;頁簽中使用，可用於開發和測試，以監控資料和檢查結果。 您可以在開發環境中使用此選項，但絕不在生產環境中使用。 保持臨時表可導致資料庫的大小顯著增加，最終達到大小限制。 此外，它還會減緩備份速度。

   僅保留上次執行工作流的工作表。 前次執行的工作表由每天運行的&#x200B;**[!UICONTROL cleanup]**&#x200B;工作流清除。

   >[!CAUTION]
   >
   >在生產工作流程中，請勿勾選此選項。 此選項可用來分析結果，且設計僅用於測試用途，因此只能用於開發或測試環境。

* **在日誌中記錄SQL查詢**

   在工作流屬性的&#x200B;**[!UICONTROL Execution]**&#x200B;標籤中可用，此選項將記錄工具從不同活動生成的所有SQL查詢。 這是檢視平台實際執行內容的好方法。 不過，此選項僅應在開發期間暫時使用，而不應在生產時啟動。

不再需要記錄檔時，請加以清除。 不會自動清除工作流歷史記錄：預設會保留所有訊息。 您可以透過&#x200B;**[!UICONTROL File > Actions]**功能表或按一下清單上方工具列中的「動作」按鈕來清除歷史記錄。 選擇清除歷史記錄。
若要了解如何清除記錄檔，請參閱本[檔案](../../workflow/using/starting-a-workflow.md)。

### 工作流計畫{#workflow-planning}

* 嘗試在一天中維持穩定的活動水準，並避免達到尖峰，以防止執行個體過載。 若要這麼做，請在一整天內平均分配工作流程開始時間。
* 安排隔夜資料載入以減少資源爭用。
* 長的工作流程可能會對伺服器和資料庫資源造成影響。 分割最長的工作流程以縮短處理時間。
* 若要縮短整體執行時間，請以簡化且更快速的活動取代耗時的活動。
* 避免同時執行超過20個工作流程。 同時執行太多工作流程時，系統可能會耗盡資源而變得不穩定。 有關工作流可能未啟動的原因的詳細資訊，請參閱本[文章](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html)。

### 工作流程執行 {#workflow-execution}

最佳做法是不要將工作流安排為每隔15分鐘以上運行，因為它可能會阻礙整體系統效能並在資料庫中建立塊。

請避免將工作流程維持暫停狀態。 如果建立臨時工作流，請確保它能夠正確完成，並且不會保持在&#x200B;**[!UICONTROL paused]**&#x200B;狀態。 如果暫停，則意味著需要保留臨時表，從而增加資料庫的大小。 在「工作流屬性」(Workflow Properties)下分配「工作流監管者」(Assign Workflows)，以便在工作流失敗或系統暫停時發送警報。

若要避免工作流程處於暫停狀態：

* 請定期檢查您的工作流程，以確保沒有未預期的錯誤。
* 盡可能簡單地保持工作流程，例如將大型工作流程分割成數個不同的工作流程。 您可以使用&#x200B;**[!UICONTROL External signal]**&#x200B;活動根據其他工作流程的執行來觸發其執行。
* 避免在工作流程中停用流程的活動，讓執行緒開啟，並導致許多可能佔用大量空間的臨時表格。 請勿在工作流程中保留&#x200B;**[!UICONTROL Do not enable]**&#x200B;或&#x200B;**[!UICONTROL Enable but do not execute]**&#x200B;狀態中的活動。

此外，停止未使用的工作流程。 持續執行的工作流程會維護與資料庫的連線。

在最少情況下，只使用無條件停止。 請勿定期使用此動作。 未對工作流生成到資料庫的連接執行清理關閉會影響效能。

### 在引擎選項{#execute-in-the-engine-option}中執行

在&#x200B;**[!UICONTROL Workflow properties]**&#x200B;視窗中，永不勾選&#x200B;**[!UICONTROL Execute in the engine]**&#x200B;選項。 啟用此選項時，工作流程會優先，而所有其他工作流程會由工作流程引擎停止，直到此工作流程完成為止。

![](assets/wf-execute-in-engine.png)

## 工作流程屬性 {#workflow-properties}

### 工作流資料夾{#workflow-folders}

Adobe建議您在專用資料夾中建立工作流程。

如果工作流影響整個平台（例如清理過程），您可以考慮在內建&#x200B;**[!UICONTROL Technical Workflows]**&#x200B;資料夾中添加子資料夾。

### 工作流命名{#workflow-naming}

由於若未以預期方式執行，可讓工作流程更容易找到並疑難排解，Adobe建議您為工作流程指定適當的名稱和標籤：填寫工作流程的說明欄位，彙總要執行的程式，讓運算子輕鬆瞭解。

如果工作流是涉及多個工作流的流程的一部分，則在輸入標籤時可以是明確的；使用數字是排序工作流程的絕佳方式（依標籤）。

例如：

* 001 — 匯入 — 匯入收件者
* 002 — 匯入 — 匯入銷售
* 003 — 導入 — 導入銷售詳細資訊
* 010 — 匯出 — 匯出傳送記錄檔
* 011 — 匯出 — 匯出追蹤記錄檔

### 工作流嚴重性{#workflow-severity}

您可以在&#x200B;**[!UICONTROL Execution]**&#x200B;標籤的工作流屬性中配置工作流的嚴重性：

* 正常
* 生產
* 關鍵

在建立工作流程時提供此資訊，有助於您了解所設定程式的嚴重性。

此選項對促銷活動工作流程以外的工作流程沒有功能影響。

具有較高嚴重性的促銷活動工作流程（作為促銷活動/操作一部分建立的工作流程）會以優先順序執行，以防促銷活動有許多應同時執行的程式。 根據選項NmsOperation_LimitConcurrency，預設只能在一個促銷活動中同時執行10個進程。 例如，如果促銷活動包含25個工作流程，則嚴重性較高的工作流程將在10個流程的第一個池中執行。

### 監視工作流程 {#workflow-monitoring}

應監控所有在生產環境上執行的已排程工作流程，以便在發生錯誤時收到警報。

在工作流屬性中，選擇預設&#x200B;**[!UICONTROL Workflow supervisors]**&#x200B;或自定義組。 請確定至少有一個運算子屬於此群組，並設定了電子郵件。

開始建立工作流之前，請記得定義工作流主管。 若發生錯誤，將會以電子郵件通知他們。 有關詳細資訊，請參閱[管理錯誤](../../workflow/using/monitoring-workflow-execution.md#managing-errors)。

定期檢查&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤，以檢視作用中工作流程的整體狀態。 有關詳細資訊，請參閱[實例監督](../../workflow/using/monitoring-workflow-execution.md#instance-supervision)。

工作流程熱度圖可讓Adobe Campaign平台管理員監控執行個體的負載，並據此規劃工作流程。 有關詳細資訊，請參閱[工作流監視](../../workflow/using/heatmap.md)。

## 使用活動{#using-activities}

>[!CAUTION]
>
>您可以在相同的工作流程中複製和貼上活動。 不過，我們不建議跨不同的工作流程複製貼上活動。 某些附加至活動（例如傳送和排程器）的設定在執行目標工作流程時可能會導致衝突和錯誤。 反之，我們建議您&#x200B;**複製**&#x200B;工作流程。 如需詳細資訊，請參閱[複製工作流程](../../workflow/using/building-a-workflow.md#duplicating-workflows)。

### 活動的名稱{#name-of-the-activity}

開發工作流程時，所有活動都會有名稱，所有Adobe Campaign物件也一樣。 由工具產生名稱時，建議您在設定名稱時以明確的名稱重新命名。 稍後執行該操作的風險在於，它可能會使用另一個先前活動的名稱來中斷使用活動的工作流程。 因此，要更新名稱將是一項困難的工作。

可在&#x200B;**[!UICONTROL Advanced]**&#x200B;索引標籤中找到活動名稱。 請勿將其命名為&#x200B;**[!UICONTROL query]**、**[!UICONTROL query1]**、**[!UICONTROL query11]**，但請為它們指定明確的名稱，例如&#x200B;**[!UICONTROL querySubscribedRecipients]**。 此名稱將顯示在日誌中，如果SQL日誌中適用，這將有助於在配置工作流時調試該工作流。

### 第一個和最後一個活動{#first-and-last-activities}

* 一律以&#x200B;**[!UICONTROL Start]**&#x200B;活動或&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動啟動工作流程。 相關時，您也可以使用&#x200B;**[!UICONTROL External signal]**&#x200B;活動。
* 在建立工作流程時，每個分支僅使用一個&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動。 如果工作流程的同一分支有多個排程器（相互連結），則要執行的任務數量將呈指數倍增，這將使得資料庫大幅超載。此規則也適用於具有&#x200B;**[!UICONTROL Scheduling & History]**&#x200B;索引標籤的所有活動。 深入了解[排程](../../workflow/using/scheduler.md)。

   ![](assets/wf-scheduler.png)

* 對每個工作流使用&#x200B;**[!UICONTROL End]**&#x200B;活動。 這可讓Adobe Campaign釋出工作流程中用於計算的暫存空間。 有關詳細資訊，請參閱：[開始和結束](../../workflow/using/start-and-end.md)。

### 活動{#javascript-within-an-activity}內的Javascript

初始化工作流程活動時，您可能想要新增JavaScript。 您可以在活動的&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤中完成此作業。

為了更輕鬆找出工作流程，建議您在活動標籤的開頭和結尾使用雙破折號，如下所示： — 我的標籤 — 。

### 訊號 {#signal}

大多數時候，您都不知道訊號的來源。 為避免此問題，請使用信號活動&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤內的&#x200B;**[!UICONTROL Comment]**&#x200B;欄位，記錄此活動的信號的預期來源。

![](assets/workflow-signal-bp.png)

## 工作流更新{#workflow-update}

生產工作流程不應直接更新。 除非此程式包含使用範本工作流程建立行銷活動，否則應先在開發環境中測試程式。 經過此驗證後，工作流程便可部署並在生產環境中啟動。

在開發或測試環境（而非生產環境）中執行所有測試。 在這種情況下，無法確保效能。

封存的工作流程可以保留在開發或測試平台上、封存的資料夾中，但生產環境應盡可能保持乾淨。 如果舊的工作流程處於非作用中狀態，則應從生產環境中移除舊的工作流程。
