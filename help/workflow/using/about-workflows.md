---
product: campaign
title: 關於工作流程
description: 使用工作流程自動化程序，管理資料和對象、傳送訊息等。
audience: workflow
content-type: reference
topic-tags: introduction
exl-id: 51be6b90-2a7a-4757-9754-d16c540a87ff
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 26%

---

# 開始使用工作流程{#gs-workflows}

![](../../assets/common.svg)

## 關於工作流程{#about-workflows}

Adobe Campaign 包括一個工作流程模組，可跨應用程式伺服器的不同模組策劃所有流程和任務。使用這個全方位的圖像式環境，您可以設計各式流程，包含細分、行銷活動執行、檔案處理、人力參與等。工作流程引擎將執行並追蹤這些流程。

例如，您可以使用工作流程從伺服器下載檔案、解壓縮，然後將其中的記錄匯入 Adobe Campaign 資料庫。

此外，工作流程也涉及到要進行通知的一或多個操作者，或者是可以選擇並核准流程的相關人員。如此一來就可以實行傳遞行動，將任務指派給一或多位操作者，指定目標且在傳遞前進行核准。

工作流程會在行銷活動管理流程的不同內容和階段中進行。

Adobe Campaign使用工作流程：

* 執行定位促銷活動。 [深入瞭解](building-a-workflow.md#implementation-steps-)
* 建立行銷活動：對於每個促銷活動， **[!UICONTROL Workflow]**&#x200B;標籤可讓您建立目標並建立傳送。 [深入瞭解](building-a-workflow.md#campaign-workflows)
* 執行技術流程：清除、收集追蹤資訊或臨時計算。 [深入瞭解](building-a-workflow.md#technical-workflows)

工作流程可以指流程定義（工作流模型，它表示應發生的事件）和此流程的實例（工作流實例，表示實際發生的事件）。

工作流程範本說明要執行的各種工作，以及如何將這些工作連結在一起。 任務模板稱為活動，由表徵圖表示。 它們通過轉變而連結在一起。

![](assets/example1.png)

每個工作流程都包含：

* **[!UICONTROL Activities]**

   活動描述任務模板。 可用的各種活動在圖表上以表徵圖表示。 每種類型都有共同屬性和特定屬性。 例如，雖然所有活動都有名稱和標籤，但只有&#x200B;**[!UICONTROL Approval]**&#x200B;活動有指派。

   在工作流程圖中，指定的活動可以產生多個任務，尤其是當有循環或循環（定期）動作時。

   所有工作流活動都列在[此部分](about-activities.md)中，包括使用案例和示例。

* **[!UICONTROL Transitions]**

   轉變可讓您連結活動並定義其順序。 轉變會將來源活動連結至目的地活動。 有數種轉變，取決於來源活動。 有些轉變有其他參數，例如持續時間、條件或篩選器。

   未連結至目的地活動的轉變為橙色，箭頭標題會顯示為菱形。

   >[!NOTE]
   >
   >仍可執行包含未終止轉變的工作流程：系統會產生警告訊息，工作流程一旦到達轉變，就會暫停，但不會產生錯誤。 因此，您可以在工作流程未完成的情況下開始工作流程，並隨著您的操作將其新增。

   有關如何構建工作流的詳細資訊，請參閱[此部分](building-a-workflow.md)。

* **[!UICONTROL Worktables]**

   工作台包含該轉變所攜帶的所有資訊。 每個工作流程都使用數個工作表。 在這些表中傳送的資料可以加速，並在整個工作流的生命週期中使用，只要不清除。 事實上，每次工作流被鈍化時，都會清除不需要的表，而且可能是在執行最大的工作流程時清除，以避免伺服器過載。

   在[此小節](how-to-use-workflow-data.md)中深入了解工作流程資料和表格。

## 主要原則和最佳實務{#principles-workflows}

請參閱以下章節，了解使用工作流程自動化流程的指引和最佳實務：

* 深入了解[此頁面](how-to-use-workflow-data.md)中的工作流程活動。
* 了解如何在[此小節](building-a-workflow.md)中建立工作流程。
* 探索如何使用工作流程在[此區段](../../platform/using/import-export-workflows.md)中匯入Campaign中的資料。
* 在[此頁面](workflow-best-practices.md)中詳細說明工作流程最佳實務。
* 在[此部分](starting-a-workflow.md)中查找有關工作流執行的指導。
* 了解如何在[此頁面](monitoring-workflow-execution.md)中監控工作流程。
* 了解如何授與使用者的存取權，以在[本頁面](managing-rights.md)中使用工作流程。
