---
title: 關於工作流程
seo-title: 關於工作流程
description: 關於工作流程
seo-description: null
page-status-flag: never-activated
uuid: 19adb0e5-042d-47a0-9f92-24e4b3045dbe
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: introduction
discoiquuid: 868940d1-f19d-4e9a-bffa-8654abb4441c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 關於工作流程{#about-workflows}

Adobe Campaign包含工作流程模組，可讓您協調應用程式伺服器不同模組的所有流程和工作。 使用這個全方位的圖像式環境，您可以設計各式流程，包括細分、行銷活動執行、檔案處理、人力參與等。工作流程引擎將執行並追蹤這些流程。

例如，您可以使用工作流程從伺服器下載檔案、解壓縮，然後將其中的記錄匯入 Adobe Campaign 資料庫。

此外，工作流程也涉及到要進行通知的一或多個操作者，或者是可以選擇並核准流程的相關人員。如此一來就可以實行傳遞行動，將任務指派給一或多位操作者，指定目標且在傳遞前進行核准。

工作流程會在促銷活動管理程式的不同上下文和階段中進行。

Adobe Campaign使用工作流程：

* 進行定位促銷活動。 For more on this, refer to [Implementation steps](../../workflow/using/building-a-workflow.md#implementation-steps-).
* 建立促銷活動：對於每個促銷活動， **[!UICONTROL Workflow]** 標籤可讓您建立目標並建立傳送。 For more on this, refer to [Campaign workflows](../../workflow/using/building-a-workflow.md#campaign-workflows).
* 執行技術流程：清除、收集追蹤資訊或臨時計算。 For more on this, refer to [Technical workflows](../../workflow/using/building-a-workflow.md#technical-workflows).

工作流可以表示流程定義（工作流模型，它表示應發生的事件）和此流程的實例（工作流實例，它表示實際發生的事件）。

工作流程範本說明要執行的各種工作，以及它們如何連結在一起。 任務模板稱為活動，由表徵圖表示。 它們通過轉換而連接在一起。

![](assets/example1.png)

每個工作流程都包含：

* **[!UICONTROL Activities]**

   活動描述任務模板。 圖中用表徵圖表示各種可用活動。 每種類型都有通用屬性和特定屬性。 例如，雖然所有活動都有名稱和標籤，但只有活 **[!UICONTROL Approval]** 動有分配。

   在工作流程圖中，特定活動可以產生多個任務，特別是當存在循環或循環（週期）動作時。

   本節列出所有工作流 [程活動](../../workflow/using/about-activities.md)，包括使用案例和範例。

* **[!UICONTROL Transitions]**

   轉場效果可讓您連結活動並定義其順序。 轉換會將源活動連結到目標活動。 有幾種轉場方式取決於源活動。 有些轉場會有其他參數，例如持續時間、條件或篩選。

   未連結到目標活動的過渡為橙色，箭頭頭顯示為菱形。

   >[!NOTE]
   >
   >仍可執行包含未終止轉場的工作流程：將會產生警告訊息，工作流程在轉場時會暫停，但不會產生錯誤。 因此，您可以在不完成工作流程的情況下開始工作，並隨時加入工作流程。

   有關如何構建工作流的詳細資訊，請參閱 [本部分](../../workflow/using/building-a-workflow.md)。

* **[!UICONTROL Worktables]**

   工作台包含轉移所攜帶的所有資訊。 每個工作流都使用多個工作表。 在這些表中傳送的資料可以在整個工作流生命週期中加速並使用，只要不清除。 事實上，在每次鈍化工作流時，都會清除不需要的表，而且可能在執行最大的工作流時，會清除這些表，以避免伺服器過載。

   進一步瞭解本節中的工作流程資料 [和表格](../../workflow/using/how-to-use-workflow-data.md)。

