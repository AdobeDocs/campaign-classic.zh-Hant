---
solution: Campaign Classic
product: campaign
title: 建立定位工作流程
description: 瞭解如何透過專屬的使用案例來執行A/B測試。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 8%

---


# 建立定位工作流程 {#step-1--creating-a-targeting-workflow}

您必須在促銷活動的&#x200B;**[!UICONTROL Targeting and Workflows]**&#x200B;標籤中建立工作流程。 它由&#x200B;**[!UICONTROL Query]**&#x200B;活動、與兩個&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動連結的&#x200B;**[!UICONTROL Split]**&#x200B;活動、**[!UICONTROL Wait]**&#x200B;活動、**[!UICONTROL JavaScript code]**&#x200B;活動和&#x200B;**[!UICONTROL Delivery]**&#x200B;活動組成。

1. 如果您尚未建立促銷活動，請建立促銷活動（如需詳細資訊，請參閱此[章節](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)）。

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. 移至 **[!UICONTROL Targeting and Workflows]** 索引標籤。

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 變更現有工作流程的標籤，或按一下&#x200B;**[!UICONTROL Add]**&#x200B;以建立新工作流程（如需詳細資訊，請參閱此[章節](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)）。

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 使用滑鼠將活動拖放到工作流圖中，包括&#x200B;**[!UICONTROL Query]**（**[!UICONTROL Target]**&#x200B;標籤）、**[!UICONTROL Split]**（**[!UICONTROL Target]**&#x200B;標籤）、兩個&#x200B;**[!UICONTROL Email deliveries]**（**[!UICONTROL Deliveries]**&#x200B;標籤）、**[!UICONTROL Wait]**&#x200B;活動（**[!UICONTROL Flow Control]**&#x200B;標籤）、**[!UICONTROL JavaScript code]**&#x200B;活動（**[!UICONTROL Actions]**&#x200B;標籤）和&#x200B;**[!UICONTROL Delivery]**&#x200B;活動（**[!UICONTROL Actions]**&#x200B;標籤）。

![](assets/use_case_abtesting_targetwkfl_004.png)

您現在可以設定人口樣本(請參閱[步驟2:配置人口樣本](../../delivery/using/a-b-testing-uc-population-samples.md))。
