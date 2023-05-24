---
product: campaign
title: 行銷活動傳遞
description: 進一步瞭解行銷活動傳遞
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Campaigns, Resource Management, Cross Channel Orchestration
exl-id: 1dd3c080-444d-45f8-9562-d2d01a9d2860
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 2%

---

# 行銷活動傳遞 {#marketing-campaign-deliveries}

傳遞可透過行銷活動控制面板、行銷活動工作流程建立，或直接透過傳遞概述建立。

從行銷活動建立傳遞時，會連結至此行銷活動，並在行銷活動層級合併。

![](assets/do-not-localize/how-to-video.png)[ 在影片中探索此功能](#create-email-video)

## 建立傳遞 {#creating-deliveries}

若要建立連結至行銷活動的傳送，請按一下 **[!UICONTROL Add a delivery]** 行銷活動控制面板中的連結。

![](assets/campaign_op_add_delivery.png)

建議的設定適用於不同型別的傳送：直接郵件、電子郵件、行動裝置頻道。 [了解更多](../../delivery/using/steps-about-delivery-creation-steps.md)。

## 開始傳遞 {#starting-a-delivery}

取得所有核准後，即可開始傳遞。 然後，傳遞程式取決於傳遞型別。 如需電子郵件或行動裝置頻道傳遞內容，請參閱 [開始線上傳遞](#starting-an-online-delivery)，如果是直接郵件傳送，請參閱 [開始離線傳遞](#starting-an-offline-delivery).

### 開始線上傳遞 {#starting-an-online-delivery}

在核准所有核准請求後，傳送狀態會變更為 **[!UICONTROL Pending confirmation]** 和可以由運運算元啟動。 在適當的情況下，被指定為開始傳送的稽核者的Adobe Campaign操作員（或操作員群組）會收到傳送已準備好開始的通知。

>[!NOTE]
>
>如果指定特定操作員或操作員群組來開始傳送的屬性傳送，您也可以允許負責傳送的操作員確認傳送。 若要這麼做，請啟動 **NMS_ActivateOwnerConfirmation** 選項，方法是輸入 **1** 做為值。 這些選項的管理方式為 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** 節點(在Adobe Campaign總管中)。
>  
>若要停用此選項，請輸入 **0** 做為值。 然後，傳送確認程式會以預設方式運作：只有傳送屬性中指定用於傳送的運運算元或運運算元群組（或管理員）才能確認並執行傳送。

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

此資訊也會顯示在行銷活動控制面板上。 此 **[!UICONTROL Confirm delivery]** 連結可讓您開始傳遞。

![](assets/s_ncs_user_edit_del_to_start.png)

確認訊息可讓您確保此動作的安全。

### 開始離線傳遞 {#starting-an-offline-delivery}

取得所有核准後，傳遞狀態會變更為 **[!UICONTROL Pending extraction]**. 擷取檔案是透過特殊工作流程建立的，在預設設定中，當直接郵件傳送擱置擷取時，會自動啟動。 當程式正在進行時，它會顯示於控制面板中，並可透過其連結進行編輯。

>[!NOTE]
>
>與Campaign套件相關的技術工作流程在中呈現 [技術工作流程清單](../../workflow/using/about-technical-workflows.md).

**步驟1 — 檔案核准**

成功執行擷取工作流程後，必須核准擷取檔案（前提是在傳送設定中選取了擷取檔案核准）。

有關詳細資訊，請參閱 [核准擷取檔案](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file).

**步驟2 — 核准給服務提供者的訊息**

* 擷取檔案獲得核准後，您就可以產生路由器通知電子郵件的校樣。 此電子郵件訊息是根據傳遞範本所建構。 必須經過核准。

   >[!NOTE]
   >
   >只有在核准視窗中啟用了證明的傳送和核準時，此步驟才可用。

![](assets/s_ncs_user_file_valid_select_BAT.png)


* 按一下 **[!UICONTROL Send a proof]** 按鈕以建立校樣。

   必須預先定義校樣目標。

   您可以視需要建立儘可能多的校樣。 這些檔案可透過 **[!UICONTROL Direct mail...]** 傳遞詳細資料的連結。

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* 傳遞狀態變更為 **[!UICONTROL To submit]**. 按一下 **[!UICONTROL Submit proofs]** 按鈕以開始核准流程。

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* 傳遞狀態變更為 **[!UICONTROL Proof to validate]** 和按鈕可讓您接受或拒絕核准。

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   您可以接受或拒絕此核准，或返回擷取步驟。

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* 擷取檔案會傳送至路由器，而傳遞作業即告完成。

### 成本與庫存的計算 {#calculation-of-costs-and-stocks}

檔案擷取會啟動兩項作業：預算計算和庫存計算。 預算專案會更新。

* 此 **[!UICONTROL Budget]** 索引標籤可讓您管理行銷活動的預算。 成本專案的總計會顯示在 **[!UICONTROL Calculates cost]** 行銷活動主要標籤及其所屬方案的欄位。 這些金額也會反映在行銷活動預算中。

   實際成本最終將根據路由器提供的資訊計算。 只有實際傳送的訊息才會開立發票。

* 庫存定義於 **[!UICONTROL Administration > Campaign management > Stocks]** 樹狀結構的節點，以及成本結構 **[!UICONTROL Administration > Campaign management > Service providers]** 節點。

   坯件線會顯示在坯件區段中。 若要定義初始坯件，請開啟坯件線。 每次進行交貨時，庫存都會減少。 您可以定義警示等級與通知。

>[!NOTE]
>
>如需成本計算與存貨管理的詳細資訊，請參閱 [供應商、庫存和預算](../../campaign/using/providers--stocks-and-budgets.md).

## 管理相關文件 {#managing-associated-documents}

您可以為行銷活動跟各種檔案建立關聯：報告、照片、網頁、圖表等。這些檔案可以是任何格式(Microsoft Word、PowerPoint、PNG、JPG、AcrobatPDF等)。 瞭解如何將檔案與行銷活動連結 [在本節中](../../campaign/using/marketing-campaign-assets.md).

>[!IMPORTANT]
>
>此模式為小型檔案保留。

在行銷活動中，您也可以參考其他專案，例如促銷優惠券、與特定分公司或商店相關的特殊優惠等。 當這些元素包含在大綱中時，它們可以與直接郵件傳遞相關聯。 [了解更多](#associating-and-structuring-resources-linked-via-a-delivery-outline)。

>[!NOTE]
>
>如果您使用MRM，您也可以管理行銷資源庫，供多名參與者共同作業使用。 另請參閱 [管理行銷資源](../../mrm/using/managing-marketing-resources.md).

### 新增檔案 {#adding-documents}

檔案可以在行銷活動層級（情境檔案）或方案層級（一般檔案）相關聯。

此 **[!UICONTROL Documents]** 索引標籤包含：

* 內容所需的所有檔案清單（範本、影像等） 可由Adobe Campaign運運算元透過適當許可權從本機下載，
* 包含路由器資訊的檔案（如果有）。

檔案透過以下連結至方案或行銷活動： **[!UICONTROL Edit > Documents]** 標籤。

![](assets/s_ncs_user_op_add_document.png)

您也可以透過行銷活動控制面板中提供的連結，將檔案新增至行銷活動。

![](assets/add_a_document_in_op.png)

按一下 **[!UICONTROL Details]** 圖示可檢視檔案內容並新增資訊：

![](assets/s_ncs_user_op_add_document_details.png)

在控制面板中，與行銷活動相關聯的檔案會分組在 **[!UICONTROL Document(s)]** 區段，如下列範例所示：

![](assets/s_ncs_user_op_edit_document.png)

您也可以從此檢視編輯和修改它們。

### 透過傳遞大網建立連結的關聯和結構資源 {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>傳遞大網僅用於直接郵件行銷活動的內容。

傳遞大網表示一組結構化元素（檔案、分支/商店、促銷優惠券等） 在公司中並為特定行銷活動建立。

這些元素會分組在傳遞大網中，而特定傳遞大網將與傳遞相關聯；它將在傳送至的擷取檔案中參考 **服務提供者** 以便附加至傳遞。 例如，您可以建立傳遞大網，指出分支及其使用的行銷手冊。

對於行銷活動，傳遞大綱可讓您根據特定條件來建構要與傳遞相關聯的外部元素：相關分支、已授與的促銷優惠、本機活動的邀請等。

#### 建立大綱 {#creating-an-outline}

若要建立輪廓，請按一下 **[!UICONTROL Delivery outlines]** 中的子標籤 **[!UICONTROL Edit > Documents]** 相關行銷活動的索引標籤。

>[!NOTE]
>
>如果此索引標籤不存在，則此功能不適用於此行銷活動。 請參閱行銷活動範本設定。
>   
>有關詳細資訊，請參閱 [行銷活動範本](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

![](assets/s_ncs_user_op_composition_link.png)

接下來，按一下 **[!UICONTROL Add a delivery outline]** 並建立行銷活動大綱的階層：

1. 以滑鼠右鍵按一下樹狀結構的根目錄，然後選取 **[!UICONTROL New > Delivery outlines]**.
1. 以滑鼠右鍵按一下您剛建立的大綱，然後選取 **[!UICONTROL New > Item]** 或 **[!UICONTROL New > Personalization fields]**.

![](assets/s_ncs_user_op_add_composition.png)

大綱可包含專案和個人化欄位、資源和選件：

* 專案可以是實體檔案，例如，此處參考和說明的檔案，且會附加至傳遞。
* 個人化欄位可讓您建立與傳遞相關的個人化元素，而不是收件者。 因此，您可以建立用於特定目標傳遞（歡迎優惠、折扣等）的值 它們是在Adobe Campaign中建立，並透過匯入大綱 **[!UICONTROL Import personalization fields...]** 連結。

   ![](assets/s_ncs_user_op_add_composition_field.png)

   也可以直接在大綱中建立它們，方法是按一下 **[!UICONTROL Add]** 圖示加以顯示。

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* 這些資源是行銷資源控制面板中產生的行銷資源，存取方式為 **[!UICONTROL Resources]** 的連結 **[!UICONTROL Campaigns]** 標籤。

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >如需行銷資源的詳細資訊，請參閱 [管理行銷資源](../../mrm/using/managing-marketing-resources.md).

#### 選取大綱 {#selecting-an-outline}

對於每個傳送，您可以從保留給擷取大綱的區段中選取要關聯的大綱，如下列範例所示：

![](assets/s_ncs_user_op_select_composition.png)

然後所選輪廓會顯示在視窗的下半部。 您可以使用欄位右側的圖示加以編輯，或使用下拉式清單加以變更：

![](assets/s_ncs_user_op_select_composition_b.png)

此 **[!UICONTROL Summary]** 傳遞的標籤也會顯示下列資訊：

![](assets/s_ncs_user_op_select_composition_c.png)

#### 擷取結果 {#extraction-result}

在擷取並傳送給服務提供者的檔案中，大綱的名稱以及適當時其特徵（成本、說明等） 會根據與服務提供者相關聯之匯出範本中的資訊新增至內容。

在下列範例中，與傳遞相關的大綱的標籤、預估成本和說明將新增至擷取檔案。

![](assets/s_ncs_user_op_composition_in_export_template.png)

匯出模型必須與為相關傳遞選取的服務提供者相關聯。 另請參閱 [建立服務提供者及其成本結構](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures).

>[!NOTE]
>
>如需匯出的詳細資訊，請參閱 [快速入門](../../platform/using/get-started-data-import-export.md) 區段。

#### 教學課程影片 {#create-email-video}

此影片說明如何在Adobe Campaign中建立行銷活動和電子郵件。

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

有其他Campaign操作說明影片可供使用 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).
