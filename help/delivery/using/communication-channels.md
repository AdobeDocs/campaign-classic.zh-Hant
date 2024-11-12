---
product: campaign
title: 通訊通道
description: 建立傳遞，以在不同通道上傳送個人化訊息。
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 41296a0acaee93d31874bf58287e51085c6c1261
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 61%

---

# 通訊通道{#communication-channels}

透過Adobe Campaign，您可以傳送跨頻道行銷活動，包括電子郵件、簡訊、LINE訊息、推播通知和直接郵件，並使用各種專屬的[報告](../../reporting/using/delivery-reports.md)衡量其成效。 這些訊息是透過傳遞進行設計和傳送，而且可針對每位收件者進行個人化。

核心功能包括目標定位、定義和個人化訊息、通訊執行及相關的營運報告。 主要功能存取點是傳送助理。 此存取點可導向 Adobe Campaign 涵括的多種功能。

>[!NOTE]
>
>Adobe Campaign提供一組工具，用於監視傳遞能力並最佳化電子郵件傳送。 若要了解詳細資訊，請參閱[本章節](about-deliverability.md)。

傳遞傳送可在工作流程中透過準備傳遞和/或傳送來自動化。 如需工作流程中傳遞型別活動的詳細資訊，請參閱[本區段](../../workflow/using/about-action-activities.md)。

Adobe Campaign提供下列傳送管道：

