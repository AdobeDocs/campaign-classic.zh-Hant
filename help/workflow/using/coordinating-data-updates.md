---
product: campaign
title: 協調資料更新
description: 協調資料更新
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: 9959e22e-9aa0-410f-b22c-9ca1cac46b97
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 3%

---

# 協調資料更新{#coordinating-data-updates}



此使用案例詳細說明了如何建立工作流程，讓您在使用工作流程的數個執行時管理伴隨的更新。

目的是在執行另一更新操作之前檢查更新過程是否已結束。 為此，我們將設定一個實例變數，並讓工作流測試是否正在運行實例以決定是否繼續執行工作流並執行更新。

![](assets/uc_dataupdate_wkf.png)

此工作流程由下列部分組成：

* a **排程器** 活動，在特定頻率上執行工作流程。
* a **測試** 會檢查工作流程是否已執行的活動。
* **查詢** 和 **更新資料** 活動，以備工作流程尚未執行時使用，之後會 **結束** 將工作流程例項變數重新初始化為false的活動。
* 安 **結束** 活動（如果工作流程已執行）。

若要建立工作流程，請遵循下列步驟：

1. 新增 **排程器** 活動，然後根據您的需求設定其頻率。
1. 新增 **測試** 活動以檢查工作流程是否已執行，然後如下配置。

   >[!NOTE]
   >
   >「isRunning」是我們為此範例選擇的執行個體變數名稱。 這不是內建變數。

   ![](assets/uc_dataupdate_test.png)

1. 新增 **結束** 活動 **否** 分叉。 如此一來，如果工作流程已執行，則不會執行任何動作。
1. 將所需的活動新增至 **是** 分叉。 就我們而言， **查詢** 和 **更新資料** 活動。
1. 開啟第一個活動，然後新增 **instance.vars.isRunning = true** 命令 **[!UICONTROL Advanced]** 標籤。 如此一來，執行個體變數就會設為執行中。

   ![](assets/uc_dataupdate_query.png)

1. 新增 **結束** 活動結尾 **[!UICONTROL Yes]** 分叉，然後新增 **instance.vars.isRunning = false** 命令 **[!UICONTROL Advanced]** 標籤。

   如此一來，只要工作流程執行中，就不會執行任何動作。

   ![](assets/uc_dataupdate_end.png)

**相關主題：**

* [防止同時執行多個執行](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [更新資料活動](update-data.md)
