---
product: campaign
title: 開始使用異動訊息
description: 進一步瞭解Adobe Campaign Classic交易式訊息傳送操作原理和關鍵步驟
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Transactional Messaging
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 6%

---


# 開始使用異動訊息 {#about-transactional-messaging}



## 概覽 {#overview}

**異動訊息傳送** （訊息中心）是Campaign模組，專為管理從外部資訊系統傳送的事件產生的自訂觸發通知而設計。

交易式訊息是個別且唯一的通訊，由提供者（例如網站）即時傳送。 此為特別預期行為，因為它包含收件者要檢查或確認的重要資訊。

異動訊息功能的設計可支援擴充性，並提供7天24小時的服務。

* **何時到期？** 由於此訊息包含重要資訊，使用者預期會即時傳送。 因此，觸發的事件與到達訊息之間的延遲必須非常短。

* **為什麼這很重要？** 一般而言，交易式訊息具有高開啟率。 因此，應謹慎設計，因為它在定義使用者端關係時對客戶行為會有強烈的影響。

* **例如？** 可能是建立帳戶後的歡迎訊息、確認訂單已出貨、發票、確認密碼變更的訊息、客戶瀏覽您的網站後的通知、產品無法使用通訊、帳戶宣告等。

>[!IMPORTANT]
>
>異動訊息傳送需要特定授權。 請檢查您的授權合約。

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## 交易式訊息傳遞操作原則 {#transactional-messaging-operating-principle}

Adobe Campaign異動訊息模組整合至資訊系統，可傳回要變更為個人化異動訊息的事件。 這些訊息可以個別傳送，或透過電子郵件、簡訊或推播通知分批傳送。

此功能需仰賴特定架構，其中 **執行例項** 分隔自 **控制例項**. 此分佈可確保更高的可用性和更好的負載管理。 如需詳細資訊，請參閱 [異動訊息架構](../../message-center/using/transactional-messaging-architecture.md).

>[!NOTE]
>
>若要為Adobe Cloud上託管的訊息中心執行例項建立新使用者，您需要聯絡 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). 訊息中心使用者是特定操作者，需要專用許可權才能存取 **[!UICONTROL Real time events (nmsRtEvent)]** 資料夾。

異動訊息傳送的整體程式可描述如下：

![](assets/transactional-msg-overview.png)

例如，假設您有一家公司，其網站可供客戶購買產品。

Adobe Campaign可讓您傳送通知電子郵件給已將產品新增至購物車的客戶。 當其中一人離開您的網站而未完成購買（觸發促銷活動事件的外部事件）時，就會自動傳送購物車放棄電子郵件給他們（交易式訊息傳送）。

要實施此程式碼的主要步驟詳述於以下的 [本節](#key-steps).

>[!NOTE]
>
>Adobe Campaign會優先處理交易式訊息，而非任何其他傳送。

## 主要步驟 {#key-steps}

在Adobe Campaign中建立和管理個人化交易式訊息的主要步驟概述如下。

### 在控制例項上執行的步驟

於 **控制例項**，您必須執行下列動作：

1. [建立事件型別](../../message-center/using/creating-event-types.md).
1. [建立及設計訊息範本](../../message-center/using/creating-the-message-template.md). 您必須在此步驟中將事件連結至訊息。
1. [測試訊息](../../message-center/using/testing-message-templates.md).
1. [發佈訊息範本](../../message-center/using/publishing-message-templates.md).

>[!NOTE]
>
>上述所有步驟都是在 **控制例項**. 在控制例項上發佈範本也會在全部上發佈 **執行例項**. 如需異動訊息執行個體的詳細資訊，請參閱 [異動訊息架構](../../message-center/using/transactional-messaging-architecture.md).

### 執行例項上的事件處理

設計和發佈交易式訊息範本後，如果觸發了相應的事件，則會在上執行以下主要步驟 **執行例項**：

1. 當外部資訊系統產生事件時，相關資料會透過以下方式傳送至Campaign： **推送事件** 和 **推送事件** 方法。 另請參閱 [事件集合](../../message-center/using/about-event-processing.md#event-collection).
1. 事件會連結至適當的訊息範本。 另請參閱 [路由至範本](../../message-center/using/about-event-processing.md#routing-towards-a-template).
1. 擴充階段完成後，會傳送傳遞。 另請參閱 [傳遞執行](../../message-center/using/delivery-execution.md). 每個目標收件者都會收到個人化訊息。

## 相關主題 {#related-topics}

* [開始使用通訊頻道](../../delivery/using/communication-channels.md)
* [傳遞建立關鍵步驟](../../delivery/using/steps-about-delivery-creation-steps.md)
* [異動訊息傳送架構](../../message-center/using/transactional-messaging-architecture.md)
* [關於異動訊息傳送報告](../../message-center/using/about-transactional-messaging-reports.md)
