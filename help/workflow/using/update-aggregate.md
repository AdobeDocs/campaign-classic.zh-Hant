---
product: campaign
title: 更新彙總
description: 瞭解有關更新聚合工作流活動的詳細資訊
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 4%

---

# 更新彙總{#update-aggregate}

![](../../assets/common.svg)

聚合在多維資料集級別定義以用於報告目的。 A **[!UICONTROL Workflow]** 頁籤在配置聚合時可用。

有關在Adobe Campaign使用立方和聚合的詳細資訊，請參閱專用 [節](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates)。

的 **[!UICONTROL Update aggregate]** 活動，您可以選擇要應用的更新模式：全部或部分。

預設情況下，在每次計算期間執行完全更新。 要啟用部分更新，請選擇相關選項並定義更新條件。

![](assets/s_advuser_cube_agregate_05.png)

**良好做法**:a **[!UICONTROL Scheduler]** 活動可用於指定計算更新的頻率。

![](assets/s_advuser_cube_agregate_04.png)
