---
product: campaign
title: 傳遞控制
description: 進一步瞭解傳遞控制工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows
exl-id: c7cface2-0837-4e6a-91dc-b8353010a7a4
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 9%

---

# 傳遞控制{#delivery-control}



A **傳遞控制**-type動作可讓您開始、暫停或停止傳遞。

這可以是轉變中指定的傳遞、明確選取的傳遞或指令碼計算的傳遞。 有關詳細資訊，請參閱 [傳遞](delivery.md).

![](assets/edit_diffusion_act.png)

如果您選取 **[!UICONTROL Start]**，活動會執行開始傳送所需的所有步驟（目標計算、內容準備、傳送）。 如果先前的工作流程活動已執行其中某些步驟，則不會再執行這些步驟。 例如，如果目標估計已經由 **[!UICONTROL Delivery]** 型別活動(請參閱 [傳遞](delivery.md))， **[!UICONTROL Act on the delivery]** 活動將啟動其餘步驟（內容準備和傳送）。

可以使用以下選項：

* **[!UICONTROL Generate an outbound transition]**

  建立將在執行結束時啟用的出站轉變。 您可以選擇是否要擷取傳出傳遞的目標。

* **[!UICONTROL Processing errors]**

  請參閱 [正在處理錯誤](monitoring-workflow-execution.md#processing-errors).

## 輸入引數 {#input-parameters}

* deliveryId

傳遞識別碼，如果選取的動作為 **[!UICONTROL Specified in the transition]**.
