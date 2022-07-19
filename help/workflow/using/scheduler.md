---
product: campaign
title: 排程器
description: 瞭解有關計畫程式工作流活動的詳細資訊
feature: Workflows
exl-id: 30a9bd2a-afb1-481c-ab5f-5acebd9cbb5a
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 10%

---

# 排程器 {#scheduler}

![](../../assets/v7-only.svg)

的 **調度程式** 是在其時間表指定的時間激活其轉換的持久任務。

**[!UICONTROL Scheduler]** 活動應視為已排程的開始。圖表中的活動定位規則與活動 **[!UICONTROL Start]** 的定位規則相同。此活動不得具有入站轉變。

## 最佳實務 {#best-practices}

* 不要將工作流安排為每15分鐘運行一次以上，因為它可能會妨礙總體系統效能並在資料庫中建立塊。

* 永遠不要使用多個 **[!UICONTROL Scheduler]** 工作流中每個分支的活動。 請參閱 [使用活動](workflow-best-practices.md#using-activities)。

* 使用調度程式活動可能會導致多個工作流同時運行。 例如，您可以讓調度程式每小時觸發工作流執行，但有時整個工作流的執行需要超過一小時。

   如果工作流已在運行，則可能要跳過執行。 有關如何防止工作流同時執行的詳細資訊，請參閱 [此頁](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)。

* 請注意，如果工作流正在執行長期任務（如導入），或wfserver模組已停止一段時間，則可以在幾小時後激活該轉換。 在這種情況下，可能需要將調度器激活的任務的執行限制到一定的時間範圍內。

## 配置調度程式活動 {#configuring-scheduler-activity}

調度程式定義轉換的激活調度。 要配置它，請按兩下圖形對象，然後按一下 **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

使用嚮導可以定義活動的頻率和有效期。 配置步驟如下：

1. 選擇激活頻率，然後按一下 **[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_scheduler2.png)

1. 提供激活時間和天數。 此步驟的參數取決於在上一步驟中選擇的頻率。 如果您選擇每天啟動幾次活動，則配置選項如下：

   ![](assets/s_user_segmentation_scheduler3.png)

1. 定義計畫的有效期，或指定將執行計畫的次數。

   ![](assets/s_user_segmentation_scheduler4.png)

1. 檢查配置，然後按一下 **[!UICONTROL Finish]** 來保存。

   ![](assets/s_user_segmentation_scheduler5.png)
