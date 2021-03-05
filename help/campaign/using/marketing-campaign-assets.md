---
solution: Campaign Classic
product: campaign
title: 行銷宣傳檔案和傳送大綱
description: 進一步瞭解行銷宣傳檔案和發佈大綱
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---


# 管理相關文檔{#managing-associated-documents}

您可以將各種檔案與促銷活動建立關聯：報表、像片、網頁、圖表等。 這些檔案可以是任何格式(Microsoft Word、PowerPoint、PNG、JPG、AcrobatPDF等)。

>[!IMPORTANT]
>
>此功能保留給小型資產和檔案。

在促銷活動中，您也可以參考其他項目，例如促銷優惠券、與特定品牌或商店相關的特殊優惠等。 當這些元素包含在大綱中時，它們可以與直接郵件發送相關聯。 請參閱[關聯和結構通過交付大綱連結的資源](#associating-and-structuring-resources-linked-via-a-delivery-outline)。

>[!NOTE]
>
>如果您使用「促銷活動行銷資源管理」模組，您也可以管理可供數位使用者共同作業的行銷資源庫。 [進一步瞭解](../../campaign/using/managing-marketing-resources.md)。

## 添加文檔{#adding-documents}

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

## 關聯並構建通過交付大綱{#associating-and-structuring-resources-linked-via-a-delivery-outline}連結的資源

>[!NOTE]
>
>傳送大綱只用於直接郵件促銷活動的內容中。

傳送大綱表示一組結構化元素（檔案、商店、促銷優惠券等） 公司和特定促銷活動所建立。

這些元素被分組在傳送大綱中，每個傳送大綱都與傳送相關聯；它將在發送到&#x200B;**服務提供者**&#x200B;的抽取檔案中引用，以便附加到傳送。 例如，您可以建立參考分支及其使用的行銷手冊的傳送大綱。

對於促銷活動，傳送大綱可讓您根據特定條件建構要與傳送關聯的外部元素：相關分支、已授予的促銷優惠、邀請參加當地活動等。

### 建立大綱{#creating-an-outline}

若要建立大綱，請按一下相關促銷活動之&#x200B;**[!UICONTROL Edit > Documents]**&#x200B;標籤中的&#x200B;**[!UICONTROL Delivery outlines]**&#x200B;子標籤。

>[!NOTE]
>
>如果此標籤不存在，則此功能不適用於此促銷活動。 請參閱促銷活動範本設定。
>   
>有關模板的詳細資訊，請參閱[本節](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

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

* 資源是在行銷資源儀表板中產生的行銷資源，可透過&#x200B;**[!UICONTROL Campaigns]**&#x200B;宇宙的&#x200B;**[!UICONTROL Resources]**&#x200B;連結存取。

   ![](assets/s_ncs_user_mkg_resource_ovv.png)

   >[!NOTE]
   >
   >如需行銷資源的詳細資訊，請參閱[本節](../../campaign/using/managing-marketing-resources.md)。

### 選擇大綱{#selecting-an-outline}

對於每個傳送，可以從為提取大綱保留的節中選擇要關聯的大綱，如以下示例所示：

![](assets/s_ncs_user_op_select_composition.png)

然後，所選輪廓將顯示在窗口的下部區域。 您可使用欄位右側的圖示加以編輯，或使用下拉式清單進行變更：

![](assets/s_ncs_user_op_select_composition_b.png)

傳送的&#x200B;**[!UICONTROL Summary]**&#x200B;標籤也會顯示下列資訊：

![](assets/s_ncs_user_op_select_composition_c.png)

### 提取結果{#extraction-result}

在提取併發送給服務提供商的檔案中，大綱的名稱以及其特性（成本、說明等）（如果適用） 根據與服務提供商相關聯的導出模板中的資訊添加到內容中。

在以下示例中，與傳送相關聯的大綱的標籤、估計成本和說明將添加到提取檔案中。

![](assets/s_ncs_user_op_composition_in_export_template.png)

導出模型必須與為相關交付選擇的服務提供商相關聯。 請參閱[本節](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

>[!NOTE]
>
>有關導出的詳細資訊，請參閱[本節](../../platform/using/get-started-data-import-export.md)節。
