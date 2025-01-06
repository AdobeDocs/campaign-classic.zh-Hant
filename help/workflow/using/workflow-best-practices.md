---
product: campaign
title: 工作流程最佳實務
description: 瞭解行銷活動工作流程最佳實務
feature: Workflows
exl-id: 39c57f61-2629-4214-91e4-cb97dc039deb
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1381'
ht-degree: 11%

---

# 工作流程最佳實務{#workflow-best-practices}



## 執行與效能 {#execution-and-performance}

以下列出最佳化行銷活動效能的一般准則，包括套用至您工作流程的最佳實務。

[Campaign Classicv7生產指南](../../production/using/workflow-execution.md)中還提供了與工作流程執行相關的疑難排解指南。

### 記錄 {#logs}

JavaScript方法&#x200B;**[!UICONTROL logInfo()]**&#x200B;是偵錯工作流程的絕佳解決方案。 這個變數很有用，但必須謹慎使用，尤其是經常執行的活動：它會讓記錄超載，並大幅增加記錄表格的大小。 但您也可能需要&#x200B;**[!UICONTROL logInfo()]**&#x200B;以上的專案。

另外兩種解決方案可提供協助：

* **保留兩個執行之間的臨時母體結果**

  此選項會保留工作流程兩個執行之間的臨時表格。 它可在工作流程屬性的&#x200B;**[!UICONTROL General]**&#x200B;標籤中使用，並可用於開發和測試目的，以監視資料並檢查結果。 您可以在開發環境中使用此選項，但切勿在生產環境中使用它。保留臨時表能會導致資料庫顯著變大，最終會達到上限。此外，它會減慢備份速度。

  只保留最後一次執行工作流程的工作表。**[!UICONTROL cleanup]**&#x200B;工作流程會清除先前執行的工作表，該工作流程會每天執行。

  >[!CAUTION]
  >
  >在生產工作流程中，請勿勾選此選項。 此選項用於分析結果，且僅供用於測試目的，因此只能在開發或中繼環境中使用。

* **在日誌中記錄SQL查詢**

  此選項可在工作流程屬性的&#x200B;**[!UICONTROL Execution]**&#x200B;標籤中使用，將記錄工具從不同活動產生的所有SQL查詢。 這是檢視平台實際執行動作的好方法。 不過，此選項僅應在開發期間暫時使用，而不應在生產環境中啟用。

當不再需要記錄時，請清除這些記錄。 系統不會自動清除工作流程歷史記錄：預設會保留所有訊息。 您可以透過&#x200B;**[!UICONTROL File > Actions]**功能表或按一下位於清單上方工具列中的[動作]按鈕，清除歷史記錄。 選取永久刪除歷史記錄。
若要瞭解如何清除記錄檔，請參閱此[檔案](starting-a-workflow.md)。

### 工作流程規劃 {#workflow-planning}

