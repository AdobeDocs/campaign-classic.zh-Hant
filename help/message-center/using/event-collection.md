---
title: 事件集合
seo-title: 事件集合
description: 事件集合
seo-description: null
page-status-flag: never-activated
uuid: 8c373962-40d4-4982-9bd1-ce1cf8261dd5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: cfff302a-6ac0-461a-a1e4-8e4b617fe134
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 事件集合{#event-collection}

資訊系統生成的事件可以使用兩種模式進行收集：

* 對SOAP方法的呼叫可讓您推送Adobe Campaign中的事件：pushevent方法可讓您一次傳送一個事件，而PushEvents方法可讓您一次傳送數個事件。 請參閱事 [件說明](../../message-center/using/event-description.md)。
* 建立工作流允許您通過導入檔案或通過SQL網關(使用同盟資料存取選 **項** )恢復事件。

收集事件後，會依技術工作流程在執行例項的即時佇列和批次佇列之間劃分事件，同時等待連結至訊息範本。

![](assets/messagecenter_events_queues_001.png)

