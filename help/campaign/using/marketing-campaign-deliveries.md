---
product: campaign
title: 行銷活動傳遞
description: 瞭解有關市場營銷活動交付的更多資訊
feature: Resource Management, Cross Channel Orchestration
exl-id: 1dd3c080-444d-45f8-9562-d2d01a9d2860
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 2%

---

# 行銷活動傳遞 {#marketing-campaign-deliveries}

![](../../assets/common.svg)

可通過市場活動控制面板、市場活動工作流或直接通過交貨概覽建立交貨。

從市場活動建立交貨後，交貨將連結到此市場活動並在市場活動級別進行合併。

![](assets/do-not-localize/how-to-video.png)[ 在影片中探索此功能](#create-email-video)

## 建立傳遞 {#creating-deliveries}

要建立連結到市場活動的交貨，請按一下 **[!UICONTROL Add a delivery]** 連結。

![](assets/campaign_op_add_delivery.png)

建議的配置適用於不同類型的交付：直郵、電子郵件、移動頻道。 [了解更多](../../delivery/using/steps-about-delivery-creation-steps.md)。

## 開始交貨 {#starting-a-delivery}

一旦所有批准都獲得批准，交付即可開始。 然後，交貨過程取決於交貨類型。 有關電子郵件或移動渠道交付，請參閱 [啟動聯機交貨](#starting-an-online-delivery)，有關直接郵件遞送，請參閱 [啟動離線傳遞](#starting-an-offline-delivery)。

### 開始聯機交貨 {#starting-an-online-delivery}

一旦授予所有批准請求，交貨狀態將更改為 **[!UICONTROL Pending confirmation]** 可由操作員啟動。 在適當情況下，將通知指定為審閱者以開始交付的Adobe Campaign操作員（或操作員組）準備開始交付。

>[!NOTE]
>
>如果指定特定運算子或一組運算子用於在交貨的屬性中啟動交貨，則您還可以允許負責交貨的操作員確認發送。 為此，請激活 **NMS_ActivateOwnerConfirmation** 選項 **1** 值。 這些選項是從 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** 的子菜單。
>  
>要停用此選項，請輸入 **0** 值。 然後，發送確認過程將作為預設值運行：只有指定用於發送的操作員或一組操作員（或管理員）才能確認和執行發送。

![](assets/s_ncs_user_edit_del_to_start_from_del.png)

該資訊也顯示在市場活動控制面板上。 的 **[!UICONTROL Confirm delivery]** 連結可啟動交貨。

![](assets/s_ncs_user_edit_del_to_start.png)

通過確認消息，您可以保護此操作。

### 啟動離線交貨 {#starting-an-offline-delivery}

一旦所有批准都獲得，交貨狀態將更改為 **[!UICONTROL Pending extraction]**。 提取檔案通過特殊工作流建立，在預設配置中，當直郵遞送處於待提取狀態時，該工作流自動啟動。 當進程正在進行時，該進程將顯示在儀表板中，並可通過其連結進行編輯。

>[!NOTE]
>
>與市場活動包相關的技術工作流在 [技術工作流清單](../../workflow/using/about-technical-workflows.md)。

**步驟1 — 檔案批准**

抽取工作流成功執行後，必須批准抽取檔案（前提是在傳遞設定中選擇了抽取檔案批准）。

有關此內容的詳細資訊，請參閱 [批准提取檔案](../../campaign/using/marketing-campaign-approval.md#approving-an-extraction-file)。

**步驟2 — 向服務提供商批准消息**

* 一旦提取檔案獲得批准，您就可以生成路由器通知電子郵件的證明。 此電子郵件消息基於傳遞模板構建。 必須批准。

   >[!NOTE]
   >
   >只有在批准窗口中啟用了校樣的發送和批准時，此步驟才可用。

![](assets/s_ncs_user_file_valid_select_BAT.png)


* 按一下 **[!UICONTROL Send a proof]** 按鈕。

   證明目標必須事先確定。

   您可以根據需要建立盡可能多的校樣。 通過 **[!UICONTROL Direct mail...]** 交貨詳細資訊的連結。

   ![](assets/s_ncs_user_file_notif_submit_proof.png)

* 交貨狀態更改為 **[!UICONTROL To submit]**。 按一下 **[!UICONTROL Submit proofs]** 按鈕啟動審批流程。

   ![](assets/s_ncs_user_file_notif_submit_proof_validation.png)

* 交貨狀態更改為 **[!UICONTROL Proof to validate]** 按鈕允許您接受或拒絕批准。

   ![](assets/s_ncs_user_file_notif_supplier_link.png)

   您可以接受或拒絕此審批，或返回提取步驟。

   ![](assets/s_ncs_user_file_notif_supplier_link_confirm.png)

* 提取檔案將發送到路由器，並完成傳送。

### 費用和庫存計算 {#calculation-of-costs-and-stocks}

檔案提取將啟動兩個操作：預算計算和庫存計算。 將更新預算條目。

* 的 **[!UICONTROL Budget]** 頁籤，用於管理市場活動的預算。 成本條目的合計顯示在 **[!UICONTROL Calculates cost]** 市場活動主頁籤的欄位及其所屬的程式。 金額也反映在市場活動預算中。

   實際成本最終將由路由器提供的資訊計算。 只對實際發送的消息開票。

* 股票於 **[!UICONTROL Administration > Campaign management > Stocks]** 樹的節點，以及 **[!UICONTROL Administration > Campaign management > Service providers]** 的下界。

   坯件行在坯件部分中可見。 要定義初始庫存，請開啟一個庫存行。 每次交貨時，庫存都會減少。 您可以定義預警級別和通知。

>[!NOTE]
>
>有關成本計算和庫存管理的詳細資訊，請參閱 [供應商、庫存和預算](../../campaign/using/providers--stocks-and-budgets.md)。

## 管理相關文件 {#managing-associated-documents}

您可以為行銷活動跟各種檔案建立關聯：報告、照片、網頁、圖表等。這些文檔可以採用任何格式(MicrosoftWord、PowerPoint、PNG、JPG、AcrobatPDF等)。 瞭解如何將文檔與市場活動連結 [此部分](../../campaign/using/marketing-campaign-assets.md)。

>[!IMPORTANT]
>
>此模式保留用於小文檔。

在市場活動中，您還可以參考其他項目，如促銷優惠券、與特定分店或商店相關的特別優惠等。 當這些元素包含在大綱中時，它們可以與直接郵寄相關聯。 [了解更多](#associating-and-structuring-resources-linked-via-a-delivery-outline)。

>[!NOTE]
>
>如果您使用MRM，您還可以管理市場營銷資源庫，這些資源庫可供多個參與者協作工作。 請參閱 [管理市場營銷資源](../../mrm/using/managing-marketing-resources.md)。

### 添加文檔 {#adding-documents}

文檔可以在市場活動層（上下文文檔）或方案層（一般文檔）關聯。

的 **[!UICONTROL Documents]** 頁籤包含：

* 內容所需的所有文檔的清單（模板、影像等） 可以由Adobe Campaign運營商在本地下載，
* 包含路由器資訊的文檔（如果有）。

文檔通過 **[!UICONTROL Edit > Documents]** 頁籤。

![](assets/s_ncs_user_op_add_document.png)

您還可以通過其控制面板中提供的連結將文檔添加到市場活動。

![](assets/add_a_document_in_op.png)

按一下 **[!UICONTROL Details]** 表徵圖，查看檔案內容並添加資訊：

![](assets/s_ncs_user_op_add_document_details.png)

在控制面板中，與市場活動關聯的文檔將分組到 **[!UICONTROL Document(s)]** 部分，如下例所示：

![](assets/s_ncs_user_op_edit_document.png)

也可以從此視圖編輯和修改它們。

### 通過交貨大綱連結的關聯和結構資源 {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>在直接郵寄活動的上下文中專門使用遞送大綱。

交貨大綱表示一組結構化元素（文檔、分支/商店、促銷優惠券等） 為公司和特定市場活動建立的。

這些元素按交貨大綱分組，特定交貨大綱將與交貨相關聯；將在發送到 **服務提供者** 才能被附在貨物上。 例如，您可以建立一個交付大綱，該大綱引用分支及其使用的營銷手冊。

對於市場活動，交貨大綱允許您根據以下特定標準構造要與交貨關聯的外部要素：分行、授予的促銷優惠、參加當地活動的邀請等。

#### 建立大綱 {#creating-an-outline}

要建立大綱，請按一下 **[!UICONTROL Delivery outlines]** 頁籤 **[!UICONTROL Edit > Documents]** 頁籤。

>[!NOTE]
>
>如果此標籤不存在，則此功能不可用於此市場活動。 請參閱市場活動模板配置。
>   
>有關此內容的詳細資訊，請參閱 [市場活動模板](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

![](assets/s_ncs_user_op_composition_link.png)

下一步，按一下 **[!UICONTROL Add a delivery outline]** 建立市場活動大綱的層次結構：

1. 按一下右鍵樹的根並選擇 **[!UICONTROL New > Delivery outlines]**。
1. 按一下右鍵剛建立的大綱並選擇 **[!UICONTROL New > Item]** 或 **[!UICONTROL New > Personalization fields]**。

![](assets/s_ncs_user_op_add_composition.png)

大綱可包含項目和個性化欄位、資源和優惠：

* 項目可以是物理文檔，例如，這些文檔在此處引用和描述，並將附加到交貨中。
* 通過個性化欄位，您可以建立與交貨相關的個性化元素，而不是收件人。 因此，可以為特定目標（歡迎優惠、折扣等）建立要在交貨中使用的值。 它們在Adobe Campaign建立，並通過 **[!UICONTROL Import personalization fields...]** 的子菜單。

   ![](assets/s_ncs_user_op_add_composition_field.png)

   也可以通過按一下 **[!UICONTROL Add]** 表徵圖。

   ![](assets/s_ncs_user_op_add_composition_field_button.png)

* 資源是在通過以下方式訪問的市場營銷資源控制面板中生成的市場營銷資源 **[!UICONTROL Resources]** 連結 **[!UICONTROL Campaigns]** 頁籤。

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >有關市場營銷資源的詳細資訊，請參閱 [管理市場營銷資源](../../mrm/using/managing-marketing-resources.md)。

#### 選擇大綱 {#selecting-an-outline}

對於每個交貨，您都可以從為提取大綱保留的節中選擇要關聯的大綱，如下例所示：

![](assets/s_ncs_user_op_select_composition.png)

選定的輪廓隨後顯示在窗口的下部。 可以使用欄位右側的表徵圖編輯它，或使用下拉清單更改它：

![](assets/s_ncs_user_op_select_composition_b.png)

的 **[!UICONTROL Summary]** 的子菜單中，還顯示以下資訊：

![](assets/s_ncs_user_op_select_composition_c.png)

#### 提取結果 {#extraction-result}

在提取併發送到服務提供商的檔案中，列出大綱的名稱，並在適當情況下列出其特徵（成本、說明等） 根據與服務提供商相關聯的導出模板中的資訊添加到內容。

在以下示例中，與交貨關聯的大綱的標籤、估計成本和說明將添加到提取檔案。

![](assets/s_ncs_user_op_composition_in_export_template.png)

導出模型必須與為相關交貨選擇的服務提供商關聯。 請參閱 [建立服務提供商及其成本結構](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

>[!NOTE]
>
>有關出口的詳細資訊，請參閱 [入門](../../platform/using/get-started-data-import-export.md) 的子菜單。

#### 教程視頻 {#create-email-video}

這段視頻說明了如何在Adobe Campaign建立活動和電子郵件。

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

還提供了其他市場活動操作視頻 [這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)。
