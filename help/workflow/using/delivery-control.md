---
product: campaign
title: 傳遞控制
description: 進一步瞭解傳遞控制工作流程活動
feature: Workflows
hide: true
hidefromtoc: true
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 5%

---

# 傳遞控制{#delivery-control}



**傳遞控制**&#x200B;型別動作可讓您開始、暫停或停止傳遞。

這可以是轉變中指定的傳遞、明確選取的傳遞或指令碼計算的傳遞。 如需詳細資訊，請參閱[傳遞](delivery.md)。

![](assets/edit_diffusion_act.png)

如果您選取&#x200B;**[!UICONTROL Start]**，活動將會執行啟動傳送所需的所有步驟（目標計算、內容準備、傳送）。 如果先前的工作流程活動已執行其中某些步驟，則不會再執行這些步驟。 例如，如果目標估計已由&#x200B;**[!UICONTROL Delivery]**&#x200B;型別活動（請參閱[傳送](delivery.md)）執行，**[!UICONTROL Act on the delivery]**&#x200B;活動將啟動其餘步驟（內容準備和傳送）。

可以使用以下選項：

* **[!UICONTROL Generate an outbound transition]**

  建立將在執行結束時啟用的出站轉變。 您可以選擇是否要擷取傳出傳遞的目標。

* **[!UICONTROL Processing errors]**

  請參閱[處理錯誤](monitoring-workflow-execution.md#processing-errors)。

## 輸入引數 {#input-parameters}

* deliveryId

傳遞識別碼（如果選取的動作是&#x200B;**[!UICONTROL Specified in the transition]**）。
