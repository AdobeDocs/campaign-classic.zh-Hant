---
title: 傳送控制
seo-title: 傳送控制
description: 傳送控制
seo-description: null
page-status-flag: never-activated
uuid: f9cef2d9-a6a5-45bd-8c7a-fabc11879628
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 0b5ee05c-4b96-425a-ab0f-60b930de21bd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# 傳送控制{#delivery-control}

「傳 **送控制**-類型」動作可讓您啟動、暫停或停止傳送。

這可以是轉場中指定的傳送、明確選取的傳送，或由指令碼計算的傳送。 For more on this, refer to [Delivery](../../workflow/using/delivery.md).

![](assets/edit_diffusion_act.png)

如果您選 **[!UICONTROL Start]**&#x200B;取，活動將執行開始傳送（目標計算、內容準備、傳送）所需的所有步驟。 如果這些步驟中的某些步驟已經由先前的工作流活動執行，則不會再執行這些步驟。 例如，如果目標估計已由類型活動執 **[!UICONTROL Delivery]** 行(請參閱 [Delivery](../../workflow/using/delivery.md))，活動將啟 **[!UICONTROL Act on the delivery]** 動其餘步驟（內容準備和傳送）。

可以使用以下選項：

* **[!UICONTROL Generate an outbound transition]**

   建立將在執行結束時激活的出站轉移。 您可以選擇是否檢索出站傳送的目標。

* **[!UICONTROL Processing errors]**

   請參閱「 [處理錯誤](../../workflow/using/monitoring-workflow-execution.md#processing-errors)」。

## 輸入參數 {#input-parameters}

* deliveryId

傳送識別碼(如果選取的動作為 **[!UICONTROL Specified in the transition]**)。
