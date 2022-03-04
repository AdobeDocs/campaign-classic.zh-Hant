---
product: campaign
title: 使用內容範本
description: 使用內容範本
feature: Templates
exl-id: e43dd68e-2e95-4367-9029-4622fbcb1759
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 3%

---

# 使用內容範本{#using-a-content-template}

![](../../assets/common.svg)

## 關於內容模板 {#about-content-templates}

內容模板可以直接在交付中引用和使用。 請參閱 [通過內容管理建立交付](#creating-a-delivery-via-content-management)

它們還可用於建立內容實例。 一旦建立了這些實例，這些實例就可以交付(請參閱 [提供內容實例](#delivering-a-content-instance))或導出(請參閱 [建立內容實例](#creating-a-content-instance))。

## 通過內容管理建立交付 {#creating-a-delivery-via-content-management}

在使用輸入欄位輸入內容時，可以在交貨中引用內容模板。 將附加標籤添加到傳遞嚮導中以定義傳遞內容。

![](assets/s_ncs_content_deliver_a_content.png)

佈局將基於所選設定自動應用。 要查看它，請按一下 **[!UICONTROL HTML preview]** 或 **[!UICONTROL Text preview]** )並選擇一個收件人以test個性化元素。

![](assets/s_ncs_content_deliver_a_content_html.png)

有關詳細資訊，請參閱完整實施示例： [在傳遞嚮導中建立內容](use-case--creating-content-management.md#creating-content-in-the-delivery-wizard)。

## 建立內容實例 {#creating-a-content-instance}

您可以直接在Adobe Campaign樹中建立內容，以用於工作流、導出或直接注入到新交貨中。

應用以下步驟：

1. 選擇 **[!UICONTROL Resources > Contents]** 的子目錄，按一下右鍵並選擇 **[!UICONTROL Properties]**。

   ![](assets/s_ncs_content_folder_properties.png)

1. 選擇此資料夾將處於活動狀態的發佈模板。

   ![](assets/s_ncs_content_folder_templates.png)

1. 您現在可以使用 **[!UICONTROL New]** 按鈕。

   ![](assets/s_ncs_content_folder_create_a_template.png)

1. 在窗體中輸入欄位。

   ![](assets/s_ncs_content_folder_use_a_template.png)

1. 然後按一下 **[!UICONTROL HTML preview]** 頁籤 此處，未輸入從資料庫獲取的個性化欄位。

   ![](assets/s_ncs_content_folder_use_a_template_preview.png)

1. 建立內容後，內容將添加到可用內容清單中。 按一下 **[!UICONTROL Properties]** 連結以更改其標籤、狀態或查看其歷史記錄。

   ![](assets/s_ncs_content_folder_template_properties.png)

1. 如有必要，內容一旦獲得批准，就可以使用工具欄上的相應按鈕生成。

   ![](assets/s_ncs_content_folder_template_generate.png)

   >[!NOTE]
   >
   >您可以授權生成未批准的內容。 為此，請更改發佈模板中的相關選項。 有關此內容的詳細資訊，請參閱 [建立和配置模板](publication-templates.md#creating-and-configuring-the-template)。

   預設情況下，HTML和文本內容將在 **發佈** 資料夾。 您可以更改發佈資料夾，這要歸功於 **NcmPublishingDir** 的雙曲餘切值。

## 提供內容實例 {#delivering-a-content-instance}

要建立內容實例並傳遞它，需要將傳遞模板連結到用於生成此內容的發佈模板。 有關此內容的詳細資訊，請參閱 [交貨](publication-templates.md#delivery)。

此外，內容儲存資料夾必須專用於從此發佈模板獲取的內容（當內容資料夾允許您生成多種類型的內容時，無法自動建立傳送）。

要根據所選內容自動建立傳遞，請按一下 **[!UICONTROL Delivery]** 表徵圖，然後選擇模板。

![](assets/s_ncs_content_folder_create_the_delivery.png)

文本和HTML內容將自動輸入。
