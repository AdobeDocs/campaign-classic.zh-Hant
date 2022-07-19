---
product: campaign
title: 營銷活動文檔和交付大綱
description: 瞭解有關市場營銷活動文檔和交付大綱的詳細資訊
feature: Campaigns
exl-id: 891252b0-4700-4a2a-a632-63aad5ce75d7
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 1%

---

# 管理相關文件 {#managing-associated-documents}

![](../../assets/v7-only.svg)

您可以將各種單據與市場活動關聯：報告、照片、網頁、圖表等。 這些文檔可以採用任何格式(MicrosoftWord、PowerPoint、PNG、JPG、AcrobatPDF等)。

>[!IMPORTANT]
>
>此功能保留用於小資產和文檔。

在市場活動中，您還可以參考其他項目，如促銷優惠券、與特定品牌或商店相關的特別優惠等。 當這些元素包含在大綱中時，它們可以與直接郵寄相關聯。 請參閱 [通過交貨大綱連結的關聯和結構資源](#associating-and-structuring-resources-linked-via-a-delivery-outline)。

>[!NOTE]
>
>如果您使用「市場活動市場營銷資源管理」模組，您還可以管理市場營銷資源庫，這些資源庫可供多個用戶協作工作。 [了解更多資訊](../../mrm/using/managing-marketing-resources.md)。

## 添加文檔 {#adding-documents}

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

## 通過交貨大綱連結的關聯和結構資源 {#associating-and-structuring-resources-linked-via-a-delivery-outline}

>[!NOTE]
>
>在直接郵寄活動的上下文中專門使用遞送大綱。

交貨大綱表示一組結構化元素（文檔、商店、促銷優惠券等） 由公司建立，並用於特定市場活動。

這些元素按交貨大綱分組，每個交貨大綱都與交貨相關聯；將在發送到 **服務提供者** 才能被附在貨物上。 例如，您可以建立一個交付大綱，該大綱引用分支及其使用的營銷手冊。

對於市場活動，交貨大綱允許您根據以下特定標準構造要與交貨關聯的外部要素：分行、授予的促銷優惠、參加當地活動的邀請等。

### 建立大綱 {#creating-an-outline}

要建立大綱，請按一下 **[!UICONTROL Delivery outlines]** 頁籤 **[!UICONTROL Edit > Documents]** 頁籤。

>[!NOTE]
>
>如果此標籤不存在，則此功能不可用於此市場活動。 請參閱市場活動模板配置。
>   
>有關模板的詳細資訊，請參閱 [此部分](../../campaign/using/marketing-campaign-templates.md#campaign-templates)。

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
   >有關市場營銷資源的詳細資訊，請參閱 [此部分](../../mrm/using/managing-marketing-resources.md)。

### 選擇大綱 {#selecting-an-outline}

對於每個交貨，您都可以從為提取大綱保留的節中選擇要關聯的大綱，如下例所示：

![](assets/s_ncs_user_op_select_composition.png)

選定的輪廓隨後顯示在窗口的下部。 可以使用欄位右側的表徵圖編輯它，或使用下拉清單更改它：

![](assets/s_ncs_user_op_select_composition_b.png)

的 **[!UICONTROL Summary]** 的子菜單中，還顯示以下資訊：

![](assets/s_ncs_user_op_select_composition_c.png)

### 提取結果 {#extraction-result}

在提取併發送到服務提供商的檔案中，列出大綱的名稱，並在適當情況下列出其特徵（成本、說明等） 根據與服務提供商相關聯的導出模板中的資訊添加到內容。

在以下示例中，與交貨關聯的大綱的標籤、估計成本和說明將添加到提取檔案。

![](assets/s_ncs_user_op_composition_in_export_template.png)

導出模型必須與為相關交貨選擇的服務提供商關聯。 請參閱[本節](../../campaign/using/providers--stocks-and-budgets.md#creating-service-providers-and-their-cost-structures)。

>[!NOTE]
>
>有關出口的詳細資訊，請參閱 [此部分](../../platform/using/get-started-data-import-export.md) 的子菜單。
