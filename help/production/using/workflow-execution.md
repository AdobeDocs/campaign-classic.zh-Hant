---
title: 工作流程執行
seo-title: 工作流程執行
description: 工作流程執行
seo-description: null
page-status-flag: never-activated
uuid: 115256f6-bdf2-4594-885c-e90d02a25b80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 7d8828c5-5776-49ca-b4f7-a4a6aaaa9db1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---


# 工作流程執行{#workflow-execution}

以下章節提供與工作流程執行相關的常見問題，以及如何疑難排解的資訊。

如需工作流程的詳細資訊，請參閱下列章節：

* [關於工作流程](../../workflow/using/about-workflows.md)
* [啟動工作流](../../workflow/using/starting-a-workflow.md)
* [工作流程生命週期](../../workflow/using/workflow-life-cycle.md)
* [使用工作流程時的最佳實務](../../workflow/using/workflow-best-practices.md)

## 在促銷活動中盡快開始 {#start-as-soon-as-possible-in-campaigns}

在某些情況下，從促銷活動執行的工作流程不會在按一下按鈕時 **[!UICONTROL Start]** 啟動。 它不會開始，而是進入「盡快開始」狀態。

此問題可能有數個原因，請依照下列步驟加以解決：

1. 檢查技術 [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) 工作流程狀態。 此工作流程管理促銷活動內的工作或工作流程。 如果失敗，這會導致工作流程無法啟動／停止。 重新啟動它以繼續執行促銷活動工作流程。

   有關技術工作流程監控的詳細資訊，請參 [閱本頁](../../workflow/using/monitoring-technical-workflows.md)。

   >[注意]
   >
   >重新啟動工作流程後，請確定您執行待審任務(按一下右鍵活動 **[!UICONTROL Scheduler]** / **[!UICONTROL Execute pending task(s) now]**)，以便檢查它是否在任何活動上再次失敗。

   如果工作流仍然失敗，請檢查審計日誌中是否有特定錯誤，並據以進行故障排除，然後再次重新啟動工作流。

1. 在標籤 **[!UICONTROL wfserver]** 中檢查模組狀態， **[!UICONTROL Monitoring]** 可從Campaign Classic首頁存取(請參閱 [監控程式](../../production/using/monitoring-processes.md))。 此程式負責執行所有工作流程。

   管理員用戶還可以使用以下 **命令檢查wfserver@`<instance>`**module是否在主應用程式伺服器上啟動。

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
   >以 **`<instancename>`** 例項名稱取代（生產、開發等）。 實例名稱通過配置檔案標識：
   >`[path of application]nl6/conf/config-<instancename>.xml`

   有關如何重新啟動模組的詳細資訊，請參 [閱本節](../../production/using/usual-commands.md#module-launch-commands)。

1. 檢查執行 **個體上執行的促銷活動** ，進程數是否超過臨界值。 選項會定義一個限制， [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) 限制可同時在例項上執行多少促銷活動程式。 當達到此限制時，只要執行的工作流程數量超過限制，工作流程就會維持在「盡快開始」狀態。

   若要解決此問題，請停止不想要的工作流程並刪除失敗的傳送。 如果達到閾值，則允許運行新進程。

   若要檢查執行個體的工作流程數目，建議使用預先定義的檢視，預設可在 **[!UICONTROL Administration]** /資料夾 **[!UICONTROL Audit]** 中存取。 For more information, refer to [this page](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[警告]
   >
   >增加選 **[!UICONTROL NmsOperation_LimitConcurrency]** 項臨界值可能會導致執行個體的效能問題。 無論如何，請勿自行執行此動作，並聯絡您的Adobe Campaign聯絡人。

如需如何監控工作流程的詳細資訊，請參閱 [本節](../../workflow/using/monitoring-workflow-execution.md)。

## 開始進行中 {#start-in-progress}

如果工作流未執行且其狀態為「 **開始」**，這可能表示工作流模組未啟動。

要檢查此問題並在必要時啟動模組，請應用以下步驟：

1. 在標籤 **[!UICONTROL wfserver]** 中檢查模組狀態， **[!UICONTROL Monitoring]** 可從Campaign Classic首頁存取(請參閱 [監控程式](../../production/using/monitoring-processes.md))。

   管理員用戶還可以使用以下 **命令檢查wfserver@`<instance>`**module是否在主應用程式伺服器上啟動。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   有關如何監視模組的詳細資訊，請參 [閱本節](../../production/using/usual-commands.md#monitoring-commands-)。

1. 如果模組未執行，請聯絡Adobe客戶服務。 如果您有內部部署安裝，管理員必須使用以下命令重新啟動安裝。

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >以 **`<instancename>`** 例項名稱取代（生產、開發等）。 實例名稱通過配置檔案標識：
   >`[path of application]nl6/conf/config-<instancename>.xml`

   有關如何重新啟動模組的詳細資訊，請參 [閱本節](../../production/using/usual-commands.md#module-launch-commands)。

## 工作流程失敗 {#failed-workflow}

如果工作流失敗，請執行以下步驟：

1. 檢查工作流日記帳。 有關詳細資訊，請參閱「監 [控工作流執行](../../workflow/using/monitoring-workflow-execution.md) 」 [和「顯示日誌](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) 」部分。
1. 監控技術工作流程。 For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. 尋找個別工作流程活動的失敗之處。
