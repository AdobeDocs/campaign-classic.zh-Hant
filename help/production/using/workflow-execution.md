---
product: campaign
title: 工作流程執行
description: 工作流程執行
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 3%

---

# 工作流程執行{#workflow-execution}



以下部分介紹與工作流執行相關的常見問題以及如何排除它們。

有關工作流的詳細資訊，請參閱以下各節：

* [關於工作流程](../../workflow/using/about-workflows.md)
* [啟動工作流程](../../workflow/using/starting-a-workflow.md)
* [工作流程生命週期](../../workflow/using/workflow-life-cycle.md)
* [使用工作流時的最佳做法](../../workflow/using/workflow-best-practices.md)

## 在市場活動中盡快開始 {#start-as-soon-as-possible-in-campaigns}

在某些情況下，從市場活動執行的工作流在按一下 **[!UICONTROL Start]** 按鈕 它不是啟動，而是進入「盡快啟動」狀態。

此問題可能有多種原因，請按照以下步驟解決：

1. 檢查 [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) 技術工作流狀態。 此工作流管理市場活動內的作業或工作流。 如果失敗，則將導致工作流不啟動/停止。 重新啟動它以繼續運行市場活動工作流。

   有關技術工作流監控的詳細資訊，請參閱 [此頁](../../workflow/using/monitoring-technical-workflows.md)。

   >[!NOTE]
   >
   >重新啟動工作流後，確保執行掛起的任務(按一下右鍵 **[!UICONTROL Scheduler]** 活動/ **[!UICONTROL Execute pending task(s) now]**)，以檢查是否在任何活動上再次失敗。

   如果工作流仍然失敗，請檢查審核日誌中是否有特定錯誤，並進行相應的故障排除，然後重新啟動工作流。

1. 檢查 **[!UICONTROL wfserver]** 模組狀態 **[!UICONTROL Monitoring]** 頁籤，可從Campaign Classic首頁訪問(請參閱 [監視進程](../../production/using/monitoring-processes.md))。 此進程負責運行所有工作流。

   管理員用戶還可以檢查 **wfserver@`<instance>`** 在主應用程式伺服器上使用以下命令啟動模組。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   如果模組未運行，請與Adobe客戶服務部聯繫。 如果您進行了內部安裝，管理員用戶必須使用下面的命令重新啟動服務。

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >替換 **`<instance-name>`** 實例名稱（生產、開發等）。 實例名稱通過配置檔案標識：
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   有關如何重新啟動模組的詳細資訊，請參閱 [此部分](../../production/using/usual-commands.md#module-launch-commands)。

1. 檢查 **運行的市場活動進程數** 實例上的值大於閾值。 存在由 [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) 選項，以確定實例上可以並行運行多少促銷流程。 達到此限制後，只要運行的工作流數量超過限制，工作流就會保持「盡快啟動」狀態。

   要解決此問題，請停止不需要的工作流並刪除失敗的交貨。 如果達到閾值，則允許運行新進程。

   要檢查實例運行的工作流數，建議使用預定義視圖，在 **[!UICONTROL Administration]** / **[!UICONTROL Audit]** 的子菜單。 如需詳細資訊，請參閱[本頁面](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)。

   >[!IMPORTANT]
   >
   >增加 **[!UICONTROL NmsOperation_LimitConcurrency]** 選項閾值可能會導致實例的效能問題。 無論如何，不要自行執行此操作，並聯繫您的Adobe Campaign聯繫人。

有關如何監視工作流的詳細資訊，請參閱 [此部分](../../workflow/using/monitoring-workflow-execution.md)。

## 正在啟動 {#start-in-progress}

如果工作流未執行且其狀態為 **正在啟動**，這可能表示未啟動工作流模組。

要檢查此項並在必要時啟動模組，請應用以下步驟：

1. 檢查 **[!UICONTROL wfserver]** 模組狀態 **[!UICONTROL Monitoring]** 頁籤，可從Campaign Classic首頁訪問(請參閱 [監視進程](../../production/using/monitoring-processes.md))。

   管理員用戶還可以檢查 **wfserver@`<instance>`** 在主應用程式伺服器上使用以下命令啟動模組。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   有關如何監視模組的詳細資訊，請參閱 [此部分](../../production/using/usual-commands.md#monitoring-commands-)。

1. 如果模組未運行，請與Adobe客戶服務部聯繫。 如果您有內部安裝，管理員必須使用下面的命令重新啟動它。

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >替換 **`<instance-name>`** 實例名稱（生產、開發等）。 實例名稱通過配置檔案標識：
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   有關如何重新啟動模組的詳細資訊，請參閱 [此部分](../../production/using/usual-commands.md#module-launch-commands)。

## 工作流失敗 {#failed-workflow}

如果工作流失敗，請執行以下步驟：

1. 檢查工作流日記帳。 有關詳細資訊，請參閱 [監視工作流執行](../../workflow/using/monitoring-workflow-execution.md) 和 [顯示日誌](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) 的下界。
1. 監視技術工作流程. 有關詳情，請參閱 [此部分](../../workflow/using/monitoring-technical-workflows.md)。
1. 查找單個工作流活動的失敗。
