---
product: campaign
title: 設定並傳送傳遞
description: 瞭解如何設定並傳送傳遞
feature: Channel Configuration
role: User
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: 41296a0acaee93d31874bf58287e51085c6c1261
workflow-type: tm+mt
source-wordcount: '1517'
ht-degree: 11%

---

# 設定並傳送傳遞 {#configuring-and-sending-the-delivery}

## 權限{#delivery-permissions}

只有傳遞擁有者可以開始傳遞。 若要讓其他操作員（或操作員群組）能夠開始傳遞，請在&#x200B;**[!UICONTROL Delivery start:]**&#x200B;欄位中將他們新增為稽核者。 [了解更多](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers)。

## 傳遞其他引數 {#delivery-additiona-parameters}

在傳送傳遞之前，您可以透過&#x200B;**[!UICONTROL Delivery]**&#x200B;索引標籤，在傳遞屬性中定義傳送引數。

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**：使用此選項可設定優先順序等級，以變更您傳送的傳送順序：正常、高或低。

* **[!UICONTROL Message batch quantity]**：使用此選項可定義在同一XML傳遞套件中分組的訊息數目。 如果引數設為0，訊息會自動分組。 封裝大小由計算`<delivery size>/1024`定義，每個封裝至少有8個和256個訊息。

  >[!IMPORTANT]
  >
  >當透過複製現有傳遞建立傳遞時，此引數會重設。

