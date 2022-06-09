---
product: campaign
title: 交集
description: 交集
feature: Workflows, Targeting Activity
exl-id: f426bf02-9899-49eb-b699-728d51b57c64
source-git-commit: eb7a8cd2c9ff476a830dcc6e8e7c29ccd72c24f0
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 交集{#intersection}

>[!CONTEXTUALHELP]
>id="ac_workflow_intersection"
>title="交集活動"
>abstract="「交集」類型活動從接收目標的交集建立目標。 交叉點允許您僅提取所有入站活動結果公用的總體。 建立目標時會收到所有結果：因此，必須先完成所有先前的活動，然後才能執行交集。"


![](../../assets/common.svg)

安 **交集**-type活動從接收到的目標的交集建立目標。

交叉點允許您僅提取所有入站活動結果公用的總體。 建立目標時會收到所有結果：因此，必須先完成所有先前的活動，然後才能執行交集。 要配置此活動，您需要輸入該活動的標籤以及與結果相關的選項。

![](assets/s_user_segmentation_inter.png)

有關配置和使用交叉點活動的詳細資訊，請參閱 [提取接頭資料（交集）](targeting-data.md#extracting-joint-data--intersection-)。

檢查 **[!UICONTROL Generate complement]** 頁籤 補碼將包含所有入站活動結果的聯合，並減去交叉點。 然後，將向活動添加一個額外的出站轉移，如下所示：

![](assets/s_user_segmentation_inter_compl.png)

## 交集示例 {#intersection-example}

在下例中，交集的目的是計算三個簡單查詢的共用收件人，以便建立清單。

1. 在三個簡單查詢後，插入 **[!UICONTROL Intersection]** -type活動。

   在本例中；調查對象分別是男性、住在巴黎的收件人和18至30歲的收件人。

1. 配置交叉點。 要執行此操作，請選擇 **[!UICONTROL Keys only]** 協調方法，因為由查詢產生的總體包含一致的資料。
1. 如果已為查詢輸入了附加資料，則您可以選擇通過選中相關框來僅保留由收件人共用的資料。
1. 如果希望使用其餘的資料（與查詢有關，但不是其交集），請檢查 **[!UICONTROL Generate complement]** 框。
1. 在交叉點結果後添加清單更新活動。 如果您也希望使用此功能，還可以將清單更新添加到補碼中。
1. 執行工作流。 此處，兩個收件人同時應用於所有三個輸入查詢。 補碼由五個收件人組成，他們只應用於三個查詢中的一兩個。

   交集結果被發送到第一個清單更新。 如果您選擇使用補碼，則還會將其發送到第二個清單更新。

   ![](assets/intersection_example.png)

## 輸入參數 {#input-parameters}

* 表名
* 架構

每個入站事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* 表名
* 架構
* 記錄計數

這組三個值標識由交叉點生成的目標。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的架構(通常 **[!UICONTROL nms:recipient]**) **[!UICONTROL recCount]** 是表中的元素數。
