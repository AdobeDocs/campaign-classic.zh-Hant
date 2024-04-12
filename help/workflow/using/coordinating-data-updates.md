---
product: campaign
title: 協調資料更新
description: 協調資料更新
feature: Workflows, Data Management
exl-id: 9959e22e-9aa0-410f-b22c-9ca1cac46b97
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 3%

---

# 協調資料更新{#coordinating-data-updates}



此使用案例詳細說明如何建立工作流程，以便您在使用工作流程的多個執行時管理伴隨的更新。

目的是在執行另一個更新作業之前，檢查更新流程是否已結束。 為此，我們將設定一個執行個體變數，並讓工作流程測試執行個體是否正在執行，以決定是否繼續執行工作流程並執行更新。

![](assets/uc_dataupdate_wkf.png)

此工作流程由以下部分組成：

* a **排程器** 活動，在特定頻率上執行工作流程。
* a **測試** 活動可檢查工作流程是否已執行。
* **查詢** 和 **更新資料** 活動以防工作流程尚未執行，隨後會顯示 **結束** 將工作流程例項變數重新初始化為false的活動。
* 一個 **結束** 活動（如果工作流程已在執行）。

若要建置工作流程，請遵循下列步驟：

1. 新增 **排程器** 活動，然後根據您的需求設定其頻率。
1. 新增 **測試** 活動以檢查工作流程是否已在執行，然後如下所述進行設定。

   >[!NOTE]
   >
   >&quot;isRunning&quot;是我們針對此範例選擇的執行個體變數名稱。 這不是內建變數。

   ![](assets/uc_dataupdate_test.png)

1. 新增 **結束** 活動至 **否** 分支。 如此一來，如果工作流程已執行，則不會執行任何動作。
1. 將所需的活動新增至 **是** 分支。 在我們的案例中， **查詢** 和 **更新資料** 活動。
1. 開啟第一個活動，然後新增 **instance.vars.isRunning = true** 中的命令 **[!UICONTROL Advanced]** 標籤。 如此一來，執行個體變數就會設定為執行中。

   ![](assets/uc_dataupdate_query.png)

1. 新增 **結束** 活動結尾的 **[!UICONTROL Yes]** 分支，然後新增 **instance.vars.isRunning = false** 中的命令 **[!UICONTROL Advanced]** 標籤。

   如此一來，只要工作流程仍在執行中，就不會執行任何動作。

   ![](assets/uc_dataupdate_end.png)

**相關主題：**

* [防止同時執行多個專案](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [更新資料活動](update-data.md)
