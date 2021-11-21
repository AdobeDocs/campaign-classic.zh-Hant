---
product: campaign
title: 更新彙總
description: 深入了解更新匯總工作流程活動
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 4%

---

# 更新彙總{#update-aggregate}

![](../../assets/common.svg)

匯總是在多維資料集層級定義，以用於報告用途。 A **[!UICONTROL Workflow]** 標籤。

如需Adobe Campaign中多維度資料集和使用匯總的詳細資訊，請參閱專用 [節](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

此 **[!UICONTROL Update aggregate]** 活動可讓您選取要套用的更新模式：完整或部分。

依預設，會在每次計算期間執行完整更新。 要啟用部分更新，請選擇相關選項並定義更新條件。

![](assets/s_advuser_cube_agregate_05.png)

**良好做法**:a **[!UICONTROL Scheduler]** 活動可用來指定計算更新的頻率。

![](assets/s_advuser_cube_agregate_04.png)
