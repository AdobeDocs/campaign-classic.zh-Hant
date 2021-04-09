---
solution: Campaign Classic
product: campaign
title: 設定和傳送傳送
description: 設定和傳送傳送
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '1521'
ht-degree: 5%

---

# 配置和發送傳送{#configuring-and-sending-the-delivery}

>[!NOTE]
>
>只有傳送擁有者才能開始傳送。 為了讓其他運算元（或運算元群組）能夠開始傳送，您必須在&#x200B;**[!UICONTROL Delivery start:]**&#x200B;欄位中將其新增為審閱者。 有關詳細資訊，請參閱[本節](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers)。

## 傳送其他參數{#delivery-additiona-parameters}

在傳送傳送之前，您可以透過&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤，在傳送屬性中定義傳送參數。

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**:此選項可讓您指出傳送的優先順序等級（一般、高或低），以影響傳送的傳送順序。這可讓您將特定、更緊急的遞送訂單排在優先順序，而非其他遞送。

* **[!UICONTROL Message batch quantity]**:此選項允許您定義在同一XML傳送包內分組的消息數。如果參數設為0，則消息會自動分組。 軟體包大小由計算`<delivery size>/1024`定義，每個軟體包最少8條消息，最多256條消息。

   >[!IMPORTANT]
   >
   >複製傳送時，會重設參數。

