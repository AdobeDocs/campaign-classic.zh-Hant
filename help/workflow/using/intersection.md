---
product: campaign
title: 交集
description: 交集
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: f426bf02-9899-49eb-b699-728d51b57c64
source-git-commit: 3ffa32fbaa588904b79a1343c39f5b5b5f2b134f
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 12%

---

# 交集{#intersection}

>[!CONTEXTUALHELP]
>id="ac_workflow_intersection"
>title="交集活動"
>abstract="交集類型活動會根據收到的目標的交集建立目標。交集讓您僅擷取所有傳入活動結果共有的母體。"

**交集**&#x200B;型別活動會從接收目標的交集建立目標。

交集可讓您僅擷取所有入站活動結果通用的母體。 建立目標時會收到所有結果：因此，必須先完成所有先前的活動，才能執行交集。 若要設定此活動，您必須輸入其標籤以及有關結果的選項。

![](assets/s_user_segmentation_inter.png)

如需設定及使用交集活動的詳細資訊，請參閱[擷取聯合資料（交集）](targeting-data.md#extracting-joint-data--intersection-)。

如果要處理剩餘母體，請核取&#x200B;**[!UICONTROL Generate complement]**&#x200B;選項。 此補集會包含所有傳入活動減去交集的聯合結果。然後，會將額外的出站轉變新增至活動，如下所示：

![](assets/s_user_segmentation_inter_compl.png)

## 交集範例 {#intersection-example}

在以下範例中，交集的目的是計算三個簡單查詢共用的收件者，以建立清單。

1. 在三個簡單查詢之後，插入&#x200B;**[!UICONTROL Intersection]** -type活動。

   在此範例中，查詢分別針對居住在巴黎的男性、收件者以及年齡介於18至30歲的收件者。

1. 設定交集。 若要這麼做，請選取&#x200B;**[!UICONTROL Keys only]**&#x200B;調解方法，因為查詢產生的母體包含一致的資料。
1. 如果您已輸入查詢的其他資料，則可勾選相關方塊，選擇僅保留收件者共用的資料。
1. 如果您想要使用其餘資料（關於查詢而非其交集），請核取&#x200B;**[!UICONTROL Generate complement]**&#x200B;方塊。
1. 在交集結果後新增清單更新活動。 如果您也想要使用它，您也可以將清單更新新增到補充中。
1. 執行工作流程。 在此，兩個收件者會同時套用至所有三個輸入的查詢。 補充由五個收件者組成，他們僅套用至三個查詢中的一個或兩個。

   交集結果會傳送給第一個清單更新。 如果您已選擇使用補充，也會將其傳送至第二個清單更新。

   ![](assets/intersection_example.png)

## 輸入引數 {#input-parameters}

* tableName
* 結構描述

每個傳入事件都必須指定由這些引數定義的目標。

## 輸出引數 {#output-parameters}

* tableName
* 結構描述
* recCount

這組三個值會識別從交集產生的目標。 **[!UICONTROL tableName]**&#x200B;是記錄目標識別碼的資料表的名稱，**[!UICONTROL schema]**&#x200B;是母體的結構描述（通常是&#x200B;**[!UICONTROL nms:recipient]**），**[!UICONTROL recCount]**&#x200B;是資料表中的元素數目。
