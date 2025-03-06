---
product: campaign
title: 更新彙總
description: 深入瞭解更新彙總工作流程活動
feature: Workflows
hide: true
hidefromtoc: true
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 3%

---

# 更新彙總{#update-aggregate}



聚總是在多維資料庫層級定義，以用於報表用途。 設定彙總時可使用&#x200B;**[!UICONTROL Workflow]**&#x200B;索引標籤。

彙總在處理大量資料時很有用。 它們會根據專用工作流程方塊中定義的設定自動更新，以將最近收集的資料整合到指標中

彙總會在每個立方結構的相關頁簽中定義。

![](assets/s_advuser_cube_agregate_01.png)


**[!UICONTROL Update aggregate]**&#x200B;活動可讓您選取要套用的更新模式：完整或部分。

依預設，每次計算期間都會執行完整更新。 若要啟用部分更新，請選取相關選項並定義更新條件。

![](assets/s_advuser_cube_agregate_05.png)

**良好做法**：可以使用&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動來指定計算更新的頻率。

![](assets/s_advuser_cube_agregate_04.png)
