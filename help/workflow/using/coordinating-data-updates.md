---
product: campaign
title: 協調資料更新
description: 協調資料更新
feature: Workflows, Data Management
exl-id: 9959e22e-9aa0-410f-b22c-9ca1cac46b97
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 3%

---

# 協調資料更新{#coordinating-data-updates}

![](../../assets/common.svg)

此使用案例詳細說明了工作流的建立過程，該過程允許您在使用工作流的多個執行時管理伴隨更新。

目的是在執行另一個更新操作之前檢查更新過程是否已結束。 為此，我們將設定一個實例變數，並在實例正在運行時讓工作流test決定是否繼續執行工作流並執行更新。

![](assets/uc_dataupdate_wkf.png)

此工作流由以下組成：

* a **調度程式** 活動，它在特定頻率上執行工作流。
* a **Test** 檢查工作流是否已在執行的活動。
* **查詢** 和 **更新資料** 在工作流尚未執行時執行活動，然後是 **結束** 將工作流實例變數重新初始化為false的活動。
* 安 **結束** 活動。

要構建工作流，請執行以下步驟：

1. 添加 **調度程式** 活動，然後根據需要配置其頻率。
1. 添加 **Test** 活動：檢查工作流是否已執行，然後按如下方式配置。

   >[!NOTE]
   >
   >&quot;isRunning&quot;是我們為此示例選擇的實例變數名稱。 這不是內置變數。

   ![](assets/uc_dataupdate_test.png)

1. 添加 **結束** 活動 **否** 叉子。 這樣，如果工作流已在執行，則不會執行任何操作。
1. 將所需的活動添加到 **是** 叉子。 就我們而言， **查詢** 和 **更新資料** 活動。
1. 開啟第一個活動，然後添加 **instance.vars.isRunning = true** 的 **[!UICONTROL Advanced]** 頁籤。 這樣，實例變數將設定為正在運行。

   ![](assets/uc_dataupdate_query.png)

1. 添加 **結束** 在 **[!UICONTROL Yes]** fork，然後添加 **instance.vars.isRunning =false** 的 **[!UICONTROL Advanced]** 頁籤。

   這樣，只要工作流正在執行，就不會執行任何操作。

   ![](assets/uc_dataupdate_end.png)

**相關主題：**

* [防止同時執行多個執行](monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [更新資料活動](update-data.md)
