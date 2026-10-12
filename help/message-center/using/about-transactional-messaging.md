---
product: campaign
title: 開始使用交易型訊息
description: 進一步瞭解Adobe Campaign Classic異動訊息傳送操作原理和關鍵步驟
feature: Transactional Messaging, Message Center
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
TQID: 'https://experienceleague.adobe.com/n4w2hZkuzHlD3Axc1tUCGfBQ13D28j3Xpmdh07tVr4g'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 8%
---
# 開始使用交易型訊息 {#about-transactional-messaging}



## 概觀 {#overview}

**異動訊息** （訊息中心）是Campaign模組，專為管理從外部資訊系統傳送的事件產生的自訂觸發通知所設計。

作為從Campaign v7轉變到v8的一部分，Campaign Classic檔案集已簡化並重新組織。 Campaign v8檔案集中現在提供常見功能。 若要進一步瞭解異動訊息，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}。

[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional){target=_blank}

本節說明交易式傳訊架構，以及控制和執行執行個體的設定，尤其是內部部署和混合部署。

>[!IMPORTANT]
>
>異動訊息傳送需要特定授權。 請檢查您的授權合約。

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## 異動訊息傳遞操作原則 {#transactional-messaging-operating-principle}

Adobe Campaign異動訊息模組整合至資訊系統，可傳回要變更為個人化異動訊息的事件。 這些訊息可透過電子郵件、簡訊或推播通知個別或批次傳送。

此功能依賴特定架構，其中&#x200B;**執行執行個體**&#x200B;與&#x200B;**控制執行個體**&#x200B;分開。 此分佈可確保更高的可用性和更好的負載管理。 如需詳細資訊，請參閱[異動訊息架構](../../message-center/using/transactional-messaging-architecture.md)。

>[!NOTE]
>
>若要為Adobe Cloud上託管的訊息中心執行執行個體建立新使用者，您必須聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 訊息中心使用者是特定操作者，需要專用許可權才能存取&#x200B;**[!UICONTROL Real time events (nmsRtEvent)]**&#x200B;資料夾。

>[!NOTE]
>
>Adobe Campaign會優先處理交易式訊息，而非其他傳送。

## 主要步驟 {#key-steps}

在Adobe Campaign中建立和管理個人化交易式訊息的主要步驟概述如下。

### 在控制例項上執行的步驟

在&#x200B;**控制項執行個體**&#x200B;上，您必須執行下列動作：

1. [建立事件型別](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional){target="_blank"} （Campaign v8檔案）。
1. [建立及設計訊息範本](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} （Campaign v8檔案）。 您必須在此步驟將事件連結至訊息。
1. [測試訊息](../../message-center/using/testing-message-templates.md)。
1. [發佈訊息範本](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} （Campaign v8檔案）。

>[!NOTE]
>
>上述所有步驟都是在&#x200B;**控制執行個體**&#x200B;上執行。 在控制項執行個體上發佈範本也會在所有&#x200B;**執行個體**&#x200B;上發佈。 如需異動訊息執行個體的詳細資訊，請參閱[異動訊息架構](../../message-center/using/transactional-messaging-architecture.md)。

### 執行例項上的事件處理

設計和發佈異動訊息範本後，如果觸發了對應的事件，則會在&#x200B;**執行執行個體**&#x200B;上執行以下主要步驟：

1. 當外部資訊系統產生事件時，相關資料會透過&#x200B;**PushEvent**&#x200B;和&#x200B;**PushEvents**&#x200B;方法傳送至Campaign。 請參閱[事件集合](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-collection){target="_blank"} （Campaign v8檔案）。
1. 事件會連結至適當的訊息範本。 請參閱[路由至範本](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/event-processing#event-to-template){target="_blank"} （Campaign v8檔案）。
1. 擴充階段完成後，會傳送傳遞。 請參閱[傳遞執行](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} （Campaign v8檔案）。 每個目標收件者都會收到個人化訊息。

## 相關主題 {#related-topics}

* [開始使用通訊頻道](../../delivery/using/communication-channels.md)
* [傳遞建立關鍵步驟](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=zh-Hant){target="_blank"}
* [異動訊息傳送架構](../../message-center/using/transactional-messaging-architecture.md)
* [存取異動訊息傳送報告](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/event/delivery-execution){target="_blank"} （Campaign v8檔案）
