---
product: campaign
title: 關於傳遞設定
description: 探索特定的v7傳遞設定
feature: Channel Configuration
role: User
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 12%

---

# 傳遞設定 {#about-delivery-settings}

以下設定專屬於Campaign Classic。 如需其他傳遞設定，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html){target="_blank"}。

## 傳遞分析 {#delivery-analysis}

### 改善傳遞分析效能 {#improving-delivery-analysis}

若要加速傳遞準備，您可以在啟動分析之前核取&#x200B;**[!UICONTROL Prepare the delivery parts in the database]**&#x200B;選項。

啟用此選項時，會直接在資料庫中執行傳遞準備，大幅加快分析。

目前，此選項只有在符合下列條件時才可用：

* 傳遞必須是電子郵件。 目前不支援其他管道。
* 您不得使用中間來源或外部路由，只能使用大量傳遞路由型別。 您可以檢查&#x200B;**[!UICONTROL Delivery properties]**&#x200B;之&#x200B;**[!UICONTROL General]**&#x200B;索引標籤中使用的路由。
* 您無法鎖定來自外部檔案的母體。 若為單一傳遞，請從&#x200B;**[!UICONTROL Email parameters]**&#x200B;按一下&#x200B;**[!UICONTROL To]**&#x200B;連結，並檢查是否已選取&#x200B;**[!UICONTROL Defined in the database]**&#x200B;選項。 針對工作流程中使用的傳遞，檢查收件者在&#x200B;**[!UICONTROL Delivery]**&#x200B;索引標籤中是否為&#x200B;**[!UICONTROL Specified by the inbound event(s)]**。
* 您必須使用PostgreSQL資料庫。

### 設定分析優先順序 {#analysis-priority-}

當傳遞為行銷活動的一部分時，**[!UICONTROL Advanced]**&#x200B;索引標籤會提供其他選項。 這可讓您在相同行銷活動中組織傳送的處理順序。

傳送前，會分析每個傳遞。 分析持續時間取決於傳遞擷取檔案。 檔案大小愈大，分析所需的時間愈長，下列傳送作業就會等待一段時間。

**[!UICONTROL Message preparation by the scheduler]**&#x200B;的選項可讓您在行銷活動工作流程中排定傳遞分析的優先順序。

![](assets/delivery_analysis_priority.png)

如果傳送過大，最好將低優先順序指派給它，以避免減慢分析其他工作流程傳送的速度。

>[!NOTE]
>
>若要確保較大的傳遞分析不會減慢工作流程的進度，您可以按一下&#x200B;**[!UICONTROL Schedule execution for a time of low activity]**&#x200B;以排程其執行。

## 傳遞傳送 {#delivery-sending}

### 設定重試 {#configuring-retries}

因為&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;錯誤而暫時未傳遞的郵件可能會自動重試。 傳送失敗型別和原因顯示於此[區段](understanding-delivery-failures.md#delivery-failure-types-and-reasons)。

>[!IMPORTANT]
>
>對於託管或混合式安裝，如果您已升級至[Enhanced MTA](sending-with-enhanced-mta.md)，Campaign將不再使用傳送中的重試設定。 軟退信重試次數和兩次之間的時間長度由Enhanced MTA根據從訊息的電子郵件網域傳回的退信回應的型別和嚴重性來決定。

對於使用舊版Campaign MTA的內部部署安裝和託管/混合安裝，傳送引數的&#x200B;**[!UICONTROL Delivery]**&#x200B;索引標籤的中央區段會指出在傳送後一天應執行多少次重試，以及重試之間的最小延遲。

![](assets/s_ncs_user_wizard_retry_param.png)

根據預設，排程在傳送的第一天進行五次重試，最小間隔為一小時分佈在一天中的24小時。 之後及傳遞期限（在&#x200B;**[!UICONTROL Validity]**&#x200B;索引標籤中定義）之前，每天會設定一次重試。 請參閱[定義有效期間](#defining-validity-period)。

### 定義有效期間 {#defining-validity-period}

當傳送已啟動時，可傳送訊息（以及任何重試），直到傳送期限為止。 透過&#x200B;**[!UICONTROL Validity]**&#x200B;索引標籤在傳遞屬性中指出這點。

![](assets/s_ncs_user_email_del_valid_period.png)

* **[!UICONTROL Delivery duration]**&#x200B;欄位可讓您輸入全域傳遞重試的限制。 這表示 Adobe Campaign 會傳送從開始日期開始的訊息，然後，對於僅傳回錯誤的訊息，會執行一般、可設定的重試，直到達到效度限制為止。

  您也可以選擇指定日期。若要這麼做，請選取&#x200B;**[!UICONTROL Explicitly set validity dates]**。 在此情況下，傳遞和有效期限制日期也讓您指定時間。預設使用目前時間，但您可以直接在輸入欄位中修改。

  >[!IMPORTANT]
  >
  >針對託管或混合式安裝，如果您已升級至[Enhanced MTA](sending-with-enhanced-mta.md)，則只有在設為&#x200B;**3.5天或更短時間時，才會使用Campaign電子郵件傳遞中的&#x200B;**[!UICONTROL Delivery duration]**設定**。 如果您定義的值超過3.5天，則不會考慮該值。

* **資源效度限制**： **[!UICONTROL Validity limit]**&#x200B;欄位是用於上傳的資源，主要用於映象頁面和影像。 本頁上的資源在限定時間內有效（以節省磁碟空間）。

  此欄位中的值可以以[此區段](../../platform/using/adobe-campaign-workspace.md#default-units)中列出的單位來表示。
