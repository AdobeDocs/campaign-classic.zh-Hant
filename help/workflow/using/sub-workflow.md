---
title: 子工作流程
seo-title: 子工作流程
description: 子工作流程
seo-description: null
page-status-flag: never-activated
uuid: c952633f-1aca-44cf-bb50-a67e9b086030
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: a4441820-1b3d-4bac-a6e3-1c9c14466d19
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 子工作流程{#sub-workflow}

此活 **[!UICONTROL Sub-workflow]** 動可讓您觸發另一個工作流程的執行並復原結果。 本練習可讓您在使用簡化介面時使用複雜的工作流程。

您可以在單一工作流程中呼叫多個子工作流程。 子工作流程會同步執行。

>[!NOTE]
>
>要正確運行子工作流，您必須只有一個「到達」類型跳轉（編號最低），而只有一個「開始」類型跳轉（編號最高）。 例如，如果您的「開始」類型跳轉的優先順序為1、2和3，則只應有一個「開始」類型跳轉，優先順序為3。

1. 建立工作流程，以當成其他工作流程中的子工作流程。
1. 在工 **[!UICONTROL Jump (end point)]** 作流程的開頭插入優先順序為1的活動。 如果您有多個「到達」類型跳轉，Adobe Campaign會使用「到達」跳轉的編號最低。

   在工 **[!UICONTROL Jump (start point)]** 作流程結束時插入優先順序為2的活動。 如果您有多個「開始」類型跳轉，Adobe Campaign會使用「開始」跳轉，其數字最高。

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >如果子工作流活動引用了具有多個活動的工作流 **[!UICONTROL Jump]** ，則子工作流在「到貨」類型跳轉與「開始」類型跳轉之間執行，「到貨」類型跳轉與「起始」類型跳轉與最大數目。

1. 完成並儲存此「子工作流程」。
1. 建立「主」工作流程。
1. 插入活 **[!UICONTROL Sub-workflow]** 動並將其開啟。
1. 從下拉式清單中選取您要使用 **[!UICONTROL Workflow template]** 的工作流程。

   ![](assets/subworkflow_selection.png)

1. 您也可以新增設定指令碼來變更參考的工作流程。
1. 按一下 **[!UICONTROL Ok]**. 它會自動建立對外轉場，其中包含所選工作流程 **[!UICONTROL Jump (start point)]** 中活動的標籤。

   ![](assets/subworkflow_outbound.png)

1. 執行工作流程。

在執行後，稱為子工作流的工作流仍處於狀 **[!UICONTROL Being edited]** 態，這表示：

* 您無法以滑鼠右鍵按一下轉場來顯示目標。
* 無法顯示中間人口的計數。
* 記錄檔會在「主」工作流程中匯總，而且只會標示為「子工作流程」。

事實上，此工作流程只是範本。 當從「主」工作流程呼叫時，會建立以此範本為基礎的新子工作流程。

## 輸入參數（可選） {#input-parameters--optional-}

* tableName
* 架構

每個傳入事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* tableName
* 架構
* recCount

這三個值集標識查詢所定位的人口。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常是nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。

* targetSchema

此值是工作表的模式。 此參數對於包含和的所有轉場都 **[!UICONTROL tableName]** 有效 **[!UICONTROL schema]**。
