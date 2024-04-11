---
product: campaign
title: 建立目標定位工作流程
description: 瞭解如何透過專屬的使用案例執行A/B測試
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%

---

# AB測試：建立目標定位工作流程 {#step-1--creating-a-targeting-workflow}

您必須在以下位置建立工作流程： **[!UICONTROL Targeting and Workflows]** 行銷活動的索引標籤。 它由一個 **[!UICONTROL Query]** 活動， a **[!UICONTROL Split]** 連結至兩個的活動 **[!UICONTROL Email delivery]** 活動， a **[!UICONTROL Wait]** 活動， a **[!UICONTROL JavaScript code]** 活動和 **[!UICONTROL Delivery]** 活動。

1. 如果您尚未這麼做，請建立行銷活動(如需詳細資訊，請參閱 [本節](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign))。

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. 前往 **[!UICONTROL Targeting and Workflows]** 標籤。

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 變更現有工作流程的標籤，或按一下 **[!UICONTROL Add]** 若要建立新的URL (如需詳細資訊，請參閱 [本節](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population))。

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 使用滑鼠將活動拖放至工作流程圖中，包括 **[!UICONTROL Query]** (**[!UICONTROL Target]** 標籤)， a **[!UICONTROL Split]** (**[!UICONTROL Target]** 標籤)，二 **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** 標籤)， a **[!UICONTROL Wait]** 活動(**[!UICONTROL Flow Control]** 標籤)， a **[!UICONTROL JavaScript code]** 活動(**[!UICONTROL Actions]** 標籤)，以及 **[!UICONTROL Delivery]** 活動(**[!UICONTROL Actions]** 標籤)。

![](assets/use_case_abtesting_targetwkfl_004.png)

您現在可以設定母體樣本。 [了解更多](a-b-testing-uc-population-samples.md)。
