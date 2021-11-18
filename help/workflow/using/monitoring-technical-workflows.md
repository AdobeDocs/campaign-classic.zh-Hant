---
product: campaign
title: 監控技術工作流程
description: 監控技術工作流程
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 5e77d196-5c71-438e-8dae-10c6a6e4f29c
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 8%

---

# 監控技術工作流程 {#monitoring-technical-workflows}

![](../../assets/common.svg)

需要監控技術工作流程，並在工作流程失敗時採取動作。

監控不同促銷活動程式的其他方式，請參閱 [本頁](../../production/using/monitoring-guidelines.md).

## 執行個體監控控制面板 {#instance-monitoring-dashboard}

例項監控控制面板可透過 **[!UICONTROL Monitoring]** 標籤。

![](assets/monitoring_technical_workflows1.png)

在「System Indicators（系統指標）」和核心檔案下，檢查是否沒有以紅色突出顯示任何指標。 如果情況確實如此，您應：

* 檢查必要的進程是否始終運行，
* 檢查所有流程是否都太舊，
* 檢查不同進程的日誌檔案中是否包含警告和重複錯誤。

## 技術工作流程 {#technical-workflows}

技術工作流程可從以下網址取得： **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

視技術工作流程而定，請依照下列詳細步驟操作，以確保一切皆如預期般運作。

若要深入了解每個技術工作流程應執行的動作，請參閱此 [節](about-technical-workflows.md).

針對 **[!UICONTROL Database Cleanup workflow (‘cleanup’)]**:

1. 檢查 **[!UICONTROL Database Cleanup]** 工作流程每天都成功執行並完成。 如需關於此項目的詳細資訊，請參閱此[頁面](delivery.md)。
1. 查看日誌，驗證經過的時間隨時間相對恆定，並且不會干擾其他工作流。
1. 如需詳細資訊，請查看此 [頁面](../../production/using/database-cleanup-workflow.md).

針對 **[!UICONTROL Tracking workflow (‘tracking’)]**:

檢查「追蹤」工作流程是否如計畫（預設為每小時）執行，以及日記帳是否不會反覆標示經常發生的錯誤。 如需詳細資訊，請參閱本[區段](delivery.md)。

針對 **[!UICONTROL Deliverability update (‘deliverabilityUpdate’)]**:

1. 檢查 **[!UICONTROL Deliverability update]** 工作流程每天都成功執行並完成。 如需關於此項目的詳細資訊，請參閱此[頁面](delivery.md)。
1. 在日誌中驗證規則是否定期更新。

針對 **[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**:

1. 查看位於 **[!UICONTROL Campaign process]** 檔案夾。 如需關於此項目的詳細資訊，請參閱此[頁面](about-technical-workflows.md)。
1. 檢查工作流程是否如計畫運行，以及日誌是否不會突出顯示經常性錯誤。

## 工作流程監控 {#workflow-supervision}

此 **[!UICONTROL Workflow supervisors]** 群組應包含需要隨時通知失敗的運算子，以及可及時採取動作的運算子。

![](assets/monitoring_technical_workflows3.png)

如果出現問題，應生成警報並將其發送到正確的組。

請確定每個運算子都有有效的電子郵件地址。

為了讓平台持續運作而應執行的任何工作流程（例如每日資料匯入）都應宣告為「生產」（核取方塊），並以粗體顯示。

## 工作流程維護清單 {#workflow-maintenance-list}

所有自訂技術工作流程都應記錄在包含下列項目的工作表中：

* 工作流程的名稱和位置。
* 目的。
* 排程和相依性。
* 負責監控的操作員。
* 錯誤時該做什麼的說明。

![](assets/monitoring_technical_workflows4.png)

## 監控的規劃和自動化 {#planning-and-automation-of-monitoring}

規劃工作流監視提高了其效率。 某些任務需要每天執行，而其他任務可以每週或每月執行。

在以循環命名、並依執行排程排序的資料夾中設定工作流程，可提高監控效率。

監控的自動化降低了資源開銷並確保任務以適當的頻率進行調度。

您可以建立監控工作流程，以在某些任務失敗或關鍵表過大時傳送電子郵件。

您可以建立檢視，以便監控功能區域或系統範圍內的所有工作流程。

您也可以使用Adobe Campaign工作或報表功能，依需要建立檔案，而且隨時都是最新的。
