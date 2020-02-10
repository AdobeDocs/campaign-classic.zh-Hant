---
title: 監控技術工作流程
seo-title: 監控技術工作流程
description: 監控技術工作流程
seo-description: null
page-status-flag: never-activated
uuid: 4d215ff4-a61d-4294-8f15-17c612022577
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 6a71f5ee-c8e0-4ac4-acae-6dffbf799d0c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d60f47f03949177b97509166a8d9e640849e5fd7

---


# 監控技術工作流程 {#monitoring-technical-workflows}

技術工作流程需要受到監控，而且必須在失敗時採取行動。

本頁提供其他監控不同促銷活動程式的 [方式](https://helpx.adobe.com/campaign/kb/acc-maintenance.html)。

## 例項監控控制面板 {#instance-monitoring-dashboard}

例項監控儀表板可透過宇宙存 **[!UICONTROL Monitoring]** 取。

![](assets/monitoring_technical_workflows1.png)

在「System Indicators（系統指示器）」和核心檔案下，檢查沒有以紅色突出顯示的指示器。 如果情況確實如此，而且有些情況確實如此，您應：

* 檢查所需的流程是否始終在運行，
* 檢查流程是否都過舊，
* 檢查不同進程的日誌檔案中是否不包含警告和週期性錯誤。

## 技術工作流程 {#technical-workflows}

技術工作流程可從 **[!UICONTROL Administration]** > **[!UICONTROL Production]** >取得 **[!UICONTROL Technical workflows]**。

視技術工作流程而定，請遵循下列詳細步驟，以確保一切正常運作。

若要進一步瞭解每個技術工作流程的用途，請參閱本 [節](../../workflow/using/about-technical-workflows.md)。

針對 **[!UICONTROL Database Cleanup workflow (‘cleanup’)]**:

1. 檢查工作流程 **[!UICONTROL Database Cleanup]** 是否每天都能順利執行並完成。 For more on this, refer to this [page](../../workflow/using/delivery.md).
1. 查看日誌，確認經過的時間隨時間的變化是相對恆定的，並且不會干擾其他工作流。
1. 如需詳細資訊，請勾選此 [頁面](../../production/using/database-cleanup-workflow.md)。

針對 **[!UICONTROL Tracking workflow (‘tracking’)]**:

檢查「追蹤」工作流程是否如計畫般執行（預設為每小時），以及日記帳是否不會反覆標示經常發生的錯誤。 For more on this, refer to this [section](../../workflow/using/delivery.md).

針對 **[!UICONTROL Deliverability update (‘deliverabilityUpdate’)]**:

1. 檢查工作流程 **[!UICONTROL Deliverability update]** 是否每天都能順利執行並完成。 For more on this, refer to this [page](../../workflow/using/delivery.md).
1. 在日誌中確認規則正在定期更新。

針對 **[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**:

1. 查看資料夾下方的所有工作 **[!UICONTROL Campaign process]** 流程。 For more on this, refer to this [page](../../workflow/using/campaign.md).
1. 檢查工作流程是否如計畫般執行，以及日記帳是否不會反覆顯示錯誤。

## 工作流程監督 {#workflow-supervision}

群 **[!UICONTROL Workflow supervisors]** 組中應包含需要隨時得知失敗情況的運算子，以及哪些運算子可以及時採取行動。

![](assets/monitoring_technical_workflows3.png)

如果出現問題，應生成警報並將其發送到正確的組。

請確定每個營運商都有有效的電子郵件地址。

為了讓平台持續運作而應執行的任何工作流程（例如每日資料匯入）都應宣告為「生產」（核取方塊），並以粗體顯示。

## 工作流程維護清單 {#workflow-maintenance-list}

所有自訂技術工作流程都應記錄在包含下列項目的工作表中：

* 工作流的名稱和位置。
* 目的。
* 排程與相依性。
* 負責監控的營運商。
* 說明在發生錯誤時要執行什麼動作。

![](assets/monitoring_technical_workflows4.png)

## 監控的規劃與自動化 {#planning-and-automation-of-monitoring}

規劃工作流程監控可提高其效率。 有些工作需要每天進行，而其他工作則可以每週或每月進行。

在以重複方式命名並依執行排序的檔案夾中設定工作流程，可提高監控的效率。

自動監控可降低資源開銷，並確保以適當的頻率排程工作。

您可以構建監控工作流，在某些任務失敗或關鍵表過大時發送電子郵件。

您可以建立檢視，以便監控整個功能區域或整個系統的所有工作流程。

您也可以使用Adobe Campaign工作或報表功能，根據需求建立檔案，檔案隨時都是最新的。
