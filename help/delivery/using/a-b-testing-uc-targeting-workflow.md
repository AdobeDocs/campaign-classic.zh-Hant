---
product: campaign
title: 建立目標定位工作流程
description: 透過專屬的使用案例了解如何執行A/B測試
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 10%

---

# 建立目標定位工作流程 {#step-1--creating-a-targeting-workflow}



您需要在 **[!UICONTROL Targeting and Workflows]** 行銷活動的標籤。 由 **[!UICONTROL Query]** 活動， a **[!UICONTROL Split]** 連結至兩個 **[!UICONTROL Email delivery]** 活動， a **[!UICONTROL Wait]** 活動， a **[!UICONTROL JavaScript code]** 活動，和 **[!UICONTROL Delivery]** 活動。

1. 如果您尚未這麼做，請建立促銷活動(如需詳細資訊，請參閱 [本節](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign))。

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. 移至 **[!UICONTROL Targeting and Workflows]** 索引標籤。

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 變更現有工作流程的標籤，或按一下 **[!UICONTROL Add]** 若要建立新的一個(如需詳細資訊，請參閱 [本節](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population))。

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 使用滑鼠將活動拖放至工作流程圖表中，包括 **[!UICONTROL Query]** (**[!UICONTROL Target]** ), **[!UICONTROL Split]** (**[!UICONTROL Target]** tab), 2 **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** ), **[!UICONTROL Wait]** 活動(**[!UICONTROL Flow Control]** ), **[!UICONTROL JavaScript code]** 活動(**[!UICONTROL Actions]** ) **[!UICONTROL Delivery]** 活動(**[!UICONTROL Actions]** 標籤)。

![](assets/use_case_abtesting_targetwkfl_004.png)

您現在可以設定母體範例。 [了解更多](a-b-testing-uc-population-samples.md)。
