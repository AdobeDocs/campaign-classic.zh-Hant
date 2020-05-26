---
title: 啟動工作流
description: 瞭解如何開始工作流程並探索工作流程動作工具列和按一下滑鼠右鍵的功能表。
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---


# 啟動工作流 {#starting-a-workflow}

工作流程一律以手動方式啟動。 但是，啟動時，它可以根據通過調度程式指定的資訊(請參見 [Scheduler](../../workflow/using/scheduler.md))或活動調度來保持非活動狀態。

與定位工作流程執行（啟動、停止、暫停等）相關的動作 是非 **同步進程** : 訂單會記錄下來，當伺服器可供套用時，訂單就會生效。

工具列可讓您啟動並追蹤工作流程的執行。

功能表和右鍵功能表 **[!UICONTROL Actions]** 中可用選項的清單在下方詳述。

## 動作工具列 {#actions-toolbar}

本節將詳細介紹工具欄 [按鈕](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)。 此按 **[!UICONTROL Actions]** 鈕可讓您存取其他執行選項，以便在選取的工作流程上執行。 您也可以使用功 **[!UICONTROL File > Actions]** 能表，或以滑鼠右鍵按一下工作流程並選取 **[!UICONTROL Actions]**。

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   此動作可讓您開始執行工作流程： 已完成、正在編 **輯**&#x200B;或暫 **停的工作流將狀** 態更改為 ********&#x200B;已啟動 然後，工作流引擎將處理此工作流的執行。 如果暫停了工作流，則會繼續，否則工作流會從頭開始，並激活初始活動。

   啟動是非同步程式： 請求會儲存，並由工作流程伺服器盡快處理。

* **[!UICONTROL Pause]**

   此動作會將工作流程的狀態設為「暫 **停」**。 在工作流恢復之前，不會激活任何活動； 但不會暫停進行中的操作。

* **[!UICONTROL Stop]**

   此動作會停止目前執行的工作流程。 實例的狀態設定為「已 **完成」**。 如果可能，將停止正在進行的操作。 導入和SQL查詢會立即取消。

   停止是非同步進程。 該請求被註冊，然後工作流伺服器或伺服器取消正在進行的操作。 因此，停止工作流實例可能需要時間，尤其是當工作流在多個伺服器上運行時，每個伺服器都必須控制其中的一個，以取消正在進行的任務。

* **[!UICONTROL Restart]**

   此動作會停止，然後重新啟動工作流程。 在大多數情況下，它可以更快地重新啟動。 當停止需要一定時間時，自動重新啟動也很有用： 這是因為當工作流停止時，「停止」命令不可用。

   這些 **[!UICONTROL Start / Pause / Stop / Restart]** 動作也可透過工具列中的執行圖示使用。 For more on this, refer to this [section](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge history]**

   此動作可讓您清除工作流程歷史記錄。 有關詳細資訊，請參閱 [清除日誌](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs)。

* **[!UICONTROL Start in simulation mode]**

   此選項可讓您在模擬模式中啟動工作流程，而非實際模式。 這表示啟用此模式時，僅執行不影響資料庫或檔案系統的活動(如 **[!UICONTROL Query]**、 **[!UICONTROL Union]**、 **[!UICONTROL Intersection]**&#x200B;等等)。 具有影響的活動(例如 **[!UICONTROL Export]**、 **[!UICONTROL Import]**&#x200B;等) 以及之後（位於相同分支）的執行。

* **[!UICONTROL Execute pending tasks now]**

   此動作可讓您盡快開始所有待審工作。 要啟動特定任務，請按一下右鍵其活動並選擇 **[!UICONTROL Execute pending task(s) now]**。

* **[!UICONTROL Unconditional stop]**

   此選項會將工作流狀態更改為 **[!UICONTROL Finished]**。 只有在正常停止進程在幾分鐘後失敗時，才應將此操作用作最後選擇。 只有在確定沒有實際工作流作業正在進行時，才使用無條件停止。

   >[!CAUTION]
   >
   >此選項保留給專家用戶。

* **[!UICONTROL Save as template]**

   此動作會根據選取的工作流程建立新的工作流程範本。 您需要指定要儲存檔案夾的資料夾(在欄位 **[!UICONTROL Folder]** 中)。

   這些 **[!UICONTROL Mass update of selected lines]** 和 **[!UICONTROL Merge selected lines]** 選項是所有功能表中可用的通用平台 **[!UICONTROL Actions]** 選項。 For more on this, refer to this [section](../../platform/using/updating-data.md).

## 右鍵功能表 {#right-click-menu}

在選取一或多個工作流程活動時，您可以按一下滑鼠右鍵，對您的選取動作。

![](assets/contextual_menu.png)

右鍵功能表提供下列選項：

**[!UICONTROL Open]**: 此選項可讓您存取活動屬性。

**[!UICONTROL Display logs:]** 此選項可讓您查看所選活動的任務執行日誌。 請參閱顯 [示日誌](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)。

**[!UICONTROL Execute pending task(s) now:]** 此動作可讓您盡快開始待審工作。

**[!UICONTROL Workflow restart from a task:]** 此選項可讓您使用先前儲存的此活動結果，重新啟動工作流程。

**[!UICONTROL Cut/Copy/Paste/Delete:]** 這些選項可讓您剪下、複製、貼上和刪除活動。

**[!UICONTROL Copy as bitmap:]** 此選項可讓您擷取所有活動的螢幕擷取。

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 這些選項也可在活動屬 **[!UICONTROL Advanced]** 性的頁籤中使用。 這些內容在「執行」 [中詳述](../../workflow/using/advanced-parameters.md#execution)。

**[!UICONTROL Save / Cancel:]** 可讓您儲存或取消對工作流程所做的變更。

>[!NOTE]
>
>您可以選取一組活動，並將其中一個命令套用至活動。

本節中也詳述了右鍵功 [能表](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow)。
