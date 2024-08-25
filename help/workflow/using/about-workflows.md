---
product: campaign
title: 關於工作流程
description: 使用工作流程自動化程序、管理資料和客群、傳送訊息等
feature: Workflows, Data Management
exl-id: 51be6b90-2a7a-4757-9754-d16c540a87ff
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 37%

---

# 開始使用工作流程{#gs-workflows}



## 關於工作流程{#about-workflows}

Adobe Campaign 包括一個工作流程模組，可跨應用程式伺服器的不同模組策劃所有流程和任務。使用這個全方位的圖像式環境，您可以設計各式流程，包含細分、行銷活動執行、檔案處理、人力參與等。工作流程引擎將執行並追蹤這些流程。

例如，您可以使用工作流程從伺服器下載檔案、解壓縮，然後將其中的記錄匯入 Adobe Campaign 資料庫。

此外，工作流程也涉及到要進行通知的一或多個操作者，或者是可以選擇並核准流程的相關人員。如此一來就可以實行傳遞行動，將任務指派給一或多位操作者，指定目標且在傳遞前進行核准。

工作流程會在行銷活動管理流程的不同內容和階段中進行。

Adobe Campaign使用工作流程來：

* 執行目標定位行銷活動。 [了解更多](building-a-workflow.md#implementation-steps-)
* 建立行銷活動：對於每個行銷活動，**[!UICONTROL Workflow]**&#x200B;索引標籤可讓您建立目標及建立傳送。 [了解更多](building-a-workflow.md#campaign-workflows)
* 執行技術流程：清理、收集追蹤資訊或臨時計算。 [了解更多](building-a-workflow.md#technical-workflows)

工作流程可能同時代表流程定義（工作流程模型，代表應該發生的事情）和此流程的執行個體（工作流程執行個體，代表實際發生的事情）。

工作流程範本描述要執行的各種任務以及任務如何連結在一起。任務範本稱為活動並以圖示表示。它們透過轉變連結在一起。

![](assets/example1.png)

每個工作流程都包含：

* **[!UICONTROL Activities]**

  活動說明任務範本。 各種可用活動在圖表中以圖示表示。每種型別都有共同屬性和特定屬性。 例如，雖然所有活動都有名稱和標籤，但只有&#x200B;**[!UICONTROL Approval]**&#x200B;活動有指派。

  在工作流程圖表中，指定的活動可以產生多個任務，尤其是當有回圈或循環（定期）動作時。

  [本節](about-activities.md)中列出所有工作流程活動，包括使用案例和範例。

* **[!UICONTROL Transitions]**

  轉變可讓您連結活動並定義其順序。 轉變會將來源活動連結至目的地活動。 轉換有多種型別，視來源活動而定。 有些轉變還有其他引數，例如持續時間、條件或篩選器。

  未連結至目的地活動的轉變顯示為橘色，而箭頭標頭顯示為菱形。

  >[!NOTE]
  >
  >仍可執行包含未終止轉變的工作流程：將會產生警告訊息，工作流程在轉變時會暫停，但不會產生錯誤。 因此，可以在工作流程未完成的情況下啟動工作流程，並在執行時將其新增。

  如需如何建立工作流程的詳細資訊，請參閱[本節](building-a-workflow.md)。

* **[!UICONTROL Worktables]**

  工作表包含轉接所攜帶的所有資訊。 每個工作流程會使用多個工作表。只要不清除資料，這些表格中傳送的資料就可以加速，並在整個工作流程的生命週期中使用。 事實上，每次工作流程不活躍時，不需要的工作表都會被清除，並且可能在最大工作流程執行期間被清除，以避免伺服器過載。

  在[本節](how-to-use-workflow-data.md)中進一步瞭解工作流程資料和表格。

## 主要原則和最佳作法{#principles-workflows}

請參閱下列章節，以尋找使用工作流程自動化流程的指引和最佳實務：

* 在[此頁面](how-to-use-workflow-data.md)中進一步瞭解工作流程活動。
* 在[本節](building-a-workflow.md)中瞭解如何建立工作流程。
* 在[本節](../../platform/using/import-export-workflows.md)中探索如何使用工作流程匯入Campaign中的資料。
* [此頁面](workflow-best-practices.md)中詳細說明了工作流程最佳實務。
* 在[本節](starting-a-workflow.md)中尋找有關工作流程執行的指引。
* 瞭解如何監視[此頁面](monitoring-workflow-execution.md)的工作流程。
* 瞭解如何授予使用者存取權，以便在[此頁面](managing-rights.md)中使用工作流程。
