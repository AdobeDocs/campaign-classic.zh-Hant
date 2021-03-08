---
solution: Campaign Classic
product: campaign
title: 工作流程最佳實務
description: 瞭解促銷活動工作流程最佳實務
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 5%

---


# 工作流程最佳實務{#workflow-best-practices}

## 執行和效能{#execution-and-performance}

以下列出有關最佳化促銷活動效能的一般准則，包括套用至您工作流程的最佳實務。

有關工作流執行的故障排除指導，請參閱[本節](../../production/using/workflow-execution.md)。

### 日誌{#logs}

JavaScript方法&#x200B;**[!UICONTROL logInfo()]**&#x200B;是除錯工作流程的絕佳解決方案。 它很有用，但必須謹慎使用，尤其是對於經常運行的活動：它可以使日誌過載，並顯著增加日誌表的大小。 但您可能還需要&#x200B;**[!UICONTROL logInfo()]**&#x200B;以上。

另外還提供兩種解決方案，以協助您：

* **將臨時人口結果保存在兩次處決之間**

   此選項可在工作流的兩個執行之間保留臨時表。 它可在工作流程屬性的&#x200B;**[!UICONTROL General]**&#x200B;標籤中使用，可用於開發和測試，以監控資料和檢查結果。 您可以在開發環境中使用此選項，但絕不能在生產環境中使用。 保留臨時表可導致資料庫的大小顯著增加，最終達到大小限制。 此外，它還會減緩備份速度。

   只保留工作流上次執行的工作表。 以前執行中的工作表由每天運行的&#x200B;**[!UICONTROL cleanup]**&#x200B;工作流清除。

   >[!CAUTION]
   >
   >在生產工作流程中，不得勾選此選項。 此選項用於分析結果，僅用於測試，因此只能用於開發或測試環境。

* **日誌中的SQL查詢**

   此選項在工作流屬性的&#x200B;**[!UICONTROL Execution]**&#x200B;頁籤中可用，它將記錄工具從不同活動中生成的所有SQL查詢。 這是瞭解平台實際執行的最佳方式。 不過，這個選項只應在開發期間暫時使用，而不應在生產時啟動。

不再需要記錄檔時，請加以清除。 工作流歷史記錄不會自動清除：預設情況下會保留所有消息。 您可以透過&#x200B;**[!UICONTROL File > Actions]**功能表，或按一下清單上方工具列中的「動作」按鈕，來清除歷史記錄。 選擇清除歷史記錄。
要瞭解如何清除日誌，請參閱[文檔](../../workflow/using/starting-a-workflow.md)。

### 工作流程規劃{#workflow-planning}

* 請盡量在一天中維持穩定的活動等級，並避免尖峰，以防止例項超載。 若要這麼做，請在一天中平均分發工作流程開始時間。
* 安排隔夜資料載入以減少資源爭用。
* 冗長的工作流程可能會對伺服器和資料庫資源造成影響。 分割最長的工作流程，以縮短處理時間。
* 若要縮短整體執行時間，請以簡化且更快速的活動取代耗時的活動。
* 避免同時執行超過20個工作流程。 同時執行過多的工作流程時，系統會耗盡資源而變得不穩定。 如需工作流程可能無法啟動的詳細資訊，請參閱此[文章](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html)。

### 工作流程執行 {#workflow-execution}

最好不要將工作流計畫為每15分鐘多運行一次，因為它可能會影響系統的整體效能並在資料庫中建立塊。

請避免將工作流程保留在暫停狀態。 如果您建立暫時工作流程，請確定它能正確完成，而不會維持在&#x200B;**[!UICONTROL paused]**&#x200B;狀態。 如果暫停，則表示您需要保留臨時表，從而增加資料庫的大小。 在「工作流屬性」下指派「工作流監督者」，以便在工作流失敗或系統暫停時傳送警報。

若要避免工作流程處於暫停狀態：

* 定期檢查您的工作流程，以確保沒有未預期的錯誤。
* 讓您的工作流程盡可能簡單，例如，將大型工作流程分割為數個不同的工作流程。 您可以使用&#x200B;**[!UICONTROL External signal]**&#x200B;活動根據其他工作流的執行觸發其執行。
* 避免停用工作流中的流，導致線程開啟並導致許多臨時表佔用大量空間。 請勿在工作流程中保留&#x200B;**[!UICONTROL Do not enable]**&#x200B;或&#x200B;**[!UICONTROL Enable but do not execute]**&#x200B;狀態的活動。

此外，還可停止未使用的工作流程。 持續執行的工作流程會維持與資料庫的連線。

在最少的情況下，僅使用無條件停止。 請勿定期使用此動作。 不對工作流生成的到資料庫的連接執行乾淨的關閉會影響效能。

### 在引擎選項{#execute-in-the-engine-option}中執行

在&#x200B;**[!UICONTROL Workflow properties]**&#x200B;窗口中，切勿選中&#x200B;**[!UICONTROL Execute in the engine]**&#x200B;選項。 啟用此選項後，工作流將優先處理，而工作流引擎將停止所有其它工作流，直到此工作流完成。

![](assets/wf-execute-in-engine.png)

## 工作流程屬性 {#workflow-properties}

### 工作流資料夾{#workflow-folders}

Adobe建議您在專用資料夾中建立工作流程。

如果工作流影響整個平台（例如清理流程），您可以考慮在內置&#x200B;**[!UICONTROL Technical Workflows]**&#x200B;資料夾中添加子資料夾。

### 工作流程命名{#workflow-naming}

由於若未以預期方式執行，可讓工作流程更容易找到並疑難排解，Adobe建議您為工作流程指定適當的名稱和標籤：填寫工作流程的說明欄位，彙總要執行的程式，讓運算子輕鬆瞭解。

