---
product: campaign
title: 監控技術工作流程
description: 監控技術工作流程
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 5e77d196-5c71-438e-8dae-10c6a6e4f29c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 8%

---

# 監控技術工作流程 {#monitoring-technical-workflows}

需要監控技術工作流程，並在工作流程失敗時採取動作。

監控不同促銷活動程式的其他方式顯示在[此頁面](../../production/using/monitoring-guidelines.md)中。

## 執行個體監控控制面板{#instance-monitoring-dashboard}

您可透過&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤存取執行個體監控控制面板。

![](assets/monitoring_technical_workflows1.png)

在「System Indicators（系統指標）」和核心檔案下，檢查是否沒有以紅色突出顯示任何指標。 如果情況確實如此，您應：

* 檢查必要的進程是否始終運行，
* 檢查所有流程是否都太舊，
* 檢查不同進程的日誌檔案中是否包含警告和重複錯誤。

## 技術工作流程 {#technical-workflows}

**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**&#x200B;提供技術工作流程。

視技術工作流程而定，請依照下列詳細步驟操作，以確保一切皆如預期般運作。

若要更清楚了解每個技術工作流程應執行的動作，請參閱此[區段](../../workflow/using/about-technical-workflows.md)。

對於&#x200B;**[!UICONTROL Database Cleanup workflow (‘cleanup’)]**:

1. 檢查&#x200B;**[!UICONTROL Database Cleanup]**&#x200B;工作流程是否每天成功執行並完成。 如需關於此項目的詳細資訊，請參閱此[頁面](../../workflow/using/delivery.md)。
1. 查看日誌，驗證經過的時間隨時間相對恆定，並且不會干擾其他工作流。
1. 如需詳細資訊，請查看此[page](../../production/using/database-cleanup-workflow.md)。

對於&#x200B;**[!UICONTROL Tracking workflow (‘tracking’)]**:

檢查「追蹤」工作流程是否如計畫（預設為每小時）執行，以及日記帳是否不會反覆標示經常發生的錯誤。 如需詳細資訊，請參閱本[區段](../../workflow/using/delivery.md)。

對於&#x200B;**[!UICONTROL Deliverability update (‘deliverabilityUpdate’)]**:

1. 檢查&#x200B;**[!UICONTROL Deliverability update]**&#x200B;工作流程是否每天成功執行並完成。 如需關於此項目的詳細資訊，請參閱此[頁面](../../workflow/using/delivery.md)。
1. 在日誌中驗證規則是否定期更新。

對於&#x200B;**[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**:

1. 查看&#x200B;**[!UICONTROL Campaign process]**&#x200B;資料夾下方的所有工作流。 如需關於此項目的詳細資訊，請參閱此[頁面](../../workflow/using/about-technical-workflows.md)。
1. 檢查工作流程是否如計畫運行，以及日誌是否不會突出顯示經常性錯誤。

## 工作流監督{#workflow-supervision}

**[!UICONTROL Workflow supervisors]**&#x200B;組應包含需要不斷通知故障以及哪些人可以及時採取行動的運算子。

![](assets/monitoring_technical_workflows3.png)

如果出現問題，應生成警報並將其發送到正確的組。

請確定每個運算子都有有效的電子郵件地址。

為了讓平台持續運作而應執行的任何工作流程（例如每日資料匯入）都應宣告為「生產」（核取方塊），並以粗體顯示。

## 工作流維護清單{#workflow-maintenance-list}

所有自訂技術工作流程都應記錄在包含下列項目的工作表中：

* 工作流程的名稱和位置。
* 目的。
* 排程和相依性。
* 負責監控的操作員。
* 錯誤時該做什麼的說明。

![](assets/monitoring_technical_workflows4.png)

## {#planning-and-automation-of-monitoring}監控的規劃和自動化

規劃工作流監視提高了其效率。 某些任務需要每天執行，而其他任務可以每週或每月執行。

在以循環命名、並依執行排程排序的資料夾中設定工作流程，可提高監控效率。

監控的自動化降低了資源開銷並確保任務以適當的頻率進行調度。

您可以構建監控工作流，以便在某些任務失敗或關鍵表太大時發送電子郵件。

您可以建立檢視，以便監控功能區域或系統範圍內的所有工作流程。

您也可以使用Adobe Campaign工作或報表功能，依需要建立檔案，而且隨時都是最新的。
