---
product: campaign
title: 工作流程執行
description: 工作流程執行
feature: Monitoring, Workflows
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '643'
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

在某些情況下，從行銷活動執行的工作流程不會在按一下 **[!UICONTROL Start]** 按鈕。 此狀態不會開始，而會進入「儘快開始」狀態。

此問題可能有幾個原因，請遵循下列步驟加以解決：

1. 檢查 [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) 技術工作流程狀態。 此工作流程可管理行銷活動內的工作或工作流程。 如果失敗，會導致工作流程無法啟動/停止。 重新啟動以繼續行銷活動工作流程執行。

   有關技術工作流程監控的詳細資訊，請參閱 [此頁面](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >工作流程重新啟動後，請務必執行擱置中的工作(以滑鼠右鍵按一下 **[!UICONTROL Scheduler]** 活動/ **[!UICONTROL Execute pending task(s) now]**)，以檢查它是否在任何活動中再次失敗。

   如果工作流程仍然失敗，請檢查稽核記錄檔中的特定錯誤，並據此進行疑難排解，然後再次重新啟動工作流程。

1. 檢查 **[!UICONTROL wfserver]** 中的模組狀態 **[!UICONTROL Monitoring]** 索引標籤，可從Campaign Classic首頁存取(請參閱 [監控流程](../../production/using/monitoring-processes.md))。 此程式負責執行所有工作流程。

   管理員使用者還可以檢查 **wfserver@`<instance>`** 模組會使用以下命令在您的主要應用程式伺服器上啟動。

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
   >取代 **`<instance-name>`** 執行個體的名稱（生產、開發等）。 執行個體名稱會透過設定檔案識別：
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   有關如何重新啟動模組的詳細資訊，請參閱 [本節](../../production/using/usual-commands.md#module-launch-commands).

1. 檢查 **執行中的行銷活動處理序數量** 執行個體上的值大於臨界值。 有一個由定義的限制 [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) 可在執行個體上並行執行之行銷活動程式的選項。 當達到此限制時，只要執行的工作流程數量超過限制，工作流程就會維持在「儘快開始」狀態。

   若要解決此問題，請停止不需要的工作流程並刪除失敗的傳送。 如果達到臨界值，將允許執行新程式。

   若要檢查執行個體正在執行的工作流程數量，我們建議使用預先定義的檢視，預設可在中存取 **[!UICONTROL Administration]** / **[!UICONTROL Audit]** 資料夾。 如需詳細資訊，請參閱[本頁面](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)。

   >[!IMPORTANT]
   >
   >增加 **[!UICONTROL NmsOperation_LimitConcurrency]** 選項臨界值可能會導致執行個體出現效能問題。 無論如何，請勿自行執行此動作，並聯絡Adobe Campaign聯絡人。

有關如何監視工作流程的詳細資訊，請參閱 [本節](../../workflow/using/monitoring-workflow-execution.md).

## 開始進行中 {#start-in-progress}

如果工作流程未執行，其狀態為 **開始進行中**，這可能表示未啟動工作流程模組。

若要勾選此專案並在必要時啟動模組，請套用下列步驟：

1. 檢查 **[!UICONTROL wfserver]** 中的模組狀態 **[!UICONTROL Monitoring]** 索引標籤，可從Campaign Classic首頁存取(請參閱 [監控流程](../../production/using/monitoring-processes.md))。

   管理員使用者還可以檢查 **wfserver@`<instance>`** 模組會使用以下命令在您的主要應用程式伺服器上啟動。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   有關如何監視模組的詳細資訊，請參閱 [本節](../../production/using/usual-commands.md#monitoring-commands-).

1. 如果模組未執行，請聯絡Adobe客戶服務。 如果您有內部部署安裝，管理員必須使用下列命令將其重新啟動。

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >取代 **`<instance-name>`** 執行個體的名稱（生產、開發等）。 執行個體名稱會透過設定檔案識別：
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   有關如何重新啟動模組的詳細資訊，請參閱 [本節](../../production/using/usual-commands.md#module-launch-commands).

## 失敗的工作流程 {#failed-workflow}

如果工作流程失敗，請執行以下步驟：

1. 檢查工作流程日誌。 有關詳細資訊，請參閱 [監視工作流程的執行](../../workflow/using/monitoring-workflow-execution.md) 和 [顯示記錄](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) 區段。
1. 監視技術工作流程。 如需詳細資訊，請參閱 [本節](../../workflow/using/monitoring-technical-workflows.md).
1. 尋找個別工作流程活動上的失敗。
