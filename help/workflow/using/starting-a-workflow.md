---
product: campaign
title: 開始工作流程
description: 瞭解如何啟動工作流程，並探索工作流程動作工具列和滑鼠右鍵選單
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 1baf424138c95b16add37d9d556e3a2566a869c2
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 2%

---

# 開始工作流程 {#starting-a-workflow}



工作流程一律以手動方式啟動。 但是，啟動後，它會根據透過排程器指定的資訊保持非使用中(請參閱 [排程器](scheduler.md))或活動排程。

與目標工作流程執行相關的動作（啟動、停止、暫停等） 為 **非同步** 處理序：此順序會記錄下來，一旦伺服器可供套用就會生效。

工具列可讓您啟動及追蹤工作流程的執行。

中可用的選項清單 **[!UICONTROL Actions]** 功能表和右鍵功能表詳述如下。

>[!IMPORTANT]
>
>請記住，當運運算元在工作流程上執行動作（啟動、停止、暫停等）時，該動作不會立即執行，而是放置在佇列中，以便由 [工作流程模組](architecture.md).

## 動作工具列 {#actions-toolbar}

此頁面中詳細說明了工具列按鈕 [區段](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). 此 **[!UICONTROL Actions]** 按鈕可讓您存取對所選工作流程執行動作的其他執行選項。 您也可以使用 **[!UICONTROL File > Actions]** 功能表，或以滑鼠右鍵按一下工作流程並選取「 」 **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

  此動作可讓您開始執行工作流程：此工作流程已 **已完成**， **正在編輯** 或 **已暫停** 將狀態更改為 **已開始**. 然後，工作流程引擎會處理此工作流程的執行。 如果工作流程已暫停，則會繼續，否則會從頭開始工作流程並啟動初始活動。

  啟動為非同步流程：系統會儲存請求，並儘快由工作流程伺服器處理。

* **[!UICONTROL Pause]**

  此動作會將工作流程的狀態設為 **已暫停**. 在繼續工作流程之前，不會啟用任何活動，但不會暫停進行中的作業。

* **[!UICONTROL Stop]**

  此動作會停止目前正在執行的工作流程。 執行個體的狀態設為 **已完成**. 如果可能的話，進行中的作業會停止。 立即取消匯入和SQL查詢。

  >[!IMPORTANT]
  >
  >停止工作流程為非同步程式：要求已註冊，然後一或多個工作流程伺服器會取消進行中的操作。 因此，停止工作流程執行個體可能需要一些時間，尤其是如果工作流程正在多個伺服器上執行時，每個伺服器都必須取得控制權才能取消進行中的工作。 若要避免發生任何問題，請等候停止作業完成，並且不要在同一工作流程上執行多個停止要求。

* **[!UICONTROL Unconditional stop]**

  此選項會將工作流程狀態變更為 **[!UICONTROL Finished]**. 只有在數分鐘後正常停止程式失敗時，才應將此動作作為最後手段。 只有在您確定沒有進行中的實際工作流程工作時，才使用無條件停止。

  >[!CAUTION]
  >
  >此選項為專家使用者保留。

* **[!UICONTROL Restart]**

  此動作會停止，然後重新啟動工作流程。 在大多數情況下，它可以讓您更快速地重新啟動。 當停止需要一定的時間時，自動重新啟動也很實用：這是因為當工作流程停止時，「停止」命令無法使用。

  此 **[!UICONTROL Start / Pause / Stop / Restart]** 您也可以透過工具列中的執行圖示執行動作。 如需詳細資訊，請參閱本[區段](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)。

