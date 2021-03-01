---
solution: Campaign Classic
product: campaign
title: 關於工作流程
description: 使用工作流程自動化程序，管理資料和對象、傳送訊息等。
audience: workflow
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: bb7e3ce726e2c589c033686cf3ab2960de140d91
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 20%

---


# 開始使用工作流程{#gs-workflows}

## 關於工作流程{#about-workflows}

Adobe Campaign包含工作流模組，可讓您跨應用程式伺服器的不同模組協調各種流程和工作。 使用這個全方位的圖像式環境，您可以設計各式流程，包含細分、行銷活動執行、檔案處理、人力參與等。工作流程引擎將執行並追蹤這些流程。

例如，您可以使用工作流程從伺服器下載檔案、解壓縮，然後將其中的記錄匯入 Adobe Campaign 資料庫。

此外，工作流程也涉及到要進行通知的一或多個操作者，或者是可以選擇並核准流程的相關人員。如此一來就可以實行傳遞行動，將任務指派給一或多位操作者，指定目標且在傳遞前進行核准。

工作流程會在促銷活動管理程式的不同上下文和階段中進行。

Adobe Campaign使用工作流程：

* 進行定位促銷活動。 [進一步了解](../../workflow/using/building-a-workflow.md#implementation-steps-)
* 建立促銷活動：對於每個促銷活動，**[!UICONTROL Workflow]**&#x200B;標籤可讓您建立目標並建立傳送。 [進一步了解](../../workflow/using/building-a-workflow.md#campaign-workflows)
* 執行技術流程：清除、收集追蹤資訊或臨時計算。 [進一步了解](../../workflow/using/building-a-workflow.md#technical-workflows)

工作流可以表示流程定義（工作流模型，它表示應發生的事件）和此流程的實例（工作流實例，它表示實際發生的事件）。

工作流程範本說明要執行的各種工作，以及它們如何連結在一起。 任務模板稱為活動，由表徵圖表示。 它們通過轉換而連接在一起。

![](assets/example1.png)

每個工作流程都包含：

* **[!UICONTROL Activities]**

   活動描述任務模板。 圖中用表徵圖表示各種可用活動。 每種類型都有通用屬性和特定屬性。 例如，雖然所有活動都有名稱和標籤，但只有&#x200B;**[!UICONTROL Approval]**&#x200B;活動有分配。

   在工作流程圖中，特定活動可以產生多個任務，特別是當存在循環或循環（週期）動作時。

   所有工作流活動列在[本節](../../workflow/using/about-activities.md)中，包括使用案例和示例。

* **[!UICONTROL Transitions]**

   轉場效果可讓您連結活動並定義其順序。 轉換會將源活動連結到目標活動。 有幾種轉場方式取決於源活動。 有些轉場會有其他參數，例如持續時間、條件或篩選。

   未連結到目標活動的過渡為橙色，箭頭頭顯示為菱形。

   >[!NOTE]
   >
   >仍可執行包含未終止轉場的工作流程：將會產生警告訊息，工作流程在轉場時會暫停，但不會產生錯誤。 因此，您可以在不完成工作流程的情況下開始工作，並隨時加入工作流程。

   有關如何構建工作流的詳細資訊，請參閱[本節](../../workflow/using/building-a-workflow.md)。

* **[!UICONTROL Worktables]**

   工作台包含轉移所攜帶的所有資訊。 每個工作流都使用多個工作表。 在這些表中傳送的資料可以在整個工作流生命週期中加速並使用，只要不清除。 事實上，在每次鈍化工作流時，都會清除不需要的表，而且可能在執行最大的工作流時，會清除這些表，以避免伺服器過載。

   進一步瞭解[本節](../../workflow/using/how-to-use-workflow-data.md)中的工作流程資料和表格。

## 主要原則和最佳實務{#principles-workflows}

請參閱這些章節，以尋找使用工作流程自動化流程的指引和最佳實務：

* 進一步瞭解[本頁](../../workflow/using/how-to-use-workflow-data.md)中的工作流程活動。
* 瞭解如何在[本節](../../workflow/using/building-a-workflow.md)中建立工作流程。
* 瞭解如何使用工作流程，在[本節](../../platform/using/import-export-workflows.md)的Campaign中匯入資料。
* 工作流程最佳實踐詳見[本頁](../../workflow/using/workflow-best-practices.md)。
* 在[本節](../../workflow/using/starting-a-workflow.md)中尋找有關工作流執行的指導。
* 瞭解如何在[本頁](../../workflow/using/monitoring-workflow-execution.md)中監控工作流程。
* 瞭解如何授與使用者使用[本頁](../../workflow/using/managing-rights.md)工作流程的存取權。
