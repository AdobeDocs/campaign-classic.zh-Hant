---
product: campaign
title: 驗證傳遞
description: 瞭解如何驗證傳遞
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability, Email Rendering, Proofs
exl-id: c2f4d8d0-f0fe-4d1a-92fd-91edaf9729f3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1666'
ht-degree: 8%

---

# 驗證傳遞 {#validating-the-delivery}



建立並設定傳送後，您必須先驗證傳送內容，才能將其傳送至主要目標。

操作步驟：

1. **分析傳遞**：此步驟可讓您準備要傳送的訊息。 [了解更多](#analyzing-the-delivery)。

   分析期間套用的規則會顯示在 [本節](#validation-process-with-typologies). 有關可用驗證模式的詳情，請參閱 [變更核准模式](#changing-the-approval-mode) 區段。

1. **傳送校樣**：此步驟可讓您控制內容、URL、個人化等。 進一步瞭解 [傳送證明](steps-validating-the-delivery.md#sending-a-proof) 和 [定義特定校訂目標](steps-defining-the-target-population.md#defining-a-specific-proof-target).

>[!IMPORTANT]
>
>上述兩個步驟必須在每次修改訊息內容後執行。

## 分析傳遞 {#analyzing-the-delivery}

分析是計算目標母體及準備傳遞內容的階段。 完成後，即可傳送傳遞。

### 啟動分析 {#launching-the-analysis}

1. 若要啟動傳遞分析，請按一下 **[!UICONTROL Send]**.
1. 選取 **[!UICONTROL Deliver as soon as possible]**。

   ![](assets/s_ncs_user_email_del_send.png)

1. 按一下 **[!UICONTROL Analyze]** 以手動啟動分析。

   進度列會顯示分析的進度。

   ![](assets/s_ncs_user_email_del_analyze_progress.png)

   >[!NOTE]
   >
   >有關分析期間使用的驗證規則，請參見 [驗證程式與型別](steps-validating-the-delivery.md#validation-process-with-typologies) 區段。

1. 您可以隨時按一下來停止分析 **[!UICONTROL Stop]**.

   ![](assets/s_ncs_user_wizard_email01_16.png)

   在準備階段期間不會傳送任何訊息。 因此，您可以開始或取消分析而不會有風險。

   >[!IMPORTANT]
   >
   >執行時，分析會凍結傳送（或證明）。 對傳送（或證明）所做的任何變更都必須先進行其他分析，才能適用。

1. 等候分析完成。

   分析完成後，視窗的上半部會指出傳遞準備是否已完成，或是否有任何錯誤發生。 會列出所有驗證步驟、警告和錯誤。彩色圖示顯示訊息類型：
   * 藍色圖示表示資訊訊息。
   * 黃色圖示表示非嚴重的處理錯誤。
   * 紅色圖示表示會阻止傳送傳遞的嚴重錯誤。

   ![](assets/s_ncs_user_email_del_analyze_error.png)

1. 按一下 **[!UICONTROL Close]** 以更正錯誤（若有的話）。

1. 進行變更後，按一下以重新啟動分析 **[!UICONTROL Analyze]**.

檢查完分析結果後，您就可以按一下 **[!UICONTROL Confirm delivery]** 將訊息傳送至指定的目標。 確認訊息可讓您啟動傳送。

![](assets/s_ncs_user_email_del_analyze_ok.png)

>[!NOTE]
>
>按一下 **[!UICONTROL Change the main delivery target]** 如果要傳送的訊息數目不符合您的設定時連結。 這可讓您變更目標母體的定義，並重新啟動分析。

### 分析設定 {#analysis-parameters}

此 **[!UICONTROL Analysis]** 傳遞屬性的索引標籤可讓您定義有關在分析階段準備訊息的一組資訊。

![](assets/s_ncs_user_email_del_analyze_adv_param.png)

此索引標籤可讓您存取下列選項：

* **[!UICONTROL Label and code of the delivery]** ：此區段中的選項用於在傳送分析階段期間計算這些欄位的值。 此 **[!UICONTROL Compute the execution folder during the delivery analysis]** 欄位會計算分析階段將包含此傳遞動作的資料夾名稱。
* **[!UICONTROL Approval mode]** ：此欄位可讓您定義分析完成時的手動或自動傳送。 有關驗證模式的詳情，請參閱 [變更核准模式](#changing-the-approval-mode) 區段。
* **[!UICONTROL Prepare the delivery parts in the database]** ：此選項可讓您改善傳送分析效能。 如需詳細資訊，請參閱[本節](#improving-delivery-analysis)。
* **[!UICONTROL Prepare the personalization data with a workflow]** ：此選項可讓您以自動工作流程準備傳送中包含的個人化資料，這可讓您大幅提升執行個人化的效能。 如需詳細資訊，請參閱 [最佳化個人化](personalization-fields.md#optimizing-personalization).
* **[!UICONTROL Start job in a detached process]** ：此選項可讓您透過個別程式開始傳送分析。 依預設，分析函式會使用Adobe Campaign應用程式伺服器處理序(web nlserver)。 選取此選項可確保即使在應用程式伺服器發生故障時，也能完成分析。
* **[!UICONTROL Log SQL queries generated during the analysis in the journal]** ：此選項會在分析階段將SQL查詢記錄檔新增至傳遞日誌。
* **[!UICONTROL Ignore personalization scripts during sending]** ：此選項可讓您略過HTML內容中JavaScript指示詞的解譯。 它們將顯示為已傳送內容中的原樣。 這些指示詞是隨 **&lt;%=** 標籤)。

### 改善傳遞分析效能 {#improving-delivery-analysis}

若要加快傳送準備作業，您可以檢查 **[!UICONTROL Prepare the delivery parts in the database]** 選項。

啟用此選項後，會直接在資料庫中執行傳遞準備，大幅加快分析。

目前，此選項只有在符合下列條件時才可用：
* 傳遞必須是電子郵件。 目前不支援其他管道。
* 您不得使用中間來源或外部路由，而只能使用大量傳遞路由型別。 您可以檢查中使用的製程 **[!UICONTROL General]** 的標籤 **[!UICONTROL Delivery properties]**.
* 您無法鎖定來自外部檔案的母體。 若要進行單一傳遞，請按一下 **[!UICONTROL To]** 連結自 **[!UICONTROL Email parameters]** 並檢查 **[!UICONTROL Defined in the database]** 選項時才會選擇此選項。 對於工作流程中使用的傳遞，檢查收件者是否為 **[!UICONTROL Specified by the inbound event(s)]** 在 **[!UICONTROL Delivery]** 標籤。
* 您必須使用PostgreSQL資料庫。

### 設定分析優先順序 {#analysis-priority-}

當傳遞是行銷活動的一部分時， **[!UICONTROL Advanced]** tab提供其他選項。 這可讓您組織相同行銷活動中傳送的處理順序。

傳送前，會分析每個傳遞。 分析持續時間取決於傳遞擷取檔案。 檔案大小愈大，分析所需的時間愈長，下列傳送作業就會等候。

的選項 **[!UICONTROL Message preparation by the scheduler]** 可讓您優先處理行銷活動工作流程中的傳遞分析。

![](assets/delivery_analysis_priority.png)

如果傳遞太大，最好指派低優先順序，以避免減慢分析其他工作流程傳遞的速度。

>[!NOTE]
>
>為了確保大型傳送分析不會減慢工作流程的進度，您可以按一下 **[!UICONTROL Schedule execution for a time of low activity]**.

## 傳送證明 {#sending-a-proof}

若要檢測訊息設定中可能出現的錯誤，Adobe 強烈建議您配置傳遞驗證階段。要經常性地透過傳送驗證訊息測試收件者，確保核准內容。每次進行變更時都必須傳送驗證訊息，以核准內容。

>[!NOTE]
>
>* 有關可用驗證模式的詳情，請參閱 [變更核准模式](steps-validating-the-delivery.md#changing-the-approval-mode).
>* 中說明校樣目標的設定 [定義特定校訂目標](steps-defining-the-target-population.md#defining-a-specific-proof-target).
>


若要傳送證明，請遵循下列步驟：

1. 請確定校樣目標已如所述設定 [定義特定校訂目標](steps-defining-the-target-population.md#defining-a-specific-proof-target).
1. 按一下 **[!UICONTROL Send a proof]** 在傳遞精靈的頂端列上。

   ![](assets/s_ncs_user_email_del_send_proof.png)

1. 開始訊息分析。 另請參閱 [分析傳遞](steps-validating-the-delivery.md#analyzing-the-delivery).
1. 您現在可以傳送傳遞(請參閱 [傳送傳遞](steps-sending-the-delivery.md))。

   傳送後，證明將顯示在傳送清單中，並自動建立和編號。 如果您想要存取其內容和屬性，可以編輯它。 如需關於此項目的詳細資訊，請參閱此[頁面](about-delivery-monitoring.md)。

   ![](assets/s_ncs_user_delivery_validation_cycle_03a.png)

   >[!NOTE]
   >
   >如果為傳遞建立了幾種格式(HTML和文字)，您可以在視窗的下半部分選擇要傳送給校樣收件者的訊息格式。

   ![](assets/s_ncs_user_email_del_send_proof_formats.png)

收到校樣之驗證群組所做的任何評論後，您可能會想要修改傳遞的內容。 進行變更後，您必須重新啟動分析，然後傳送另一個校樣。 每個新校樣都進行了編號並記錄在傳送日誌中。

分析傳遞後，您可以檢視透過傳送的各種校樣 **[!UICONTROL Proofs]** 記錄檔的子索引標籤(**[!UICONTROL Audit]** 標籤)。

![](assets/s_ncs_user_delivery_validation_cycle_03.png)

您必須視需要傳送儘可能多的校樣，直到完成傳送內容為止。 之後，您可以將傳遞傳送至主要目標並關閉驗證週期。

此 **[!UICONTROL Advanced]** 傳遞屬性的索引標籤可讓您定義證明的屬性。 如有需要，您可以覆寫收件者排除規則。

![](assets/s_ncs_user_wizard_email01_145.png)

可以使用以下選項：

* 第一個選項可讓您將校樣保留兩倍。
* 以下兩個選項都可讓您保留封鎖清單中的收件者和隔離地址。 請參閱以下文章中針對主要目標提供的這些選項說明： [自訂排除設定](steps-defining-the-target-population.md#customizing-exclusion-settings). 不像預設情況下會排除這些地址的傳送目標，這些地址會預設為校樣的目標。
* 此 **[!UICONTROL Keep the delivery code for the proof]** 選項可讓您為校樣提供與其相關傳送所定義相同的傳送代碼。 此程式碼會在傳遞精靈的第一步中指定。
* 依預設，校訂的主題會以「Proof #」為前置詞，其中#是校訂的編號。 您可以在 **[!UICONTROL Label prefix]** 欄位。

## 驗證程式與型別 {#validation-process-with-typologies}

在傳送任何訊息之前，您應該分析行銷活動以核准其內容和設定。 在分析階段期間套用的檢查規則定義於 **型別**. 根據預設，針對電子郵件，分析會涵蓋下列幾點：

* 核准物件
* 核准URL和影像
* 核准URL標籤
* 核准取消訂閱連結
* 檢查校訂的大小
* 檢查有效期
* 檢查波段排程

要套用至每個傳送的型別，會在 **[!UICONTROL Typologies]** 索引標籤進行標籤。

您可以透過以下方式檢視及編輯核准規則、其內容、其執行順序及其完整說明： **[!UICONTROL Administration > Campaign execution > Typology management > Typology rules]** 節點。

您可以從此節點建立新規則及定義新型別。 不過，這些工作會保留給熟悉JavaScript的專家使用者。

如需型別規則的詳細資訊，請參閱 [此頁面](../../campaign-opt/using/about-campaign-typologies.md).

若要編輯目前的分類，請按一下 **[!UICONTROL Edit link]** 圖示右側 **[!UICONTROL Typology]** 欄位。

![](assets/s_ncs_user_email_del_typo_tab.png)

此 **[!UICONTROL Rule]** 索引標籤提供要套用的型別規則清單。 選取規則並按一下 **[!UICONTROL Detail...]** 圖示以檢視其設定：

![](assets/s_ncs_user_email_del_typo_rules_edit.png)

>[!NOTE]
>
>**[!UICONTROL Arbitration]** 型別型別用於銷售壓力管理的架構中。 如需詳細資訊，請參閱[本章節](../../mrm/using/about-marketing-resource-management.md)。

## 變更核准模式 {#changing-the-approval-mode}

此 **[!UICONTROL Analysis]** 傳遞屬性的索引標籤可讓您選取驗證模式。 如果在分析期間產生警告（例如，如果傳送的主題中強調某些字元，等等），您可以設定傳送以定義是否仍應執行。 依預設，使用者必須在分析階段結束時確認傳送訊息：這是&#x200B;**手動**&#x200B;驗證。

從適當欄位的下拉式清單中選取其他核准模式。

![](assets/s_ncs_user_email_del_validation_mode.png)

可使用下列核准模式：

* **[!UICONTROL Manual]**：在分析階段結束時，使用者必須確認傳送才能開始傳送。 若要這麼做，請按一下 **[!UICONTROL Start]** 按鈕以啟動傳遞。
* **[!UICONTROL Semi-automatic]**：如果分析階段未產生警告訊息，則會自動開始傳送。
* **[!UICONTROL Automatic]**：傳送會在分析階段結束時自動開始，無論結果為何。
