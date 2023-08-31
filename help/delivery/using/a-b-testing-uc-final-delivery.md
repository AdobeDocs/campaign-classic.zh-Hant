---
product: campaign
title: 定義最終傳遞
description: 瞭解如何透過專屬的使用案例執行A/B測試
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 6%

---

# AB測試：定義最終傳遞 {#step-6--defining-the-final-delivery}

建立指令碼以選取A/B測試獲勝者後，您可以定義最終傳送的引數。

1. 連線 **[!UICONTROL JavaScript code]** 活動至剩餘 **[!UICONTROL Delivery]** 活動。
1. 開啟 **[!UICONTROL Delivery]** 活動。
1. 取消核取 **[!UICONTROL Generate an outbound transition]** 使用此活動完成工作流程的選項。
1. 將其他選項保留為其預設值。

   ![](assets/ab_test_final_delivery.png)

透過準備轉變中指定的傳遞(透過 **[!UICONTROL Javascript Code]** 活動)後，您就可以核准活動並開始傳送，如下一個步驟所述。

您現在可以開始工作流程。 [了解更多](a-b-testing-uc-start-workflow.md)。
