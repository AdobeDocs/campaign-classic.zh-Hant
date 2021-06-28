---
product: campaign
title: 行銷活動檔案和傳遞大綱
description: 進一步了解行銷活動檔案和傳送大綱
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
exl-id: 891252b0-4700-4a2a-a632-63aad5ce75d7
source-git-commit: 690f7c4e62203127da7a7055afa0ee8ad4a2bce4
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 1%

---

# 管理相關文件 {#managing-associated-documents}

您可以將各種檔案與促銷活動建立關聯：報告、照片、網頁、圖表等。 這些檔案可以是任何格式(Microsoft Word、PowerPoint、PNG、JPG、Acrobat PDF等)。

>[!IMPORTANT]
>
>此功能專為小型資產和檔案保留。

在促銷活動中，您也可以參考其他項目，例如促銷優惠券、與特定品牌或商店相關的特別優惠等。 當這些元素包含在大綱中時，它們可以與直接郵件傳送相關聯。 請參閱[關聯和結構通過傳遞大綱連結的資源](#associating-and-structuring-resources-linked-via-a-delivery-outline)。

>[!NOTE]
>
>如果您使用「促銷活動行銷資源管理」模組，您也可以管理可供數位使用者協作工作的行銷資源庫。 [深入瞭解](../../mrm/using/managing-marketing-resources.md)。

## 添加文檔 {#adding-documents}

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

## 關聯並結構通過傳遞大綱連結的資源 {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>傳送大綱專門用於直接郵件促銷活動的內容。

傳遞大綱表示一組結構化元素（文檔、商店、促銷優惠券等） 由公司建立，並用於特定促銷活動。

這些元素會分組在傳送大綱中，每個傳送大綱都與傳送相關聯；會在傳送至&#x200B;**服務提供者**&#x200B;的解壓縮檔案中參考它，以便附加至傳送。 例如，您可以建立傳遞大綱，參考分支及其使用的行銷手冊。

對於促銷活動，傳送大綱可讓您根據特定條件來建構要與傳送相關聯的外部元素：相關分支、已授予的促銷優惠、參加當地活動的邀請等。

### 建立大綱 {#creating-an-outline}

若要建立大綱，請按一下相關促銷活動&#x200B;**[!UICONTROL Edit > Documents]**&#x200B;標籤中的&#x200B;**[!UICONTROL Delivery outlines]**&#x200B;子標籤。

>[!NOTE]
>
>如果此標籤不存在，則此功能無法用於此促銷活動。 請參閱促銷活動範本設定。
>   
>有關模板的詳細資訊，請參閱[此部分](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

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
   >如需行銷資源的詳細資訊，請參閱[此區段](../../mrm/using/managing-marketing-resources.md)。

### 選擇大綱 {#selecting-an-outline}

對於每個傳送，可以從為提取大綱保留的節中選擇要關聯的大綱，如下例所示：

![](assets/s_ncs_user_op_select_composition.png)

然後，所選大綱將顯示在窗口的下部部分。 您可以使用欄位右側的圖示加以編輯，或使用下拉式清單加以變更：

![](assets/s_ncs_user_op_select_composition_b.png)

傳送的&#x200B;**[!UICONTROL Summary]**&#x200B;標籤也會顯示此資訊：

![](assets/s_ncs_user_op_select_composition_c.png)

### 提取結果 {#extraction-result}

在提取併發送到服務提供商的檔案中，大綱的名稱，並在適當時，其特徵（成本、說明等） 根據與服務提供者相關聯的匯出範本中的資訊，將其新增至內容。

在以下示例中，與傳送關聯的大綱的標籤、估計成本和說明將添加到解壓縮檔案中。

![](assets/s_ncs_user_op_composition_in_export_template.png)

導出模型必須與為相關傳送選擇的服務提供商相關聯。 請參閱[本節](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

>[!NOTE]
>
>有關導出的詳細資訊，請參閱[此部分](../../platform/using/get-started-data-import-export.md)部分。
