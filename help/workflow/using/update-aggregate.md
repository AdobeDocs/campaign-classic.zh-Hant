---
product: campaign
title: 更新彙總
description: 深入瞭解更新彙總工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 8%

---

# 更新彙總{#update-aggregate}



聚總是在多維資料庫層級定義，以用於報表用途。 A **[!UICONTROL Workflow]** 標籤在設定彙總時可供使用。

彙總在處理大量資料時很有用。 它們會根據專用工作流程方塊中定義的設定自動更新，以將最近收集的資料整合到指標中

彙總會在每個立方結構的相關頁簽中定義。

![](assets/s_advuser_cube_agregate_01.png)


此 **[!UICONTROL Update aggregate]** 活動可讓您選取要套用的更新模式：完整或部分。

依預設，每次計算期間都會執行完整更新。 若要啟用部分更新，請選取相關選項並定義更新條件。

![](assets/s_advuser_cube_agregate_05.png)

**良好實務**：a **[!UICONTROL Scheduler]** 活動可用於指定計算更新的頻率。

![](assets/s_advuser_cube_agregate_04.png)