* **[!UICONTROL Send using multiple waves]**:有關詳細資訊，請參 [閱使用多波發送](#sending-using-multiple-waves)。

* **[!UICONTROL Test SMTP delivery]**:此選項允許您測試通過SMTP發送的傳送。傳送會處理到連接到SMTP伺服器，但不會發送。

   >[!NOTE]
   >
   >當安裝使用中間採購來源時，不建議使用此選項，即不呼叫mta。 有關配置SMTP伺服器的詳細資訊，請參閱[以瞭解本節](../../installation/using/configure-delivery-settings.md)。

* **[!UICONTROL Email BCC]**:此選項可讓您透過密件副本將電子郵件儲存在外部系統上，只要在訊息目標中新增密件副本電子郵件地址即可。如需詳細資訊，請參閱[本章節](../../delivery/using/sending-messages.md#archiving-emails)。

## 確認傳送{#confirming-delivery}

當已設定傳送並準備傳送時，請確定您已執行傳送分析。

若要這麼做，請按一下&#x200B;**[!UICONTROL Send]**，選取所要的動作，然後按一下&#x200B;**[!UICONTROL Analyze]**。 有關詳細資訊，請參閱[啟動分析](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。

![](assets/s_ncs_user_email_del_send.png)

完成後，按一下&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;以啟動消息傳送。

然後，您可以關閉傳送精靈並從&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤追蹤傳送的執行，此標籤可透過此傳送的詳細資料或傳送清單存取。

傳送訊息後，您可以監控及追蹤傳送內容。 如需詳細資訊，請參閱下列區段。

* [監視](../../delivery/using/about-delivery-monitoring.md)
* [瞭解傳送故障](../../delivery/using/understanding-delivery-failures.md)
* [關於訊息追蹤](../../delivery/using/about-message-tracking.md)

## 排程傳送{#scheduling-the-delivery-sending}的傳送

為了排程傳遞，管理銷售壓力以及避免過度行銷，您可以推延郵件的傳遞。

1. 按一下&#x200B;**[!UICONTROL Send]**&#x200B;按鈕並選擇&#x200B;**[!UICONTROL Postpone delivery]**&#x200B;選項。

1. 在&#x200B;**[!UICONTROL Contact date]**&#x200B;欄位中指定開始日期。

![](assets/dlv_email_del_plan.png)

1. 然後，您可以開始傳送分析，然後確認傳送傳送。 不過，傳送傳送要等到&#x200B;**[!UICONTROL Contact date]**&#x200B;欄位中指定的日期才會開始。

>[!IMPORTANT]
>
>開始分析後，您定義的連絡人日期即為固定。 如果您修改此日期，則必須重新開始分析，以便將您的修改納入考量。

![](assets/s_ncs_user_email_del_start_delayed.png)

在傳送清單中，傳送將會顯示&#x200B;**[!UICONTROL Pending]**&#x200B;狀態。

![](assets/s_ncs_user_email_del_waiting.png)

您也可以透過傳送的&#x200B;**[!UICONTROL Scheduling]**&#x200B;按鈕，在上游設定排程。

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

它可讓您將傳送延遲至稍後的日期，或將傳送儲存在臨時日曆中。

* **[!UICONTROL Schedule delivery (no automatic execution)]**&#x200B;選項可讓您排程傳送的臨時分析。

   保存此配置後，傳送狀態將更改為&#x200B;**[!UICONTROL Targeting pending]**。 分析將在指定日期啟動。

* **[!UICONTROL Schedule delivery (automatic execution on planned date)]**&#x200B;選項可讓您指定傳送日期。

   按一下&#x200B;**[!UICONTROL Send]**&#x200B;並選取&#x200B;**[!UICONTROL Postpone delivery]**，然後啟動分析並確認傳送。 分析完成後，傳送目標就緒，訊息會在指定日期自動傳送。

日期和時間以目前運算子的時區表示。 位於連絡人日期輸入欄位下方的&#x200B;**[!UICONTROL Time zone]**&#x200B;下拉式清單可讓您自動將輸入的日期和時間轉換為選取的時區。

例如，如果您排程交貨將在倫敦時間的8點自動執行，則該時間會自動轉換為選定時區：

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## 使用多個波發送{#sending-using-multiple-waves}

要平衡負載，您可以將交貨分成幾批。 配置批數及其相對於整個交貨的比例。

>[!NOTE]
>
>只能定義兩個連續波之間的大小和延遲。 無法配置每個波的接收者選擇標準。

1. 開啟傳送屬性視窗，然後按一下&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤。
1. 選擇&#x200B;**[!UICONTROL Send using multiple waves]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Define waves...]**&#x200B;連結。

   ![](assets/s_ncs_user_wizard_waves.png)

1. 要配置波，您可以執行以下任一操作：

   * 定義每個波的大小。 例如，如果您在對應欄位中輸入&#x200B;**[!UICONTROL 30%]**，則每個訊息會代表傳送中包含的30%訊息，但最後一個訊息除外，後者將代表10%訊息。

      在&#x200B;**[!UICONTROL Period]**&#x200B;欄位中，指定兩個連續波開始之間的延遲。 例如，如果您輸入&#x200B;**[!UICONTROL 2d]**，第一個波會立即開始，第二個波會在兩天後開始，第三個波會在四天後開始，依此類推。

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * 定義傳送每個波浪的日曆。

      在&#x200B;**[!UICONTROL Start]**&#x200B;欄中，指定兩個連續波開始之間的延遲。 在&#x200B;**[!UICONTROL Size]**&#x200B;欄中，輸入固定數字或百分比。

      在以下範例中，第一波代表傳送中包含的訊息總數的25%，並會立即開始。 接下來的兩波將完成傳送，並設為以6小時間隔開始。

      ![](assets/s_ncs_user_wizard_waves_create.png)
   特定的排版規則&#x200B;**[!UICONTROL Wave scheduling check]**&#x200B;可確保最後一波在傳送有效性限制之前就已規劃好。 在傳送屬性的&#x200B;**[!UICONTROL Typology]**&#x200B;標籤中設定的促銷活動類型及其規則，會在[驗證程式中顯示有類型](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)。

   >[!IMPORTANT]
   >
   >請確定最後的波不會超過&#x200B;**[!UICONTROL Validity]**&#x200B;標籤中定義的傳送期限。 否則，可能無法發送某些消息。
   >
   >配置最後一個波時，還必須允許足夠的時間進行重試。 請參閱[本節](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)。

1. 若要監控您的傳送，請前往傳送記錄檔。 請參閱[本頁](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)。

   您可以看到已在處理波中發送的交貨（**[!UICONTROL Sent]**&#x200B;狀態），以及將在剩餘波中發送的交貨（**[!UICONTROL Pending]**&#x200B;狀態）。

以下兩個範例是使用多波時最常見的使用案例。

* **在升級過程中**

   當使用新平台傳送電子郵件時，網際網路服務供應商(ISP)會懷疑無法辨識的IP位址。 如果突然傳送大量電子郵件，ISP通常會將它們標示為垃圾訊息。

   為避免標示為垃圾訊息，您可以逐步增加使用波浪傳送的音量。 這應確保啟動階段的順利開發，並讓您降低無效地址的總體速率。

   若要這麼做，請使用&#x200B;**[!UICONTROL Schedule waves according to a calendar]**&#x200B;選項。 例如，將第一波設為10%，將第二波設為15%，依此類推。

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **涉及客服中心的促銷活動**

   在管理電話忠誠度促銷活動時，您的組織處理聯絡訂閱者來電數的能力有限。

   使用電波，您可將訊息數量限制為每天20個訊息，即呼叫中心的日常處理能力。

   若要這麼做，請選取&#x200B;**[!UICONTROL Schedule multiple waves of the same size]**&#x200B;選項。 在&#x200B;**[!UICONTROL Period]**&#x200B;欄位中輸入&#x200B;**[!UICONTROL 20]**&#x200B;作為波的大小和&#x200B;**[!UICONTROL 1d]**。

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## 配置重試次數{#configuring-retries}

由於&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;錯誤而暫時未傳送的訊息會遭到自動重試。 [部分](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)中列出了交付失敗類型和原因。

>[!IMPORTANT]
>
>對於代管或混合安裝，如果您已升級至[增強的MTA](../../delivery/using/sending-with-enhanced-mta.md)，促銷活動將不再使用傳送中的重試設定。 軟反彈重試次數及其間的時間長度，由增強的MTA根據訊息電子郵件網域傳回的反彈回應類型和嚴重性來決定。

對於使用舊版促銷活動MTA的內部部署安裝和代管／混合安裝，傳送參數的&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤的中央區段會指出在傳送後一天應執行多少次重試，以及兩次重試之間的最小延遲。

![](assets/s_ncs_user_wizard_retry_param.png)

依預設，會在傳送的第一天排程五次重試，最少間隔為一小時，在一天中的24小時內分佈。 每天一次重試的程式設定在此之後，直到交貨期限為止（在&#x200B;**[!UICONTROL Validity]**&#x200B;標籤中定義）（請參閱[定義有效期](#defining-validity-period)）。

## 定義有效期{#defining-validity-period}

當傳送啟動後，訊息（以及任何重試）可傳送至傳送期限。 這會透過&#x200B;**[!UICONTROL Validity]**&#x200B;標籤在傳送屬性中指出。

![](assets/s_ncs_user_email_del_valid_period.png)

* **[!UICONTROL Delivery duration]**&#x200B;欄位可讓您輸入全域傳送重試的限制。 這意味著Adobe Campaign發送從開始日期開始的消息，然後，對於僅返回錯誤的消息，將執行常規的可配置重試，直到達到有效性限制。

   您也可以選擇指定日期。 要執行此操作，請選擇&#x200B;**[!UICONTROL Explicitly set validity dates]**。 在此情況下，傳送和有效性限制日期也可讓您指定時間。 目前時間預設會使用，但您可以直接在輸入欄位中修改。

   >[!IMPORTANT]
   >
   >對於代管或混合安裝，如果您已升級至[增強的MTA](../../delivery/using/sending-with-enhanced-mta.md)，則只有在設為&#x200B;**3.5天或更短的**&#x200B;時，才會使用促銷活動電子郵件傳送中的&#x200B;**[!UICONTROL Delivery duration]**&#x200B;設定。  如果您定義的值超過　3.5　天，則不會考慮該值。

* **資源的有效性限制**:此欄 **[!UICONTROL Validity limit]** 位用於上傳的資源，主要用於鏡像頁面和影像。本頁上的資源在限定時間內有效（以節省磁碟空間）。

   此欄位中的值可以用[本節](../../platform/using/adobe-campaign-workspace.md#default-units)中列出的單位表示。
