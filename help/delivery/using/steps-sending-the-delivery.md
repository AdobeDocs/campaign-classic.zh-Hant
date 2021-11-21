---
product: campaign
title: 設定和傳送傳遞
description: 設定和傳送傳遞
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1521'
ht-degree: 5%

---

# 設定和傳送傳遞 {#configuring-and-sending-the-delivery}

![](../../assets/common.svg)

>[!NOTE]
>
>只有傳送擁有者才能開始傳送。 為了讓其他運算子（或運算子群組）能夠開始傳送，您必須在 **[!UICONTROL Delivery start:]** 欄位。 有關詳細資訊，請參閱 [本節](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## 傳送其他參數 {#delivery-additiona-parameters}

在傳送傳送之前，您可以透過 **[!UICONTROL Delivery]** 標籤。

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**:此選項可讓您指出傳送的優先順序等級（一般、高或低），以影響傳送的傳送順序。 這可讓您排定特定、更緊急傳送的訂單優先順序，而非其他傳送。

* **[!UICONTROL Message batch quantity]**:此選項可讓您定義在相同XML傳送套件中分組的訊息數。 如果參數設為0，則會自動將訊息分組。 包大小由計算定義 `<delivery size>/1024`，每個封裝至少8封，最多256封訊息。

   >[!IMPORTANT]
   >
   >傳送重複時，參數會重設。

* **[!UICONTROL Send using multiple waves]**:有關詳細資訊，請參閱 [使用多波次傳送](#sending-using-multiple-waves).

* **[!UICONTROL Test SMTP delivery]**:此選項可讓您測試透過SMTP傳送的傳送。 會處理傳送，直到連線至SMTP伺服器為止，但不會傳送。

   >[!NOTE]
   >
   >安裝使用中間來源時不建議使用此選項，以免呼叫mta。 有關配置SMTP伺服器的詳細資訊，請參閱 [到本節](../../installation/using/configure-delivery-settings.md).

* **[!UICONTROL Email BCC]**:此選項可讓您透過密件副本將密件副本電子郵件地址新增至訊息目標，借此將電子郵件儲存在外部系統上。 如需詳細資訊，請參閱[本章節](sending-messages.md#archiving-emails)。

## 確認傳送 {#confirming-delivery}

當已設定傳送並準備好傳送時，請確定您已執行傳送分析。

要執行此操作，請按一下 **[!UICONTROL Send]**，請選取所需的動作，然後按一下 **[!UICONTROL Analyze]**. 有關詳細資訊，請參閱 [啟動分析](steps-validating-the-delivery.md#analyzing-the-delivery).

![](assets/s_ncs_user_email_del_send.png)

完成後，按一下 **[!UICONTROL Confirm delivery]** 啟動訊息傳送。

然後，您可以關閉傳送精靈，並從 **[!UICONTROL Delivery]** 索引標籤，可透過此傳送的詳細資訊或傳送清單存取。

傳送訊息後，您可以監控及追蹤您的傳送。 如需詳細資訊，請參閱下列區段。

* [監視傳遞](about-delivery-monitoring.md)
* [瞭解傳遞故障](understanding-delivery-failures.md)
* [關於訊息追蹤](about-message-tracking.md)

## 排程傳送傳送 {#scheduling-the-delivery-sending}

為了排程傳遞，管理銷售壓力以及避免過度行銷，您可以推延郵件的傳遞。

1. 按一下 **[!UICONTROL Send]** 按鈕並選取 **[!UICONTROL Postpone delivery]** 選項。

1. 在 **[!UICONTROL Contact date]** 欄位。

![](assets/dlv_email_del_plan.png)

1. 接著，您可以開始傳送分析，然後確認傳送。 不過，傳送要等到 **[!UICONTROL Contact date]** 欄位。

>[!IMPORTANT]
>
>開始分析後，您定義的聯絡日期即會固定。 如果您修改此日期，則必須重新啟動分析，以便將您的修改納入考量。

![](assets/s_ncs_user_email_del_start_delayed.png)

在傳送清單中，傳送會以顯示 **[!UICONTROL Pending]** 狀態。

![](assets/s_ncs_user_email_del_waiting.png)

您也可以透過 **[!UICONTROL Scheduling]** 按鈕。

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

它可讓您將傳送延遲至較晚的日期，或在臨時日曆中儲存傳送。

* 此 **[!UICONTROL Schedule delivery (no automatic execution)]** 選項可讓您排程傳送的臨時分析。

   儲存此設定時，傳送會變更為 **[!UICONTROL Targeting pending]** 狀態。 分析將在指定日期啟動。

* 此 **[!UICONTROL Schedule delivery (automatic execution on planned date)]** 選項可讓您指定傳送日期。

   按一下 **[!UICONTROL Send]** 選取 **[!UICONTROL Postpone delivery]** 然後啟動分析並確認傳送。 分析完成時，傳遞目標已就緒，訊息將在指定日期自動傳送。

日期和時間會以目前運算子的時區表示。 此 **[!UICONTROL Time zone]** 位於「聯繫人日期輸入」欄位下方的下拉式清單，可讓您自動將輸入的日期和時間轉換為選取的時區。

例如，如果您排程在倫敦時間8點自動執行傳送，則該時間會自動轉換為選取的時區：

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## 使用多波次傳送 {#sending-using-multiple-waves}

若要平衡負載，您可以將傳送分為數個批次。 配置批的數量及其相對於整個交貨的比例。

>[!NOTE]
>
>只能定義兩個連續波之間的大小和延遲。 無法配置每個波次的接收者選擇標準。

1. 開啟傳送屬性視窗，然後按一下 **[!UICONTROL Delivery]** 標籤。
1. 選取 **[!UICONTROL Send using multiple waves]** ，然後按一下 **[!UICONTROL Define waves...]** 連結。

   ![](assets/s_ncs_user_wizard_waves.png)

1. 要配置波，可以執行以下任一操作：

   * 定義每個波的大小。 例如，若您輸入 **[!UICONTROL 30%]** 在對應欄位中，每個波次將代表傳送中包含之訊息的30%，最後一個波次則代表訊息的10%。

      在 **[!UICONTROL Period]** 欄位，指定兩個連續波開始之間的延遲。 例如，若您輸入 **[!UICONTROL 2d]**，第一波會立即開始，第二波會在兩天後開始，第三波會在四天後開始，以此類推。

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * 定義傳送每個波次的日曆。

      在 **[!UICONTROL Start]** 欄，指定兩個連續波開始之間的延遲。 在 **[!UICONTROL Size]** 欄，輸入固定數字或百分比。

      在以下範例中，第一波代表傳送中包含且將立即開始的訊息總數的25%。 接下來的兩個波段會完成傳送，並設為以6小時間隔開始。

      ![](assets/s_ncs_user_wizard_waves_create.png)
   特定的類型規則， **[!UICONTROL Wave scheduling check]**，可確保在傳送有效期限之前已規劃最後一波。 在 **[!UICONTROL Typology]** 的索引標籤，顯示在 [使用類型驗證程式](steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >請確定最後的批次不會超過傳送期限，此期限定義於 **[!UICONTROL Validity]** 標籤。 否則，某些訊息可能無法傳送。
   >
   >配置最後一波時，您也必須有足夠的時間重試。 請參閱[本節](steps-sending-the-delivery.md#configuring-retries)。

1. 若要監控您的傳送，請前往傳送記錄檔。 請參閱[此頁面](delivery-dashboard.md#delivery-logs-and-history)。

   您可以看到已在處理波次中傳送的傳送(**[!UICONTROL Sent]** 狀態)和要在其餘波段中傳送的傳送(**[!UICONTROL Pending]** 狀態)。

以下兩個範例是使用多波時最常用的使用案例。

* **在上升過程中**

   使用新平台傳送電子郵件時，網際網路服務提供者(ISP)會懷疑無法辨識的IP位址。 如果突然發送了大量電子郵件，ISP通常會將它們標籤為垃圾郵件。

   為避免標籤為垃圾郵件，您可以逐步增加使用批次傳送的數量。 這應確保啟動階段的順利開發，並讓您降低無效地址的總體速率。

   若要這麼做，請使用 **[!UICONTROL Schedule waves according to a calendar]** 選項。 例如，將第一波設為10%、將第二波設為15%，依此類推。

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **與客服中心相關的行銷活動**

   管理電話忠誠度促銷活動時，您的組織處理聯絡訂閱者之呼叫數的能力有限。

   使用波次，您可以將訊息的數量限制為每天20個，即呼叫中心的每日處理能力。

   若要這麼做，請選取 **[!UICONTROL Schedule multiple waves of the same size]** 選項。 輸入 **[!UICONTROL 20]** 波的大小和 **[!UICONTROL 1d]** 在 **[!UICONTROL Period]** 欄位。

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## 配置重試 {#configuring-retries}

由於 **軟** 或 **已忽略** 錯誤可能會自動重試。 傳遞失敗類型和原因如下 [節](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>若為托管或混合安裝，若您已升級至 [增強的MTA](sending-with-enhanced-mta.md),Campaign不再使用傳送中的重試設定。 軟退信重試次數及兩者之間的時間長度，由Enhanced MTA根據來自訊息電子郵件網域傳回之退信的類型和嚴重性決定。

若為內部部署安裝，以及使用舊版Campaign MTA的托管/混合安裝，位於 **[!UICONTROL Delivery]** 索引標籤（傳送參數）指出在傳送後一天應執行多少次重試，以及兩次重試之間的最小延遲。

![](assets/s_ncs_user_wizard_retry_param.png)

依預設，會為傳送的第一天排程五次重試，最小間隔為一小時，分散於一天的24小時內。 在此之後，每天會編寫一次重試程式，直到傳送截止日期(定義於 **[!UICONTROL Validity]** 標籤(請參閱 [定義有效期](#defining-validity-period))。

## 定義有效期 {#defining-validity-period}

傳送啟動後，可以傳送訊息（和任何重試），直到傳送截止時間為止。 這會透過 **[!UICONTROL Validity]** 標籤。

![](assets/s_ncs_user_email_del_valid_period.png)

* 此 **[!UICONTROL Delivery duration]** 欄位可讓您輸入全域傳送重試的限制。 這表示Adobe Campaign會傳送從開始日期開始的訊息，然後，對於僅傳回錯誤的訊息，會執行一般、可設定的重試，直到達到有效性限制為止。

   您也可以選擇指定日期。 要執行此操作，請選取 **[!UICONTROL Explicitly set validity dates]**. 在此情況下，傳送和有效性限制日期也可讓您指定時間。 預設會使用目前時間，但您可以直接在輸入欄位中修改。

   >[!IMPORTANT]
   >
   >若為托管或混合安裝，若您已升級至 [增強的MTA](sending-with-enhanced-mta.md), **[!UICONTROL Delivery duration]** 設定(只有在設為 **3.5天或更少**.  如果您定義的值超過　3.5　天，則不會考慮該值。

* **資源的有效性限制**:此 **[!UICONTROL Validity limit]** 欄位是用於上傳的資源，主要用於鏡像頁面和影像。 本頁上的資源在限定時間內有效（以節省磁碟空間）。

   此欄位中的值可以以 [本節](../../platform/using/adobe-campaign-workspace.md#default-units).
