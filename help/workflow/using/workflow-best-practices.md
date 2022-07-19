---
product: campaign
title: 工作流程最佳實務
description: 瞭解市場活動工作流最佳實踐
feature: Workflows
exl-id: 39c57f61-2629-4214-91e4-cb97dc039deb
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1687'
ht-degree: 6%

---

# 工作流程最佳實務{#workflow-best-practices}

![](../../assets/v7-only.svg)

## 執行和效能 {#execution-and-performance}

下面列出了有關優化市場活動績效的一般指導，包括適用於您的工作流的最佳做法。

有關工作流執行的疑難解答指導也請參見 [Campaign Classicv7生產指南](../../production/using/workflow-execution.md)。

### 日誌 {#logs}

JavaScript方法 **[!UICONTROL logInfo()]** 是調試工作流的絕佳解決方案。 它很有用，但必須謹慎使用，尤其是對經常運行的活動：它可以使日誌過載，並顯著增加日誌表的大小。 但你可能還需要 **[!UICONTROL logInfo()]**。

還提供了另外兩個解決方案，以幫助：

* **在兩次處決之間保留臨時人口的結果**

   此選項在工作流的兩個執行之間保留臨時表。 在工作流屬性中可用 **[!UICONTROL General]** 頁籤，可用於開發和test以監視資料和檢查結果。 您可以在開發環境中使用此選項，但永遠不要在生產環境中使用它。 保留臨時表可能會導致資料庫的大小顯著增加，並最終達到大小限制。 而且會減緩後援。

   只保留上次執行工作流的工作表。 將清除先前執行中的工作表 **[!UICONTROL cleanup]** 工作流，每天運行。

   >[!CAUTION]
   >
   >在生產工作流程中，請勿勾選此選項。 此選項用於分析結果，並且僅用於測試目的，因此必須僅用於開發或試運行環境。

* **日誌中的SQL查詢**

   在 **[!UICONTROL Execution]** 頁籤中，此選項將記錄工具從不同活動生成的所有SQL查詢。 這是一個很好的觀察平台實際執行了什麼的方法。 但是，此選項只應在開發期間暫時使用，而不應在生產時激活。

在不再需要日誌時清除日誌。 工作流歷史記錄不會自動清除：預設情況下，所有消息都會保留。 歷史記錄可通過 **[!UICONTROL File > Actions]** 或按一下清單上方工具欄中的「操作」按鈕。 選擇清除歷史記錄。
要瞭解如何清除日誌，請參閱 [文檔](starting-a-workflow.md)。

### 工作流計畫 {#workflow-planning}

* 嘗試在一天中保持活動的穩定級別，避免出現高峰，以防止實例超載。 為此，請在一天中平均分配工作流開始時間。
* 計畫夜間資料載入以減少資源爭用。
* 長工作流可能會對伺服器和資料庫資源產生影響。 拆分最長的工作流以減少處理時間。
* 要減少總的運行時間，請用簡化且更快的活動替換耗時的活動。
* 避免同時運行20多個工作流。 當同時執行過多的工作流時，系統會耗盡資源，變得不穩定。 有關工作流可能未啟動原因的詳細資訊，請參閱此 [文章](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html)。

### 工作流程執行 {#workflow-execution}

**不要將工作流計畫為每15分鐘運行一次以上** 因為它可能會妨礙總體系統效能並在資料庫中建立塊。

**避免將工作流置於暫停狀態**。 如果建立臨時工作流，請確保它能夠正確完成，並且不會留在 **[!UICONTROL paused]** 狀態。 如果暫停，則意味著需要保留臨時表，從而增加資料庫的大小。 在「工作流屬性」下分配「工作流主管」，以便在工作流失敗或系統暫停時發送警報。

要避免工作流處於暫停狀態：

* 定期檢查您的工作流以確保沒有意外錯誤。
* 盡可能簡化工作流，例如將大型工作流拆分到多個不同的工作流中。 您可以使用 **[!UICONTROL External signal]** 活動根據其他工作流的執行觸發其執行。
* 避免禁用工作流中的流活動，使線程處於開啟狀態並導致許多可能佔用大量空間的臨時表。 不要將活動保留在 **[!UICONTROL Do not enable]** 或 **[!UICONTROL Enable but do not execute]** 工作流中的狀態。

**停止未使用的工作流**。 持續運行的工作流維護與資料庫的連接。

**僅在最罕見的情況下使用無條件停止**。 不要定期使用此操作。 未對工作流生成到資料庫的連接執行乾淨關閉會影響效能。

**不在同一工作流上執行多個停止請求**。 停止工作流是一個非同步進程：註冊該請求，然後工作流伺服器或伺服器取消正在進行的操作。 因此，停止工作流實例可能需要時間，尤其是當工作流正在多個伺服器上運行時，每個伺服器都必須控制以取消正在進行的任務。 為避免任何問題，請等待停止操作完成，並避免多次停止工作流。

### 在引擎選項中執行 {#execute-in-the-engine-option}

在 **[!UICONTROL Workflow properties]** 窗口，從不檢查 **[!UICONTROL Execute in the engine]** 的雙曲餘切值。 啟用此選項後，工作流將處於優先地位，所有其它工作流將由工作流引擎停止，直到此工作流完成。

![](assets/wf-execute-in-engine.png)

## 工作流程屬性 {#workflow-properties}

### 工作流資料夾 {#workflow-folders}

Adobe建議您在專用資料夾中建立工作流。

如果工作流影響整個平台（例如清理進程），可以考慮在內置資料夾中添加子資料夾 **[!UICONTROL Technical Workflows]** 的子菜單。

### 工作流命名 {#workflow-naming}

