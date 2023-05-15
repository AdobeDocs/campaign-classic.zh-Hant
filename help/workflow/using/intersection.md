---
product: campaign
title: 交集
description: 交集
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: f426bf02-9899-49eb-b699-728d51b57c64
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 13%

---

# 交集{#intersection}

>[!CONTEXTUALHELP]
>id="ac_workflow_intersection"
>title="交集活動"
>abstract="交集類型活動會根據收到的目標的交集建立目標。交集讓您僅擷取所有傳入活動結果共有的母體。"
>additional-url="https://video.tv.adobe.com/v/329373" text="觀看示範影片"




安 **交集**-type活動從接收目標的交集建立目標。

交集讓您僅擷取所有傳入活動結果共有的母體。目標建立時會收到所有結果：因此，必須先完成所有先前的活動，才能執行交集。 若要設定此活動，您必須輸入該活動的標籤以及與結果相關的選項。

![](assets/s_user_segmentation_inter.png)

如需設定和使用交集活動的詳細資訊，請參閱 [提取聯合資料（交集）](targeting-data.md#extracting-joint-data--intersection-).

檢查 **[!UICONTROL Generate complement]** 選項。 補充將包含所有入站活動結果的聯合，減去交集。 接著，會新增其他出站轉變至活動，如下所示：

![](assets/s_user_segmentation_inter_compl.png)

## 交集範例 {#intersection-example}

在以下範例中，交集的目的是計算三個簡單查詢的共同收件者，以建立清單。

1. 在三個簡單查詢後，插入 **[!UICONTROL Intersection]** -type活動。

   在此範例中；這些查詢分別針對男性、居住在巴黎的收件者和18至30歲的收件者。

1. 設定交集。 若要這麼做，請選取 **[!UICONTROL Keys only]** 調解方法，因為查詢產生的母體包含一致的資料。
1. 如果您已為查詢輸入其他資料，則可以選中相關框，以僅保留由收件者共用的資料。
1. 如果您想使用其餘的資料（關於查詢，但不涉及其交集），請核取 **[!UICONTROL Generate complement]** 框。
1. 在交集結果之後新增清單更新活動。 如果您也想使用此功能，也可以將清單更新添加到補充功能。
1. 執行工作流程。 在此，兩個收件者同時套用至所有三個輸入的查詢。 補充內容由五個收件者組成，這些收件者只適用於三個查詢中的一或兩個。

   交集結果會傳送至第一個清單更新。 如果您選擇使用補充，則也會將其發送到第二個清單更新。

   ![](assets/intersection_example.png)

## 輸入參數 {#input-parameters}

* tableName
* 綱要

每個入站事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* tableName
* 綱要
* recCount

這組三個值用於標識交叉點產生的目標。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是母體的結構(通常 **[!UICONTROL nms:recipient]**)和 **[!UICONTROL recCount]** 是表格中的元素數。
