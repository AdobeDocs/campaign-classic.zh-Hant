---
product: campaign
title: 開始工作流程
description: 瞭解如何啟動工作流和發現工作流操作工具欄以及按一下右鍵菜單
feature: Workflows
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 9126e2cc088ef0e5761cc20bd19980d323f3a3ea
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 2%

---

# 開始工作流程 {#starting-a-workflow}

![](../../assets/common.svg)

工作流始終手動啟動。 但是，啟動時，它可以保持非活動狀態，這取決於通過調度程式指定的資訊(請參見 [調度程式](scheduler.md))或活動計畫。

與目標工作流執行（啟動、停止、暫停等）相關的操作 是 **非同步** 進程：訂單將被記錄，一旦伺服器可以應用，訂單將立即生效。

工具欄允許您啟動和跟蹤工作流的執行。

中可用選項的清單 **[!UICONTROL Actions]** 菜單和右鍵菜單。

>[!IMPORTANT]
>
>請記住，當操作員對工作流執行操作（啟動、停止、暫停等）時，不會立即執行該操作，而是將其放在隊列中，以便由 [工作流模組](architecture.md)。

## 操作工具欄 {#actions-toolbar}

工具欄按鈕在此中詳細介紹 [節](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)。 的 **[!UICONTROL Actions]** 按鈕允許您訪問其他執行選項以對所選工作流執行操作。 您還可以使用 **[!UICONTROL File > Actions]** ，或按一下右鍵工作流並選擇 **[!UICONTROL Actions]**。

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   此操作允許您開始執行工作流：工作流 **已完成**。 **正在編輯** 或 **已暫停** 更改狀態 **已啟動**。 然後，工作流引擎將處理此工作流的執行。 如果工作流已暫停，則它將繼續，否則，工作流將從開始啟動，初始活動將被激活。

   啟動是一個非同步進程：該請求被保存，並由工作流伺服器盡快處理。

* **[!UICONTROL Pause]**

   此操作將工作流的狀態設定為 **已暫停**。 在恢復工作流之前，不激活任何活動；但是，不會暫停正在進行的操作。

* **[!UICONTROL Stop]**

   此操作將停止當前正在執行的工作流。 實例的狀態設定為 **已完成**。 如果可能，將停止正在執行的操作。 立即取消導入和SQL查詢。

   >[!IMPORTANT]
   >
   >停止工作流是一個非同步進程：註冊該請求，然後工作流伺服器或伺服器取消正在進行的操作。 因此，停止工作流實例可能需要時間，尤其是當工作流正在多個伺服器上運行時，每個伺服器都必須控制以取消正在進行的任務。 要避免任何問題，請等待停止操作完成，並且不要在同一工作流上執行多個停止請求。

* **[!UICONTROL Restart]**

   此操作停止，然後重新啟動工作流。 在大多數情況下，它使重啟速度更快。 在停止需要一定時間時自動重新啟動也很有用：這是因為當工作流停止時「停止」命令不可用。

   的 **[!UICONTROL Start / Pause / Stop / Restart]** 操作也可通過工具欄中的執行表徵圖進行。 如需詳細資訊，請參閱本[區段](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)。

* **[!UICONTROL Purge history]**

   此操作允許您清除工作流歷史記錄。 有關此內容的詳細資訊，請參閱 [清除日誌](monitoring-workflow-execution.md#purging-the-logs)。

* **[!UICONTROL Start in simulation mode]**

   此選項允許您在模擬模式下啟動工作流，而不是在實際模式下啟動。 這意味著在啟用此模式時，只執行不影響資料庫或檔案系統的活動(例如， **[!UICONTROL Query]**。 **[!UICONTROL Union]**。 **[!UICONTROL Intersection]**&#x200B;等)。 具有影響的活動(例如 **[!UICONTROL Export]**。 **[!UICONTROL Import]**&#x200B;等) 以及之後（在同一分支中）的不執行。

* **[!UICONTROL Execute pending tasks now]**

   此操作允許您盡快啟動所有掛起的任務。 要啟動特定任務，請按一下右鍵其活動並選擇 **[!UICONTROL Execute pending task(s) now]**。

* **[!UICONTROL Unconditional stop]**

   此選項將工作流狀態更改為 **[!UICONTROL Finished]**。 只有在正常停止進程在幾分鐘後失敗時，才應將此操作用作最後手段。 僅當確定沒有實際工作流作業正在進行時才使用無條件停止。

   >[!CAUTION]
   >
   >此選項保留給專家用戶。

* **[!UICONTROL Save as template]**

   此操作將基於所選工作流建立新的工作流模板。 您需要指定保存資料夾的位置(在 **[!UICONTROL Folder]** )。

   的 **[!UICONTROL Mass update of selected lines]** 和 **[!UICONTROL Merge selected lines]** 選項是所有可用的通用平台選項 **[!UICONTROL Actions]** 菜單開啟它。 如需詳細資訊，請參閱本[區段](../../platform/using/updating-data.md)。

## 按一下右鍵菜單 {#right-click-menu}

選擇一個或多個工作流活動後，可以按一下右鍵以對所選內容執行操作。

![](assets/contextual_menu.png)

右擊菜單中提供了以下選項：

**[!UICONTROL Open]**:此選項允許您訪問活動屬性。

**[!UICONTROL Display logs:]** 此選項允許您查看所選活動的任務執行日誌。 請參閱 [顯示日誌](monitoring-workflow-execution.md#displaying-logs)。

**[!UICONTROL Execute pending task(s) now:]** 此操作允許您盡快開始掛起的任務。

**[!UICONTROL Workflow restart from a task:]** 此選項允許您使用先前為此活動儲存的結果重新啟動工作流。

**[!UICONTROL Cut/Copy/Paste/Delete:]** 這些選項允許您剪切、複製、貼上和刪除活動。

**[!UICONTROL Copy as bitmap:]** 此選項允許您拍攝所有活動的螢幕快照。

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 這些選項也可在 **[!UICONTROL Advanced]** 頁籤。 詳細資訊 [執行](advanced-parameters.md#execution)。

**[!UICONTROL Save / Cancel:]** 允許您保存或取消對工作流所做的更改。

>[!NOTE]
>
>您可以選擇一組活動，並將其中一個命令應用到活動。

按一下右鍵菜單也在此中詳細介紹 [節](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow)。
