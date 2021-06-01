---
product: campaign
title: 傳遞控制
description: 深入了解傳遞控制工作流程活動
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 5%

---

# 傳遞控制{#delivery-control}

**傳遞控制**&#x200B;類型動作可讓您啟動、暫停或停止傳遞。

這可以是轉變中指定的傳送、明確選取的傳送，或由指令碼計算的傳送。 如需詳細資訊，請參閱[傳送](../../workflow/using/delivery.md)。

![](assets/edit_diffusion_act.png)

如果您選取&#x200B;**[!UICONTROL Start]**，活動將執行開始傳送（目標計算、內容準備、傳送）所需的所有步驟。 如果其中某些步驟已由先前的工作流程活動執行，則不會再執行。 例如，如果目標估計已由&#x200B;**[!UICONTROL Delivery]**&#x200B;類型活動執行（請參閱[傳送](../../workflow/using/delivery.md)），則&#x200B;**[!UICONTROL Act on the delivery]**&#x200B;活動將啟動其餘步驟（內容準備和傳送）。

可以使用以下選項：

* **[!UICONTROL Generate an outbound transition]**

   建立將在執行結束時啟動的出站轉變。 您可以選擇是否擷取出站傳送的目標。

* **[!UICONTROL Processing errors]**

   請參閱[處理錯誤](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

## 輸入參數{#input-parameters}

* deliveryId

傳送識別碼，如果選取的動作為&#x200B;**[!UICONTROL Specified in the transition]**。
