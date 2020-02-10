---
title: 關於Web表單
seo-title: 關於Web表單
description: 關於Web表單
seo-description: null
page-status-flag: never-activated
uuid: 1d129af4-008b-4f6a-9094-b2edd6c1eee1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 3b8e4691-fcbc-48ef-b529-11c9a9a9d788
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 關於Web表單{#about-web-forms}

Adobe Campaign整合了圖形模組，用於定義和發佈Web表單，以建立包含輸入和選擇欄位的頁面，並可能包含資料在資料庫中。 這可讓您設計並張貼網頁，讓使用者可存取這些網頁以檢視或輸入資訊。

本章詳細說明Web表單的建立與管理、如何管理欄位和頁面，以及儲存與儲存模式。

>[!CAUTION]
>
>基於隱私權原因，我們建議對所有外部資源使用HTTPS。

## 建立Web表單的步驟 {#steps-for-creating-a-web-form}

本章詳細說明在Adobe Campaign中設計 **webForm** type表單所需的步驟，以及可用的選項和設定。 Adobe Campaign可讓您將此Web表格提供給使用者，並收集和封存資料庫中的答案。

>[!CAUTION]
>
>在設定Web應用程式和Web表單時，您需要最低900像素的垂直解析度(例如：1600x900)。

您可透過「促銷活動」標籤的「Web應用程式」選單來存 **取Web** 表格。 在Adobe Campaign樹狀結構中，這些促銷活動會分組在節 **[!UICONTROL Resources > Online > Web Applications]** 點下。

要建立Web表單，請按一下Web **[!UICONTROL Create]** 應用程式清單上方的按鈕。

![](assets/webapp_create_new.png)

選擇Web表單範本( **[!UICONTROL newWebForm]** 預設)。

![](assets/s_ncs_admin_survey_select_template.png)

這會帶您進入表單的控制面板。

![](assets/webapp_empty_dashboard.png)

此標 **[!UICONTROL Edit]** 簽可讓您建立內容。

![](assets/webapp_edit_tab.png)

要定義Web表單的配置和內容，請應用以下步驟：

* 首先，請建立必要的頁面並進行檢查：輸入欄位、下拉式清單、HTML內容等。

   此步驟在下面詳述。

* 定義頁面順序並設定顯示條件。

   此步驟在定義Web表 [單頁面順序中詳述](../../web/using/defining-web-forms-page-sequencing.md)。

* 視需要翻譯內容。

   此步驟在轉換Web表 [單中有詳細說明](../../web/using/translating-a-web-form.md)。

## 關於網頁表單設計 {#about-web-forms-designing}

表單的頁面是透過特定編輯器建立的，可讓您定義和設定輸入區域（文字）、選擇欄位（清單、核取方塊等）和靜態元素（影像、HTLM內容等）。 您可將它們分組至容器，並依您的需求變更其版面配置(如需詳細資訊，請參閱「建 [立容器](../../web/using/defining-web-forms-layout.md#creating-containers)」)。

以下章節詳細說明如何定義表單畫面的內容和版面：

* [新增欄位至Web表格](../../web/using/adding-fields-to-a-web-form.md),
* [插入HTML內容](../../web/using/static-elements-in-a-web-form.md#inserting-html-content),
* [Web表單中的靜態元素](../../web/using/static-elements-in-a-web-form.md),
* [定義Web表單版面](../../web/using/defining-web-forms-layout.md)。

>[!NOTE]
>
>* 在頁面設計期間，您可以在標籤中檢視最終演 **[!UICONTROL Preview]** 算。 若要檢視變更，請先儲存表單。 任何錯誤都會顯示在標 **[!UICONTROL Log]** 簽中。
>* 若要確保頁面顯示和資訊儲存以適當順序進行，請在Web表單中啟用除錯模式。 若要這麼做，請前往子標 **[!UICONTROL Preview]** 簽並核取方 **[!UICONTROL Enable debug mode]** 塊：所有收集的資訊和可能的執行錯誤都會顯示在每個頁面的底部。
>



### 使用工具列中的圖示 {#using-the-icons-in-the-toolbar}

您也可以使用工具列中的圖示，或按一下滑鼠右鍵以插入輸入區域。

![](assets/s_ncs_admin_webform_add_selection.png)

在這種情況下，首先選擇要添加的欄位類型並回答儲存模式。

![](assets/s_ncs_admin_webform_select_storage.png)

按一 **[!UICONTROL Ok]** 下以核准選擇。

![](assets/s_ncs_admin_webform_confirm_storage.png)

