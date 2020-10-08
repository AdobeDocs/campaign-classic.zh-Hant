---
title: 使用增量查詢更新每季清單
description: 在此使用案例中，增量查詢會用來自動更新收件者清單。
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# 使用增量查詢更新每季清單 {#quarterly-list-update}

在下例中，增量查 [詢用於](../../workflow/using/incremental-query.md) 自動更新收件者清單。 這些收件者會定位為季節性行銷活動的一部分。

由於這些活動是在每季開始時啟動，以提供相關的體育活動，因此每季都會更新這些清單。 不過，此促銷活動每9個月只能定位一次此處的收件者。 這可讓您省去收件者的資格頻率，並提供多年來不同季節的活動。

![](assets/incremental_query_example.png)

1. 將增量查詢以及清單更新活動新增至新工作流程。
1. 按照創 **[!UICONTROL Incremental query]** 建查詢中指定的方式配 [置活動的頁籤](../../workflow/using/query.md#creating-a-query)。
1. 選取標 **[!UICONTROL Scheduling & History]** 簽，然後指定270天的歷史記錄。 已定位的收件者將不再定位270天，即大約9個月。

   Then click the **[!UICONTROL Change...]** button.

1. 若要確保在每個季節開始前更新清單，請選取 **[!UICONTROL Monthly]**。
1. 在下一個畫面中，選擇3月、6月、9月和12月。 選擇當月20日，然後選擇您要啟動工作流程的時間。
1. 接下來，選擇查詢的有效期。 例如，如果您希望此活動永久活動，請選擇 **[!UICONTROL Permanent validity]**。

   ![](assets/incremental_query_example_2.png)

1. 批准增量查詢後，請按照清單更新中的說明配置清單更 [新活動](../../workflow/using/list-update.md)。

因此，工作流程將會在每季開始前自動啟動。 清單將會更新為新的合格收件者，以接收選件。
