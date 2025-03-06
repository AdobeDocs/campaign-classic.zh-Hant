---
product: campaign
title: 監視技術工作流程
description: 監視技術工作流程
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 5e77d196-5c71-438e-8dae-10c6a6e4f29c
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 5%

---

# 監視技術工作流程 {#monitoring-technical-workflows}



技術工作流程需要監控，並在失敗時採取行動。

監視不同Campaign處理序的其他方法會顯示在[此頁面](../../production/using/monitoring-guidelines.md)中。

## 執行個體監視儀表板 {#instance-monitoring-dashboard}

可以透過&#x200B;**[!UICONTROL Monitoring]**&#x200B;索引標籤存取執行個體監視儀表板。

![](assets/monitoring_technical_workflows1.png)

在「系統指示器和核心檔案」下，檢查指示器是否以紅色反白顯示。 如果是這種情況，並且有些是這種情況，您應該：

* 檢查必要的程式是否一律在執行中，
* 檢查流程是否都不太舊，
* 檢查不同處理程式的記錄檔是否不包含警示和週期性錯誤。

## 技術工作流程 {#technical-workflows}

技術工作流程可從&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**&#x200B;取得。

根據技術工作流程，請遵循以下詳細步驟以確保一切都如期運作。

若要進一步瞭解每個技術工作流程應該要執行的動作，請參閱本[區段](about-technical-workflows.md)。

針對&#x200B;**[!UICONTROL Database Cleanup workflow (‘cleanup’)]**：

1. 檢查&#x200B;**[!UICONTROL Database Cleanup]**&#x200B;工作流程是否每天都執行並順利完成。 如需詳細資訊，請參閱此[頁面](../../production/using/database-cleanup-workflow.md)。
1. 檢視日誌，驗證經過的時間在一段時間內相對穩定，不會干擾其他工作流程。

針對&#x200B;**[!UICONTROL Tracking workflow (‘tracking’)]**：

檢查「追蹤」工作流程是否依排程執行（預設為每小時執行一次），以及分錄是否未反白顯示週期性錯誤。 如需詳細資訊，請參閱本[區段](delivery.md)。

針對&#x200B;**[!UICONTROL Refresh for Deliverability (deliverabilityUpdate)]**：

1. 檢查&#x200B;**[!UICONTROL Refresh for Deliverability]**&#x200B;工作流程是否每天都執行並順利完成。
1. 在日誌中驗證規則是否定期更新。

針對&#x200B;**[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**：

1. 檢視&#x200B;**[!UICONTROL Campaign process]**&#x200B;資料夾下的所有工作流程。 如需關於此項目的詳細資訊，請參閱此[頁面](about-technical-workflows.md)。
1. 檢查工作流程是否以排程方式執行，以及分錄是否未反白顯示重複錯誤。

## 工作流程監督 {#workflow-supervision}

**[!UICONTROL Workflow supervisors]**&#x200B;群組應該包含需要通知失敗情況的操作者，以及可以及時採取動作的操作者。

![](assets/monitoring_technical_workflows3.png)

應產生警示，並在發生問題時傳送至正確的群組。

請確定每個操作員都有有效的電子郵件地址。

任何為了讓平台運作而執行的工作流程（例如每日資料匯入）都應宣告為「生產」（核取方塊），並以粗體顯示。

## 工作流程維護清單 {#workflow-maintenance-list}

所有自訂技術工作流程都應記錄在包含下列內容的工作表中：

* 工作流程的名稱和位置。
* 用途。
* 正在排程和相依性。
* 負責監控的運運算元。
* 發生錯誤時應採取哪些措施的說明。

![](assets/monitoring_technical_workflows4.png)

## 監控的規劃和自動化 {#planning-and-automation-of-monitoring}

計畫工作流程監視可改善其效率。 有些任務需要每天執行，而其他任務則可以每週或每月執行。

在按週期命名並按執行排程排序的資料夾中設定工作流程可改善監視效率。

監控自動化可減少資源負荷，並確保以適當的頻率排程工作。

您可以建立監控工作流程，以便在某些工作失敗或重要表格變得太大時傳送電子郵件。

您可以建立檢視，以便監視跨功能區域或系統範圍的所有工作流程。

您也可以使用Adobe Campaign工作或報告功能來隨需建置檔案，隨時保持最新狀態。
