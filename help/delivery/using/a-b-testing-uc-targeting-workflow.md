---
product: campaign
title: 建立目標定位工作流程
description: 透過專屬的使用案例了解如何執行A/B測試。
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
source-git-commit: 895aa2fd4fa9c7c71c0073e9be33c12d4e92c9fa
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 10%

---

# 建立目標定位工作流程 {#step-1--creating-a-targeting-workflow}

您需要在促銷活動的&#x200B;**[!UICONTROL Targeting and Workflows]**&#x200B;標籤中建立工作流程。 它由&#x200B;**[!UICONTROL Query]**&#x200B;活動、連結至兩個&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動的&#x200B;**[!UICONTROL Split]**&#x200B;活動、**[!UICONTROL Wait]**&#x200B;活動、**[!UICONTROL JavaScript code]**&#x200B;活動和&#x200B;**[!UICONTROL Delivery]**&#x200B;活動組成。

1. 如果您尚未這麼做，請建立促銷活動（如需詳細資訊，請參閱[此區段](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)）。

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. 移至 **[!UICONTROL Targeting and Workflows]** 索引標籤。

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 更改現有工作流的標籤，或按一下&#x200B;**[!UICONTROL Add]**&#x200B;建立新工作流（有關詳細資訊，請參閱[此部分](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)）。

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 使用滑鼠將活動拖放到工作流圖中，包括&#x200B;**[!UICONTROL Query]**（**[!UICONTROL Target]**&#x200B;標籤）、**[!UICONTROL Split]**（**[!UICONTROL Target]**&#x200B;標籤）、兩個&#x200B;**[!UICONTROL Email deliveries]**（**[!UICONTROL Deliveries]**&#x200B;標籤）、 **[!UICONTROL Wait]**&#x200B;活動（**[!UICONTROL Flow Control]**&#x200B;標籤）、 **[!UICONTROL JavaScript code]**&#x200B;活動（**[!UICONTROL Actions]**&#x200B;標籤）和&#x200B;**[!UICONTROL Delivery]**&#x200B;活動（**[!UICONTROL Actions]**&#x200B;標籤）。

![](assets/use_case_abtesting_targetwkfl_004.png)

您現在可以設定母體範例。 [瞭解更多](a-b-testing-uc-population-samples.md)。
