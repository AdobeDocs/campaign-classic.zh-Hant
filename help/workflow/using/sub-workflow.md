---
product: campaign
title: 子工作流程
description: 深入了解子工作流程活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# 子工作流程{#sub-workflow}

![](../../assets/common.svg)

**[!UICONTROL Sub-workflow]**&#x200B;活動可讓您觸發另一個工作流程的執行並復原結果。 此活動可讓您使用簡化的介面，同時使用複雜的工作流程。

您可以在單一工作流程中呼叫多個子工作流程。 子工作流程會同步執行。

在以下範例中，主要工作流程使用跳轉呼叫子工作流程。 有關跳轉類型圖形對象的詳細資訊，請參見[此部分](jump--start-point-and-end-point-.md)。

1. 建立要作為另一個工作流程中子工作流程的工作流程。
1. 在工作流程的開頭插入優先順序為1的&#x200B;**[!UICONTROL Jump (end point)]**&#x200B;活動。 如果您有多個「端點」類型跳轉，Adobe Campaign將使用「端點」跳轉，且數字最低。
1. 在工作流程結尾處插入優先順序為2的&#x200B;**[!UICONTROL Jump (start point)]**&#x200B;活動。 如果您有多個「起始點」類型跳轉，Adobe Campaign會使用「起始點」跳轉，且數字最多。

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >如果子工作流活動引用了具有多個&#x200B;**[!UICONTROL Jump]**&#x200B;活動的工作流，則子工作流將在具有最低數字的「端點」類型跳轉和具有最高數字的「起始點」類型跳轉之間執行。
   >
   >要正確運行子工作流，您必須只有一個「終點」類型跳轉，其編號最低，並且只有一個「起始點」類型跳轉，其編號最高。

1. 完成並儲存此「子工作流程」。
1. 建立主要工作流程。
1. 插入&#x200B;**[!UICONTROL Sub-workflow]**&#x200B;活動並開啟。
1. 從&#x200B;**[!UICONTROL Workflow template]**&#x200B;下拉式清單中選取您要使用的工作流程。

   ![](assets/subworkflow_selection.png)

1. 您也可以新增設定指令碼來變更參考的工作流程。
1. 按一下 **[!UICONTROL Ok]**。它會自動建立出站轉變，其中包含所選工作流程中&#x200B;**[!UICONTROL Jump (start point)]**&#x200B;活動的標籤。

   ![](assets/subworkflow_outbound.png)

1. 執行工作流程。

執行後，作為子工作流調用的工作流將保持&#x200B;**[!UICONTROL Being edited]**&#x200B;狀態，這表示：

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

這組三個值標識查詢所定位的母體。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是母體（通常為nms:recipient）的模式， **[!UICONTROL recCount]** 是表中的元素數。

* targetSchema:此值是工作表的架構。 此參數對於具有&#x200B;**[!UICONTROL tableName]**&#x200B;和&#x200B;**[!UICONTROL schema]**&#x200B;的所有轉變都有效。
