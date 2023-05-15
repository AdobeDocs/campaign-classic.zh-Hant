---
product: campaign
title: 子工作流程
description: 深入了解子工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# 子工作流程{#sub-workflow}



此 **[!UICONTROL Sub-workflow]** 活動可讓您觸發另一個工作流程的執行並復原結果。 此活動可讓您使用簡化的介面，同時使用複雜的工作流程。

您可以在單一工作流程中呼叫多個子工作流程。 子工作流程會同步執行。

在以下範例中，主要工作流程使用跳轉呼叫子工作流程。 有關跳轉類型圖形對象的詳細資訊，請參見 [本節](jump--start-point-and-end-point-.md).

1. 建立要作為另一個工作流程中子工作流程的工作流程。
1. 插入 **[!UICONTROL Jump (end point)]** 工作流程開始時優先順序為1的活動。 如果您有多個「端點」類型跳轉，Adobe Campaign將使用「端點」跳轉，且數字最低。
1. 插入 **[!UICONTROL Jump (start point)]** 工作流程結束時優先順序為2的活動。 如果您有多個「起始點」類型跳轉，Adobe Campaign會使用「起始點」跳轉，且數字最多。

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >如果子工作流程活動參考具有數個 **[!UICONTROL Jump]** 活動中，子工作流程會在數字最低的「結束點」類型跳轉和數字最高的「開始點」類型跳轉之間執行。
   >
   >要正確運行子工作流，您必須只有一個「終點」類型跳轉，其編號最低，並且只有一個「起始點」類型跳轉，其編號最高。

1. 完成並儲存此「子工作流程」。
1. 建立主要工作流程。
1. 插入 **[!UICONTROL Sub-workflow]** 活動並開啟。
1. 從 **[!UICONTROL Workflow template]** 下拉式清單。

   ![](assets/subworkflow_selection.png)

1. 您也可以新增設定指令碼來變更參考的工作流程。
1. 按一下 **[!UICONTROL Ok]**。它會自動建立外站轉變，並搭配 **[!UICONTROL Jump (start point)]** 活動。

   ![](assets/subworkflow_outbound.png)

1. 執行工作流程。

執行後，作為子工作流程呼叫的工作流程會維持在 **[!UICONTROL Being edited]** 狀態，這表示：

* 您無法以滑鼠右鍵按一下轉變來顯示目標。
* 無法顯示中間母體的計數。
* 子工作流程記錄檔會顯示在主要工作流程中。

   ![](assets/subworkflow_logs.png)

>[!NOTE]
>
>如果子工作流中發生任何錯誤，則主要工作流將暫停，並建立子工作流的副本。

## 輸入參數（可選） {#input-parameters--optional-}

* tableName
* 綱要

每個入站事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* tableName
* 綱要
* recCount

這組三個值標識查詢所定位的母體。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是母體的綱要（通常為nms:recipient）和 **[!UICONTROL recCount]** 是表格中的元素數。

* targetSchema:此值是工作表的架構。 此參數適用於所有具有 **[!UICONTROL tableName]** 和 **[!UICONTROL schema]**.
