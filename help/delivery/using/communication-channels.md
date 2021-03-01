---
solution: Campaign Classic
product: campaign
title: 通訊通道
description: 建立傳遞，以在不同通道上傳送個人化訊息。
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
translation-type: tm+mt
source-git-commit: 44f2aed49a12d51bb3b38f304e6b922f0faf68cc
workflow-type: tm+mt
source-wordcount: '1210'
ht-degree: 12%

---


# 通訊通道{#communication-channels}

有了Adobe Campaign，您可以傳送跨通道宣傳，包括電子郵件、簡訊、LINE訊息、推播通知和直接郵件，並使用各種專用的[報告](../../reporting/using/delivery-reports.md)來評估宣傳的成效。 這些訊息是透過傳送進行設計和傳送，而且可針對每位收件者個人化。

核心功能包括定位、定義和個人化訊息、通訊執行及相關的營運報告。 主要功能存取點是傳送精靈。 此接入點可提供Adobe Campaign涵蓋的多種功能。

>[!NOTE]
>
>Adobe Campaign提供一套工具，可監控您的傳遞能力並最佳化電子郵件傳送。 如需詳細資訊，請參閱[Deliverability getting started](../../delivery/using/deliverability-key-points.md)和[Deliverability management](../../delivery/using/about-deliverability.md)。

傳送傳送可透過準備傳送和／或在工作流程中傳送來自動化。 如需工作流程中傳送類型活動的詳細資訊，請參閱[本節](../../workflow/using/about-action-activities.md)。

Adobe Campaign提供下列傳送渠道：

1. **電子郵件通道**:電子郵件傳送功能可讓您傳送個人化電子郵件給目標人群。請參閱[關於電子郵件通道](../../delivery/using/about-email-channel.md)。
1. **直接郵件渠道**:直接郵件傳送可讓您產生擷取檔案，其中包含目標人口的資料。請參閱[關於直接郵件通道](../../delivery/using/about-direct-mail-channel.md)。
1. **行動頻道**:行動頻道上的傳送可讓您傳送個人化的SMS或LINE訊息給目標群體。請參閱[SMS頻道](../../delivery/using/sms-channel.md)。
1. **行動應用程式頻道**:行動應用程式傳送可讓您傳送通知至iOS和Android系統。請參閱[行動應用程式頻道](../../delivery/using/about-mobile-app-channel.md)一章。

   其他頻道在[本頁](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)中說明。

   >[!NOTE]
   >
   >可用渠道的數量取決於您的合約。 請檢查您的授權合約。

傳送可進行&#x200B;**線上**（透過電子郵件、其中一個行動頻道和推播通知），以及&#x200B;**離線**（直接郵件頻道）。

視頻道而定，傳送模式可以是：

* 透過Adobe Campaign直接進行大量傳送（電子郵件渠道的預設模式）。
* 透過專家運算子進行外部傳送，而專家運算子會收到傳送精靈產生的輸出檔案（直接郵件頻道的預設模式）。

外部帳戶通過&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;節點進行配置。 此設定只能由專家使用者執行。

## 電子郵件傳送 {#email-deliveries}

[電子郵件渠道](../../delivery/using/about-email-channel.md)是Adobe Campaign的核心渠道之一，可讓您排程個人化電子郵件，並傳送給特定目標。

您可以傳送不同類型的電子郵件：

* 單一傳送電子郵件：您只需傳送一次至已定義目標的電子郵件。 通常用於促銷特定內容，只準備一次並傳送一次（電子報、促銷電子郵件等）。
* 循環寄送電子郵件：在促銷活動中，定期傳送相同的電子郵件，並定期匯總每個傳送及其報表。 相同的電子郵件會根據傳送當日的合格目標傳送，但通常會傳送至不同的目標。 一個常見的例子是生日電子郵件。 如需詳細資訊，請參閱[循環傳送](../../workflow/using/recurring-delivery.md)。
* 交易電子郵件：根據客戶行為觸發的單一電子郵件。 請參閱[Transactional messaging](../../message-center/using/about-transactional-messaging.md)。

若要瞭解傳送用途和建議，請參閱Campaign [傳送最佳實務](../../delivery/using/delivery-best-practices.md)。

