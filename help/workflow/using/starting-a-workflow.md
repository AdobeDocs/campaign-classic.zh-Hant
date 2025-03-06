---
product: campaign
title: 開始工作流程
description: 瞭解如何啟動工作流程，並探索工作流程動作工具列和滑鼠右鍵選單
feature: Workflows
hide: true
hidefromtoc: true
exl-id: d345ba62-c2fb-43df-a2a1-e9e4292d301a
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 1%

---

# 開始工作流程 {#starting-a-workflow}



工作流程一律以手動方式啟動。 但是，啟動後，它會根據透過排程器（請參閱[排程器](scheduler.md)）或活動排程指定的資訊，保持非使用中。

與目標工作流程執行（啟動、停止、暫停等）相關的動作為&#x200B;**非同步**&#x200B;程式：此順序會記錄下來，而且會在伺服器可供套用時立即生效。

工具列可讓您啟動及追蹤工作流程的執行。

**[!UICONTROL Actions]**&#x200B;功能表及右鍵功能表中可用的選項清單詳述如下。

>[!IMPORTANT]
>
>請記住，當運運算元在工作流程上執行動作（啟動、停止、暫停等）時，該動作不會立即執行，而是放在佇列中以便由[工作流程模組](architecture.md)處理。

## 動作工具列 {#actions-toolbar}

此[區段](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)中詳細說明了工具列按鈕。 **[!UICONTROL Actions]**&#x200B;按鈕可讓您存取對所選工作流程執行動作的其他執行選項。 您也可以使用&#x200B;**[!UICONTROL File > Actions]**&#x200B;功能表，或以滑鼠右鍵按一下工作流程並選取&#x200B;**[!UICONTROL Actions]**。

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

  此動作可讓您開始執行工作流程： **已完成**、**正在編輯**&#x200B;或&#x200B;**已暫停**&#x200B;的工作流程會將狀態變更為&#x200B;**已開始**。 然後，工作流程引擎會處理此工作流程的執行。 如果工作流程已暫停，則會繼續，否則會從頭開始工作流程並啟動初始活動。

  啟動為非同步流程：系統會儲存請求，並儘快由工作流程伺服器處理。

* **[!UICONTROL Pause]**

  此動作會將工作流程的狀態設為&#x200B;**已暫停**。 在繼續工作流程之前，不會啟用任何活動，但不會暫停進行中的作業。

* **[!UICONTROL Stop]**

  此動作會停止目前正在執行的工作流程。 執行個體的狀態設定為&#x200B;**已完成**。 如果可能的話，進行中的作業會停止。 立即取消匯入和SQL查詢。

  >[!IMPORTANT]
  >
  >停止工作流程為非同步程式：要求已註冊，然後一或多個工作流程伺服器會取消進行中的操作。 因此，停止工作流程執行個體可能需要一些時間，尤其是如果工作流程正在多個伺服器上執行時，每個伺服器都必須取得控制權才能取消進行中的工作。 若要避免發生任何問題，請等候停止作業完成，並且不要在同一工作流程上執行多個停止要求。

* **[!UICONTROL Unconditional stop]**

  此選項會將工作流程狀態變更為&#x200B;**[!UICONTROL Finished]**。 只有在數分鐘後正常停止程式失敗時，才應將此動作作為最後手段。 只有在您確定沒有進行中的實際工作流程工作時，才使用無條件停止。

  >[!CAUTION]
  >
  >管理員使用者僅限無條件停止。

* **[!UICONTROL Restart]**

  此動作會停止，然後重新啟動工作流程。 在大多數情況下，它可以讓您更快速地重新啟動。 當停止需要一定的時間時，自動重新啟動也很實用：這是因為當工作流程停止時，「停止」命令無法使用。

  **[!UICONTROL Start / Pause / Stop / Restart]**&#x200B;動作也可透過工具列中的執行圖示使用。 如需詳細資訊，請參閱本[區段](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow)。

  請注意，**重新啟動**&#x200B;動作不會清除與&#x200B;**執行**、**停止**&#x200B;和&#x200B;**開始**&#x200B;動作相較的工作流程執行個體變數（執行個體變數會在啟動動作時清除）。 重新啟動工作流程時，執行個體變數仍可與保留值搭配使用。 若要清除這些專案，您可以：
   * 執行&#x200B;**停止**&#x200B;和&#x200B;**啟動**&#x200B;動作。
   * 在工作流程執行結束時，新增以下javascript程式碼：

     ```
     var wkf = xtk.workflow.load(instance.id)
     wkf.variables='<variables/>'
     wkf.save()
     ```

