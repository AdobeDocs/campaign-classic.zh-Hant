---
product: campaign
title: 定義最終傳遞
description: 瞭解如何透過專屬的使用案例執行A/B測試
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 5%

---

# AB測試：定義最終傳遞 {#step-6--defining-the-final-delivery}

建立指令碼以選取A/B測試獲勝者後，您可以定義最終傳送的引數。

1. 將&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動連線至其餘&#x200B;**[!UICONTROL Delivery]**&#x200B;活動。
1. 開啟&#x200B;**[!UICONTROL Delivery]**&#x200B;活動。
1. 取消核取&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;選項以完成此活動的工作流程。
1. 將其他選項保留為其預設值。

   ![](assets/ab_test_final_delivery.png)

透過準備轉變中指定的傳遞（透過&#x200B;**[!UICONTROL Javascript Code]**&#x200B;活動定義），您就可以核准它並開始傳送，如下一個步驟所述。

您現在可以開始工作流程。 [了解更多](a-b-testing-uc-start-workflow.md)。