* 請試著維持一天的穩定活動水準，並避免尖峰以防止執行個體過載。 若要這麼做，請在一天中平均分配工作流程開始時間。
* 排程整夜載入資料，以減少資源爭用。
* 長的工作流程可能會對伺服器和資料庫資源造成影響。 分割最長的工作流程，以減少處理時間。
* 為縮短整體執行時間，請以簡化且更快的活動取代耗時的活動。
* 請避免同時執行超過20個工作流程。 如果同時執行的工作流程太多，系統可能會耗盡資源並且變得不穩定。 有關工作流程未啟動原因的詳細資訊，請參閱本[文章](https://helpx.adobe.com/ie/campaign/kb/workflows-not-starting-in-a-campaign-technical-workflows.html)。


### 在引擎選項中執行 {#execute-in-the-engine-option}

在&#x200B;**[!UICONTROL Workflow properties]**&#x200B;視窗中，請勿勾選&#x200B;**[!UICONTROL Execute in the engine]**&#x200B;選項。 啟用此選項後，工作流程會取得優先順序，而所有其他工作流程會由工作流程引擎停止，直到此工作流程完成為止。

![](assets/wf-execute-in-engine.png)

## 工作流程屬性 {#workflow-properties}

### 工作流程資料夾 {#workflow-folders}

Adobe建議您在專用資料夾中建立工作流程。

如果工作流程影響整個平台（例如清除程式），您可以考慮在內建&#x200B;**[!UICONTROL Technical Workflows]**&#x200B;資料夾中新增子資料夾。

### 工作流程命名 {#workflow-naming}

由於若未以預期方式執行，可讓工作流程更容易找到並疑難排解，Adobe建議您為工作流程指定適當的名稱和標籤：填寫工作流程的說明欄位，彙總要執行的程式，讓運算子輕鬆瞭解。

如果工作流程是涉及多個工作流程的流程的一部分，您可以明確輸入標籤；使用數字是排序工作流程的絕佳方式（依標籤）。

例如：

* 001 — 匯入 — 匯入收件者
* 002 — 匯入 — 匯入銷售
* 003 — 匯入 — 匯入銷售明細
* 010 — 匯出 — 匯出傳送記錄檔
* 011 — 匯出 — 匯出追蹤記錄

### 工作流程嚴重性 {#workflow-severity}

您可以在&#x200B;**[!UICONTROL Execution]**&#x200B;索引標籤的工作流程屬性中設定工作流程的嚴重性：

* 正常
* 生產
* 重要

在建立工作流程時提供此資訊可協助您瞭解所設定流程的嚴重性。

此選項對行銷活動工作流程以外的工作流程沒有功能影響。

如果行銷活動有多個應同時執行的流程，則會優先執行嚴重性較高的行銷活動工作流程（作為行銷活動/作業的一部分建立的工作流程）。 根據選項NmsOperation_LimitConcurrency，預設情況下，一個行銷活動中只能同時執行10個流程。 例如，如果行銷活動包含25個工作流程，則嚴重性較高的工作流程將在10個流程的第一個集區中執行。

### 監視工作流程 {#workflow-monitoring}

應監視在生產環境中執行的所有排程工作流程，以便在發生錯誤時收到警報。

在工作流程屬性中，選取監督員群組，可以是預設&#x200B;**[!UICONTROL Workflow supervisors]**&#x200B;或自訂群組。 請確定至少有一個運運算元屬於此群組，並設定了電子郵件。

開始建立工作流程之前，請記得定義工作流程主管。 如果發生錯誤，他們會收到電子郵件通知。 如需詳細資訊，請參閱[管理錯誤](monitoring-workflow-execution.md#managing-errors)。

定期檢查&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤以檢視作用中工作流程的整體狀態。 如需詳細資訊，請參閱[執行個體監督](monitoring-workflow-execution.md#instance-supervision)。

工作流程熱度圖可讓Adobe Campaign平台管理員監控執行個體的負載，並據此規劃工作流程。 如需詳細資訊，請參閱[工作流程監視](heatmap.md)。

## 使用活動 {#using-activities}

>[!CAUTION]
>
>您可以在相同的工作流程中複製和貼上活動。 不過，我們不建議跨不同的工作流程複製貼上活動。 某些附加至傳送和排程器等活動的設定，在執行目標工作流程時可能會導致衝突和錯誤。 我們建議您&#x200B;**複製**&#x200B;工作流程。 如需詳細資訊，請參閱[複製工作流程](building-a-workflow.md#duplicating-workflows)。

### 活動的名稱 {#name-of-the-activity}

在開發工作流程時，所有活動都會有名稱，所有Adobe Campaign物件亦然。 雖然該名稱是由工具產生的，但我們建議您在設定時，以明確的名稱來重新命名它。 稍後執行此動作的風險在於，它可能會使用另一個先前活動的名稱中斷工作流程的活動。 因此，後續更新名稱會是一項困難的工作。

可在&#x200B;**[!UICONTROL Advanced]**&#x200B;索引標籤中找到活動名稱。 不要保留名為&#x200B;**[!UICONTROL query]**、**[!UICONTROL query1]**、**[!UICONTROL query11]**&#x200B;的檔案，但請賦予其明確的名稱，例如&#x200B;**[!UICONTROL querySubscribedRecipients]**。 此名稱將會顯示在日誌中，如果適用，還會顯示在SQL記錄中，這有助於在設定工作流程時對其進行偵錯。

### 第一個和最後一個活動 {#first-and-last-activities}

* 一律以&#x200B;**[!UICONTROL Start]**&#x200B;活動或&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動開始您的工作流程。 相關時，您也可以使用&#x200B;**[!UICONTROL External signal]**&#x200B;活動。
* 在建立工作流程時，每個分支僅使用一個&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動。 如果工作流程的同一分支有多個排程器（相互連結），則要執行的任務數量將呈指數倍增，這將使資料庫大幅超載。 此規則也適用於所有具有&#x200B;**[!UICONTROL Scheduling & History]**&#x200B;索引標籤的活動。 深入瞭解[排程](scheduler.md)。

  ![](assets/wf-scheduler.png)

* 針對每個工作流程使用&#x200B;**[!UICONTROL End]**&#x200B;活動。 這可讓Adobe Campaign釋出用於工作流程中計算的暫存空間。 有關詳細資訊，請參閱： [開始和結束](start-and-end.md)。

### 活動中的Javascript {#javascript-within-an-activity}

初始化工作流程活動時，您可能想要新增JavaScript。 這可以在活動的&#x200B;**[!UICONTROL Advanced]**&#x200B;索引標籤中完成。

若要更輕鬆地尋找工作流程，我們建議在活動標籤的開頭和結尾使用雙破折號，如下所示： — 我的標籤 — 。

### 訊號 {#signal}

在大多數情況下，您不會知道從哪裡呼叫訊號。 為了避免此問題，請使用訊號活動&#x200B;**[!UICONTROL Advanced]**&#x200B;索引標籤內的&#x200B;**[!UICONTROL Comment]**&#x200B;欄位，來記錄此活動的訊號預期來源。

![](assets/workflow-signal-bp.png)

## 工作流程更新 {#workflow-update}

不應直接更新生產工作流程。 除非流程包含使用範本工作流程建立行銷活動，否則應先在開發環境中測試流程。 此驗證後，工作流程即可部署並在生產環境中啟動。

在開發或中繼環境中執行所有測試，而不是在生產環境中執行。 在這種情況下，無法確保效能。

封存的工作流程可能會保留在開發或測試平台上的封存資料夾中，但生產環境應儘可能保持乾淨。 如果舊的工作流程處於非使用中狀態，則應將其從生產環境中移除。
