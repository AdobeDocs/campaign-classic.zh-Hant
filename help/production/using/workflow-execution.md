---
product: campaign
title: 工作流程執行
description: 工作流程執行
feature: Monitoring, Workflows
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---

# 工作流程執行{#workflow-execution}



以下區段提供與工作流程執行相關的常見問題以及如何疑難排解這些問題的資訊。

如需工作流程的詳細資訊，請參閱下列區段：

* [關於工作流程](../../workflow/using/about-workflows.md)
* [啟動工作流程](../../workflow/using/starting-a-workflow.md)
* [工作流程生命週期](../../workflow/using/workflow-life-cycle.md)
* [使用工作流程時的最佳實務](../../workflow/using/workflow-best-practices.md)

## 在行銷活動中儘快開始 {#start-as-soon-as-possible-in-campaigns}

在某些情況下，按一下&#x200B;**[!UICONTROL Start]**&#x200B;按鈕時，從行銷活動執行的工作流程不會開始。 此狀態不會開始，而會進入「儘快開始」狀態。

此問題可能有幾個原因，請遵循下列步驟加以解決：

1. 檢查[**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md)技術工作流程狀態。 此工作流程可管理行銷活動內的工作或工作流程。 如果失敗，會導致工作流程無法啟動/停止。 重新啟動以繼續行銷活動工作流程執行。

   如需技術工作流程監視的詳細資訊，請參閱[此頁面](../../workflow/using/monitoring-technical-workflows.md)。

   >[!NOTE]
   >
   >工作流程重新啟動後，請確定您執行擱置中的任務（以滑鼠右鍵按一下&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動/ **[!UICONTROL Execute pending task(s) now]**），以檢查它是否在任何活動上再次失敗。

   如果工作流程仍然失敗，請檢查稽核記錄檔中的特定錯誤，並據此進行疑難排解，然後再次重新啟動工作流程。

1. 檢查&#x200B;**[!UICONTROL Monitoring]**&#x200B;索引標籤中的&#x200B;**[!UICONTROL wfserver]**&#x200B;模組狀態，可從Campaign Classic首頁存取（請參閱[監視處理序](../../production/using/monitoring-processes.md)）。 此程式負責執行所有工作流程。

   管理員使用者也可以使用以下命令，檢查是否已在您的主要應用程式伺服器上啟動&#x200B;**wfserver@`<instance>`**&#x200B;模組。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   如果模組未執行，請聯絡Adobe客戶服務。 如果您是內部部署安裝，管理員使用者必須使用下列命令重新啟動服務。

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >將&#x200B;**`<instance-name>`**取代為您執行個體的名稱（生產、開發等）。 執行個體名稱會透過設定檔案識別：
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   如需如何重新啟動模組的詳細資訊，請參閱[本節](../../production/using/usual-commands.md#module-launch-commands)。

1. 檢查在執行個體上執行&#x200B;**的行銷活動處理序的**&#x200B;數目是否超過臨界值。 [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management)選項定義了一個限制，限制在執行個體上並行執行多少行銷活動程式。 當達到此限制時，只要執行的工作流程數量超過限制，工作流程就會維持在「儘快開始」狀態。

   若要解決此問題，請停止不需要的工作流程並刪除失敗的傳送。 如果達到臨界值，將允許執行新程式。

   若要檢查執行個體正在執行的工作流程數目，我們建議使用預先定義的檢視，預設可在&#x200B;**[!UICONTROL Administration]** / **[!UICONTROL Audit]**&#x200B;資料夾中存取。 如需詳細資訊，請參閱[本頁面](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)。

   >[!IMPORTANT]
   >
   >提高&#x200B;**[!UICONTROL NmsOperation_LimitConcurrency]**&#x200B;選項臨界值可能會導致執行個體出現效能問題。 無論如何，請勿自行執行此動作，並聯絡Adobe Campaign聯絡人。

如需如何監視工作流程的詳細資訊，請參閱[本節](../../workflow/using/monitoring-workflow-execution.md)。

## 開始進行中 {#start-in-progress}

如果工作流程未執行，且其狀態為&#x200B;**正在啟動**，這可能表示工作流程模組未啟動。

若要勾選此專案並在必要時啟動模組，請套用下列步驟：

1. 檢查&#x200B;**[!UICONTROL Monitoring]**&#x200B;索引標籤中的&#x200B;**[!UICONTROL wfserver]**&#x200B;模組狀態，可從Campaign Classic首頁存取（請參閱[監視處理序](../../production/using/monitoring-processes.md)）。

   管理員使用者也可以使用以下命令，檢查是否已在您的主要應用程式伺服器上啟動&#x200B;**wfserver@`<instance>`**&#x200B;模組。

   ```sql
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   如需如何監視模組的詳細資訊，請參閱[本節](../../production/using/usual-commands.md#monitoring-commands-)。

1. 如果模組未執行，請聯絡Adobe客戶服務。 如果您有內部部署安裝，管理員必須使用下列命令將其重新啟動。

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >將&#x200B;**`<instance-name>`**取代為您執行個體的名稱（生產、開發等）。 執行個體名稱會透過設定檔案識別：
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   如需如何重新啟動模組的詳細資訊，請參閱[本節](../../production/using/usual-commands.md#module-launch-commands)。

## 失敗的工作流程 {#failed-workflow}

如果工作流程失敗，請執行以下步驟：

1. 檢查工作流程日誌。 如需詳細資訊，請參閱[監視工作流程執行](../../workflow/using/monitoring-workflow-execution.md)及[顯示記錄](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)區段。
1. 監視技術工作流程。 如需詳細資訊，請參閱[本節](../../workflow/using/monitoring-technical-workflows.md)。
1. 尋找個別工作流程活動上的失敗。
