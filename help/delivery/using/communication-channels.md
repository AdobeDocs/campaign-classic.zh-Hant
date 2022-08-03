---
product: campaign
title: 通訊頻道
description: 建立傳遞，以在不同通道上傳送個人化訊息。
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 19%

---

# 通訊頻道{#communication-channels}

![](../../assets/common.svg)

通過Adobe Campaign，您可以發送跨渠道的活動，包括電子郵件、簡訊、LINE消息、推送通知和直接郵件，並使用各種專用的活動來衡量其有效性 [報告](../../reporting/using/delivery-reports.md)。 這些訊息是透過傳遞進行設計和傳送，而且可針對每位收件者進行個人化。

核心功能包括目標定位、定義和個人化訊息、通訊執行及相關的營運報告。 主要功能訪問點是傳遞嚮導。 此存取點可導向 Adobe Campaign 涵括的多種功能。

>[!NOTE]
>
>Adobe Campaign提供了一組工具來監控您的傳輸能力並優化電子郵件發送。 瞭解詳情 [此部分](about-deliverability.md)。

通過準備遞送和/或在工作流進程中發送遞送可以自動化。 有關工作流中的交付類型活動的詳細資訊，請參閱 [此部分](../../workflow/using/about-action-activities.md)。

Adobe Campaign提供以下交付渠道：

