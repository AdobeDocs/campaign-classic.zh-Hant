---
product: campaign
title: 使用內容範本
description: 使用內容範本
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Templates
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# 使用內容範本{#using-a-content-template}



## 關於內容範本 {#about-content-templates}

內容範本可供參考，並直接用於傳遞。 請參閱 [透過內容管理建立傳遞](#creating-a-delivery-via-content-management)

它們也可用來建立內容例項。 建立這些例項後，即可傳送(請參閱 [傳遞內容例項](#delivering-a-content-instance))或匯出(請參閱 [建立內容例項](#creating-a-content-instance))。

## 透過內容管理建立傳遞 {#creating-a-delivery-via-content-management}

在使用輸入欄位輸入內容的檢視中，您可以參考傳送中的內容範本。 傳送精靈中會新增另一個索引標籤，以定義傳送內容。

![](assets/s_ncs_content_deliver_a_content.png)

版面將會根據選取的設定自動套用。 若要檢視，請按一下 **[!UICONTROL HTML preview]** (或 **[!UICONTROL Text preview]** )，然後選取要測試個人化元素的收件者。

![](assets/s_ncs_content_deliver_a_content_html.png)

如需詳細資訊，請參閱完整實作範例： [在傳遞精靈中建立內容](use-case--creating-content-management.md#creating-content-in-the-delivery-wizard).

## 建立內容例項 {#creating-a-content-instance}

您可以直接在Adobe Campaign樹狀結構中建立內容，以用於工作流程、匯出或直接插入新傳送。

應用以下步驟：

1. 選取 **[!UICONTROL Resources > Contents]** 節點，按一下右鍵並選擇 **[!UICONTROL Properties]**.

   ![](assets/s_ncs_content_folder_properties.png)

1. 選擇將對此資料夾處於活動狀態的發佈模板。

   ![](assets/s_ncs_content_folder_templates.png)

1. 您現在可以使用 **[!UICONTROL New]** 按鈕。

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. 輸入表單中的欄位。

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. 然後按一下 **[!UICONTROL HTML preview]** 標籤來檢視呈現。 在此，不會輸入從資料庫擷取的個人化欄位。

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. 建立內容後，內容會新增至可用內容清單。 按一下 **[!UICONTROL Properties]** 連結以變更其標籤、狀態或檢視其歷史記錄。

   ![](assets/s_ncs_content_folder_template_properties.png)

1. 如有必要，內容一經核准後，即可使用工具列上的適當按鈕產生。

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >您可以授權產生未核准的內容。 若要這麼做，請變更發佈範本中的相關選項。 有關詳細資訊，請參閱 [建立和設定範本](publication-templates.md#creating-and-configuring-the-template).

   HTML和文字內容預設會在 **發佈** Adobe Campaign例項的資料夾。 您可以透過 **NcmPublishingDir** 選項。

## 傳遞內容例項 {#delivering-a-content-instance}

若要建立內容例項並傳送，傳遞範本必須連結至用於產生此內容的發佈範本。 有關詳細資訊，請參閱 [傳送](publication-templates.md#delivery).

此外，內容儲存資料夾必須專用於從此發佈範本擷取的內容（當內容資料夾可讓您產生數種內容類型時，無法自動建立傳送）。

若要根據選取的內容自動建立傳送，請按一下 **[!UICONTROL Delivery]** 圖示並選取範本。

![](assets/s_ncs_content_folder_create_the_delivery.png)

自動輸入文本和HTML內容。
