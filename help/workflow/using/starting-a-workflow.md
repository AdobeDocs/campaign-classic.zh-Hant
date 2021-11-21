---
product: campaign
title: 啟動工作流程
description: 了解如何開始工作流程，並探索工作流程動作工具列和滑鼠右鍵功能表
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 2%

---

# 啟動工作流程 {#starting-a-workflow}

![](../../assets/common.svg)

工作流程一律手動啟動。 不過，啟動後，視透過排程器指定的資訊而定，可能會維持非作用中狀態(請參閱 [排程器](scheduler.md))或活動排程。

與目標工作流程執行（啟動、停止、暫停等）相關的動作 為 **非同步** 流程：訂單會記錄下來，當伺服器可供套用時，訂單就會生效。

工具列可讓您啟動及追蹤工作流程的執行。

中可用的選項清單 **[!UICONTROL Actions]** 功能表和滑鼠右鍵功能表於下方詳細說明。

>[!IMPORTANT]
>
>請記住，當運算子對工作流程（開始、停止、暫停等）執行動作時，該動作不會立即執行，而會放在佇列中，以便由 [工作流程模組](architecture.md).

## 動作工具列 {#actions-toolbar}

工具列按鈕在此中有詳細說明 [節](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). 此 **[!UICONTROL Actions]** 按鈕可讓您存取其他執行選項，以依所選工作流程執行動作。 您也可以使用 **[!UICONTROL File > Actions]** ，或按一下右鍵工作流並選擇 **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   此動作可讓您開始執行工作流程：工作流 **已完成**, **正在編輯** 或 **已暫停** 更改狀態 **已開始**. 然後，工作流引擎將處理此工作流的執行。 如果工作流程已暫停，則會繼續，否則工作流程會從頭開始，並啟動初始活動。

   啟動是非同步程式：系統會儲存要求，並盡快由工作流程伺服器處理。

* **[!UICONTROL Pause]**

   此動作會將工作流程的狀態設定為 **已暫停**. 在繼續工作流程之前，不會啟動任何活動；但不會暫停進行中的操作。

* **[!UICONTROL Stop]**

   此動作會停止目前執行的工作流程。 執行個體的狀態設為 **已完成**. 如果可能，將停止正在進行的操作。 立即取消導入和SQL查詢。

   停止是非同步進程。 請求已註冊，然後工作流伺服器或伺服器取消正在進行的操作。 因此，停止工作流實例可能需要時間，尤其是當工作流在多個伺服器上運行時，每個伺服器都必須控制以取消正在進行的任務。

* **[!UICONTROL Restart]**

   此動作會停止，然後重新啟動工作流程。 在大多數情況下，可以更快地重新啟動。 在停止需要一定時間時自動重新啟動也很有用：這是因為當工作流停止時，「停止」命令不可用。

   此 **[!UICONTROL Start / Pause / Stop / Restart]** 動作也可透過工具列中的執行圖示使用。 如需詳細資訊，請參閱本[區段](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)。

* **[!UICONTROL Purge history]**

   此動作可讓您清除工作流程歷史記錄。 有關詳細資訊，請參閱 [清除日誌](monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

   此選項可讓您在模擬模式中啟動工作流程，而非實際模式。 這表示當您啟用此模式時，只會執行不影響資料庫或檔案系統的活動(例如 **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**&#x200B;等)。 確實有影響的活動(例如 **[!UICONTROL Export]**, **[!UICONTROL Import]**&#x200B;等) 以及之後的不會執行（在相同分支中）。

* **[!UICONTROL Execute pending tasks now]**

   此動作可讓您盡快開始所有待處理的工作。 若要啟動特定任務，請以滑鼠右鍵按一下其活動並選取 **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Unconditional stop]**

   此選項會將工作流程狀態變更為 **[!UICONTROL Finished]**. 只有在正常停止程式在幾分鐘後失敗時，才應將此動作當作最後手段。 只有在您確定沒有實際工作流程作業正在進行時，才使用無條件停止。

   >[!CAUTION]
   >
   >此選項保留給專家使用者。

* **[!UICONTROL Save as template]**

   此操作會根據所選工作流建立新的工作流模板。 您必須指定要儲存該資料夾的位置(在 **[!UICONTROL Folder]** 欄位)。

   此 **[!UICONTROL Mass update of selected lines]** 和 **[!UICONTROL Merge selected lines]** 選項是所有 **[!UICONTROL Actions]** 功能表。 如需詳細資訊，請參閱本[區段](../../platform/using/updating-data.md)。

## 右鍵功能表 {#right-click-menu}

選取一或多個工作流程活動時，您可以按一下滑鼠右鍵，以對您選取的項目採取動作。

![](assets/contextual_menu.png)

滑鼠右鍵功能表中提供下列選項：

**[!UICONTROL Open]**:此選項可讓您存取活動屬性。

**[!UICONTROL Display logs:]** 此選項可讓您查看所選活動的任務執行日誌。 請參閱 [顯示日誌](monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** 此動作可讓您盡快開始待定任務。

**[!UICONTROL Workflow restart from a task:]** 此選項可讓您使用先前為此活動儲存的結果來重新啟動工作流程。

**[!UICONTROL Cut/Copy/Paste/Delete:]** 這些選項可讓您剪下、複製、貼上和刪除活動。

**[!UICONTROL Copy as bitmap:]** 此選項可讓您擷取所有活動的螢幕擷取畫面。

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 這些選項也可在 **[!UICONTROL Advanced]** 標籤。 詳細資訊於 [執行](advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** 可讓您儲存或取消對工作流程所做的變更。

>[!NOTE]
>
>您可以選取一組活動，並將其中一個命令套用至這些活動。

右鍵功能表在此也有詳細說明 [節](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