1. **電子郵件管道**：電子郵件傳遞功能可讓您傳送個人化電子郵件給目標群體。請參閱[關於電子郵件頻道](about-email-channel.md)。
1. **直接郵件管道**：直接郵件傳遞可讓您產生擷取檔案，其中包含目標群體的資料。請參閱[關於直接郵件頻道](about-direct-mail-channel.md)。
1. **行動裝置頻道**：行動裝置頻道上的傳遞可讓您傳送個人化SMS或LINE訊息給目標群體。 請參閱[簡訊頻道](sms-channel.md)。
1. **行動應用程式頻道**：行動應用程式傳送可讓您傳送通知至iOS和Android系統。 請參閱[行動應用程式頻道](about-mobile-app-channel.md)章節。

   其他管道的描述見[本節](#other-channels)。

   >[!NOTE]
   >
   >可用管道的數量取決於您的合約。 請檢查您的授權合約。

傳遞可以在&#x200B;**線上** （透過電子郵件、其中一個行動裝置頻道和推播通知）和&#x200B;**離線** （直接郵件頻道）進行。

視通道而定，傳送模式可以是：

* 透過Adobe Campaign的直接大量傳送（電子郵件通道的預設模式）。
* 透過專家操作員進行外部傳遞，操作員將收到傳遞助理產生的輸出檔案（直接郵件頻道的預設模式）。

外部帳戶是透過&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;節點設定。 此設定僅能由專家使用者執行。

## 電子郵件傳送 {#email-deliveries}

[電子郵件管道](about-email-channel.md)是 Adobe Campaign 的核心管道之一，可讓您排程個人化電子郵件並將其傳送到特定目標。

您可以傳送不同類型的電子郵件：

* 單次傳送電子郵件：您可以向指定目標傳送一次性的電子郵件。 它們通常用於宣傳僅準備傳送一次的特定內容 (電子報、促銷電子郵件等)。
* 定期電子郵件：在行銷活動中，定期傳送同一封電子郵件，並定期彙總每次傳送的電子郵件及其報告。 傳送相同的電子郵件，但通常傳送到不同的目標，具體取決於傳送當日的合格目標。 一個常見的例子是生日電子郵件。如需詳細資訊，請參閱[定期傳遞](../../workflow/using/recurring-delivery.md)。
* 交易型電子郵件：根據客戶行為觸發的單一電子郵件。 請參閱[交易型訊息傳送](../../message-center/using/about-transactional-messaging.md)。

若要瞭解傳遞使用情況與建議，請參閱Campaign [傳遞最佳實務](delivery-best-practices.md)。

有關不同類型傳送的詳細資訊，請參閱[本節](#types-of-deliveries)。

## 行動傳遞 {#mobile-deliveries}

Adobe Campaign 可讓您在行動裝置上傳送[簡訊](sms-channel.md)和 [LINE](line-channel.md) 訊息。

對於 SMS 訊息，您只能以文字格式建立、修改和個人化訊息。 您也可以在傳送簡訊之前先預覽簡訊。

對於 LINE 訊息，您可以傳送文字或影像與連結。

若要將簡訊或 LINE 訊息傳送至行動電話，您需要：

* 在&#x200B;**[!UICONTROL Mobile (SMS)]**&#x200B;管道或在&#x200B;**[!UICONTROL LINE]**&#x200B;管道設定外部帳戶。
* 正確連結至此外部帳戶的簡訊或 LINE 傳遞範本。

## 推播通知 {#push-notifications}

Adobe Campaign可讓您透過專用應用程式，在iOS和Android行動裝置上傳送個人化和分段的[推播通知](about-mobile-app-channel.md)。 執行設定和整合步驟後，即可建立並傳送iOS和Android傳遞。 您也可以設計包含影像或影片的豐富通知。

## 直接郵件 {#direct-mail}

[直接郵件](about-direct-mail-channel.md)是離線通道，可讓您個人化並產生直接郵件供應商所需的檔案。 它可讓您在客戶歷程中混合使用線上和離線通道。

線上頻道可讓您建立訊息（電子郵件、簡訊、行動應用程式傳送等），並直接從Adobe Campaign傳送給您的對象。 離線通道則不同。當您準備直接郵件傳送時，Adobe Campaign 會產生一個檔案，其中包含所有目標輪廓和選取的聯絡資訊（例如，郵遞區號）。然後，您就可以將此檔案傳送給直接郵件提供者，由他們負責實際傳送。

## 其他管道 {#other-channels}

Adobe Campaign提供電話傳遞範本，用於建立外部傳遞。 使用此通道表示您設定處理輸出檔案的專用方法。 設定步驟與[直接郵件管道](about-direct-mail-channel.md)相同。

>[!NOTE]
>
>電話管道無法立即使用。 實施需要 Adobe Consulting 或 Adobe 合作夥伴的參與。 如需詳細資訊，請聯絡您的 Adobe 代表。

此外，「其他」型別傳遞會使用不會執行流程的特定技術範本：這可讓他們管理在Adobe Campaign平台外部執行的行銷動作。

此管道沒有特定機制。 此通用頻道有其專屬的外部帳戶路由選項、傳送範本型別和行銷活動工作流程活動，就像Adobe Campaign中可用的任何其他通訊頻道。

此管道專為描述性用途而設計，例如，定義您想要對其在 Adobe Campaign 以外的工具執行之行銷活動目標保持追蹤的傳送。

## 傳遞型別{#types-of-deliveries}

Campaign 的傳遞物件有三種：

### 單次傳遞 {#single-delivery}

 **傳遞**&#x200B;是執行一次的獨立傳送物件。 它可以複製、重新準備，但只要處於最終狀態 (取消、停止、完成)，就無法重複使用。

您可以從傳遞清單建立傳遞，或透過在工作流程中建立[傳遞](../../workflow/using/delivery.md)活動。

工作流程也會根據您想使用的管道類型，提供特定的傳遞活動。 有關這些活動的詳細資訊，請參閱[本節](../../workflow/using/cross-channel-deliveries.md)。

### 週期性傳遞 {#recurring-delivery}

**循環傳遞**&#x200B;可讓您在每次執行活動時建立新的傳遞。 這可避免您必須為週期性任務建立新的傳送。

例如，如果您每月執行一次這類活動，一年後最終將有 12 次傳遞。

定期傳遞是透過在工作流程中建立[定期傳遞活動](../../workflow/using/recurring-delivery.md)。本節將介紹此活動使用方式的範例：[在目標工作流程中建立定期傳送](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

### 持續傳遞 {#continuous-delivery}

**持續傳遞**&#x200B;可讓您將新收件者新增至現有傳遞，以避免每次執行時都必須建立新傳遞。

如果傳送中的資訊變更 (內容、名稱等)，則會在傳送執行時建立新的傳送物件。如果未變更任何資訊，則會重複使用相同的傳遞對象，並將傳送和追蹤記錄新增至相同的物件中。

例如，如果您每月執行一次這類活動，一年後會收到單一傳送 (前提是您未對傳送進行任何變更)。

持續傳遞在工作流程中，透過[持續傳遞活動](../../workflow/using/continuous-delivery.md)建立。
