---
product: campaign
title: 事件處理
description: 了解在Adobe Campaign Classic中如何處理交易式訊息事件。
audience: message-center
content-type: reference
topic-tags: event-processing
exl-id: 3d85866a-6339-458c-807a-b267cce772b8
source-git-commit: b46a483594f210c4530a934194c6d2b73deaeaf9
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 2%

---

# 事件處理 {#about-event-processing}

在交易式訊息傳送的內容中，事件由外部資訊系統產生，並透過&#x200B;**[!UICONTROL PushEvent]**&#x200B;和&#x200B;**[!UICONTROL PushEvents]**&#x200B;方法傳送至Adobe Campaign（請參閱[事件說明](../../message-center/using/event-description.md)）。

此事件包含連結至事件的資料，例如[type](../../message-center/using/creating-event-types.md)（訂單確認、在網站上建立帳戶等）、電子郵件地址或行動電話號碼，以及其他可讓您在傳送前擴充及個人化交易式訊息的資訊（客戶聯絡資訊、訊息的語言、電子郵件格式等）。

事件資料範例：

![](assets/messagecenter_events_request_001.png)

## 事件處理步驟{#event-processing}

若要處理交易式訊息事件，會對執行例項套用下列步驟：

1. [事件集合](#event-collection)
1. [事件傳輸至訊息範本](#routing-towards-a-template)
1. 使用個人化資料擴充事件
1. [傳遞執行](../../message-center/using/delivery-execution.md)
1. [連結傳](#event-recycling) 送失敗(透過Adobe Campaign工作流程)的事件回收

透過執行例項執行上述所有步驟後，每個目標收件者都會收到個人化訊息。

>[!NOTE]
>
>如需交易式訊息例項的詳細資訊，請參閱[交易式訊息架構](../../message-center/using/transactional-messaging-architecture.md)。


## 事件集合 {#event-collection}

資訊系統生成的事件可以使用兩種模式來收集：

* 對SOAP方法的呼叫可讓您推送Adobe Campaign中的事件：pushEvent方法可讓您一次傳送一個事件，而PushEvents方法可讓您一次傳送多個事件。 有關詳細資訊，請參閱[事件說明](../../message-center/using/event-description.md)。

* 建立工作流程可讓您透過匯入檔案或透過SQL閘道（使用[同盟資料存取](../../installation/using/about-fda.md)選項）來復原事件。

收集事件後，當等待連結至訊息範本時，會依執行例項的即時和批次佇列之間的技術工作流程來劃分事件。

![](assets/messagecenter_events_queues_001.png)

>[!NOTE]
>
>在執行例項上，**[!UICONTROL Real time events]**&#x200B;或&#x200B;**[!UICONTROL Batch events]**&#x200B;資料夾不能設定為檢視，因為這可能導致存取正確問題。 有關將資料夾設定為視圖的詳細資訊，請參閱[此部分](../../platform/using/access-management-folders.md)。

## 路由至範本 {#routing-towards-a-template}

在執行例項上發佈訊息範本後，就會自動產生兩個範本：一個要連結至即時事件，另一個要連結至批次事件。

路由步驟包括根據以下條件將事件連結到相應的消息模板：

* 在事件本身的屬性中指定的事件類型：

   ![](assets/messagecenter_event_type_001.png)

* 在消息模板屬性中指定的事件類型：

   ![](assets/messagecenter_event_type_002.png)

依預設，路由依賴下列資訊：

* 事件類型
* 要使用的通道(預設為：電子郵件)
* 根據發佈日期的最新傳送範本

## 事件狀態{#event-statuses}

**事件歷史記錄**&#x200B;位於&#x200B;**[!UICONTROL Message Center]** > **[!UICONTROL Event history]**&#x200B;下方，將所有已處理的事件分組為單一檢視。 可依事件類型或&#x200B;**status**&#x200B;來分類。 這些狀態包括：

* **待定**:事件可以是：

   * 剛剛收集且尚未處理的事件。 **[!UICONTROL Number of errors]**&#x200B;欄顯示值0。 尚未連結電子郵件範本。
   * 已處理事件，但其確認錯誤。 **[!UICONTROL Number of errors]**&#x200B;欄顯示的值不是0。 若要知道此事件何時會再次處理，請參閱&#x200B;**[!UICONTROL Process requested on]**&#x200B;欄。

* **待定傳送**:已處理事件並連結傳送範本。電子郵件擱置傳送，且會套用傳統傳送程式。 如需詳細資訊，您可以開啟[delivery](../../delivery/using/about-message-tracking.md)。
* **傳送**、忽略 **** 和傳 **送錯誤**:這些傳送狀態會透過updateEventsStatusworkflow **** 復原。如需詳細資訊，您可以開啟相關的傳送。
* **未涵蓋的事件**:事務報文傳送路由階段失敗。例如，Adobe Campaign找不到可作為事件範本的電子郵件。
* **事件已過期**:已達到傳送嘗試次數上限。該事件被視為null。

## 事件循環{#event-recycling}

如果在特定通道上傳送訊息失敗，Adobe Campaign可以使用不同通道重新傳送訊息。 例如，如果SMS通道上的傳送失敗，會使用電子郵件通道重新傳送訊息。

為此，您需要配置一個工作流，該工作流重新建立具有&#x200B;**傳送錯誤**&#x200B;狀態的所有事件，並為其分配不同的通道。

>[!CAUTION]
>
>此步驟只能使用工作流程執行，因此會保留給專家使用者。 如需詳細資訊，請連絡您的Adobe帳戶主管。