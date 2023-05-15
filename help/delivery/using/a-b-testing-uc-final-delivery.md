---
product: campaign
title: 定義最終傳遞
description: 透過專屬的使用案例了解如何執行A/B測試
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: A/B Testing
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 9%

---

# 定義最終傳遞 {#step-6--defining-the-final-delivery}



建立指令碼以選取A/B測試獲勝者後，您可以定義最終傳送的參數。

1. 連接 **[!UICONTROL JavaScript code]** 活動至其餘 **[!UICONTROL Delivery]** 活動。
1. 開啟 **[!UICONTROL Delivery]** 活動。
1. 取消核取 **[!UICONTROL Generate an outbound transition]** 選項，以使用此活動完成工作流程。
1. 將其他選項保留為其預設值。

   ![](assets/ab_test_final_delivery.png)

準備在轉變中指定的傳送(透過 **[!UICONTROL Javascript Code]** 活動)，則您便能核准並開始傳送，如下一個步驟所述。

您現在可以啟動工作流程。 [了解更多](a-b-testing-uc-start-workflow.md)。
