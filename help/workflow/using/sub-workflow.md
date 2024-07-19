---
product: campaign
title: 子工作流程
description: 進一步瞭解子工作流程活動
feature: Workflows
exl-id: bc64ca11-2c50-4896-b6c6-ae42c0315924
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 1%

---

# 子工作流程{#sub-workflow}



**[!UICONTROL Sub-workflow]**&#x200B;活動可讓您觸發另一個工作流程的執行，並復原結果。 此活動可讓您使用複雜的工作流程，同時使用簡化的介面。

您可以在單一工作流程中呼叫多個子工作流程。 子工作流程會同步執行。

在以下範例中，主要工作流程是使用跳轉呼叫子工作流程。 如需跳轉型圖形物件的詳細資訊，請參閱[本節](jump-start-point-and-end-point.md)。

1. 建立您會作為另一個工作流程中的子工作流程的工作流程。
1. 在工作流程的開頭插入優先順序為1的&#x200B;**[!UICONTROL Jump (end point)]**&#x200B;活動。 如果您有多個「端點」型別跳轉，Adobe Campaign會使用數字最低的「端點」跳轉。
1. 在工作流程結尾插入優先順序為2的&#x200B;**[!UICONTROL Jump (start point)]**&#x200B;活動。 如果您有多個「起點」跳轉，Adobe Campaign會使用具有最高數字的「起點」跳轉。

   ![](assets/subworkflow_jumps.png)

   >[!NOTE]
   >
   >如果子工作流程活動參考具有數個&#x200B;**[!UICONTROL Jump]**&#x200B;活動的工作流程，則子工作流程會在具有最低編號的「端點」型別跳轉與具有最高編號的「起點」型別跳轉之間執行。
   >
   >若要讓子工作流程正確執行，您只能有一個編號最低的「端點」型別跳轉，以及只能有一個編號最高的「起點」型別跳轉。

1. 完成並儲存此「子工作流程」。
1. 建立主要工作流程。
1. 插入&#x200B;**[!UICONTROL Sub-workflow]**&#x200B;活動並開啟它。
1. 從&#x200B;**[!UICONTROL Workflow template]**&#x200B;下拉式清單中選取您要使用的工作流程。

   ![](assets/subworkflow_selection.png)

1. 您也可以新增設定指令碼，以變更參考的工作流程。
1. 按一下 **[!UICONTROL Ok]**。它會從選取的工作流程中，以&#x200B;**[!UICONTROL Jump (start point)]**&#x200B;活動的標籤自動建立出站轉變。

   ![](assets/subworkflow_outbound.png)

1. 執行工作流程。

執行後，呼叫為子工作流程的工作流程會維持在&#x200B;**[!UICONTROL Being edited]**&#x200B;狀態，這表示下列專案：

* 您無法用滑鼠右鍵按一下轉變來顯示目標。
* 無法顯示中間母體的計數。
* 子工作流程記錄檔會顯示在主要工作流程中。

  ![](assets/subworkflow_logs.png)

>[!NOTE]
>
>如果子工作流程中發生任何錯誤，主要工作流程將暫停，並建立子工作流程的副本。

## 輸入引數（選擇性） {#input-parameters--optional-}

* tableName
* 結構描述

每個傳入事件都必須指定由這些引數定義的目標。

## 輸出引數 {#output-parameters}

* tableName
* 結構描述
* recCount

這組三個值會識別查詢所定位的母體。 **[!UICONTROL tableName]**&#x200B;是記錄目標識別碼的資料表的名稱，**[!UICONTROL schema]**&#x200B;是母體的結構描述（通常是nms：recipient），而&#x200B;**[!UICONTROL recCount]**&#x200B;是資料表中的元素數目。

* targetSchema：此值是工作表的綱要。 此引數適用於所有具有&#x200B;**[!UICONTROL tableName]**&#x200B;和&#x200B;**[!UICONTROL schema]**&#x200B;的轉變。
