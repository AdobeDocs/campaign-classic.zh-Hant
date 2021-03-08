---
solution: Campaign Classic
product: campaign
title: 事件集合
description: 事件集合
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---


# 事件集合{#event-collection}

資訊系統生成的事件可以使用兩種模式進行收集：

* 對SOAP方法的呼叫可讓您推送Adobe Campaign的事件：pushevent方法可讓您一次傳送一個事件，而PushEvents方法可讓您一次傳送數個事件。 請參閱[事件說明](../../message-center/using/event-description.md)。
* 建立工作流允許您通過導入檔案或通過SQL網關（使用&#x200B;**Federated Data Access**&#x200B;選項）恢復事件。

收集事件後，會依技術工作流程在執行例項的即時佇列和批次佇列之間劃分事件，同時等待連結至訊息範本。

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>在執行例項上，**[!UICONTROL Real time events]**&#x200B;或&#x200B;**[!UICONTROL Batch events]**&#x200B;資料夾不能設為檢視，因為這可能導致存取正確問題。 有關將資料夾設定為視圖的詳細資訊，請參閱[本節](../../platform/using/access-management-folders.md)。
