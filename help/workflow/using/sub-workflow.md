---
product: campaign
title: 子工作流程
description: 進一步瞭解子工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 2%

---

# 子工作流程{#sub-workflow}



此 **[!UICONTROL Sub-workflow]** 活動可讓您觸發另一個工作流程的執行，並復原結果。 此活動可讓您使用複雜的工作流程，同時使用簡化的介面。

您可以在單一工作流程中呼叫多個子工作流程。 子工作流程會同步執行。

在以下範例中，主要工作流程是使用跳轉呼叫子工作流程。 有關跳轉型別圖形物件的詳細資訊，請參閱 [本節](jump-start-point-and-end-point.md).

1. 建立您會作為另一個工作流程中的子工作流程的工作流程。
1. 插入 **[!UICONTROL Jump (end point)]** 在工作流程開頭具有優先順序1的活動。 如果您有多個「端點」型別跳轉，Adobe Campaign會使用數字最低的「端點」跳轉。
1. 插入 **[!UICONTROL Jump (start point)]** 在工作流程結束時，具有優先順序2的活動。 如果您有多個「起點」跳轉，Adobe Campaign會使用具有最高數字的「起點」跳轉。

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >如果子工作流程活動參考的工作流程具有多個 **[!UICONTROL Jump]** 活動時，子工作流程會在具有最低編號的「端點」型別跳轉與具有最高編號的「起點」型別跳轉之間執行。
   >
   >若要讓子工作流程正確執行，您只能有一個編號最低的「端點」型別跳轉，以及只能有一個編號最高的「起點」型別跳轉。

1. 完成並儲存此「子工作流程」。
1. 建立主要工作流程。
1. 插入 **[!UICONTROL Sub-workflow]** 活動並開啟它。
1. 從中選擇您要使用的工作流程 **[!UICONTROL Workflow template]** 下拉式清單。

   ![](assets/subworkflow_selection.png)

1. 您也可以新增設定指令碼，以變更參考的工作流程。
1. 按一下 **[!UICONTROL Ok]**。這會自動建立外站轉變，其標籤為 **[!UICONTROL Jump (start point)]** 活動。

   ![](assets/subworkflow_outbound.png)

1. 執行工作流程。

執行後，呼叫為子工作流程的工作流程會保留在 **[!UICONTROL Being edited]** 狀態，表示下列專案：

* 您無法用滑鼠右鍵按一下轉變來顯示目標。
* 無法顯示中間母體的計數。
* 子工作流程記錄檔會顯示在主要工作流程中。

  ![](assets/subworkflow_logs.png)

>[!NOTE]
>
>如果子工作流程中發生任何錯誤，主要工作流程將暫停，並建立子工作流程的副本。

## 輸入引數（選擇性） {#input-parameters--optional-}

* tableName
* 綱要

每個傳入事件都必須指定由這些引數定義的目標。

## 輸出引數 {#output-parameters}

* tableName
* 綱要
* recCount

這組三個值會識別查詢所定位的母體。 **[!UICONTROL tableName]** 是記錄目標識別碼的資料表名稱， **[!UICONTROL schema]** 是母體的綱要（通常是nms：recipient）和 **[!UICONTROL recCount]** 是表格中的元素數。

* targetSchema：此值是工作表的綱要。 此引數適用於所有具有的轉變 **[!UICONTROL tableName]** 和 **[!UICONTROL schema]**.
