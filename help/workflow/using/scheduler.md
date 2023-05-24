---
product: campaign
title: 排程器
description: 深入瞭解排程器工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 30a9bd2a-afb1-481c-ab5f-5acebd9cbb5a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 10%

---

# 排程器 {#scheduler}



此 **排程器** 是一項持續性任務，會在排程指定的時間啟動其轉變。

**[!UICONTROL Scheduler]** 活動應視為已排程的開始。圖表中的活動定位規則與活動 **[!UICONTROL Start]** 的定位規則相同。此活動不得具有入站轉變。

## 最佳實務 {#best-practices}

* 請勿將工作流程排程為每15分鐘執行一次，因為這可能會妨礙整體系統效能並在資料庫中建立區塊。

* 請勿使用超過一個 **[!UICONTROL Scheduler]** 工作流程中每個分支的活動。 另請參閱 [使用活動](workflow-best-practices.md#using-activities).

* 使用排程器活動可能會導致同時執行多個工作流程。 例如，您可以讓排程器每小時觸發一次工作流程執行，但有時整個工作流程的執行需要超過一小時。

   如果工作流程已經在執行中，您可能會想要略過執行。 有關如何防止同時執行工作流程的詳細資訊，請參閱 [此頁面](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions).

* 請注意，如果工作流程正在執行長期任務（例如匯入），或wfserver模組已停止一段時間，則可在數小時後啟動轉變。 在這種情況下，可能需要將排程器啟動的工作執行限制在特定的時間範圍內。

## 設定排程器活動 {#configuring-scheduler-activity}

排程器會定義轉變的啟動排程。 若要進行設定，請連按兩下圖形物件，然後按一下 **[!UICONTROL Change...]**

![](assets/s_user_segmentation_scheduler.png)

精靈可讓您定義活動的頻率和有效期間。 設定步驟如下：

1. 選取啟用頻率，然後按一下 **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_scheduler2.png)

1. 提供啟用時間和天數。 此步驟的引數取決於上一步驟中所選的頻率。 如果您選擇一天啟動活動多次，設定選項如下：

   ![](assets/s_user_segmentation_scheduler3.png)

1. 定義排程的有效期，或指定執行排程的次數。

   ![](assets/s_user_segmentation_scheduler4.png)

1. 檢查設定並按一下 **[!UICONTROL Finish]** 以儲存。

   ![](assets/s_user_segmentation_scheduler5.png)
