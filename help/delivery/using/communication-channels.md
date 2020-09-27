---
title: 通訊通道
seo-title: 通訊通道
description: 建立傳送，以在不同通道上傳送個人化訊息。
seo-description: null
page-status-flag: never-activated
uuid: 42975431-64c9-4ecb-98ed-b1f9b13c157e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 2e2d1134-9b83-4ada-b74f-c3842a0cf044
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: eccf0e9899426c2517748c7a72611ff098291cd2
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 11%

---


# 通訊通道{#communication-channels}

有了Adobe Campaign，您可以傳送跨通道的宣傳活動，包括電子郵件、SMS、LINE訊息、推播通知和直接郵件，並使用各種專用的報告來評估宣傳的 [成效](../../reporting/using/delivery-reports.md)。 這些訊息是透過傳送進行設計和傳送，而且可針對每位收件者個人化。

核心功能包括定位、定義和個人化訊息、通訊執行及相關的營運報告。 主要功能存取點是傳送精靈。 此存取點可提供Adobe Campaign涵蓋的數種功能。

>[!NOTE]
>
>Adobe Campaign提供一組工具，可監控您的傳遞能力並最佳化電子郵件傳送。 如需詳細資訊，請參閱「 [傳送性」快速入門](../../delivery/using/deliverability-key-points.md) , [以及「傳送性」管理](../../delivery/using/about-deliverability.md)。

傳送傳送可透過準備傳送和／或在工作流程中傳送來自動化。 如需工作流程中傳送類型活動的詳細資訊，請參 [閱本節](../../workflow/using/about-action-activities.md)。

Adobe Campaign提供下列傳送渠道：

1. **電子郵件通道**:電子郵件傳送功能可讓您傳送個人化電子郵件給目標人群。 請參閱關於 [電子郵件渠道](../../delivery/using/about-email-channel.md)。
1. **直接郵件渠道**:直接郵件傳送可讓您產生擷取檔案，其中包含目標人口的資料。 請參閱關 [於直接郵件渠道](../../delivery/using/about-direct-mail-channel.md)。
1. **行動頻道**:行動頻道上的傳送可讓您傳送個人化的SMS或LINE訊息給目標群體。 請參閱 [SMS頻道](../../delivery/using/sms-channel.md)。
1. **行動應用程式頻道**:行動應用程式傳送可讓您傳送通知至iOS和Android系統。 請參閱「行動應 [用程式頻道](../../delivery/using/about-mobile-app-channel.md) 」一章。

   本頁說明其他 [渠道](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)。

   >[!NOTE]
   >
   >使用多個渠道取決於您的套件。 請檢查您的授權合約。

您可線上(透 **過電子郵件** 、其中一個行動通道和推播通知)和離線( **直接郵件通道** )進行傳送。

視頻道而定，傳送模式可以是：

* 透過Adobe Campaign直接進行大量傳送（電子郵件渠道的預設模式）。
* 透過專家運算子進行外部傳送，而專家運算子會收到傳送精靈產生的輸出檔案（直接郵件頻道的預設模式）。

外部帳戶是通過節點配 **[!UICONTROL Administration > Platform > External accounts]** 置的。 此設定只能由專家使用者執行。

## 電子郵件傳送 {#email-deliveries}

電 [子郵件通道](../../delivery/using/about-email-channel.md) 是Adobe Campaign的核心通道之一，可讓您排程個人化電子郵件並傳送給特定目標。

您可以傳送不同類型的電子郵件：

* 單一傳送電子郵件：您只需傳送一次至已定義目標的電子郵件。 通常用於促銷特定內容，只準備一次並傳送一次（電子報、促銷電子郵件等）。
* 循環寄送電子郵件：在促銷活動中，定期傳送相同的電子郵件，並定期匯總每個傳送及其報表。 相同的電子郵件會根據傳送當日的合格目標傳送，但通常會傳送至不同的目標。 一個常見的例子是生日電子郵件。 For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* 交易電子郵件：根據客戶行為觸發的單一電子郵件。 請參閱「交 [易式訊息](../../message-center/using/about-transactional-messaging.md)」。

若要瞭解傳送用途和建議，請參閱「促銷活動傳 [送」最佳實務](../../delivery/using/delivery-best-practices.md)。

