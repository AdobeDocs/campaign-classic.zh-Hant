---
title: 排程器
seo-title: 排程器
description: 排程器
seo-description: null
page-status-flag: never-activated
uuid: e814b978-2edd-442e-9334-9633bc9ec63a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 093dbe8a-494f-4fe7-8614-3bf58486e34c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7c4e4c7d7433f782f810fdc2ecdeeedacd72b6c6

---


# 排程器{#scheduler}

The **Scheduler** is a persistent task that is its transition at the times specified by its schedule.

活 **[!UICONTROL Scheduler]** 動應視為已排程的開始。 圖表中的活動定位規則與活動的定位規則相 **[!UICONTROL Start]** 同。 此活動不得具有入站轉換。

最好不要將工作流計畫為每15分鐘多運行一次，因為它可能會影響系統的整體效能並在資料庫中建立塊。

在建立工作流程時，每個分支請勿使用 **[!UICONTROL Scheduler]** 多個活動。 For more on this, refer to: [Using activities](../../workflow/using/workflow-best-practices.md#using-activities).

排程器定義轉場的啟動排程。 若要設定，請連按兩下圖形物件，然後按一下 **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

精靈可讓您定義活動的頻率和有效期。 配置步驟如下：

1. 選取啟動頻率，然後按一下 **[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_scheduler2.png)

1. 提供啟動的時間和日期。 此步驟的參數取決於在上一步驟中選擇的頻率。 如果您選擇每天啟動多次活動，則配置選項如下：

   ![](assets/s_user_segmentation_scheduler3.png)

1. 定義排程的有效期，或指定計畫的執行次數。

   ![](assets/s_user_segmentation_scheduler4.png)

1. 檢查配置並按一下 **[!UICONTROL Finish]** 保存。

   ![](assets/s_user_segmentation_scheduler5.png)

使用調度程式活動可能導致同時運行多個工作流的執行。 例如，您可以讓排程器每小時觸發工作流程執行，但有時整個工作流程的執行需要超過一小時。 如果工作流已運行，則可能希望跳過執行。 有關如何防止同時執行工作流的詳細資訊，請參 [閱此頁](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-execution)。

另請注意，如果工作流正在執行長期任務（如導入），或wfserver模組已停止一段時間，則可在數小時後激活該轉換。 在這種情況下，可能需要將調度器激活的任務的執行限制在特定時間範圍內。
