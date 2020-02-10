---
title: 協調資料更新
seo-title: 協調資料更新
description: 協調資料更新
seo-description: null
page-status-flag: never-activated
uuid: 003d63f8-3169-4190-882e-e360a83ccafb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: efe09c66-b74b-48f0-9042-5da4342e014e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# 協調資料更新{#coordinating-data-updates}

此使用案例詳細說明了工作流程的建立，可讓您在使用工作流程的數個執行時管理伴隨更新。

目的是在執行另一個更新操作之前檢查更新進程是否已結束。 為此，我們將設定一個實例變數，並讓工作流測試是否正在運行該實例以決定是否繼續執行工作流並執行更新。

![](assets/uc_dataupdate_wkf.png)

此工作流由以下幾部分組成：

* a **Scheduler** activity, that executes workflow on a specific frequency.
* 會檢 **查工作流程是否已執行的Test** 活動。
* **在工作流尚未執行時** ，查詢和更新資料活動，接著執行 **End****** 活動，將工作流實例變數重新初始化為false。
* 如果 **工作流已執行** ，則會執行「結束」活動。

若要建立工作流程，請遵循下列步驟：

1. 新增「 **排程器** 」活動，然後根據您的需求設定其頻率。
1. 新增 **Test** （測試）活動以檢查工作流程是否已執行，然後依下列方式設定。

   >[!NOTE]
   >
   >&quot;isRunning&quot;是我們為此範例選擇的例項變數名稱。 這不是內建變數。

   ![](assets/uc_dataupdate_test.png)

1. 將End活 **動添加** 到 **No** 分叉。 這樣，如果工作流已執行，則不執行任何操作。
1. 將所需的活動新增至 **「是** 」分叉。 在本例中，「查 **詢** 」和「 **更新資料** 」活動。
1. 開啟第一個活動，然後在 **標籤中新增instance.vars.isRunning = true** 命 **[!UICONTROL Advanced]** 令。 如此，例項變數就會設為執行中。

   ![](assets/uc_dataupdate_query.png)

1. 在 **fork的結尾添加** End **[!UICONTROL Yes]** 活動，然後在標籤中添 **加instance.vars.isRunning = false****[!UICONTROL Advanced]** 命令。

   這樣，只要工作流正在執行，就不會執行任何操作。

   ![](assets/uc_dataupdate_end.png)

**相關主題：**

* [防止同時執行多個執行](../../workflow/using/monitoring-workflow-execution.md#preventing-simultaneous-multiple-executions)
* [更新資料活動](../../workflow/using/update-data.md)