有關不同類型交貨的詳細資訊，請參 [閱本節](#types-of-deliveries)。

## 行動傳送 {#mobile-deliveries}

Adobe Campaign可讓您在行動 [裝置上](../../delivery/using/sms-channel.md)[傳送SMS](../../delivery/using/line-channel.md) 和LINE訊息。

對於SMS訊息，您只能以文字格式建立、修改及個人化訊息。 您也可以在傳送SMS訊息之前先預覽。

對於LINE消息，您可以發送文本或影像和連結。

若要將SMS或LINE訊息傳送至行動電話，您需要：

* 在頻道或頻道上設 **[!UICONTROL Mobile (SMS)]** 定的外部帳 **[!UICONTROL LINE]** 戶。
* 正確連結至此外部帳戶的SMS或LINE傳送範本。

## 推播通知 {#push-notifications}

Adobe Campaign allows you to send personalized and segmented [push notifications](../../delivery/using/about-mobile-app-channel.md) on iOS and Android mobile devices, through dedicated apps. 在執行設定和整合步驟後，就可以建立和傳送iOS和Android傳送。 您也可以設計包含影像或視訊的豐富式通知。

## 直接郵件 {#direct-mail}

[直接郵件是一種離線通道，可讓您個人化並產生直接郵件供應商所需的檔案。](../../delivery/using/about-direct-mail-channel.md)它可讓您在客戶歷程中混合使用線上和離線通道。

線上通道可讓您建立訊息（電子郵件、簡訊、行動應用程式傳送等）並直接從 Adobe Campaign 傳送給您的對象。離線通道則不同。當您準備直接郵件傳送時，Adobe Campaign 會產生一個檔案，其中包含所有目標設定檔和選取的聯絡資訊（例如，郵遞區號）。然後，您就可以將此檔案傳送給直接郵件提供者，由他們負責實際傳送。

## 其他通道 {#other-channels}

Adobe Campaign提供代理商或電話傳送範本，可用來建立外部傳送。 使用這些渠道意味著您可以設定專用的方法來處理輸出檔案。 配置步驟與直接郵件通 [道的步驟相同](../../delivery/using/about-direct-mail-channel.md)。

此外，「其他」類型的交付使用不執行流程的特定技術模板：這可讓他們管理在Adobe Campaign平台以外執行的行銷動作。

此通道沒有特定的機制。 它是一般渠道，具有其自己的外部帳戶路由選項、傳送範本類型和促銷活動工作流程活動，就像Adobe Campaign中其他可用的通訊渠道一樣。

此渠道僅用於描述性用途，例如，定義要追蹤在Adobe Campaign以外工具中執行之促銷活動目標的傳送。

## 傳遞類型{#types-of-deliveries}

促銷活動中有三種類型的傳送物件：

### 單次傳送 {#single-delivery}

傳 **送** ，是執行一次的獨立傳送物件。 它可以複製、重新準備，但只要它處於最終狀態（已取消、停止、完成），就不能重複使用。

可從傳送清單或透過「傳送」活動在工作流程中建立 [傳送](../../workflow/using/delivery.md) 。

工作流程也會根據您要使用的管道類型，提供特定的傳送活動。 For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

### 重複傳送 {#recurring-delivery}

循 **環傳送** ，可讓您在每次執行活動時建立新傳送。 如此可避免您必須針對循環工作建立新的傳送。

例如，如果您每月執行此類活動一次，一年後最終會有12個傳送。

循環傳送是透過循環傳送活動在工作流程 [中建立的](../../workflow/using/recurring-delivery.md)。 本節將介紹此活動的示例： [在定位工作流程中建立循環傳送](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

### 持續傳遞 {#continuous-delivery}

持續 **傳送** ，可讓您將新收件者新增至現有的傳送，如此就不必在每次執行時建立新的傳送。

如果傳送中的資訊變更（內容、名稱等），則會在傳送執行時建立新的傳送物件。 如果未變更任何資訊，則會重複使用相同的傳送物件，而傳送和追蹤記錄檔會新增至相同的物件。

例如，如果您每月執行此類活動一次，則一年後會有單次傳送（若您未變更傳送）。

在工作流程中，會透過「連續傳送」活動 [建立連續傳送](../../workflow/using/continuous-delivery.md)。