如果工作流是涉及多個工作流的流程的一部分，則在輸入標籤時可以明確；使用數字是排序工作流程的絕佳方式（依標籤）。

例如：

* 001 —— 導入——導入收件人
* 002 —— 導入——導入銷售
* 003 —— 導入——導入銷售詳細資訊
* 010 —— 匯出——匯出傳送記錄檔
* 011 —— 匯出——匯出追蹤記錄檔

### 工作流程嚴重性{#workflow-severity}

您可以在工作流屬性中配置工作流的嚴重性，位於&#x200B;**[!UICONTROL Execution]**&#x200B;頁籤中：

* 正常
* 製作
* 重要

在建立工作流時提供此資訊將有助於您瞭解配置的流程的嚴重性。

此選項對促銷活動工作流程以外的工作流程沒有任何功能影響。

具有較高嚴重性的促銷活動工作流程（作為促銷活動／作業的一部分建立的工作流程）會以優先順序執行，以防促銷活動有許多應同時執行的程式。 根據NmsOperation_LimitConcurrency選項，在促銷活動中，預設只能同時執行10個進程。 例如，如果促銷活動包含25個工作流程，則嚴重性較高的工作流程將會在10個流程的第一個池中執行。

### 工作流監控{#workflow-monitoring}

您所有在生產環境上執行的排程工作流程都應受到監控，以便在發生錯誤時收到警告。

在工作流屬性中，選擇預設&#x200B;**[!UICONTROL Workflow supervisors]**&#x200B;或自定義組的主管組。 請確定至少有一個運算子屬於此群組，並設定電子郵件。

開始建立工作流之前，請記得定義工作流主管。 如果發生錯誤，將會以電子郵件通知他們。 有關詳細資訊，請參閱[管理錯誤](../../workflow/using/monitoring-workflow-execution.md#managing-errors)。

定期檢查&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤以檢視作用中工作流程的整體狀態。 有關詳細資訊，請參閱[實例監督](../../workflow/using/monitoring-workflow-execution.md#instance-supervision)。

Workflow HeatMap可讓Adobe Campaign平台管理員監控執行個體的負載，並據此規劃工作流程。 有關詳細資訊，請參閱[工作流監控](../../workflow/using/heatmap.md)。

## 使用活動{#using-activities}

>[!CAUTION]
>
>您可以複製和貼上相同工作流程中的活動。 不過，我們不建議跨不同的工作流程複製貼上活動。 某些附加至活動（例如「傳送」和「排程器」）的設定，在執行目標工作流程時可能會導致衝突和錯誤。 我們建議您改為&#x200B;**複製**&#x200B;工作流程。 如需詳細資訊，請參閱[複製工作流程](../../workflow/using/building-a-workflow.md#duplicating-workflows)。

### 活動的名稱{#name-of-the-activity}

在開發工作流程時，所有活動都會有名稱，所有Adobe Campaign物件也一樣。 當工具產生名稱時，我們建議您在設定名稱時，以明確的名稱來重新命名該名稱。 稍後執行該操作的風險在於，它可能會使用另一個先前活動的名稱中斷使用活動的工作流。 因此，更新名字將是一項困難的工作。

活動名稱可在&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤中找到。 請勿將其命名為&#x200B;**[!UICONTROL query]**、**[!UICONTROL query1]**、**[!UICONTROL query11]**，但請為其指定明確的名稱，例如&#x200B;**[!UICONTROL querySubscribedRecipients]**。 此名稱將顯示在日誌中，如果適用於SQL日誌，則有助於在配置工作流時對其進行調試。

### 第一個和最後一個活動{#first-and-last-activities}

* 始終以&#x200B;**[!UICONTROL Start]**&#x200B;活動或&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動啟動工作流。 相關時，您也可以使用&#x200B;**[!UICONTROL External signal]**&#x200B;活動。
* 建立工作流程時，每個分支僅使用一個&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動。 如果工作流程的同一分支有多個排程器（相互連結），則要執行的任務數量將呈指數倍增，這將使得資料庫大幅超載。此規則也適用於具有&#x200B;**[!UICONTROL Scheduling & History]**&#x200B;標籤的所有活動。 進一步瞭解[計畫](../../workflow/using/scheduler.md)。

   ![](assets/wf-scheduler.png)

* 對每個工作流程使用&#x200B;**[!UICONTROL End]**&#x200B;活動。 這可讓Adobe Campaign釋放工作流中用於計算的臨時空間。 有關詳情，請參閱：[開始和結束](../../workflow/using/start-and-end.md)。

### 活動{#javascript-within-an-activity}中的Javascript

初始化工作流程活動時，您可能想要新增JavaScript。 這可在活動的&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤中完成。

為了更輕鬆地找出工作流程，建議您在活動標籤的開始和結束處使用雙破折號，如下所示：—我的標籤—。

### 信號{#signal}

大部分時候，您都不會知道信號從何處呼叫。 為避免此問題，請使用信號活動&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤中的&#x200B;**[!UICONTROL Comment]**&#x200B;欄位記錄該活動的信號的預期來源。

![](assets/workflow-signal-bp.png)

## 工作流程更新{#workflow-update}

不應直接更新生產工作流程。 除非此程式包含使用範本工作流程建立促銷活動，否則應先在開發環境上測試程式。 在進行此驗證後，可以在生產環境中部署和啟動工作流程。

在開發或測試環境中執行所有測試，而不是在生產環境中執行。 在這種情況下，無法確保效能。

封存的工作流程可以保存在開發或測試平台上，位於封存的檔案夾中，但生產環境應盡可能保持乾淨。 如果舊工作流程處於非活動狀態，則應從生產環境中移除舊工作流程。
