---
product: campaign
title: 子工作流程
description: 瞭解有關子工作流活動的詳細資訊
feature: Workflows
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# 子工作流程{#sub-workflow}

![](../../assets/common.svg)

的 **[!UICONTROL Sub-workflow]** 活動，您可以觸發另一個工作流的執行並恢復結果。 本練習允許您在使用簡化的介面時使用複雜的工作流。

您可以在單個工作流中調用多個子工作流。 子工作流被同步執行。

在以下示例中，主工作流正在使用跳轉調用子工作流。 有關跳轉類型圖形對象的詳細資訊，請參閱 [此部分](jump--start-point-and-end-point-.md)。

1. 建立將用作另一個工作流中子工作流的工作流。
1. 插入 **[!UICONTROL Jump (end point)]** 在工作流開始時優先順序為1的活動。 如果有多個&quot;端點&quot;類型跳轉，Adobe Campaign將使用最小數的&quot;端點&quot;跳轉。
1. 插入 **[!UICONTROL Jump (start point)]** 在工作流結束時優先順序為2的活動。 如果有多個&quot;起始點&quot;類型跳轉，Adobe Campaign將使用最大數的&quot;起始點&quot;跳轉。

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >如果子工作流活動引用了具有多個 **[!UICONTROL Jump]** 活動中，子工作流在「結束點」類型跳轉和「開始點」類型跳轉之間執行，「結束點」類型跳轉的次數最少。
   >
   >要正確運行子工作流，必須只有一個「結束點」類型跳轉（具有最低數字），而只有一個「起始點」類型跳轉（具有最高數字）。

1. 完成並保存此「子工作流」。
1. 建立主工作流。
1. 插入 **[!UICONTROL Sub-workflow]** 並開啟它。
1. 從中選擇要使用的工作流 **[!UICONTROL Workflow template]** 的子菜單。

   ![](assets/subworkflow_selection.png)

1. 您還可以添加配置指令碼以更改引用的工作流。
1. 按一下 **[!UICONTROL Ok]**。它將自動建立帶有 **[!UICONTROL Jump (start point)]** 的下界。

   ![](assets/subworkflow_outbound.png)

1. 運行工作流。

運行後，稱為子工作流的工作流將保留在 **[!UICONTROL Being edited]** 狀態，即：

* 不能按一下右鍵過渡以顯示目標。
* 無法顯示中間總體的計數。
* 子工作流日誌顯示在主工作流中。

   ![](assets/subworkflow_logs.png)

>[!NOTE]
>
>如果子工作流中發生任何錯誤，則主工作流將暫停並建立子工作流的副本。

## 輸入參數（可選） {#input-parameters--optional-}

* 表名
* 架構

每個入站事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* 表名
* 架構
* 記錄計數

這三組值標識查詢所針對的填充。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常為nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。

* 目標架構：此值是工作表的架構。 此參數對於所有具有 **[!UICONTROL tableName]** 和 **[!UICONTROL schema]**。