* **[!UICONTROL Purge history]**

  此動作可讓您清除工作流程歷史記錄。 有關詳細資訊，請參閱 [清除記錄](monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

  此選項可讓您以模擬模式（而非實際模式）啟動工作流程。 這表示當您啟用此模式時，只會執行不會影響資料庫或檔案系統的活動(例如 **[!UICONTROL Query]**， **[!UICONTROL Union]**， **[!UICONTROL Intersection]**、等)。 有影響的活動(例如 **[!UICONTROL Export]**， **[!UICONTROL Import]**、等) 以及之後的專案（在相同分支中）都不會執行。

* **[!UICONTROL Execute pending tasks now]**

  此動作可讓您儘快啟動所有待處理工作。 若要啟動特定工作，請以滑鼠右鍵按一下其活動並選取「 」 **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Save as template]**

  此動作會根據所選的工作流程建立新的工作流程範本。 您必須指定其儲存所在的資料夾(位於 **[!UICONTROL Folder]** 欄位)。

  此 **[!UICONTROL Mass update of selected lines]** 和 **[!UICONTROL Merge selected lines]** 選項是通用的平台選項，所有選項皆可使用 **[!UICONTROL Actions]** 功能表。 如需詳細資訊，請參閱本[區段](../../platform/using/updating-data.md)。


## 工作流程執行最佳實務 {#workflow-execution-best-practices}

**請勿將工作流程排程為超過每15分鐘執行一次** 因為它可能會阻礙整體系統效能，並在資料庫中建立區塊。

**避免讓工作流程處於暫停狀態**. 如果您建立臨時工作流程，請確定它可正確完成且不停留在 **[!UICONTROL paused]** 州別。 如果暫停，則表示您需要保留臨時表格，因此會增加資料庫的大小。 在「工作流程屬性」下指定「工作流程主管」，以在工作流程失敗或系統暫停時傳送警報。

若要避免工作流程處於暫停狀態：

* 請定期檢查您的工作流程，確保沒有未預期的錯誤。
* 保持工作流程儘可能簡單，例如將大型工作流程分割為數個不同的工作流程。 您可以使用 **[!UICONTROL External signal]** 活動會根據其他工作流程的執行來觸發其執行。
* 請避免在工作流程中，讓流程停用的活動保持執行緒開啟，導致許多可能會佔用大量空間的臨時表格。 不要將活動保留在 **[!UICONTROL Do not enable]** 或 **[!UICONTROL Enable but do not execute]** 工作流程中的狀態。

**停止未使用的工作流程**. 持續執行的工作流程會維持與資料庫的連線。

**僅在極少數情況下使用無條件停止**. 請勿定期使用此動作。 在工作流程產生的連線上，若未對資料庫執行乾淨關閉，將會影響效能。

**請勿在同一工作流程上執行多個停止請求**. 停止工作流程為非同步程式：要求已註冊，然後一或多個工作流程伺服器會取消進行中的操作。 因此，停止工作流程執行個體可能需要一些時間，尤其是如果工作流程正在多個伺服器上執行時，每個伺服器都必須取得控制權才能取消進行中的工作。 若要避免發生任何問題，請等候停止作業完成，並避免多次停止工作流程。

## 在功能表上按一下右鍵 {#right-click-menu}

選取一或多個工作流程活動時，您可以按一下滑鼠右鍵依您的選取範圍採取行動。

![](assets/contextual_menu.png)

在右鍵功能表中提供下列選項：

**[!UICONTROL Open]**：此選項可讓您存取活動屬性。

**[!UICONTROL Display logs:]** 此選項可讓您檢視所選活動的作業執行記錄。 請參閱 [顯示記錄](monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** 此動作可讓您儘快啟動擱置中的任務。

**[!UICONTROL Workflow restart from a task:]** 此選項可讓您使用先前為此活動儲存的結果來重新啟動工作流程。

**[!UICONTROL Cut/Copy/Paste/Delete:]** 這些選項可讓您剪下、複製、貼上和刪除活動。

**[!UICONTROL Copy as bitmap:]** 此選項可讓您擷取所有活動的熒幕擷圖。

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 這些選項也適用於 **[!UICONTROL Advanced]** 活動屬性的索引標籤。 其詳細資訊請參閱 [執行](advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** 可讓您儲存或取消對工作流程所做的變更。

>[!NOTE]
>
>您可以選取一組活動，並將其中一個命令套用至這些活動。

右鍵功能表也詳載於此 [區段](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow).