有關不同類型交貨的詳細資訊，請參閱[本節](#types-of-deliveries)。

## 行動傳送{#mobile-deliveries}

Adobe Campaign允許您在手機上發送[SMS](../../delivery/using/sms-channel.md)和[LINE](../../delivery/using/line-channel.md)訊息。

對於SMS訊息，您只能以文字格式建立、修改及個人化訊息。 您也可以在傳送SMS訊息之前先預覽。

對於LINE消息，您可以發送文本或影像和連結。

若要將SMS或LINE訊息傳送至行動電話，您需要：

* 在&#x200B;**[!UICONTROL Mobile (SMS)]**&#x200B;頻道或&#x200B;**[!UICONTROL LINE]**&#x200B;頻道上配置的外部帳戶。
* 正確連結至此外部帳戶的SMS或LINE傳送範本。

## 推播通知 {#push-notifications}

Adobe Campaign可讓您透過專用應用程式，在iOS和Android行動裝置上傳送個人化和分段的[推播通知](../../delivery/using/about-mobile-app-channel.md)。 在執行設定和整合步驟後，就可以建立和傳送iOS和Android傳送。 您也可以設計包含影像或視訊的豐富式通知。

## 直接郵件 {#direct-mail}

[直接郵件是一種離線通道，可讓您個人化並產生直接郵件供應商所需的檔案。](../../delivery/using/about-direct-mail-channel.md)它可讓您在客戶歷程中混合使用線上和離線通道。

線上通道可讓您建立訊息（電子郵件、簡訊、行動應用程式傳送等）並直接從 Adobe Campaign 傳送給您的對象。離線通道則不同。當您準備直接郵件傳送時，Adobe Campaign 會產生一個檔案，其中包含所有目標設定檔和選取的聯絡資訊（例如，郵遞區號）。然後，您就可以將此檔案傳送給直接郵件提供者，由他們負責實際傳送。

## 其他通道 {#other-channels}

Adobe Campaign提供電話傳送範本，用於建立外部傳送。 使用此通道意味著您可以設定專用的方法來處理輸出檔案。 配置步驟與[直接郵件通道](../../delivery/using/about-direct-mail-channel.md)的配置步驟相同。

>[!NOTE]
>
>電話頻道無法立即使用。 其實施需要Adobe諮詢或Adobe合作夥伴參與。 如需詳細資訊，請洽詢您的Adobe代表。

此外，「其他」類型的交付使用不執行流程的特定技術模板：這可讓他們管理在Adobe Campaign平台以外執行的行銷動作。

此通道沒有特定的機制。 它是一般渠道，擁有其自己的外部帳戶路由選項、傳送範本類型和促銷活動工作流程活動，就像Adobe Campaign市的其他通訊渠道一樣。

此渠道僅用於描述性用途，例如定義傳送，以便追蹤在非Adobe Campaign工具中執行之促銷活動的目標。

## 傳遞類型{#types-of-deliveries}

促銷活動中有三種類型的傳送物件：

### 單次傳送{#single-delivery}

**delivery**&#x200B;是執行一次的獨立傳送物件。 它可以複製、重新準備，但只要它處於最終狀態（已取消、停止、完成），就不能重複使用。

可從傳送清單或透過[傳送](../../workflow/using/delivery.md)活動在工作流程中建立傳送。

工作流程也會根據您要使用的管道類型，提供特定的傳送活動。 有關這些活動的詳細資訊，請參閱[本節](../../workflow/using/cross-channel-deliveries.md)。

### 重複傳送 {#recurring-delivery}

**循環傳送**&#x200B;可讓您在每次執行活動時建立新傳送。 如此可避免您必須針對循環工作建立新的傳送。

例如，如果您每月執行此類活動一次，一年後最終會有12個傳送。

循環傳送是透過[循環傳送活動](../../workflow/using/recurring-delivery.md)在工作流程中建立。 本節將介紹此活動的示例：[在定位工作流程中建立循環傳送](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

### 持續傳遞 {#continuous-delivery}

**連續傳送**&#x200B;可讓您將新收件者新增至現有傳送，如此可避免在每次執行新傳送時建立新傳送。

如果傳送中的資訊變更（內容、名稱等），則會在傳送執行時建立新的傳送物件。 如果未變更任何資訊，則會重複使用相同的傳送物件，而傳送和追蹤記錄檔會新增至相同的物件。

例如，如果您每月執行此類活動一次，則一年後會有單次傳送（若您未變更傳送）。

在工作流中通過[Continuous交付活動](../../workflow/using/continuous-delivery.md)建立連續的交付。
