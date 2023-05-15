---
product: campaign
title: 使用增量查詢更新每季清單
description: 在此使用案例中，增量查詢用於自動更新收件人清單
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 0d3e7046-313a-42a6-9155-3365e8d60bac
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 5%

---

# 使用增量查詢更新每季清單 {#quarterly-list-update}



在下列範例中， [增量查詢](incremental-query.md) 用於自動更新收件人清單。 這些收件者會作為季節性行銷活動的目標。

由於這些促銷活動會在每個季節的開頭啟動，以提供相關的體育活動，因此每季都會更新這些清單。 不過，此促銷活動每9個月只能鎖定一次此處的收件者。 這可讓您省下收件者的資格頻率，並提供多年內不同季節的活動。

![](assets/incremental_query_example.png)

1. 將增量查詢以及清單更新活動新增至新工作流程。
1. 設定 **[!UICONTROL Incremental query]** 活動的索引標籤，如 [建立查詢](query.md#creating-a-query).
1. 選取 **[!UICONTROL Scheduling & History]** 標籤，然後指定270天的歷史記錄。 已定位的收件者將不再鎖定270天，即約9個月。

   然後按一下 **[!UICONTROL Change...]** 按鈕。

1. 若要確保清單在每個季開始之前更新，請選取 **[!UICONTROL Monthly]**.
1. 在下一個畫面中，選取3月、6月、9月和12月。 選擇當月的20日，然後選擇要啟動工作流的時間。
1. 下一步，選擇查詢的有效期。 例如，如果您希望此活動永久啟用，請選取 **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. 核准增量查詢後，請依照 [清單更新](list-update.md).

因此，工作流程將在每季開始前自動啟動。 清單將更新為新的合格收件者，以接收優惠方案。
