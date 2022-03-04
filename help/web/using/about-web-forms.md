---
product: campaign
title: 開始使用網路表單
description: 在市場活動中開始使用Web表單
feature: Landing Pages, Web Forms
exl-id: 63602bed-ace6-4632-a735-5d268a7d72d0
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 5%

---

# 開始使用網路表單{#about-web-forms}

![](../../assets/common.svg)

Adobe Campaign整合了一個圖形模組，用於定義和發佈Web表單，以建立包含輸入和選擇欄位的頁面，其中可能包含資料庫中的資料。 這允許您設計和發佈網頁，用戶可以訪問這些網頁查看或輸入資訊。

本章詳細介紹了Web表單的建立和管理、如何管理欄位和頁面以及儲存和保存模式。

>[!CAUTION]
>
>出於隱私原因，我們建議對所有外部資源使用HTTPS。

## 建立Web表單的步驟 {#steps-for-creating-a-web-form}

本章詳細介紹了設計 **Web窗體** 在Adobe Campaign鍵入form ，以及可用的選項和配置。 Adobe Campaign允許您將此Web表單提供給用戶，並收集和存檔資料庫中的答案。

>[!CAUTION]
>
>配置Web應用程式和Web表單時，需要900像素的垂直解析度最低(例如：1600x900)。

通過的Web應用程式菜單訪問Web表單 **市場活動** 頁籤。 在Adobe Campaign樹上，它們被分組在 **[!UICONTROL Resources > Online > Web Applications]** 的下界。

要建立Web表單，請按一下 **[!UICONTROL Create]** 按鈕。

![](assets/webapp_create_new.png)

選擇Web表單模板( **[!UICONTROL newWebForm]** )。

![](assets/s_ncs_admin_survey_select_template.png)

這將帶您到窗體的儀表板。

![](assets/webapp_empty_dashboard.png)

的 **[!UICONTROL Edit]** 頁籤。

![](assets/webapp_edit_tab.png)

要定義Web表單的配置和內容，請應用以下步驟：

* 首先建立所需的頁面和控制項：輸入欄位、下拉清單、HTML內容等。

   下面詳細介紹了此步驟。

* 定義頁面順序和顯示條件。

   此步驟在 [定義Web表單頁排序](defining-web-forms-page-sequencing.md)。

* 如有必要，請翻譯內容。

   此步驟在 [翻譯Web表單](translating-a-web-form.md)。

## 關於Web表單設計 {#about-web-forms-designing}

表單的頁面通過特定編輯器建立，該編輯器允許您定義和配置輸入區域（文本）、選擇欄位（清單、複選框等） 和靜態元素（影像、HTLM內容等）。 可以將它們分組到容器中，並更改其佈局以滿足您的需要(有關詳細資訊，請參閱 [建立容器](defining-web-forms-layout.md#creating-containers))。

以下各節詳細介紹了如何定義表單螢幕的內容和佈局：

* [新增欄位至網路表單](adding-fields-to-a-web-form.md),
* [插入HTML內容](static-elements-in-a-web-form.md#inserting-html-content)。
* [網路表單中的靜態元素](static-elements-in-a-web-form.md),
* [定義網路表單版面](defining-web-forms-layout.md).

>[!NOTE]
>
>* 在頁面設計期間，可在 **[!UICONTROL Preview]** 頁籤。 要查看更改，請先保存表單。 所有錯誤都顯示在 **[!UICONTROL Log]** 頁籤。
>* 要確保頁面顯示和資訊儲存按適當順序進行，請在Web窗體中啟用調試模式。 要執行此操作，請轉到 **[!UICONTROL Preview]** 頁籤，並檢查 **[!UICONTROL Enable debug mode]** 框中：所有收集到的資訊和可能的執行錯誤都將顯示在每個頁面的底部。
>


### 使用工具欄中的表徵圖 {#using-the-icons-in-the-toolbar}

也可以使用工具欄中的表徵圖或按一下右鍵來插入輸入區域。

![](assets/s_ncs_admin_webform_add_selection.png)

在這種情況下，首先選擇要添加的欄位類型和應答儲存模式。

![](assets/s_ncs_admin_webform_select_storage.png)

按一下 **[!UICONTROL Ok]** 的子菜單。

![](assets/s_ncs_admin_webform_confirm_storage.png)
