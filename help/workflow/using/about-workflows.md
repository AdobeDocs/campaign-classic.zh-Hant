---
product: campaign
title: 關於工作流程
description: 使用工作流程自動化程序、管理資料和對象、傳送訊息等。
feature: Workflows, Data Management
exl-id: 51be6b90-2a7a-4757-9754-d16c540a87ff
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 開始使用工作流程{#gs-workflows}

![](../../assets/common.svg)

## 關於工作流程{#about-workflows}

Adobe Campaign 包括一個工作流程模組，可跨應用程式伺服器的不同模組策劃所有流程和任務。使用這個全方位的圖像式環境，您可以設計各式流程，包含細分、行銷活動執行、檔案處理、人力參與等。工作流程引擎將執行並追蹤這些流程。

例如，您可以使用工作流程從伺服器下載檔案、解壓縮，然後將其中的記錄匯入 Adobe Campaign 資料庫。

此外，工作流程也涉及到要進行通知的一或多個操作者，或者是可以選擇並核准流程的相關人員。如此一來就可以實行傳遞行動，將任務指派給一或多位操作者，指定目標且在傳遞前進行核准。

工作流程會在行銷活動管理流程的不同內容和階段中進行。

Adobe Campaign使用工作流：

* 開展針對性活動。 [了解更多](building-a-workflow.md#implementation-steps-)
* 構建市場活動：每次活動， **[!UICONTROL Workflow]** 頁籤，您可以生成目標並建立交貨。 [了解更多](building-a-workflow.md#campaign-workflows)
* 執行技術流程：清理、收集跟蹤資訊或臨時計算。 [了解更多](building-a-workflow.md#technical-workflows)

工作流可以同時表示流程定義（工作流模型，它表示應發生的事件）和此流程實例（工作流實例，它表示實際發生的事件）。

工作流模板描述了要執行的各種任務以及它們如何連結在一起。 任務模板稱為活動，用表徵圖表示。 它們通過轉變而連接在一起。

![](assets/example1.png)

每個工作流都包含：

* **[!UICONTROL Activities]**

   活動描述任務模板。 圖表中顯示了各種可用活動。 每種類型都具有公用屬性和特定屬性。 例如，儘管所有活動都有名稱和標籤，但僅 **[!UICONTROL Approval]** 活動具有分配。

   在工作流圖中，給定活動可以生成多個任務，特別是當存在循環或循環（定期）操作時。

   所有工作流活動都列在 [此部分](about-activities.md)包括用例和示例。

* **[!UICONTROL Transitions]**

   轉換使您能夠連結活動並定義其順序。 轉換將源活動連結到目標活動。 存在多種類型的轉換，取決於源活動。 某些過渡具有諸如持續時間、條件或過濾器等附加參數。

   未連結到目標活動的過渡為橙色，箭頭顯示為菱形。

   >[!NOTE]
   >
   >仍然可以執行包含未終止的轉換的工作流：將生成警告消息，工作流到達轉換後將暫停，但不會生成錯誤。 因此，可以在不完成工作流的情況下啟動工作流，並在您繼續工作時添加該工作流。

   有關如何構建工作流的詳細資訊，請參閱 [此部分](building-a-workflow.md)。

* **[!UICONTROL Worktables]**

   工作台包含該轉換所攜帶的所有資訊。 每個工作流都使用多個工作表。 只要不清除這些表中傳輸的資料，就可以在工作流的整個生命週期中加速和使用它。 實際上，每次工作流被鈍化時，都會清除不需要的表，而且可能在執行最大的工作流時會清除這些表，以避免使伺服器超負荷。

   瞭解有關中的工作流資料和表的詳細資訊 [此部分](how-to-use-workflow-data.md)。

## 關鍵原則和最佳做法{#principles-workflows}

請參閱以下部分，以查找使用工作流自動化流程的指導和最佳做法：

* 瞭解有關中工作流活動的詳細資訊 [此頁](how-to-use-workflow-data.md)。
* 瞭解如何在 [此部分](building-a-workflow.md)。
* 瞭解如何使用工作流在市場活動中導入資料 [此部分](../../platform/using/import-export-workflows.md)。
* 工作流最佳實踐詳見 [此頁](workflow-best-practices.md)。
* 查找有關在 [此部分](starting-a-workflow.md)。
* 瞭解如何在中監視工作流 [此頁](monitoring-workflow-execution.md)。
* 瞭解如何授予用戶使用工作流的訪問權限 [此頁](managing-rights.md)。
