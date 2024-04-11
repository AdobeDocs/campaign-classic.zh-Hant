---
product: campaign
title: 開始使用網路表單
description: 開始使用Campaign中的網路表單
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Landing Pages, Web Forms
exl-id: 63602bed-ace6-4632-a735-5d268a7d72d0
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 1%

---

# 開始使用網路表單{#about-web-forms}



Adobe Campaign整合了圖形模組，用於定義及發佈網路表單，以建立包含輸入和選擇欄位，並可能包含資料庫資料的頁面。 這可讓您設計和張貼使用者可存取的網頁，以檢視或輸入資訊。

本章詳細說明網路表單的建立與管理、如何管理欄位和頁面，以及儲存和儲存模式。

>[!CAUTION]
>
>基於隱私權理由，我們建議對所有外部資源使用HTTPS。

## 建立網路表單的步驟 {#steps-for-creating-a-web-form}

本章詳細說明設計 **webForm** 在Adobe Campaign中鍵入表單，以及可用的選項和設定。 Adobe Campaign可讓您讓此網頁表單可供使用者使用，以及在資料庫中收集和封存答案。

>[!CAUTION]
>
>設定Web應用程式和網頁表單時，至少需要900畫素的垂直解析度（例如：1600x900）。

網路表單可透過 **行銷活動** 標籤。 在Adobe Campaign樹中，這些區段會分組在 **[!UICONTROL Resources > Online > Web Applications]** 節點。

若要建立網頁表單，請按一下 **[!UICONTROL Create]** 按鈕。

![](assets/webapp_create_new.png)

選取網路表單範本( **[!UICONTROL newWebForm]** 預設情況下)。

![](assets/s_ncs_admin_survey_select_template.png)

這會將您導向至表單的控制面板。

![](assets/webapp_empty_dashboard.png)

此 **[!UICONTROL Edit]** 索引標籤可讓您建立內容。

![](assets/webapp_edit_tab.png)

若要定義網頁表單的設定和內容，請套用下列步驟：

* 首先，請建立必要的頁面和控制項：輸入欄位、下拉式清單、HTML內容等。

  此步驟的詳細資訊如下。

* 定義頁面順序和顯示條件。

  此步驟的詳細資訊，請參閱 [定義網路表單頁面排序](defining-web-forms-page-sequencing.md).

* 如有必要，請翻譯內容。

  此步驟的詳細資訊，請參閱 [轉譯網路表單](translating-a-web-form.md).

## 關於網路表單設計 {#about-web-forms-designing}

表單的頁面是透過特定編輯器建立的，可讓您定義和設定輸入區域（文字）、選擇欄位（清單、核取方塊等） 和靜態元素（影像、HTLM內容等）。 您可以將其分組到容器中，並根據您的需求更改其版面(如需詳細資訊，請參閱 [建立容器](defining-web-forms-layout.md#creating-containers))。

以下小節詳細說明如何定義表單熒幕的內容和版面：

* [新增欄位至網路表單](adding-fields-to-a-web-form.md)，
* [插入HTML內容](static-elements-in-a-web-form.md#inserting-html-content)，
* [網路表單中的靜態元素](static-elements-in-a-web-form.md)，
* [定義網路表單版面](defining-web-forms-layout.md).

>[!NOTE]
>
>* 在頁面設計期間，您可以檢視中的最終轉譯 **[!UICONTROL Preview]** 標籤。 若要檢視變更，請先儲存表單。 任何錯誤都會顯示在 **[!UICONTROL Log]** 標籤。
>* 若要確保頁面顯示和資訊儲存的順序適當，請在Web表單中啟用偵錯模式。 若要這麼做，請前往 **[!UICONTROL Preview]** 子標籤並檢查 **[!UICONTROL Enable debug mode]** 方塊：所有收集的資訊和可能的執行錯誤都會顯示在每頁底部。
>

### 使用工具列中的圖示 {#using-the-icons-in-the-toolbar}

您也可以使用工具列中的圖示或按一下右鍵來插入輸入區域。

![](assets/s_ncs_admin_webform_add_selection.png)

在這種情況下，請先選取要新增的欄位型別和答案儲存模式。

![](assets/s_ncs_admin_webform_select_storage.png)

按一下 **[!UICONTROL Ok]** 以核准選取專案。

![](assets/s_ncs_admin_webform_confirm_storage.png)
