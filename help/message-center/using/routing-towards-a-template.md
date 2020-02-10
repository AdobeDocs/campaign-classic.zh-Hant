---
title: 向模板傳送
seo-title: 向模板傳送
description: 向模板傳送
seo-description: null
page-status-flag: never-activated
uuid: 1f8252c4-7f96-4759-9544-39b8f854961f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 8fa464e6-3c88-441c-8179-0c54960469a7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 向模板傳送{#routing-towards-a-template}

一旦消息模板發佈到執行實例上，將自動生成兩個要連結到即時或批處理事件的模板。 路由選擇步驟包括將事件連結到相應的消息模板。 連結是根據事件本身屬性和範本屬性中指定的事件類型。

事件屬性中事件類型的定義：

![](assets/messagecenter_event_type_001.png)

消息模板屬性中事件類型的定義：

![](assets/messagecenter_event_type_002.png)

預設情況下，工藝路線基於以下資訊：

* 事件類型，
* 要使用的頻道(預設為：電子郵件)、
* 最新的傳送範本，根據發佈日期。

