---
solution: Campaign Classic
product: campaign
title: 行銷促銷活動傳送
description: 進一步瞭解行銷宣傳傳遞
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 1%

---


# 行銷促銷活動傳送{#marketing-campaign-deliveries}

傳送可透過促銷活動控制面板、促銷活動工作流程或直接透過傳送概述來建立。

當從促銷活動建立傳送時，傳送將連結至此促銷活動，並在促銷活動層級進行合併。

![](assets/do-not-localize/how-to-video.png)[ 在影片中探索此功能](#create-email-video)

## 建立傳送 {#creating-deliveries}

若要建立連結至促銷活動的傳送，請按一下促銷活動控制面板中的&#x200B;**[!UICONTROL Add a delivery]**&#x200B;連結。

![](assets/campaign_op_add_delivery.png)

建議的配置適用於不同類型的交付：直效郵件、電子郵件、行動通道。 [進一步瞭解](../../delivery/using/steps-about-delivery-creation-steps.md)。

## 開始傳送{#starting-a-delivery}

一旦所有許可都已獲得批准，交貨即可開始。 然後，傳送程式會視傳送類型而定。 如需電子郵件或行動頻道傳送，請參閱[啟動線上傳送](#starting-an-online-delivery)，如需直接郵件傳送，請參閱[啟動離線傳送](#starting-an-offline-delivery)。

### 開始線上傳送{#starting-an-online-delivery}

在授與所有核准請求後，傳送狀態會變更為&#x200B;**[!UICONTROL Pending confirmation]**，可由運算子開始。 在適當情況下，被指定為審核者的Adobe Campaign操作員（或一組操作員）將通知已準備開始交付。

>[!NOTE]
>
>如果指定特定運算元或運算元群組以在傳送的屬性中開始傳送，您也可以允許負責傳送的運算元確認傳送。 要執行此操作，請輸入&#x200B;**1**&#x200B;作為值，激活&#x200B;**NMS_ActivateOwnerConfirmation**&#x200B;選項。 這些選項是從Adobe Campaign瀏覽器的&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;節點管理的。
>  
>要停用此選項，請輸入&#x200B;**0**&#x200B;作為值。 然後，傳送確認程式會依預設運作：只有為傳送屬性（或管理員）中指定的運算元或運算元群組才能確認並執行傳送。

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

資訊也會顯示在促銷活動控制面板上。 **[!UICONTROL Confirm delivery]**&#x200B;連結可讓您開始傳送。

![](assets/s_ncs_user_edit_del_to_start.png)

確認訊息可讓您保護此動作。

### 開始離線傳送{#starting-an-offline-delivery}

一旦所有批准都獲得批准，傳送狀態將變更為&#x200B;**[!UICONTROL Pending extraction]**。 抽取檔案通過特殊的工作流建立，在預設配置中，當直接郵件發送暫掛抽取時，該工作流自動啟動。 當進程進行中時，該進程會顯示在控制面板中，並可透過其連結進行編輯。

>[!NOTE]
>
>[技術工作流程清單](../../workflow/using/about-technical-workflows.md)中顯示與促銷活動套件相關的技術工作流程。

**步驟1 —— 檔案批准**

擷取工作流程成功執行後，必須核准擷取檔案（前提是在傳送設定中選取擷取檔案核准）。

有關詳細資訊，請參閱[批准抽取檔案](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file)。

**步驟2 —— 批准向服務提供商發送的消息**

* 抽取檔案獲得批准後，您就可以生成路由器通知電子郵件的證明。 該電子郵件消息基於傳送模板構建。 必須獲得批准。

   >[!NOTE]
   >
   >只有在批准窗口中啟用了校樣的發送和批准時，才可使用此步驟。

![](assets/s_ncs_user_file_valid_select_BAT.png)


* 按一下&#x200B;**[!UICONTROL Send a proof]**&#x200B;按鈕以建立校樣。

   證明目標必須事先確定。

   您可以視需要建立任意數量的校樣。 這些內容可透過傳送詳細資料的&#x200B;**[!UICONTROL Direct mail...]**&#x200B;連結存取。

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* 傳送狀態變更為&#x200B;**[!UICONTROL To submit]**。 按一下&#x200B;**[!UICONTROL Submit proofs]**&#x200B;按鈕以開始核准程式。

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* 傳送狀態變更為&#x200B;**[!UICONTROL Proof to validate]**，而按鈕可讓您接受或拒絕核准。

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   您可以接受或拒絕此批准，或返回抽取步驟。

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* 抽取檔案將發送到路由器，並完成傳送。

### 計算費用和庫存{#calculation-of-costs-and-stocks}

檔案擷取會啟動兩項作業：預算計算和庫存計算。 預算條目將更新。

* **[!UICONTROL Budget]**&#x200B;標籤可讓您管理促銷活動的預算。 成本項的合計顯示在促銷活動主標籤及其所屬程式的&#x200B;**[!UICONTROL Calculates cost]**&#x200B;欄位中。 金額也會反映在促銷活動預算中。

   實際成本最終將根據路由器提供的資訊計算。 只有實際傳送的訊息會開具發票。

* 庫存定義在樹的&#x200B;**[!UICONTROL Administration > Campaign management > Stocks]**&#x200B;節點中，成本結構定義在&#x200B;**[!UICONTROL Administration > Campaign management > Service providers]**&#x200B;節點中。

   庫存行在庫存區中可見。 要定義初始庫存，請開啟一個庫存行。 每次發生交貨時，庫存都會減少。 您可以定義警報級別和通知。

>[!NOTE]
>
>有關成本計算和庫存管理的詳細資訊，請參閱[供應商、庫存和預算](../../campaign/using/providers--stocks-and-budgets.md)。

## 管理關聯文檔{#managing-associated-documents}

您可以將各種檔案與促銷活動建立關聯：報表、像片、網頁、圖表等。 這些檔案可以是任何格式(Microsoft Word、PowerPoint、PNG、JPG、AcrobatPDF等)。 瞭解如何在本節](../../campaign/using/marketing-campaign-assets.md)中將檔案連結至促銷活動[。

>[!IMPORTANT]
>
>此模式保留給小型文檔。

在促銷活動中，您也可以參考其他項目，例如促銷優惠券、與特定分支或商店相關的特殊優惠等。 當這些元素包含在大綱中時，它們可以與直接郵件發送相關聯。 [進一步瞭解](#associating-and-structuring-resources-linked-via-a-delivery-outline)。

>[!NOTE]
>
>如果您使用MRM，您也可以管理行銷資源庫，供數位參與者共同作業。 請參閱[管理行銷資源](../../campaign/using/managing-marketing-resources.md)。

### 添加文檔{#adding-documents}

檔案可在促銷活動層級（內容相關檔案）或方案層級（一般檔案）建立關聯。

**[!UICONTROL Documents]**&#x200B;標籤包含：

* 內容（範本、影像等）所需的所有檔案清單 可由Adobe Campaign運營商在本地下載，
* 包含路由器資訊的文檔（如果有）。

文檔通過&#x200B;**[!UICONTROL Edit > Documents]**&#x200B;頁籤連結到程式或促銷活動。

![](assets/s_ncs_user_op_add_document.png)

您也可以透過其控制面板中提供的連結，將檔案新增至促銷活動。

![](assets/add_a_document_in_op.png)

按一下&#x200B;**[!UICONTROL Details]**&#x200B;表徵圖可查看檔案的內容並添加資訊：

![](assets/s_ncs_user_op_add_document_details.png)

在控制面板中，與促銷活動相關的檔案會分組在&#x200B;**[!UICONTROL Document(s)]**&#x200B;區段中，如下列範例所示：

![](assets/s_ncs_user_op_edit_document.png)

您也可以從此檢視中編輯和修改這些檢視。

### 通過交付大綱{#associating-and-structuring-resources-linked-via-a-delivery-outline}關聯和構建連結的資源

>[!NOTE]
>
>傳送大綱只用於直接郵件促銷活動的內容中。

傳送大綱表示一組結構化元素（檔案、分支／商店、促銷優惠券等） 在公司中建立，並用於特定促銷活動。

這些元素被分組在交付大綱中，特定的交付大綱將與交付相關聯；它將在發送到&#x200B;**服務提供者**&#x200B;的抽取檔案中引用，以便附加到傳送。 例如，您可以建立參考分支及其使用的行銷手冊的傳送大綱。

對於促銷活動，傳送大綱可讓您根據特定條件建構要與傳送關聯的外部元素：相關分支、已授予的促銷優惠、邀請參加當地活動等。

#### 建立大綱{#creating-an-outline}

若要建立大綱，請按一下相關促銷活動之&#x200B;**[!UICONTROL Edit > Documents]**&#x200B;標籤中的&#x200B;**[!UICONTROL Delivery outlines]**&#x200B;子標籤。

>[!NOTE]
>
>如果此標籤不存在，則此功能不適用於此促銷活動。 請參閱促銷活動範本設定。
>   
>如需詳細資訊，請參閱[促銷活動範本](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

![](assets/s_ncs_user_op_composition_link.png)

接著，按一下&#x200B;**[!UICONTROL Add a delivery outline]**&#x200B;並建立促銷活動的大綱階層：

1. 按一下右鍵樹的根，然後選擇&#x200B;**[!UICONTROL New > Delivery outlines]**。
1. 按一下右鍵剛建立的大綱，然後選擇&#x200B;**[!UICONTROL New > Item]**&#x200B;或&#x200B;**[!UICONTROL New > Personalization fields]**。

![](assets/s_ncs_user_op_add_composition.png)

大綱可包含項目和個人化欄位、資源和選件：

* 項目可以是實體檔案，例如，此處引用和說明的項目將附加至傳送。
* 個人化欄位可讓您建立與傳送相關的個人化元素，而非收件者。 因此，您可以建立值，以便用於特定目標（歡迎選件、折扣等）的傳送 它們在Adobe Campaign建立，並通過&#x200B;**[!UICONTROL Import personalization fields...]**&#x200B;連結導入到大綱中。

   ![](assets/s_ncs_user_op_add_composition_field.png)

   您也可以按一下清單區域右側的&#x200B;**[!UICONTROL Add]**&#x200B;圖示，直接在大綱中建立這些項目。

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* 資源是在行銷資源控制面板中產生的行銷資源，可透過&#x200B;**[!UICONTROL Campaigns]**&#x200B;標籤的&#x200B;**[!UICONTROL Resources]**&#x200B;連結存取。

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >有關行銷資源的詳情，請參閱[管理行銷資源](../../campaign/using/managing-marketing-resources.md)。

#### 選擇大綱{#selecting-an-outline}

對於每個傳送，可以從為提取大綱保留的節中選擇要關聯的大綱，如以下示例所示：

![](assets/s_ncs_user_op_select_composition.png)

然後，所選輪廓將顯示在窗口的下部區域。 您可使用欄位右側的圖示加以編輯，或使用下拉式清單進行變更：

![](assets/s_ncs_user_op_select_composition_b.png)

傳送的&#x200B;**[!UICONTROL Summary]**&#x200B;標籤也會顯示下列資訊：

![](assets/s_ncs_user_op_select_composition_c.png)

#### 提取結果{#extraction-result}

在提取併發送給服務提供商的檔案中，大綱的名稱以及其特性（成本、說明等）（如果適用） 根據與服務提供商相關聯的導出模板中的資訊添加到內容中。

在以下示例中，與傳送相關聯的大綱的標籤、估計成本和說明將添加到提取檔案中。

![](assets/s_ncs_user_op_composition_in_export_template.png)

導出模型必須與為相關交付選擇的服務提供商相關聯。 請參閱[建立服務提供商及其成本結構](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

>[!NOTE]
>
>有關導出的詳細資訊，請參閱[Getting Started](../../platform/using/get-started-data-import-export.md)部分。

#### 教學課程影片{#create-email-video}

此影片說明如何在Adobe Campaign建立促銷活動和電子郵件。

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

其他促銷活動操作影片可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。