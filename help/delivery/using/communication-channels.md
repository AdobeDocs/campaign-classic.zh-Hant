---
product: campaign
title: 通訊頻道
description: 建立傳遞，以在不同通道上傳送個人化訊息。
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 通訊頻道{#communication-channels}

![](../../assets/common.svg)

透過Adobe Campaign，您可以傳送跨通道行銷活動，包括電子郵件、簡訊、LINE訊息、推播通知和直接郵件，並使用各種專用的行銷活動來評估其成效 [報告](../../reporting/using/delivery-reports.md). 這些訊息是透過傳遞進行設計和傳送，而且可針對每位收件者進行個人化。

核心功能包括目標定位、定義和個人化訊息、通訊執行及相關的營運報告。 主要功能存取點是傳送精靈。 此存取點可導向 Adobe Campaign 涵括的多種功能。

>[!NOTE]
>
>Adobe Campaign提供一套工具，可監控您的傳遞能力並最佳化電子郵件傳送。 在[本節](about-deliverability.md)了解更多資訊。

傳遞傳送可透過準備傳遞和/或在工作流程程式中傳送來自動化。 如需工作流程中傳送類型活動的詳細資訊，請參閱 [本節](../../workflow/using/about-action-activities.md).

Adobe Campaign提供下列傳送管道：

1. **電子郵件頻道**：電子郵件傳遞功能可讓您傳送個人化電子郵件給目標群體。請參閱 [關於電子郵件通道](about-email-channel.md).
1. **直接郵件頻道**：直接郵件傳遞可讓您產生擷取檔案，其中包含目標群體的資料。請參閱 [關於直接郵件通道](about-direct-mail-channel.md).
1. **行動裝置頻道**:行動通道上的傳送可讓您傳送個人化SMS或LINE訊息給目標人口。 請參閱 [SMS通道](sms-channel.md).
1. **行動應用程式頻道**：行動應用程式傳送可讓您傳送通知至 iOS 和 Android 系統。請參閱 [行動應用程式頻道](about-mobile-app-channel.md) 章節。

   其他通道的說明如下 [本頁](steps-about-delivery-creation-steps.md#other-channels).

   >[!NOTE]
   >
   >可用管道的數量取決於您的合約。 請檢查您的授權合約。

可進行傳送 **線上** （透過電子郵件、其中一個行動頻道和推播通知），以及 **離線** （直接郵件通道）。

視通道而定，傳送模式可以是：

* 透過Adobe Campaign直接成批傳送（電子郵件通道的預設模式）。
* 透過專家運算子進行外部傳送，而專家運算子取得由傳送精靈產生的輸出檔案（直接郵件通道的預設模式）。

外部帳戶是透過 **[!UICONTROL Administration > Platform > External accounts]** 節點。 此設定僅應由專家使用者執行。

## 電子郵件傳送 {#email-deliveries}

此 [電子郵件通道](about-email-channel.md) 是Adobe Campaign的其中一個核心管道，可讓您排程並傳送個人化電子郵件給特定目標。

您可以傳送不同類型的電子郵件：

* 單一傳送電子郵件：您可以傳送一次給定義目標的電子郵件。 它們通常用於促銷只準備並傳送一次的特定內容（電子報、促銷電子郵件等）。
* 循環電子郵件：在行銷活動中，定期傳送相同的電子郵件，並定期匯總每個傳送及其報表。 會根據傳送當天的合格目標，傳送相同的電子郵件，但通常會傳送至不同目標。 生日電子郵件是常見的範例。 有關詳細資訊，請參閱 [循環傳送](../../workflow/using/recurring-delivery.md).
* 交易式電子郵件：根據客戶行為觸發的統一電子郵件。 請參閱 [交易式訊息傳送](../../message-center/using/about-transactional-messaging.md).

若要了解傳送使用方式和建議，請諮詢Campaign [傳遞最佳實務](delivery-best-practices.md).

如需不同傳送類型的詳細資訊，請參閱 [本節](#types-of-deliveries).

## 行動傳送 {#mobile-deliveries}

Adobe Campaign可讓您傳送 [簡訊](sms-channel.md) 和 [折線圖](line-channel.md) 在行動裝置上傳送訊息。

對於SMS訊息，您只能以文字格式建立、修改及個人化訊息。 您也可以在傳送SMS訊息之前先預覽這些訊息。

對於LINE消息，可以發送文本或影像和連結。

若要將SMS或LINE訊息傳送至您需要的行動電話：

* 在 **[!UICONTROL Mobile (SMS)]** 頻道或 **[!UICONTROL LINE]** 頻道。
* 正確連結至此外部帳戶的SMS或LINE傳遞範本。

## 推播通知 {#push-notifications}

Adobe Campaign可讓您傳送個人化和分段 [推播通知](about-mobile-app-channel.md) 在iOS和Android行動裝置上，透過專用應用程式。 執行設定和整合步驟後，即可建立及傳送iOS和Android傳送。 您也可以設計影像或影片的豐富通知。

## 直接郵件 {#direct-mail}

[直接郵件是一種離線通道，可讓您個人化並產生直接郵件供應商所需的檔案。](about-direct-mail-channel.md)它可讓您在客戶歷程中混合使用線上和離線通道。

線上通道可讓您建立訊息（電子郵件、簡訊、行動應用程式傳送等）並直接從 Adobe Campaign 傳送給您的對象。離線通道則不同。當您準備直接郵件傳送時，Adobe Campaign 會產生一個檔案，其中包含所有目標設定檔和選取的聯絡資訊（例如，郵遞區號）。然後，您就可以將此檔案傳送給直接郵件提供者，由他們負責實際傳送。

## 其他通道 {#other-channels}

Adobe Campaign提供電話傳送範本，可用來建立外部傳送。 使用此通道表示您設定了處理輸出檔案的專用方法。 配置步驟與的步驟相同 [直接郵件通道](about-direct-mail-channel.md).

>[!NOTE]
>
>電話頻道無法立即使用。 其實作需要Adobe諮詢或Adobe合作夥伴參與。 請洽詢您的Adobe代表以取得詳細資訊。

此外，「其他」類型傳遞使用不執行程式的特定技術範本：這可讓他們管理在Adobe Campaign平台外部執行的行銷動作。

此通道沒有特定機制。 它是通用管道，具有其專屬的外部帳戶路由選項、傳遞範本類型和行銷活動工作流程活動，就像Adobe Campaign中提供的任何其他通訊管道一樣。

此管道的設計僅針對描述性用途，例如，您要定義傳送，以便在Adobe Campaign以外的工具中追蹤所執行促銷活動的目標。

## 傳遞類型{#types-of-deliveries}

Campaign中有三種傳送物件類型：

### 單次傳遞 {#single-delivery}

A **傳遞** 是執行一次的獨立傳送物件。 它可以重複、重新準備，但只要它處於最終狀態（取消、停止、完成），它就不能重複使用。

傳遞可從傳遞清單建立，或透過 [傳送](../../workflow/using/delivery.md) 活動。

工作流程也會根據您要使用的管道類型，提供特定的傳送活動。 如需這些活動的詳細資訊，請參閱 [本節](../../workflow/using/cross-channel-deliveries.md).

### 重複傳送 {#recurring-delivery}

A **循環傳遞** 可讓您在每次執行活動時建立新傳送。 這可避免您為循環任務建立新的傳送。

例如，如果您每月執行此類型的活動一次，一年後將會有12個傳送。

循環傳送會透過 [循環傳送活動](../../workflow/using/recurring-delivery.md). 本節將提供此活動的範例： [在目標工作流程中建立循環傳送](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### 持續傳遞 {#continuous-delivery}

A **連續傳遞** 可讓您將新收件者新增至現有的傳送，如此可避免每次執行新傳送時都需建立新傳送。

如果傳送中的資訊變更（內容、名稱等），則會在傳送執行時建立新的傳送物件。 如果未變更任何資訊，則會重複使用相同的傳送物件，並將傳送和追蹤記錄檔新增至相同的物件。

例如，如果您每月執行一次此類型的活動，一年後會產生單一傳送（前提是您未對傳送進行任何變更）。

持續傳遞是透過 [持續傳送活動](../../workflow/using/continuous-delivery.md).
