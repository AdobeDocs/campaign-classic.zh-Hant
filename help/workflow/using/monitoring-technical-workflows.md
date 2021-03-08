---
solution: Campaign Classic
product: campaign
title: 監控技術工作流程
description: 監控技術工作流程
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 8%

---


# 監控技術工作流程 {#monitoring-technical-workflows}

技術工作流程需要受到監控，而且必須在失敗時採取行動。

監控不同促銷活動程式的其他方式，請參閱本頁[。](../../production/using/monitoring-guidelines.md)

## 實例監控控制面板{#instance-monitoring-dashboard}

您可以透過&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤存取例項監控控制面板。

![](assets/monitoring_technical_workflows1.png)

在「System Indicators（系統指示器）」和核心檔案下，檢查沒有以紅色突出顯示的指示器。 如果情況確實如此，而且有些情況確實如此，您應：

* 檢查所需的流程是否始終在運行，
* 檢查流程是否都過舊，
* 檢查不同進程的日誌檔案中是否不包含警告和週期性錯誤。

## 技術工作流程 {#technical-workflows}

技術工作流程可從&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**&#x200B;取得。

視技術工作流程而定，請遵循下列詳細步驟，以確保一切正常運作。

要更好地瞭解每個技術工作流應執行的操作，請參閱[部分](../../workflow/using/about-technical-workflows.md)。

對於&#x200B;**[!UICONTROL Database Cleanup workflow (‘cleanup’)]**:

1. 檢查&#x200B;**[!UICONTROL Database Cleanup]**&#x200B;工作流是否每天運行並成功完成。 如需關於此項目的詳細資訊，請參閱此[頁面](../../workflow/using/delivery.md)。
1. 查看日誌，確認經過的時間隨時間的變化是相對恆定的，並且不會干擾其他工作流。
1. 如需詳細資訊，請查看此[頁面](../../production/using/database-cleanup-workflow.md)。

對於&#x200B;**[!UICONTROL Tracking workflow (‘tracking’)]**:

檢查「追蹤」工作流程是否如計畫般執行（預設為每小時），以及日記帳是否不會反覆標示經常發生的錯誤。 如需詳細資訊，請參閱本[區段](../../workflow/using/delivery.md)。

對於&#x200B;**[!UICONTROL Deliverability update (‘deliverabilityUpdate’)]**:

1. 檢查&#x200B;**[!UICONTROL Deliverability update]**&#x200B;工作流是否每天運行並成功完成。 如需關於此項目的詳細資訊，請參閱此[頁面](../../workflow/using/delivery.md)。
1. 在日誌中確認規則正在定期更新。

對於&#x200B;**[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**:

1. 查看位於&#x200B;**[!UICONTROL Campaign process]**&#x200B;資料夾下的所有工作流。 如需關於此項目的詳細資訊，請參閱此[頁面](../../workflow/using/about-technical-workflows.md)。
1. 檢查工作流程是否如計畫般執行，以及日記帳是否不會反覆顯示錯誤。

## 工作流程監督{#workflow-supervision}

**[!UICONTROL Workflow supervisors]**&#x200B;群組應包含需要隨時得知失敗情況的運算子，以及哪些運算子可以及時採取行動。

![](assets/monitoring_technical_workflows3.png)

如果出現問題，應生成警報並將其發送到正確的組。

請確定每個營運商都有有效的電子郵件地址。

為了讓平台持續運作而應執行的任何工作流程（例如每日資料匯入）都應宣告為「生產」（核取方塊），並以粗體顯示。

## 工作流維護清單{#workflow-maintenance-list}

所有自訂技術工作流程都應記錄在包含下列項目的工作表中：

* 工作流的名稱和位置。
* 目的。
* 排程與相依性。
* 負責監控的營運商。
* 說明在發生錯誤時要執行什麼動作。

![](assets/monitoring_technical_workflows4.png)

## 規劃和自動監控{#planning-and-automation-of-monitoring}

規劃工作流程監控可提高其效率。 有些工作需要每天進行，而其他工作則可以每週或每月進行。

在以重複方式命名並依執行排序的檔案夾中設定工作流程，可提高監控的效率。

自動監控可降低資源開銷，並確保以適當的頻率排程工作。

您可以構建監控工作流，在某些任務失敗或關鍵表過大時發送電子郵件。

您可以建立檢視，以便監控整個功能區域或整個系統的所有工作流程。

您也可以使用Adobe Campaign的工作或報告功能來建立隨選檔案，檔案隨時都是最新的。