1. **電子郵件頻道**：電子郵件傳遞功能可讓您傳送個人化電子郵件給目標群體。請參閱 [關於電子郵件通道](about-email-channel.md)。
1. **直接郵件頻道**：直接郵件傳遞可讓您產生擷取檔案，其中包含目標群體的資料。請參閱 [關於直郵渠道](about-direct-mail-channel.md)。
1. **移動頻道**:通過移動渠道交付，您可以向目標群發送個性化的SMS或LINE消息。 請參閱 [簡訊頻道](sms-channel.md)。
1. **行動應用程式頻道**：行動應用程式傳送可讓您傳送通知至 iOS 和 Android 系統。請參閱 [移動應用頻道](about-mobile-app-channel.md) 一章。

   其他頻道在 [此頁](steps-about-delivery-creation-steps.md#other-channels)。

   >[!NOTE]
   >
   >可用頻道的數量取決於您的合同。 請檢查您的授權合約。

可以執行交貨 **線上** （通過電子郵件、一個移動通道和推送通知）, **離線** （直郵頻道）。

根據渠道的不同，交貨模式可以是：

* 通過Adobe Campaign直接成批傳送（電子郵件通道的預設模式）。
* 通過專家操作員進行外部傳遞，該操作員將收到由傳遞嚮導生成的輸出檔案（直接郵件通道的預設模式）。

通過 **[!UICONTROL Administration > Platform > External accounts]** 的下界。 此配置應僅由專家用戶執行。

## 電子郵件傳送 {#email-deliveries}

的 [電子郵件通道](about-email-channel.md) 是Adobe Campaign的核心渠道之一，允許您安排和向特定目標發送個性化電子郵件。

您可以發送不同類型的電子郵件：

* 單發電子郵件：您可以向定義的目標發送一次電子郵件。 它們通常用於宣傳將只準備和發送一次的特定內容（新聞稿、促銷電子郵件等）。
* 定期電子郵件：在活動中，定期發送相同的電子郵件，並定期匯總每個發送和報告。 同一電子郵件會根據發送日期的合格目標發送，但通常會發送到其他目標。 一個常見的例子是生日電子郵件。 有關此內容的詳細資訊，請參閱 [定期交貨](../../workflow/using/recurring-delivery.md)。
* 事務性電子郵件：根據客戶行為觸發的單一電子郵件。 請參閱 [事務性消息](../../message-center/using/about-transactional-messaging.md)。

要瞭解交貨使用情況和建議，請參考市場活動 [提供最佳做法](delivery-best-practices.md)。

有關不同類型交貨的詳細資訊，請參閱 [此部分](#types-of-deliveries)。

## 移動交付 {#mobile-deliveries}

Adobe Campaign允許你 [簡訊](sms-channel.md) 和 [線](line-channel.md) 手機上的資訊。

對於SMS消息，您只能建立、修改和個性化文本格式的消息。 您還可以在發送簡訊之前預覽它們。

對於LINE消息，可以發送文本或影像和連結。

要將SMS或LINE消息傳遞到行動電話，您需要：

* 配置在 **[!UICONTROL Mobile (SMS)]** 頻道或 **[!UICONTROL LINE]** 頻道。
* 正確連結到此外部帳戶的SMS或LINE傳遞模板。

## 推播通知 {#push-notifications}

Adobe Campaign允許您發送個性化和分段 [推送通知](about-mobile-app-channel.md) 在iOS和安卓移動設備上，通過專用應用。 一旦執行了配置和整合步驟，就可以建立併發送iOS和Android交付。 您還可以設計包含影像或視頻的豐富通知。

## 直接郵件 {#direct-mail}

[直接郵件是一種離線通道，可讓您個人化並產生直接郵件供應商所需的檔案。](about-direct-mail-channel.md)它可讓您在客戶歷程中混合使用線上和離線通道。

線上通道可讓您建立訊息（電子郵件、簡訊、行動應用程式傳送等）並直接從 Adobe Campaign 傳送給您的對象。離線通道則不同。當您準備直接郵件傳送時，Adobe Campaign 會產生一個檔案，其中包含所有目標設定檔和選取的聯絡資訊（例如，郵遞區號）。然後，您就可以將此檔案傳送給直接郵件提供者，由他們負責實際傳送。

## 其他通道 {#other-channels}

Adobe Campaign提供電話遞送模板，用於建立外部遞送。 使用此通道意味著您設定專用方法來處理輸出檔案。 配置步驟與 [直郵渠道](about-direct-mail-channel.md)。

>[!NOTE]
>
>電話通道不是開箱即用的。 其實施要求Adobe咨詢或Adobe合作夥伴參與。 請聯繫您的Adobe代表以瞭解更多資訊。

此外，「其它」類型交付使用不執行流程的特定技術模板：這樣，他們就可以管理在Adobe Campaign平台之外執行的營銷行動。

此通道沒有特定的機制。 它是一個通用渠道，擁有自己的外部帳戶路由選項、交貨模板類型和市場活動工作流活動，與Adobe Campaign提供的任何其他通信渠道一樣。

此渠道僅用於說明性目的，例如，定義要為其保留在非Adobe Campaign工具中執行的市場活動目標跟蹤的交貨。

## 傳遞類型{#types-of-deliveries}

「市場活動」中有三種類型的交付對象：

### 單次交付 {#single-delivery}

A **交貨** 是執行一次的獨立傳遞對象。 可以重複，重新準備，但只要它處於其最終狀態（已取消、停止、完成），就不能重新使用。

可以從交貨清單或通過 [交貨](../../workflow/using/delivery.md) 的子菜單。

工作流還根據您要使用的渠道類型提供特定的交付活動。 有關這些活動的詳細資訊，請參閱 [此部分](../../workflow/using/cross-channel-deliveries.md)。

### 重複傳送 {#recurring-delivery}

A **循環交付** 允許您在每次執行活動時建立新的交貨。 這樣，您就不必為循環任務建立新的傳遞。

例如，如果每月運行此類活動一次，則一年後最終將有12個交貨。

在工作流中通過 [循環交貨活動](../../workflow/using/recurring-delivery.md)。 本節介紹了使用此活動的示例： [在目標工作流中建立循環交貨](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

### 持續傳遞 {#continuous-delivery}

A **連續交付** 允許您將新收件人添加到現有交貨中，這樣可避免每次執行新交貨時都需要建立新交貨。

如果傳遞中的資訊發生更改（內容、名稱等），則在傳遞執行時建立新的傳遞對象。 如果未更改任何資訊，則重複使用同一傳遞對象，並將傳遞和跟蹤日誌添加到同一對象中。

例如，如果您每月運行此類型的活動一次，則一年後（如果您沒有對交貨進行任何更改），您最終只能進行一次交貨。

通過 [連續交付活動](../../workflow/using/continuous-delivery.md)。
