---
solution: Campaign Classic
product: campaign
title: 事件集合
description: 事件集合
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 5%

---


# 事件集合{#event-collection}

資訊系統生成的事件可以使用兩種模式進行收集：

* 對SOAP方法的呼叫可讓您推送Adobe Campaign中的事件：pushevent方法可讓您一次傳送一個事件，而PushEvents方法可讓您一次傳送數個事件。 請參閱事 [件說明](../../message-center/using/event-description.md)。
* 建立工作流允許您通過導入檔案或通過SQL網關(使用「同盟資料存取」選 **項** )恢復事件。

收集事件後，會依技術工作流程在執行例項的即時佇列和批次佇列之間劃分事件，同時等待連結至訊息範本。

![](assets/messagecenter_events_queues_001.png)
