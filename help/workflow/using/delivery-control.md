---
product: campaign
title: 傳遞控制
description: 瞭解有關交貨控制工作流活動的詳細資訊
feature: Workflows
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 5%

---

# 傳遞控制{#delivery-control}

![](../../assets/common.svg)

A **交貨控制**-type操作允許您啟動、暫停或停止傳遞。

這可以是在轉換中指定的傳遞、顯式選擇的傳遞或由指令碼計算的傳遞。 有關此內容的詳細資訊，請參閱 [交貨](delivery.md)。

![](assets/edit_diffusion_act.png)

如果選擇 **[!UICONTROL Start]**，該活動將執行啟動交付所需的所有步驟（目標計算、內容準備、交付）。 如果這些步驟中的某些步驟已由先前的工作流活動執行，則不會再次執行這些步驟。 例如，如果目標估計已由 **[!UICONTROL Delivery]** 類型活動(請參閱 [交貨](delivery.md)) **[!UICONTROL Act on the delivery]** 活動將啟動其餘步驟（內容準備和交付）。

可以使用以下選項：

* **[!UICONTROL Generate an outbound transition]**

   建立將在執行結束時激活的出站轉換。 您可以選擇是否檢索出站傳遞的目標。

* **[!UICONTROL Processing errors]**

   請參閱 [處理錯誤](monitoring-workflow-execution.md#processing-errors)。

## 輸入參數 {#input-parameters}

* 交貨ID

交貨標識符，如果所選操作為 **[!UICONTROL Specified in the transition]**。
