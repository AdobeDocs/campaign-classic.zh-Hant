---
product: campaign
title: 建立目標定位工作流程
description: 瞭解如何通過專用使用案例執行A/B測試
feature: A/B Testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 10%

---

# 建立目標定位工作流程 {#step-1--creating-a-targeting-workflow}

![](../../assets/common.svg)

您需要在 **[!UICONTROL Targeting and Workflows]** 頁籤 它由 **[!UICONTROL Query]** 活動，a **[!UICONTROL Split]** 連結到兩個活動 **[!UICONTROL Email delivery]** 活動，a **[!UICONTROL Wait]** 活動，a **[!UICONTROL JavaScript code]** 活動和 **[!UICONTROL Delivery]** 的子菜單。

1. 如果尚未建立市場活動(有關詳細資訊，請參閱 [此部分](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign))。

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. 移至 **[!UICONTROL Targeting and Workflows]** 索引標籤。

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 更改現有工作流的標籤，或按一下 **[!UICONTROL Add]** 要建立新版本(有關詳細資訊，請參閱 [此部分](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population))。

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 使用滑鼠將活動拖放到工作流圖中，包括 **[!UICONTROL Query]** (**[!UICONTROL Target]** ) **[!UICONTROL Split]** (**[!UICONTROL Target]** 頁籤，兩個 **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** ) **[!UICONTROL Wait]** 活動(A)**[!UICONTROL Flow Control]** ) **[!UICONTROL JavaScript code]** 活動(A)**[!UICONTROL Actions]** )和 **[!UICONTROL Delivery]** 活動(A)**[!UICONTROL Actions]** )的正平方根。

![](assets/use_case_abtesting_targetwkfl_004.png)

現在可以配置填充示例。 [了解更多資訊](a-b-testing-uc-population-samples.md)。
