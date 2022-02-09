---
product: campaign
title: 開始使用異動訊息
description: '瞭解有關Adobe Campaign Classic事務性消息傳遞操作原則和關鍵步驟的更多資訊。 '
feature: Transactional Messaging
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 6%

---


# 開始使用異動訊息 {#about-transactional-messaging}

![](../../assets/v7-only.svg)

## 概覽 {#overview}

**事務性消息** （消息中心）是市場活動模組，用於管理由外部資訊系統發送的事件生成的自定義觸發通知。

事務性消息是由諸如網站的提供者即時發送的單獨且唯一的通信。 特別需要它，因為它包含收件人要檢查或確認的重要資訊。

事務性消息傳遞功能旨在支援可擴充性並提供全天候服務。

* **什麼時候到期？** 由於此消息包含重要資訊，因此用戶希望該消息能夠即時發送。 因此，觸發事件和消息到達之間的延遲必須非常短。

* **為什麼這很重要？** 通常，事務性消息的開啟速率較高。 因此，它應該經過精心設計，因為它在定義客戶關係時會對客戶行為產生很大影響。

* **比如說？** 它可能是建立帳戶後的歡迎消息、訂單已發運的確認、發票、確認密碼更改的消息、客戶瀏覽網站後的通知、產品不可用性通信、帳戶對帳單等。

>[!IMPORTANT]
>
>事務性消息傳遞需要特定的許可證。 請檢查您的授權合約。

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## 交易式訊息傳遞操作原則 {#transactional-messaging-operating-principle}

Adobe Campaign事務性消息傳遞模組整合到資訊系統中，該資訊系統將要被更改的事件返回到個性化事務性消息。 這些消息可以單獨或通過電子郵件、簡訊或推式通知批量發送。

此功能依賴於特定的體系結構， **執行實例** 與 **控制實例**。 此分發可確保更高的可用性和更好的負載管理。 有關此的詳細資訊，請參閱 [事務性消息傳遞體系結構](../../message-center/using/transactional-messaging-architecture.md)。

>[!NOTE]
>
>要為托管在Adobe雲上的消息中心執行實例建立新用戶，您需要聯繫 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 消息中心用戶是需要專用權限才能訪問的特定運算子 **[!UICONTROL Real time events (nmsRtEvent)]** 資料夾。

事務性消息傳遞整個過程可描述如下：

![](assets/transactional-msg-overview.png)

例如，假設您是一家擁有網站的公司，客戶可以在該網站上購買產品。

Adobe Campaign允許您向已將產品添加到購物車的客戶發送通知電子郵件。 當其中一個人離開您的網站而未完成其購買（觸發市場活動事件的外部事件）時，將自動向他們發送購物車放棄電子郵件（事務性消息傳遞）。

實施此項措施的主要步驟如下 [此部分](#key-steps)。

>[!NOTE]
>
>Adobe Campaign優先處理事務性消息，而不是任何其他傳遞。

## 主要步驟 {#key-steps}

在Adobe Campaign建立和管理個性化事務性消息的主要步驟概述如下。

### 對控制項實例執行的步驟

在 **控制實例**，必須執行以下操作：

1. [建立事件類型](../../message-center/using/creating-event-types.md)。
1. [建立和設計消息模板](../../message-center/using/creating-the-message-template.md)。 在此步驟中，必須將事件連結到您的消息。
1. [Test消息](../../message-center/using/testing-message-templates.md)。
1. [發佈消息模板](../../message-center/using/publishing-message-templates.md)。

>[!NOTE]
>
>以上所有步驟均在 **控制實例**。 在控制實例上發佈模板也將在所有 **執行實例**。 有關事務性消息傳遞實例的詳細資訊，請參見 [事務性消息傳遞體系結構](../../message-center/using/transactional-messaging-architecture.md)。

### 執行實例上的事件處理

設計並發佈事務性消息模板後，如果觸發了相應事件，則將對 **執行實例**:

1. 當事件由外部資訊系統生成時，相關資料通過 **推送事件** 和 **推送事件** 的雙曲餘切值。 請參閱 [事件集合](../../message-center/using/about-event-processing.md#event-collection)。
1. 事件連結到相應的消息模板。 請參閱 [向模板路由](../../message-center/using/about-event-processing.md#routing-towards-a-template)。
1. 一旦濃縮階段完成，則發送遞送。 請參閱 [交付執行](../../message-center/using/delivery-execution.md)。 每個目標接收者接收個性化消息。

## 相關主題 {#related-topics}

* [開始使用通訊頻道](../../delivery/using/communication-channels.md)
* [交付建立關鍵步驟](../../delivery/using/steps-about-delivery-creation-steps.md)
* [異動訊息傳送架構](../../message-center/using/transactional-messaging-architecture.md)
* [關於異動訊息傳送報告](../../message-center/using/about-transactional-messaging-reports.md)
