---
solution: Campaign Classic
product: campaign
title: 工作流程執行
description: 工作流程執行
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: a9d58e25ab17baaabf4ff8c109b53e83c7d93218
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 3%

---


# 工作流程執行{#workflow-execution}

以下章節提供與工作流程執行相關的常見問題，以及如何疑難排解的資訊。

如需工作流程的詳細資訊，請參閱下列章節：

* [關於工作流程](../../workflow/using/about-workflows.md)
* [啟動工作流程](../../workflow/using/starting-a-workflow.md)
* [工作流程生命週期](../../workflow/using/workflow-life-cycle.md)
* [使用工作流程時的最佳實務](../../workflow/using/workflow-best-practices.md)

## 盡快開始促銷活動{#start-as-soon-as-possible-in-campaigns}

在某些情況下，從促銷活動執行的工作流程不會在按一下&#x200B;**[!UICONTROL Start]**&#x200B;按鈕時啟動。 它不會開始，而是進入「盡快開始」狀態。

此問題可能有數個原因，請依照下列步驟加以解決：

1. 檢查[**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md)技術工作流狀態。 此工作流程管理促銷活動內的工作或工作流程。 如果失敗，這會導致工作流程無法啟動／停止。 重新啟動它以繼續執行促銷活動工作流程。

   有關技術工作流監控的詳細資訊，請參閱[本頁](../../workflow/using/monitoring-technical-workflows.md)。

   >[!NOTE]
   >
   >重新啟動工作流程後，請確定您執行待審任務（按一下右鍵&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動/ **[!UICONTROL Execute pending task(s) now]**），以便檢查它是否在任何活動上再次失敗。

   如果工作流仍然失敗，請檢查審計日誌中是否有特定錯誤，並據以進行故障排除，然後再次重新啟動工作流。

1. 在&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤中檢查&#x200B;**[!UICONTROL wfserver]**&#x200B;模組狀態，該標籤可從Campaign Classic首頁存取（請參閱[監控進程](../../production/using/monitoring-processes.md)）。 此程式負責執行所有工作流程。

   管理員用戶還可以使用以下命令檢查&#x200B;**wfserver@`<instance>`**&#x200B;模組是否已在主應用程式伺服器上啟動。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   如果模組未執行，請聯絡Adobe客戶服務。 如果您有內部部署安裝，管理員使用者必須使用以下命令重新啟動服務。

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >將&#x200B;**`<instancename>`**取代為例項名稱（生產、開發等）。 實例名稱通過配置檔案標識：
   >`[path of application]nl6/conf/config-<instancename>.xml`

   有關如何重新啟動模組的詳細資訊，請參閱[本節](../../production/using/usual-commands.md#module-launch-commands)。

1. 檢查執行個體上執行&#x200B;**的促銷活動進程數是否大於臨界值。**[**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management)選項針對可並行執行於執行個體上的促銷活動程式數量定義了限制。 當達到此限制時，只要執行的工作流程數量超過限制，工作流程就會維持在「盡快開始」狀態。

   若要解決此問題，請停止不想要的工作流程並刪除失敗的傳送。 如果達到閾值，則允許運行新進程。

   若要檢查執行個體的工作流程數目，建議您使用預先定義的檢視，預設可在&#x200B;**[!UICONTROL Administration]** / **[!UICONTROL Audit]**&#x200B;資料夾中存取。 如需詳細資訊，請參閱[本頁面](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)。

   >[!IMPORTANT]
   >
   >增加&#x200B;**[!UICONTROL NmsOperation_LimitConcurrency]**&#x200B;選項臨界值可能會導致例項的效能問題。 無論如何，請勿自行執行此動作，並聯絡您的Adobe Campaign聯絡人。

有關如何監控工作流的詳細資訊，請參閱[本節](../../workflow/using/monitoring-workflow-execution.md)。

## 開始進行{#start-in-progress}

如果工作流未執行，且其狀態為&#x200B;**開始進行**，這可能表示工作流模組未啟動。

要檢查此問題並在必要時啟動模組，請應用以下步驟：

1. 在&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤中檢查&#x200B;**[!UICONTROL wfserver]**&#x200B;模組狀態，該標籤可從Campaign Classic首頁存取（請參閱[監控進程](../../production/using/monitoring-processes.md)）。

   管理員用戶還可以使用以下命令檢查&#x200B;**wfserver@`<instance>`**&#x200B;模組是否已在主應用程式伺服器上啟動。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   有關如何監視模組的詳細資訊，請參閱[本節](../../production/using/usual-commands.md#monitoring-commands-)。

1. 如果模組未執行，請聯絡Adobe客戶服務。 如果您有內部部署安裝，管理員必須使用以下命令重新啟動安裝。

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >將&#x200B;**`<instancename>`**取代為例項名稱（生產、開發等）。 實例名稱通過配置檔案標識：
   >`[path of application]nl6/conf/config-<instancename>.xml`

   有關如何重新啟動模組的詳細資訊，請參閱[本節](../../production/using/usual-commands.md#module-launch-commands)。

## 工作流{#failed-workflow}失敗

如果工作流失敗，請執行以下步驟：

1. 檢查工作流日記帳。 有關詳細資訊，請參閱[監視工作流執行](../../workflow/using/monitoring-workflow-execution.md)和[顯示日誌](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)部分。
1. 監控技術工作流程。 有關詳細資訊，請參閱[本節](../../workflow/using/monitoring-technical-workflows.md)。
1. 尋找個別工作流程活動的失敗之處。
