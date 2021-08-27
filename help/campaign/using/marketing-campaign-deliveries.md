---
product: campaign
title: 行銷活動傳遞
description: 深入了解行銷活動傳遞
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
exl-id: 1dd3c080-444d-45f8-9562-d2d01a9d2860
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 2%

---

# 行銷活動傳遞 {#marketing-campaign-deliveries}

![](../../assets/common.svg)

傳遞可透過促銷活動控制面板、促銷活動工作流程或直接透過傳遞的概觀來建立。

從促銷活動建立傳遞時，傳遞將連結至此促銷活動，並在促銷活動層級進行整合。

![](assets/do-not-localize/how-to-video.png)[ 在影片中探索此功能](#create-email-video)

## 建立傳送 {#creating-deliveries}

若要建立連結至促銷活動的傳送，請按一下促銷活動控制面板中的&#x200B;**[!UICONTROL Add a delivery]**&#x200B;連結。

![](assets/campaign_op_add_delivery.png)

建議的設定適用於不同的傳送類型：直接郵件、電子郵件、行動裝置通道。 [深入瞭解](../../delivery/using/steps-about-delivery-creation-steps.md)。

## 開始傳送 {#starting-a-delivery}

一旦所有核准都獲得授權，傳送即可開始。 然後，傳送程式取決於傳送類型。 如需電子郵件或行動通道傳送，請參閱[開始線上傳送](#starting-an-online-delivery)，如需直接郵件傳送，請參閱[開始離線傳送](#starting-an-offline-delivery)。

### 開始線上傳送 {#starting-an-online-delivery}

所有核准請求一經授與，傳送狀態就會變更為&#x200B;**[!UICONTROL Pending confirmation]**，且可由運算子啟動。 指定為審核者以開始傳送的Adobe Campaign運算子（或運算子群組）會在適當時收到通知，告知已準備好開始傳送。

>[!NOTE]
>
>如果指定了特定運算子或運算子群組，以在傳送的屬性中開始傳送，您也可以允許負責傳送的運算子確認傳送。 要執行此操作，請輸入&#x200B;**1**&#x200B;作為值，以激活&#x200B;**NMS_ActivateOwnerConfirmation**&#x200B;選項。 這些選項可從Adobe Campaign檔案總管的&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;節點進行管理。
>  
>要停用此選項，請輸入&#x200B;**0**&#x200B;作為值。 接著，傳送確認程式將依預設運作：在傳送屬性（或管理員）中，只有為傳送指定的運算子或運算子群組才能確認和執行傳送。

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

資訊也會顯示在促銷活動控制面板上。 **[!UICONTROL Confirm delivery]**&#x200B;連結可讓您開始傳送。

![](assets/s_ncs_user_edit_del_to_start.png)

確認訊息可讓您保護此動作。

### 開始離線傳送 {#starting-an-offline-delivery}

所有核准都授與後，傳送狀態會變更為&#x200B;**[!UICONTROL Pending extraction]**。 解壓縮檔案會透過特殊工作流程建立，在預設設定中，當直接郵件傳送擱置解壓縮時，此工作流程會自動啟動。 進程進行中時，會顯示在控制面板中，並可透過其連結編輯。

>[!NOTE]
>
>[技術工作流程清單](../../workflow/using/about-technical-workflows.md)中會顯示與Campaign套件相關的技術工作流程。

**步驟1 — 檔案核准**

擷取工作流程成功執行後，必須核准擷取檔案（前提是已在傳送設定中選取擷取檔案核准）。

有關詳細資訊，請參閱[核准解壓縮檔案](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file)。

**步驟2 — 向服務提供商批准消息**

* 提取檔案獲得批准後，您就可以生成路由器通知電子郵件的證明。 此電子郵件是根據傳遞模板構建的。 必須獲得批准。

   >[!NOTE]
   >
   >只有在核准視窗中啟用校樣的傳送和核準時，才能使用此步驟。

![](assets/s_ncs_user_file_valid_select_BAT.png)


* 按一下&#x200B;**[!UICONTROL Send a proof]**&#x200B;按鈕以建立校樣。

   必須預先定義校樣目標。

   您可以視需要建立任意數量的校樣。 這些可透過傳送詳細資料的&#x200B;**[!UICONTROL Direct mail...]**&#x200B;連結存取。

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* 傳送狀態變更為&#x200B;**[!UICONTROL To submit]**。 按一下&#x200B;**[!UICONTROL Submit proofs]**&#x200B;按鈕以啟動核准程式。

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* 傳送狀態變更為&#x200B;**[!UICONTROL Proof to validate]**，而按鈕可讓您接受或拒絕核准。

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   您可以接受或拒絕此批准，或返回提取步驟。

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* 解壓檔案將發送到路由器，並完成傳送。

### 費用和庫存的計算 {#calculation-of-costs-and-stocks}

檔案擷取會啟動兩個操作：預算計算和庫存計算。 預算條目會更新。

* **[!UICONTROL Budget]**&#x200B;標籤可讓您管理促銷活動的預算。 成本條目的總計顯示在促銷活動首頁簽及其所屬方案的&#x200B;**[!UICONTROL Calculates cost]**&#x200B;欄位中。 這些金額也會反映在促銷活動預算中。

   實際成本最終將根據路由器提供的資訊計算。 只有實際發送的郵件才會開具發票。

* 儲存在樹的&#x200B;**[!UICONTROL Administration > Campaign management > Stocks]**&#x200B;節點中定義，並在&#x200B;**[!UICONTROL Administration > Campaign management > Service providers]**&#x200B;節點中定義成本結構。

   庫存行在庫存區中。 要定義初始庫存，請開啟一條庫存線。 每次發生交貨時庫存都會減少。 您可以定義警報級別和通知。

>[!NOTE]
>
>有關成本計算和庫存管理的詳細資訊，請參閱[提供者、庫存和預算](../../campaign/using/providers--stocks-and-budgets.md)。

## 管理關聯文檔 {#managing-associated-documents}

您可以為行銷活動跟各種檔案建立關聯：報告、照片、網頁、圖表等。這些檔案可以是任何格式(Microsoft Word、PowerPoint、PNG、JPG、Acrobat PDF等)。 了解如何在本小節](../../campaign/using/marketing-campaign-assets.md)中將檔案連結至促銷活動[。

>[!IMPORTANT]
>
>此模式為小文檔保留。

在促銷活動中，您也可以參考其他項目，例如促銷優惠券、與特定分店或商店相關的特別優惠等。 當這些元素包含在大綱中時，它們可以與直接郵件傳送相關聯。 [深入瞭解](#associating-and-structuring-resources-linked-via-a-delivery-outline)。

>[!NOTE]
>
>如果您使用MRM，您也可以管理可供數位參與者協作工作的行銷資源庫。 請參閱[管理行銷資源](../../mrm/using/managing-marketing-resources.md)。

### 添加文檔 {#adding-documents}

可在促銷活動層級（內容檔案）或方案層級（一般檔案）將檔案建立關聯。

**[!UICONTROL Documents]**&#x200B;標籤包含：

* 內容（模板、影像等）所需的所有文檔的清單 可由Adobe Campaign營運商在本機下載，
* 包含路由器資訊的文檔（如果有）。

檔案會透過&#x200B;**[!UICONTROL Edit > Documents]**&#x200B;標籤連結至方案或促銷活動。

![](assets/s_ncs_user_op_add_document.png)

您也可以透過其控制面板中提供的連結，將檔案新增至促銷活動。

![](assets/add_a_document_in_op.png)

按一下&#x200B;**[!UICONTROL Details]**&#x200B;圖示以檢視檔案內容並新增資訊：

![](assets/s_ncs_user_op_add_document_details.png)

在控制面板中，與促銷活動相關聯的檔案會歸類到&#x200B;**[!UICONTROL Document(s)]**&#x200B;區段中，如下列範例所示：

![](assets/s_ncs_user_op_edit_document.png)

您也可以從此檢視編輯和修改這些量度。

### 通過傳送大綱關聯和構建連結的資源 {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>傳送大綱專門用於直接郵件促銷活動的內容。

傳遞大綱表示一組結構化元素（文檔、分支/商店、促銷優惠券等） 為特定促銷活動建立。

這些元素會分組在傳送大綱中，而特定傳送大綱將與傳送相關聯；會在傳送至&#x200B;**服務提供者**&#x200B;的解壓縮檔案中參考它，以便附加至傳送。 例如，您可以建立傳遞大綱，參考分支及其使用的行銷手冊。

對於促銷活動，傳送大綱可讓您根據特定條件來建構要與傳送相關聯的外部元素：相關分支、已授予的促銷優惠、參加當地活動的邀請等。

#### 建立大綱 {#creating-an-outline}

若要建立大綱，請按一下相關促銷活動&#x200B;**[!UICONTROL Edit > Documents]**&#x200B;標籤中的&#x200B;**[!UICONTROL Delivery outlines]**&#x200B;子標籤。

>[!NOTE]
>
>如果此標籤不存在，則此功能無法用於此促銷活動。 請參閱促銷活動範本設定。
>   
>如需詳細資訊，請參閱[促銷活動範本](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

![](assets/s_ncs_user_op_composition_link.png)

接下來，按一下&#x200B;**[!UICONTROL Add a delivery outline]**&#x200B;並建立促銷活動的大綱階層：

1. 按一下右鍵樹的根，然後選擇&#x200B;**[!UICONTROL New > Delivery outlines]**。
1. 按一下右鍵剛建立的大綱，然後選擇&#x200B;**[!UICONTROL New > Item]**&#x200B;或&#x200B;**[!UICONTROL New > Personalization fields]**。

![](assets/s_ncs_user_op_add_composition.png)

大綱可包含項目和個人化欄位、資源和選件：

* 項目可以是實體檔案，例如，此處會參考並說明這些檔案，並會附加至傳送。
* 個人化欄位可讓您建立與傳送相關的個人化元素，而非收件者。 因此，您可以建立要用於特定目標（歡迎優惠、折扣等）之傳送的值 它們會在Adobe Campaign中建立，並透過&#x200B;**[!UICONTROL Import personalization fields...]**&#x200B;連結匯入大綱中。

   ![](assets/s_ncs_user_op_add_composition_field.png)

   也可以按一下清單區域右側的&#x200B;**[!UICONTROL Add]**&#x200B;圖示，直接在大綱中建立它們。

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* 這些資源是在行銷資源控制面板中產生的行銷資源，可透過&#x200B;**[!UICONTROL Campaigns]**&#x200B;標籤的&#x200B;**[!UICONTROL Resources]**&#x200B;連結存取。

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >如需行銷資源的詳細資訊，請參閱[管理行銷資源](../../mrm/using/managing-marketing-resources.md)。

#### 選擇大綱 {#selecting-an-outline}

對於每個傳送，可以從為提取大綱保留的節中選擇要關聯的大綱，如下例所示：

![](assets/s_ncs_user_op_select_composition.png)

然後，所選大綱將顯示在窗口的下部部分。 您可以使用欄位右側的圖示加以編輯，或使用下拉式清單加以變更：

![](assets/s_ncs_user_op_select_composition_b.png)

傳送的&#x200B;**[!UICONTROL Summary]**&#x200B;標籤也會顯示此資訊：

![](assets/s_ncs_user_op_select_composition_c.png)

#### 提取結果 {#extraction-result}

在提取併發送到服務提供商的檔案中，大綱的名稱，並在適當時，其特徵（成本、說明等） 根據與服務提供者相關聯的匯出範本中的資訊，將其新增至內容。

在以下示例中，與傳送關聯的大綱的標籤、估計成本和說明將添加到解壓縮檔案中。

![](assets/s_ncs_user_op_composition_in_export_template.png)

導出模型必須與為相關傳送選擇的服務提供商相關聯。 請參閱[建立服務提供商及其成本結構](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

>[!NOTE]
>
>有關導出的詳細資訊，請參閱[Getting Started](../../platform/using/get-started-data-import-export.md)部分。

#### 教學課程影片 {#create-email-video}

此影片說明如何在Adobe Campaign中建立行銷活動和電子郵件。

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

您可以在[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得其他促銷活動作法影片。
