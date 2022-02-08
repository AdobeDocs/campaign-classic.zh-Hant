---
product: campaign
title: 定義最終傳遞
description: 瞭解如何通過專用使用案例執行A/B測試
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 9%

---

# 定義最終傳遞 {#step-6--defining-the-final-delivery}

![](../../assets/common.svg)

建立指令碼以選擇A/Btest贏家後，您就可以定義最終交貨的參數。

1. 連接 **[!UICONTROL JavaScript code]** 活動至其餘 **[!UICONTROL Delivery]** 的子菜單。
1. 開啟 **[!UICONTROL Delivery]** 的子菜單。
1. 取消選中 **[!UICONTROL Generate an outbound transition]** 按鈕，將選定控制項在Tab鍵次序中下移一個位置。
1. 將其它選項保留為預設值。

   ![](assets/ab_test_final_delivery.png)

通過準備在轉換中指定的傳遞(通過 **[!UICONTROL Javascript Code]** 活動)，然後您將能夠批准它並開始發送，如下一步所述。

現在可以啟動工作流。 [了解更多](a-b-testing-uc-start-workflow.md)。