* **[!UICONTROL Purge history]**

  此動作可讓您清除工作流程歷史記錄。 如需詳細資訊，請參閱[清除記錄檔](monitoring-workflow-execution.md#purging-the-logs)。

* **[!UICONTROL Start in simulation mode]**

  此選項可讓您以模擬模式（而非實際模式）啟動工作流程。 這表示當您啟用此模式時，只會執行不會影響資料庫或檔案系統的活動（例如&#x200B;**[!UICONTROL Query]**、**[!UICONTROL Union]**、**[!UICONTROL Intersection]**&#x200B;等）。 有影響的活動（例如&#x200B;**[!UICONTROL Export]**、**[!UICONTROL Import]**&#x200B;等）及其後的活動（在相同分支中）不會執行。

* **[!UICONTROL Execute pending tasks now]**

  此動作可讓您儘快啟動所有待處理工作。 若要啟動特定工作，請以滑鼠右鍵按一下其活動並選取&#x200B;**[!UICONTROL Execute pending task(s) now]**。

* **[!UICONTROL Save as template]**

  此動作會根據所選的工作流程建立新的工作流程範本。 您必須指定要儲存的資料夾（在&#x200B;**[!UICONTROL Folder]**&#x200B;欄位中）。

  **[!UICONTROL Mass update of selected lines]**&#x200B;和&#x200B;**[!UICONTROL Merge selected lines]**&#x200B;選項是所有&#x200B;**[!UICONTROL Actions]**&#x200B;功能表中都可用的通用平台選項。 如需詳細資訊，請參閱本[區段](../../platform/using/updating-data.md)。


## 工作流程執行最佳實務 {#workflow-execution-best-practices}

**請勿將工作流程排程為超過每15分鐘執行一次**，因為它可能會阻礙整體系統效能並在資料庫中建立區塊。

**請避免讓工作流程處於暫停狀態**。 如果您建立暫時性工作流程，請確定工作流程可以正確完成，而不會維持在&#x200B;**[!UICONTROL paused]**&#x200B;狀態。 如果暫停，則表示您需要保留臨時表格，因此會增加資料庫的大小。 在「工作流程屬性」下指定「工作流程主管」，以在工作流程失敗或系統暫停時傳送警報。

若要避免工作流程處於暫停狀態：

* 請定期檢查您的工作流程，確保沒有未預期的錯誤。
* 保持工作流程儘可能簡單，例如將大型工作流程分割為數個不同的工作流程。 您可以使用&#x200B;**[!UICONTROL External signal]**&#x200B;個活動，根據其他工作流程的執行觸發其執行。
* 請避免在工作流程中，讓流程停用的活動保持執行緒開啟，導致許多可能會佔用大量空間的臨時表格。 請勿將活動保留在您的工作流程中&#x200B;**[!UICONTROL Do not enable]**&#x200B;或&#x200B;**[!UICONTROL Enable but do not execute]**&#x200B;狀態。

**停止未使用的工作流程**。 持續執行的工作流程會維持與資料庫的連線。

**只在極少數情況下才使用無條件停止**。 此選項僅限管理員使用者使用。 請勿定期使用此動作。 在工作流程產生的連線上，若未對資料庫執行乾淨關閉，將會影響效能。

**請勿在同一工作流程上執行多個停止要求**。 停止工作流程為非同步程式：要求已註冊，然後一或多個工作流程伺服器會取消進行中的操作。 因此，停止工作流程執行個體可能需要一些時間，尤其是如果工作流程正在多個伺服器上執行時，每個伺服器都必須取得控制權才能取消進行中的工作。 若要避免發生任何問題，請等候停止作業完成，並避免多次停止工作流程。

## 在功能表上按一下右鍵 {#right-click-menu}

選取一或多個工作流程活動時，您可以按一下滑鼠右鍵依您的選取範圍採取行動。

![](assets/contextual_menu.png)

在右鍵功能表中提供下列選項：

**[!UICONTROL Open]**：此選項可讓您存取活動屬性。

**[!UICONTROL Display logs:]**&#x200B;此選項可讓您檢視所選活動的任務執行記錄。 請參閱[顯示記錄檔](monitoring-workflow-execution.md#displaying-logs)。

**[!UICONTROL Execute pending task(s) now:]**&#x200B;此動作可讓您儘快啟動擱置中的任務。

**[!UICONTROL Workflow restart from a task:]**&#x200B;此選項可讓您使用先前為此活動儲存的結果來重新啟動工作流程。

**[!UICONTROL Cut/Copy/Paste/Delete:]**&#x200B;這些選項可讓您剪下、複製、貼上和刪除活動。

**[!UICONTROL Copy as bitmap:]**&#x200B;此選項可讓您擷取所有活動的熒幕擷圖。

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]**&#x200B;這些選項也可在活動屬性的&#x200B;**[!UICONTROL Advanced]**&#x200B;索引標籤中使用。 它們在[執行](advanced-parameters.md#execution)中有詳細的說明。

**[!UICONTROL Save / Cancel:]**&#x200B;可讓您儲存或取消對工作流程所做的變更。

>[!NOTE]
>
>您可以選取一組活動，並將其中一個命令套用至這些活動。

在此[區段](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow)中也會詳細說明按滑鼠右鍵選單。
