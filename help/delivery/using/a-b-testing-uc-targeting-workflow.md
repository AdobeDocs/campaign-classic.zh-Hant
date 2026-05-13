---
product: campaign
title: 建立目標定位工作流程
description: 瞭解如何透過專屬的使用案例執行A/B測試
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: A/B Testing
role: User
exl-id: aa21fa33-aef9-484a-b454-0cd5a6868a98
TQID: https://experienceleague.adobe.com/D4O223FYCiIwT-P4WCXa1gYjxB56lCGVIuGL3x-fDRo
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616a
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 168
ht-degree: 23%

---

# AB測試：建立目標定位工作流程 {#step-1--creating-a-targeting-workflow}

您必須在行銷活動的&#x200B;**[!UICONTROL Targeting and Workflows]**&#x200B;索引標籤中建立工作流程。 它由一個&#x200B;**[!UICONTROL Query]**&#x200B;活動、連結到兩個&#x200B;**[!UICONTROL Email delivery]**&#x200B;活動的&#x200B;**[!UICONTROL Split]**&#x200B;活動、**[!UICONTROL Wait]**&#x200B;活動、**[!UICONTROL JavaScript code]**&#x200B;活動和&#x200B;**[!UICONTROL Delivery]**&#x200B;活動組成。

1. 如果您尚未這麼做，請建立行銷活動。 有關更多資訊，請參閱[Campaign v8 文件](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=zh-Hant){target=_blank}。

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. 移至 **[!UICONTROL Targeting and Workflows]** 索引標籤。

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. 變更現有工作流程的標籤或按一下&#x200B;**[!UICONTROL Add]**&#x200B;以建立新工作流程(如需詳細資訊，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/marketing-campaign-target.html?lang=zh-Hant){target="_blank"}。

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. 使用滑鼠將活動拖放至工作流程圖表中，包括&#x200B;**[!UICONTROL Query]** （**[!UICONTROL Target]**&#x200B;標籤）、**[!UICONTROL Split]** （**[!UICONTROL Target]**&#x200B;標籤）、兩個&#x200B;**[!UICONTROL Email deliveries]** （**[!UICONTROL Deliveries]**&#x200B;標籤）、**[!UICONTROL Wait]**&#x200B;活動（**[!UICONTROL Flow Control]**&#x200B;標籤）、**[!UICONTROL JavaScript code]**&#x200B;活動（**[!UICONTROL Actions]**&#x200B;標籤）和&#x200B;**[!UICONTROL Delivery]**&#x200B;活動（**[!UICONTROL Actions]**&#x200B;標籤）。

![](assets/use_case_abtesting_targetwkfl_004.png)

您現在可以設定母體樣本。 [了解更多資訊](a-b-testing-uc-population-samples.md)。
