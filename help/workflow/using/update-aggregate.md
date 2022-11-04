---
product: campaign
title: 更新彙總
description: 深入了解更新匯總工作流程活動
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 1635366b9e1302acd3d8997312bf07d5c1a68982
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 3%

---

# 更新彙總{#update-aggregate}

![](../../assets/v7-only.svg)

匯總是在多維資料集層級定義，以用於報告用途。 A **[!UICONTROL Workflow]** 標籤。

在處理大量資料時，聚合很有用。 系統會根據專用工作流程方塊中定義的設定自動更新這些資料，以將最近收集的資料整合至指標中

匯總會在每個多維資料集的相關索引標籤中定義。

![](assets/s_advuser_cube_agregate_01.png)


此 **[!UICONTROL Update aggregate]** 活動可讓您選取要套用的更新模式：完整或部分。

依預設，會在每次計算期間執行完整更新。 要啟用部分更新，請選擇相關選項並定義更新條件。

![](assets/s_advuser_cube_agregate_05.png)

**良好做法**:a **[!UICONTROL Scheduler]** 活動可用來指定計算更新的頻率。

![](assets/s_advuser_cube_agregate_04.png)
