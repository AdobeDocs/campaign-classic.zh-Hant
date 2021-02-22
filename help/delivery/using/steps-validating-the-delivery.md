---
solution: Campaign Classic
product: campaign
title: 驗證傳遞
description: 驗證傳遞
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '1667'
ht-degree: 5%

---


# 驗證傳遞 {#validating-the-delivery}

建立並設定傳送後，您必須先驗證傳送，才能將它傳送至主要目標。

操作步驟：

1. **分析傳送**:此步驟可讓您準備要傳送的訊息。請參閱[分析傳送](#analyzing-the-delivery)。

   分析期間套用的規則顯示在[本節](#validation-process-with-typologies)中。 [更改批准模式](#changing-the-approval-mode)部分中詳細介紹了可用的驗證模式。

1. **傳送校樣**:此步驟可讓您核准內容、URL、個人化欄位等。請參閱[發送證明](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)和[定義特定證明目標](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)。

>[!IMPORTANT]
>
>這兩個步驟都必須在對訊息內容進行每次修改後執行。

## 分析傳送{#analyzing-the-delivery}

分析是計算目標人口並準備交付內容的階段。 完成後，即可傳送。

### 啟動分析{#launching-the-analysis}

1. 若要啟動傳送分析，請按一下&#x200B;**[!UICONTROL Send]**。
1. 選取 **[!UICONTROL Deliver as soon as possible]**。

   ![](assets/s_ncs_user_email_del_send.png)

1. 按一下&#x200B;**[!UICONTROL Analyze]**&#x200B;以手動啟動分析。

   進度列顯示分析的進度。

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >分析期間使用的驗證規則在[含類型的驗證流程](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)一節中有說明。

1. 您可以隨時按一下&#x200B;**[!UICONTROL Stop]**&#x200B;來停止分析。

   ![](assets/s_ncs_user_wizard_email01_16.png)

   在準備階段不會傳送任何訊息。 因此，您可以啟動或取消分析，而不會有風險。

   >[!IMPORTANT]
   >
   >執行時，分析會凍結傳送（或證明）。 交付（或證明）的任何變更必須先進行其他分析，才能生效。

1. 等待分析完成。

   分析完成後，窗口的上部區域將指示交貨準備是否完成或是否發生任何錯誤。 列出所有驗證步驟、警告和錯誤。 彩色表徵圖顯示消息類型：
   * 藍色圖示表示資訊性訊息。
   * 黃色表徵圖表示非嚴重處理錯誤。
   * 紅色圖示表示無法傳送傳送的重大錯誤。

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. 按一下&#x200B;**[!UICONTROL Close]**&#x200B;以更正錯誤（如果有）。

1. 進行更改後，按一下&#x200B;**[!UICONTROL Analyze]**&#x200B;重新啟動分析。

檢查分析結果後，您可以按一下&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;將消息發送到指定的目標。 確認訊息可讓您啟動傳送。

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>如果要發送的消息數與您的配置不匹配，請按一下&#x200B;**[!UICONTROL Change the main delivery target]**&#x200B;連結。 這可讓您變更目標人口的定義，並重新開始分析。

### 分析參數{#analysis-parameters}

傳送屬性的&#x200B;**[!UICONTROL Analysis]**&#x200B;標籤可讓您定義分析階段中訊息準備的相關資訊集。

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

此標籤可存取下列選項：

* **[!UICONTROL Label and code of the delivery]** :本節中的選項用於計算傳送分析階段中這些欄位的值。**[!UICONTROL Compute the execution folder during the delivery analysis]**&#x200B;欄位會計算在分析階段中將包含此傳送動作的資料夾名稱。
* **[!UICONTROL Approval mode]** :此欄位可讓您定義分析完成後的人工或自動傳送。驗證模式在[更改批准模式](#changing-the-approval-mode)部分中顯示。
* **[!UICONTROL Prepare the delivery parts in the database]** :此選項可讓您改善傳送分析效能。如需詳細資訊，請參閱[本節](#improving-delivery-analysis)。
* **[!UICONTROL Prepare the personalization data with a workflow]** :此選項可讓您在自動工作流程中準備傳送時所包含的個人化資料，如此可大幅提升執行個人化的效能。如需詳細資訊，請參閱[最佳化個人化](../../delivery/using/personalization-fields.md#optimizing-personalization)。
* **[!UICONTROL Start job in a detached process]** :此選項可讓您在個別程式中啟動傳送分析。分析功能依預設會使用Adobe Campaign應用程式伺服器程式(web nlserver)。 選取此選項，即使在應用程式伺服器發生故障時，您也能確保分析完成。
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** :此選項在分析階段將SQL查詢日誌添加到傳送日誌。
* **[!UICONTROL Ignore personalization scripts during sending]** :此選項可讓您略過HTML內容中的JavaScript指令解譯。它們會如同傳送的內容一樣顯示。 這些指令是隨&#x200B;**&lt;%=**&#x200B;標籤引入的。

### 改善傳送分析效能{#improving-delivery-analysis}

要加快交付準備，可以在啟動分析之前檢查&#x200B;**[!UICONTROL Prepare the delivery parts in the database]**&#x200B;選項。

啟用此選項後，將直接在資料庫內執行交付準備，這樣可以顯著加快分析。

目前，此選項僅在符合下列條件時才可用：
* 傳送內容必須是電子郵件。 目前不支援其他頻道。
* 您不得使用中間來源補充或外部工藝路線，只能使用批量交貨工藝路線類型。 您可以檢查&#x200B;**[!UICONTROL Delivery properties]**&#x200B;的&#x200B;**[!UICONTROL General]**&#x200B;標籤中使用的路由。
* 您無法定位來自外部檔案的人口。 對於單次傳送，按一下&#x200B;**[!UICONTROL Email parameters]**&#x200B;中的&#x200B;**[!UICONTROL To]**&#x200B;連結，並檢查&#x200B;**[!UICONTROL Defined in the database]**&#x200B;選項是否已選中。 對於工作流中使用的傳送，請在&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤中檢查收件者是否為&#x200B;**[!UICONTROL Specified by the inbound event(s)]**。
* 您必須使用PostgreSQL資料庫。

### 配置分析優先順序{#analysis-priority-}

當傳送是促銷活動的一部分時，**[!UICONTROL Advanced]**&#x200B;標籤會提供其他選項。 這可讓您組織相同促銷活動中傳送的處理順序。

在傳送前，會分析每個傳送。 分析持續時間取決於傳送擷取檔案。 檔案大小愈大，分析所需時間愈長，就會等候下列傳送。

**[!UICONTROL Message preparation by the scheduler]**&#x200B;的選項可讓您在促銷活動工作流程中排定傳送分析的優先順序。

![](assets/delivery_analysis_priority.png)

如果傳送量過大，最好指定低優先順序給它，以免拖慢其他工作流程傳送的分析速度。

>[!NOTE]
>
>為確保較大的傳送分析不會拖慢工作流程的進度，您可以透過&#x200B;**[!UICONTROL Schedule execution for a time of low activity]**&#x200B;嘀嗒作響來排程執行。

## 傳送校樣 {#sending-a-proof}

若要檢測訊息設定中可能出現的錯誤，Adobe 強烈建議您配置傳遞驗證階段。要經常性地透過傳送驗證訊息測試收件者，確保核准內容。每次進行變更時都必須傳送驗證訊息，以核准內容。

>[!NOTE]
>
>* [更改批准模式](../../delivery/using/steps-validating-the-delivery.md#changing-the-approval-mode)中詳細說明了可用的驗證模式。
>* [定義特定校對目標](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)中說明了校對目標的配置。
>



若要傳送證明，請遵循下列步驟：

1. 請確定已按照[定義特定校對目標](../../delivery/using/steps-defining-the-target-population.md#defining-a-specific-proof-target)中的說明配置了校對目標。
1. 按一下傳送精靈頂端列上的&#x200B;**[!UICONTROL Send a proof]**。

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. 啟動消息分析。 請參閱[分析傳送](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。
1. 您現在可以傳送傳送（請參閱[傳送傳送](../../delivery/using/steps-sending-the-delivery.md)）。

   傳送後，證明會出現在傳送清單中，並自動建立及編號。 如果您想要存取其內容和屬性，則可加以編輯。 如需關於此項目的詳細資訊，請參閱此[頁面](../../delivery/using/about-delivery-monitoring.md)。

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >如果為傳送（HTML和文字）建立了數種格式，您可以選擇要傳送至視窗下方校樣收件者的訊息格式。

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

您可能希望修改傳送內容，因為驗證群組收到證明時所做的任何註解。 進行變更後，您必須重新啟動分析，然後傳送其他證明。 每個新校樣都會編號並記錄在傳送日誌中。

分析傳送後，您可以檢視透過記錄檔的&#x200B;**[!UICONTROL Proofs]**&#x200B;子標籤（**[!UICONTROL Audit]**&#x200B;標籤）傳送的各種校樣。

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

您必須視需要傳送多份校樣，直到傳送內容完成為止。 之後，您可將傳送內容傳送至主要目標，並關閉驗證週期。

傳送屬性的&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤可讓您定義校對的屬性。 如有需要，您可以覆寫收件者排除規則。

![](assets/s_ncs_user_wizard_email01_145.png)

可以使用以下選項：

* 第一個選項可讓您將校對加倍。
* 以下兩個選項都允許您將拒絕清單和地址中的收件人保留在隔離中。 請參閱[自訂排除設定](../../delivery/using/steps-defining-the-target-population.md#customizing-exclusion-settings)中主目標的這些選項說明。 與遞送的目標（預設會排除這些位址）不同，它們預設會保留在證明的目標。
* **[!UICONTROL Keep the delivery code for the proof]**&#x200B;選項可讓您提供與傳送相關之傳送所定義之傳送代碼相同的傳送代碼。 此程式碼是在傳送精靈的第一個步驟中指定。
* 依預設，證明的主旨是前置詞「證明#」，其中#是證明的編號。 您可以在&#x200B;**[!UICONTROL Label prefix]**&#x200B;欄位中變更此首碼。

## 使用類型的驗證流程{#validation-process-with-typologies}

在傳送任何訊息之前，您應先分析促銷活動以核准其內容和設定。 在分析階段應用的檢查規則在&#x200B;**類型學**&#x200B;中定義。 依預設，對於電子郵件，分析涵蓋下列幾點：

* 批准對象
* 核准URL和影像
* 核准URL標籤
* 核准取消訂閱連結
* 檢查校樣大小
* 檢查有效期
* 檢查波的調度

在傳送參數的&#x200B;**[!UICONTROL Typologies]**&#x200B;標籤中，選取要套用至每個傳送的類型。

您可以透過&#x200B;**[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]**&#x200B;節點檢視和編輯核准規則、其內容、執行順序及其完整說明。

您可以從此節點建立新規則並定義新類型。 但是，這些工作會保留給熟悉JavaScript的專業使用者。

如需有關類型規則的詳細資訊，請參閱[關於促銷活動類型](../../campaign/using/about-campaign-typologies.md)。

要編輯當前的類型學，請按一下&#x200B;**[!UICONTROL Typology]**&#x200B;欄位右側的&#x200B;**[!UICONTROL Edit link]**&#x200B;表徵圖。

![](assets/s_ncs_user_email_del_typo_tab.png)

**[!UICONTROL Rule]**&#x200B;標籤提供要套用的類型學規則清單。 選擇規則，然後按一下&#x200B;**[!UICONTROL Detail...]**&#x200B;表徵圖查看其配置：

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** 類型類型在銷售壓力管理的框架內使用。如需詳細資訊，請參閱[本章節](../../campaign/using/about-marketing-resource-management.md)。

## 更改批准模式{#changing-the-approval-mode}

傳送屬性的&#x200B;**[!UICONTROL Analysis]**&#x200B;標籤可讓您選取驗證模式。 如果分析期間產生警告（例如，如果某些字元在傳送的主旨中突出顯示等），您可以設定傳送來定義是否仍應執行。 預設情況下，用戶必須在分析階段結束時確認消息的發送：這是&#x200B;**manual**&#x200B;驗證。

從適當欄位的下拉式清單中選取另一個核准模式。

![](assets/s_ncs_user_email_del_validation_mode.png)

可使用下列核准模式：

* **[!UICONTROL Manual]**:在分析階段結束時，使用者必須確認傳送才能開始傳送。若要這麼做，請按一下&#x200B;**[!UICONTROL Start]**&#x200B;按鈕以啟動傳送。
* **[!UICONTROL Semi-automatic]**:如果分析階段未產生警告訊息，則自動開始傳送。
* **[!UICONTROL Automatic]**:無論其結果如何，在分析階段結束時自動開始發送。
