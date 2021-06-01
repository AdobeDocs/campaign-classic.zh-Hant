---
product: campaign
title: 定義最終傳遞
description: 透過專屬的使用案例了解如何執行A/B測試。
audience: delivery
content-type: reference
topic-tags: a-b-testing
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 7%

---

# 定義最終傳遞 {#step-6--defining-the-final-delivery}

建立指令碼以選取A/B測試獲勝者後，您可以定義最終傳送的參數。

1. 將&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動連接至其餘的&#x200B;**[!UICONTROL Delivery]**&#x200B;活動。
1. 開啟&#x200B;**[!UICONTROL Delivery]**&#x200B;活動。
1. 取消選中&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;選項以使用此活動完成工作流。
1. 將其他選項保留為其預設值。

   ![](assets/ab_test_final_delivery.png)

準備在轉變中指定的傳送（透過&#x200B;**[!UICONTROL Javascript Code]**&#x200B;活動定義）後，您就能核准傳送並開始傳送，如下一步所述。

您現在可以啟動工作流程(請參閱[步驟7:啟動工作流](../../delivery/using/a-b-testing-uc-start-workflow.md))。
