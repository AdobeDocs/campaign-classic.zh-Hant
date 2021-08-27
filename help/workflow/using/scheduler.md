---
product: campaign
title: 排程器
description: 深入了解排程器工作流程活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 30a9bd2a-afb1-481c-ab5f-5acebd9cbb5a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 10%

---

# 排程器 {#scheduler}

![](../../assets/common.svg)

**排程器**&#x200B;是一項持久性任務，在其調度指定的時間激活其轉變。

**[!UICONTROL Scheduler]** 活動應視為已排程的開始。圖表中的活動定位規則與活動 **[!UICONTROL Start]** 的定位規則相同。此活動不得具有入站轉變。

## 最佳實務 {#best-practices}

* 不要將工作流安排為每15分鐘運行多一次，因為它可能會阻礙整體系統效能並在資料庫中建立塊。

* 在工作流程中，每個分支使用的活動絕不超過一個&#x200B;**[!UICONTROL Scheduler]**。 請參閱[使用活動](workflow-best-practices.md#using-activities)。

* 使用排程器活動可能會導致同時執行多個工作流程。 例如，您可以讓排程器每小時觸發工作流程執行一次，但有時整個工作流程的執行需要超過一小時。

   如果工作流已運行，則可能要跳過執行。 有關如何防止同時執行工作流的詳細資訊，請參閱[此頁](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)。

* 請注意，如果工作流程執行長期任務（例如匯入），或wfserver模組已停止一段時間，則可在數小時後啟動轉變。 在這種情況下，可能需要將調度程式激活的任務的執行限制到特定的時間範圍。

## 設定排程器活動 {#configuring-scheduler-activity}

排程器定義轉變的啟動排程。 要配置，請按兩下圖形對象，然後按一下&#x200B;**[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

精靈可讓您定義活動的頻率和有效期間。 配置步驟如下：

1. 選擇激活頻率，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/s_user_segmentation_scheduler2.png)

1. 提供啟動時間和天數。 此步驟的參數取決於上一步驟中選取的頻率。 如果您選擇每天啟動活動幾次，設定選項如下：

   ![](assets/s_user_segmentation_scheduler3.png)

1. 定義排程的有效期，或指定執行排程的次數。

   ![](assets/s_user_segmentation_scheduler4.png)

1. 檢查配置，然後按一下&#x200B;**[!UICONTROL Finish]**&#x200B;以保存。

   ![](assets/s_user_segmentation_scheduler5.png)