* **[!UICONTROL Send using multiple waves]**：使用此選項可分批傳送訊息，而非一次傳送給整個對象。 [了解更多](#sending-using-multiple-waves)。

* **[!UICONTROL Test SMTP delivery]**：使用此選項來測試透過SMTP的傳送。 處理傳遞直到連線到 SMTP 伺服器，但不傳送：對於傳遞的每個收件者，Campaign 會連線到 SMTP 提供者伺服器，執行 SMTP RCPT TO 命令，並在 SMTP DATA 命令之前關閉連線。

  >[!NOTE]
  >
  >* 此選項不得在中間來源中設定。
  >
  >* 在[本節](../../installation/using/configure-delivery-settings.md)中進一步瞭解SMTP伺服器組態。

* **[!UICONTROL Email BCC]**：使用此選項，只要將密件副本電子郵件地址新增至您的訊息目標，即可透過密件副本在外部系統上儲存電子郵件。 [了解更多](sending-messages.md#archiving-emails)。

## 確認傳遞 {#confirming-delivery}

當傳送已設定好並準備好傳送時，請執行傳送分析。

若要這麼做，請按一下&#x200B;**[!UICONTROL Send]**，選取所需的動作，然後按一下&#x200B;**[!UICONTROL Analyze]**。 [了解更多](steps-validating-the-delivery.md#analyzing-the-delivery)。

![](assets/s_ncs_user_email_del_send.png)

完成後，按一下&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;以啟動訊息的傳遞。

然後，您可以關閉傳遞助理員並從&#x200B;**[!UICONTROL Delivery]**&#x200B;索引標籤追蹤傳遞的執行情形，可透過此傳遞的詳細資訊或傳遞清單存取。

傳送訊息後，您可以監視和追蹤您的傳遞。 如需詳細資訊，請參閱下列區段。

* [監視傳遞](about-delivery-monitoring.md)
* [瞭解傳遞失敗](understanding-delivery-failures.md)
* [關於訊息追蹤](about-message-tracking.md)

## 排程傳遞傳送 {#scheduling-the-delivery-sending}

您可以排程傳遞，以延遲訊息傳送。

1. 按一下&#x200B;**[!UICONTROL Send]**&#x200B;按鈕並選取&#x200B;**[!UICONTROL Postpone delivery]**&#x200B;選項。

1. 在&#x200B;**[!UICONTROL Contact date]**&#x200B;欄位中指定開始日期。

![](assets/dlv_email_del_plan.png)

1. 然後，您可以開始傳遞分析，然後確認傳遞傳送。 但是，要到&#x200B;**[!UICONTROL Contact date]**&#x200B;欄位中指定的日期才會開始傳送傳遞。

>[!IMPORTANT]
>
>開始分析後，您定義的聯絡日期即已固定。 如果您修改此日期，則必須重新啟動分析，以便將您的修改納入考量。

![](assets/s_ncs_user_email_del_start_delayed.png)

在傳遞清單中，傳遞將以&#x200B;**[!UICONTROL Pending]**&#x200B;狀態顯示。

![](assets/s_ncs_user_email_del_waiting.png)

您也可以透過傳遞的&#x200B;**[!UICONTROL Scheduling]**&#x200B;按鈕設定上游。

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

這可讓您將傳送延遲到較晚日期，或將傳送儲存在臨時行事曆中。

* **[!UICONTROL Schedule delivery (no automatic execution)]**&#x200B;選項可讓您排程傳遞的臨時分析。

  儲存此設定時，傳遞會變更為&#x200B;**[!UICONTROL Targeting pending]**&#x200B;狀態。 分析將會在指定的日期啟動。

* **[!UICONTROL Schedule delivery (automatic execution on planned date)]**&#x200B;選項可讓您指定傳送日期。

  按一下&#x200B;**[!UICONTROL Send]**&#x200B;並選取&#x200B;**[!UICONTROL Postpone delivery]**，然後啟動分析並確認傳遞。 分析完成後，傳遞目標已準備就緒，訊息將於指定日期自動傳送。

日期和時間會以目前運運算元的時區表示。 位於連絡人日期輸入欄位下方的&#x200B;**[!UICONTROL Time zone]**&#x200B;下拉式清單可讓您自動將輸入的日期和時間轉換為選取的時區。

例如，如果您排程在倫敦時間8點自動執行傳遞，則時間會自動轉換為所選的時區：

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## 使用多個波段傳送 {#sending-using-multiple-waves}

若要平衡負載，您可以將傳送劃分為幾個批次。 設定批次數量及其相對於整個傳送的比例。

>[!NOTE]
>
>您只能定義兩個連續波段之間的大小和延遲。 無法設定每個波次的收件者選取條件。

1. 開啟傳遞屬性視窗，然後按一下&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤。
1. 選取&#x200B;**[!UICONTROL Send using multiple waves]**&#x200B;選項並按一下&#x200B;**[!UICONTROL Define waves...]**&#x200B;連結。

   ![](assets/s_ncs_user_wizard_waves.png)

1. 若要設定波段，您可以：

   * 定義每個波段的大小。 例如，如果您在對應欄位中輸入&#x200B;**[!UICONTROL 30%]**，則每個波段將代表傳遞中所包含訊息的30%，惟最後一個波段除外，後者將代表訊息的10%。

     在&#x200B;**[!UICONTROL Period]**&#x200B;欄位中，指定兩個連續波段開始之間的延遲。 例如，如果您輸入&#x200B;**[!UICONTROL 2d]**，第一個波段會立即開始，第二個波段會在兩天內開始，第三個波段會在四天內開始，依此類推。

     ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * 定義傳送每個波次的行事曆。

     在&#x200B;**[!UICONTROL Start]**&#x200B;欄中，指定兩個連續波段開始之間的延遲。 在&#x200B;**[!UICONTROL Size]**&#x200B;欄中輸入固定數字或百分比。

     在以下範例中，第一個波段代表傳遞中包含之訊息總數的25%，並會立即開始。 接下來的兩個批次會完成傳遞，並設定為每六小時開始一次。

     ![](assets/s_ncs_user_wizard_waves_create.png)

   特定型別規則&#x200B;**[!UICONTROL Wave scheduling check]**&#x200B;可確保最後一個波段是在傳遞有效性限制之前計畫。 在傳遞屬性的&#x200B;**[!UICONTROL Typology]**&#x200B;索引標籤中設定的行銷活動型別及其規則，會顯示在具有型別的[驗證程式中](steps-validating-the-delivery.md#validation-process-with-typologies)。

   >[!IMPORTANT]
   >
   >請確定最後一個批次沒有超過在&#x200B;**[!UICONTROL Validity]**&#x200B;索引標籤中定義的傳送期限。 否則，部分訊息可能不會傳送。
   >
   >在設定最後一個波段時，您也必須允許足夠的重試時間。 請參閱[本節](steps-sending-the-delivery.md#configuring-retries)。

1. 若要監視您的傳送，請前往傳送記錄檔。 請參閱[此頁面](delivery-dashboard.md#delivery-logs-and-history)。

   您可以看到已在已處理波段（**[!UICONTROL Sent]**&#x200B;狀態）中傳送的傳遞，以及將在剩餘波段（**[!UICONTROL Pending]**&#x200B;狀態）中傳送的傳遞。

以下兩個範例是使用多個波段的最常見使用案例。

* **在啟動程式期間**

  使用新平台傳送電子郵件時，網際網路服務提供者(ISP)會懷疑無法辨識的IP位址。 如果突然傳送大量電子郵件，ISP通常會將其標籤為垃圾郵件。

  為避免被標籤為垃圾訊息，您可以逐步增加使用波段傳送的數量。 這應該可以確保啟動階段的順利發展，並且讓您降低無效的位址的整體比率。

  若要這麼做，請使用&#x200B;**[!UICONTROL Schedule waves according to a calendar]**&#x200B;選項。 例如，將第一個波段設為10%，將第二個波段設為15%，以此類推。

  ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **與客服中心有關的行銷活動**

  透過電話管理忠誠度行銷活動時，貴組織處理聯絡訂閱者之通話次數的能力有限。

  使用波段時，您可以將訊息數量限製為每天20則，例如考量客服中心的每日處理能力。

  若要這麼做，請選取&#x200B;**[!UICONTROL Schedule multiple waves of the same size]**&#x200B;選項。 輸入&#x200B;**[!UICONTROL 20]**&#x200B;作為波段大小，並在&#x200B;**[!UICONTROL Period]**&#x200B;欄位中輸入&#x200B;**[!UICONTROL 1d]**。

  ![](assets/s_ncs_user_wizard_waves_call_center.png)

## 設定重試 {#configuring-retries}

因為&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;錯誤而暫時未傳遞的郵件可能會自動重試。 傳送失敗型別和原因顯示於此[區段](understanding-delivery-failures.md#delivery-failure-types-and-reasons)。

>[!IMPORTANT]
>
>對於託管或混合式安裝，如果您已升級至[Enhanced MTA](sending-with-enhanced-mta.md)，Campaign將不再使用傳送中的重試設定。 軟退信重試次數和兩次之間的時間長度由Enhanced MTA根據從訊息的電子郵件網域傳回的退信回應的型別和嚴重性來決定。

對於使用舊版Campaign MTA的內部部署安裝和託管/混合安裝，傳送引數的&#x200B;**[!UICONTROL Delivery]**&#x200B;索引標籤的中央區段會指出在傳送後一天應執行多少次重試，以及重試之間的最小延遲。

![](assets/s_ncs_user_wizard_retry_param.png)

根據預設，排程在傳送的第一天進行五次重試，最小間隔為一小時分佈在一天中的24小時。 之後及傳遞期限（在&#x200B;**[!UICONTROL Validity]**&#x200B;索引標籤中定義）之前，每天會設定一次重試。 請參閱[定義有效期間](#defining-validity-period)。

## 定義有效期間 {#defining-validity-period}

當傳送已啟動時，可傳送訊息（以及任何重試），直到傳送期限為止。 透過&#x200B;**[!UICONTROL Validity]**&#x200B;索引標籤在傳遞屬性中指出這點。

![](assets/s_ncs_user_email_del_valid_period.png)

* **[!UICONTROL Delivery duration]**&#x200B;欄位可讓您輸入全域傳遞重試的限制。 這表示 Adobe Campaign 會傳送從開始日期開始的訊息，然後，對於僅傳回錯誤的訊息，會執行一般、可設定的重試，直到達到效度限制為止。

  您也可以選擇指定日期。若要這麼做，請選取&#x200B;**[!UICONTROL Explicitly set validity dates]**。 在此情況下，傳遞和有效期限制日期也讓您指定時間。預設使用目前時間，但您可以直接在輸入欄位中修改。

  >[!IMPORTANT]
  >
  >針對託管或混合式安裝，如果您已升級至[Enhanced MTA](sending-with-enhanced-mta.md)，則只有在設為&#x200B;**3.5天或更短時間時，才會使用Campaign電子郵件傳遞中的&#x200B;**&#x200B;[!UICONTROL Delivery duration]&#x200B;**設定**。 如果您定義的值超過3.5天，則不會考慮該值。

* **資源效度限制**： **[!UICONTROL Validity limit]**&#x200B;欄位是用於上傳的資源，主要用於映象頁面和影像。 本頁上的資源在限定時間內有效（以節省磁碟空間）。

  此欄位中的值可以以[此區段](../../platform/using/adobe-campaign-workspace.md#default-units)中列出的單位來表示。
