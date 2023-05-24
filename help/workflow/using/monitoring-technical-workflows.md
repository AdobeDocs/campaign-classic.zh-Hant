---
product: campaign
title: 監視技術工作流程
description: 監視技術工作流程
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 5e77d196-5c71-438e-8dae-10c6a6e4f29c
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 6%

---

# 監視技術工作流程 {#monitoring-technical-workflows}



技術工作流程需要監控，並在失敗時採取行動。

監視不同Campaign流程的其他方法在中介紹 [此頁面](../../production/using/monitoring-guidelines.md).

## 執行個體監視儀表板 {#instance-monitoring-dashboard}

執行個體監控控制面板的存取方式為 **[!UICONTROL Monitoring]** 標籤。

![](assets/monitoring_technical_workflows1.png)

在「系統指示器和核心檔案」下，檢查指示器是否未以紅色反白顯示。 如果是這種情況，並且有些是這種情況，您應該：

* 檢查必要的程式是否一律在執行中，
* 檢查流程是否都不太舊，
* 檢查不同處理序的記錄檔是否不包含警示和重複錯誤。

## 技術工作流程 {#technical-workflows}

技術工作流程可從以下網址取得： **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

根據技術工作流程，請遵循以下詳細步驟以確保一切都按預期運作。

若要進一步瞭解每個技術工作流程的用途，請參閱此 [區段](about-technical-workflows.md).

對象 **[!UICONTROL Database Cleanup workflow (‘cleanup’)]**：

1. 檢查 **[!UICONTROL Database Cleanup]** 工作流程每天都會順利執行並完成。 如需關於此項目的詳細資訊，請參閱此[頁面](../../production/using/database-cleanup-workflow.md)..
1. 檢視日誌以確認經過的時間在一段時間內相對穩定，不會干擾其他工作流程。

對象 **[!UICONTROL Tracking workflow (‘tracking’)]**：

檢查「追蹤」工作流程是否以排程方式執行（預設為每小時執行一次），以及分錄是否未反白顯示重複錯誤。 如需詳細資訊，請參閱本[區段](delivery.md)。

對象 **[!UICONTROL Refresh for Deliverability (deliverabilityUpdate)]**：

1. 檢查 **[!UICONTROL Refresh for Deliverability]** 工作流程每天都會順利執行並完成。
1. 在日誌中驗證規則是否定期更新。

對象 **[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**：

1. 檢視位於「 」下方的所有工作流程 **[!UICONTROL Campaign process]** 資料夾。 如需關於此項目的詳細資訊，請參閱此[頁面](about-technical-workflows.md)。
1. 檢查工作流程是否按排程執行，以及分錄是否未反白顯示重複錯誤。

## 工作流程監督 {#workflow-supervision}

此 **[!UICONTROL Workflow supervisors]** 群組應包含需要隨時通知失敗情況的操作者，以及可以及時採取行動的操作者。

![](assets/monitoring_technical_workflows3.png)

應產生警示，並在發生問題時傳送至正確的群組。

請確定每個運運算元都有有效的電子郵件地址。

任何為了讓平台運作而執行的工作流程（例如每日資料匯入）都應宣告為「生產」（核取方塊），並以粗體顯示。

## 工作流程維護清單 {#workflow-maintenance-list}

所有自訂技術工作流程都應記錄在包含下列內容的工作表中：

* 工作流程的名稱和位置。
* 目的。
* 排程和相依性。
* 負責監控的操作員。
* 發生錯誤時的操作說明。

![](assets/monitoring_technical_workflows4.png)

## 規劃及自動化監控 {#planning-and-automation-of-monitoring}

計畫工作流程監控可提升效率。 有些任務需要每天執行，而其他任務則可以每週或每月執行。

在按週期命名並按執行排程排序的資料夾中設定工作流程，可提高監控效率。

監控自動化可減少資源負荷，並確保以適當的頻率排程工作。

您可以建立監控工作流程，以便在某些任務失敗或重要表格變得太大時傳送電子郵件。

您可以建立檢視，以便監視跨功能區域或系統範圍的所有工作流程。

您也可以使用Adobe Campaign工作或報表功能來隨需建置檔案，隨時保持在最新狀態。
