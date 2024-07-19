---
product: campaign
title: 開始使用異動訊息
description: 進一步瞭解Adobe Campaign Classic異動訊息傳送操作原理和關鍵步驟
feature: Transactional Messaging, Message Center
exl-id: dc52e789-d0bf-4e8f-b448-9d69a2762cc1
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 4%

---


# 開始使用異動訊息 {#about-transactional-messaging}



## 概覽 {#overview}

**異動訊息** （訊息中心）是Campaign模組，專為管理從外部資訊系統傳送的事件產生的自訂觸發通知所設計。

交易式訊息是個別且唯一的通訊，由提供者（例如網站）即時傳送。 此為特別預期行為，因為它包含收件者要檢查或確認的重要資訊。

異動訊息功能的設計可支援擴充性並提供7天24小時的服務。

* **何時到期？**&#x200B;因為此訊息包含重要資訊，所以使用者預期訊息會即時傳送。 因此，觸發的事件與到達的訊息之間的延遲必須非常短。

* **為什麼這很重要？**&#x200B;一般而言，交易式訊息的開啟率很高。 因此，應謹慎設計，因為它在定義使用者端關係時可能對客戶行為產生強烈影響。

* **例如？**&#x200B;可能是建立帳戶後的歡迎訊息、訂單已送出的確認、發票、確認密碼變更的訊息、客戶瀏覽您的網站後的通知、產品無法使用通訊、帳戶宣告等。

>[!IMPORTANT]
>
>異動訊息傳送需要特定授權。 請檢查您的授權合約。

<!--Before starting with transactional messaging, make sure you read the corresponding [best practices and limitations]().-->

## 異動訊息傳遞操作原則 {#transactional-messaging-operating-principle}

Adobe Campaign異動訊息模組整合至資訊系統，可傳回要變更為個人化異動訊息的事件。 這些訊息可透過電子郵件、簡訊或推播通知個別或批次傳送。

此功能依賴特定架構，其中&#x200B;**執行執行個體**&#x200B;與&#x200B;**控制執行個體**&#x200B;分開。 此分佈可確保更高的可用性和更好的負載管理。 如需詳細資訊，請參閱[異動訊息架構](../../message-center/using/transactional-messaging-architecture.md)。

>[!NOTE]
>
>若要為Adobe雲端上託管的訊息中心執行執行個體建立新使用者，您必須聯絡[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。 訊息中心使用者是特定操作者，需要專用許可權才能存取&#x200B;**[!UICONTROL Real time events (nmsRtEvent)]**&#x200B;資料夾。

交易式訊息傳遞整體程式的說明如下：

![](assets/transactional-msg-overview.png)

例如，假設您是一間擁有網站的公司，客戶可以在其中購買產品。

Adobe Campaign可讓您傳送通知電子郵件給已將產品新增至購物車的客戶。 當其中一人離開您的網站而未完成購買（觸發促銷活動事件的外部事件）時，就會自動傳送購物車放棄電子郵件給他們（交易式訊息傳送）。

要設定此專案的主要步驟在[本節](#key-steps)中詳細說明。

>[!NOTE]
>
>Adobe Campaign會優先處理交易式訊息，而非其他傳送。

## 主要步驟 {#key-steps}

在Adobe Campaign中建立和管理個人化交易式訊息的主要步驟概述如下。

### 在控制例項上執行的步驟

在&#x200B;**控制項執行個體**&#x200B;上，您必須執行下列動作：

1. [建立事件型別](../../message-center/using/creating-event-types.md)。
1. [建立並設計訊息範本](../../message-center/using/creating-the-message-template.md)。 您必須在此步驟將事件連結至訊息。
1. [測試訊息](../../message-center/using/testing-message-templates.md)。
1. [Publish訊息範本](../../message-center/using/publishing-message-templates.md)。

>[!NOTE]
>
>上述所有步驟都是在&#x200B;**控制執行個體**&#x200B;上執行。 在控制項執行個體上發佈範本也會在所有&#x200B;**執行個體**&#x200B;上發佈。 如需異動訊息執行個體的詳細資訊，請參閱[異動訊息架構](../../message-center/using/transactional-messaging-architecture.md)。

### 執行例項上的事件處理

設計和發佈異動訊息範本後，如果觸發了對應的事件，則會在&#x200B;**執行執行個體**&#x200B;上執行以下主要步驟：

1. 當外部資訊系統產生事件時，相關資料會透過&#x200B;**PushEvent**&#x200B;和&#x200B;**PushEvents**&#x200B;方法傳送至Campaign。 請參閱[事件集合](../../message-center/using/about-event-processing.md#event-collection)。
1. 事件會連結至適當的訊息範本。 請參閱[路由至範本](../../message-center/using/about-event-processing.md#routing-towards-a-template)。
1. 擴充階段完成後，會傳送傳遞。 請參閱[傳遞執行](../../message-center/using/delivery-execution.md)。 每個目標收件者都會收到個人化訊息。

## 相關主題 {#related-topics}

* [開始使用通訊頻道](../../delivery/using/communication-channels.md)
* [傳遞建立關鍵步驟](../../delivery/using/steps-about-delivery-creation-steps.md)
* [異動訊息傳送架構](../../message-center/using/transactional-messaging-architecture.md)
* [關於異動訊息傳送報告](../../message-center/using/about-transactional-messaging-reports.md)