由於若未以預期方式執行，可讓工作流程更容易找到並疑難排解，Adobe建議您為工作流程指定適當的名稱和標籤：填寫工作流程的說明欄位，彙總要執行的程式，讓運算子輕鬆瞭解。

如果工作流是涉及多個工作流的流程的一部分，則在輸入標籤時可以顯式；使用數字是訂購工作流（按標籤）的極好方法。

例如：

* 001 — 導入 — 導入收件人
* 002 — 導入 — 導入銷售
* 003 — 導入 — 導入銷售詳細資訊
* 010 — 導出 — 導出交貨日誌
* 011 — 導出 — 導出跟蹤日誌

### 工作流嚴重性 {#workflow-severity}

您可以在工作流屬性中配置工作流的嚴重性， **[!UICONTROL Execution]** 頁籤：

* 正常
* 生產
* 關鍵

在建立工作流時提供此資訊將有助於您瞭解配置的進程的嚴重性。

此選項對除市場活動工作流之外的工作流沒有任何功能影響。

優先順序較高的市場活動工作流（作為市場活動/操作的一部分建立的工作流）將優先執行，以防市場活動有多個應同時運行的流程。 預設情況下，根據NmsOperation_LimitConcurrency選項，在市場活動中只能同時運行10個進程。 例如，如果市場活動包含25個工作流，則嚴重性較高的工作流將在10個進程的第一個池中執行。

### 監視工作流程 {#workflow-monitoring}

應監視在生產環境中運行的所有計畫工作流，以便在出現錯誤時收到警報。

在工作流屬性中，選擇一個Supervisor組， **[!UICONTROL Workflow supervisors]** 或自定義組。 確保至少有一個操作員屬於此組，並設定了電子郵件。

在開始構建工作流之前，請記住定義工作流主管。 如果出現錯誤，將通過電子郵件通知他們。 有關此內容的詳細資訊，請參閱 [管理錯誤](monitoring-workflow-execution.md#managing-errors)。

定期檢查 **[!UICONTROL Monitoring]** 頁籤，查看活動工作流的總體狀態。 有關此內容的詳細資訊，請參閱 [實例監督](monitoring-workflow-execution.md#instance-supervision)。

工作流熱圖使Adobe Campaign平台管理員能夠監視實例上的負載並相應地規劃工作流。 有關此內容的詳細資訊，請參閱 [工作流監視](heatmap.md)。

## 使用活動 {#using-activities}

>[!CAUTION]
>
>您可以在同一工作流中複製和貼上活動。 但是，我們不建議跨不同的工作流複製貼上活動。 附加到「交貨」和「計畫程式」等活動的某些設定在執行目標工作流時可能會導致衝突和錯誤。 相反，我們建議你  **重複** 工作流。 有關詳細資訊，請參見 [複製工作流](building-a-workflow.md#duplicating-workflows)。

### 活動名稱 {#name-of-the-activity}

在開發工作流時，所有活動都將有一個名稱，所有Adobe Campaign對象也會有這個名稱。 當該工具生成名稱時，建議您在配置該名稱時使用顯式名稱對其進行更名。 以後這樣做的風險在於，它可能會使用另一個先前活動的名稱中斷活動。 所以以後更新名字會很困難。

活動名稱可在 **[!UICONTROL Advanced]** 頁籤。 不要讓他們的名字 **[!UICONTROL query]**。 **[!UICONTROL query1]**。 **[!UICONTROL query11]**，但為其指定顯式名稱，如 **[!UICONTROL querySubscribedRecipients]**。 此名稱將顯示在日誌中，如果適用於SQL日誌，這將有助於在配置工作流時調試該工作流。

### 第一個和最後一個活動 {#first-and-last-activities}

* 始終使用 **[!UICONTROL Start]** 活動或 **[!UICONTROL Scheduler]** 的子菜單。 相關時，您還可以使用 **[!UICONTROL External signal]** 的子菜單。
* 構建工作流時，僅使用一個 **[!UICONTROL Scheduler]** 每個分支的活動。 如果工作流程的同一分支有多個排程器（相互連結），則要執行的任務數量將呈指數倍增，這將使得資料庫大幅超載。此規則也適用於具有 **[!UICONTROL Scheduling & History]** 頁籤。 瞭解更多 [計畫](scheduler.md)。

   ![](assets/wf-scheduler.png)

* 使用 **[!UICONTROL End]** 活動。 這使Adobe Campaign可以釋放用於工作流中計算的臨時空間。 有關詳細資訊，請參閱： [開始和結束](start-and-end.md)。

### 活動中的Javascript {#javascript-within-an-activity}

初始化工作流活動時，可能需要添加JavaScript。 可以在活動中 **[!UICONTROL Advanced]** 的子菜單。

為了更方便地發現工作流，我們建議在活動標籤的開始和結束處使用雙折線，如下所示： — 我的標籤 — 。

### 信號 {#signal}

大多數時候，你都不知道信號從哪裡被調用。 為避免此問題，請使用 **[!UICONTROL Comment]** 欄位 **[!UICONTROL Advanced]** 的子菜單。

![](assets/workflow-signal-bp.png)

## 工作流更新 {#workflow-update}

不應直接更新生產工作流。 除非流程包括使用模板工作流建立市場活動，否則應首先在開發環境中測試流程。 驗證後，可以在生產上部署和啟動工作流。

在開發或分段環境中執行所有測試，而不是在生產環境中執行。 在這種情況下，無法確保效能。

歸檔的工作流可以保留在開發或test平台上的「歸檔」資料夾中，但生產環境應盡可能保持乾淨。 如果舊工作流處於非活動狀態，則應從生產環境中刪除它們。
