---
solution: Campaign Classic
product: campaign
title: 開始使用網路表單
description: 開始使用Campaign中的Web表格
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: e76eb171aac1f7088ff8647f99c928ec349b24fc
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 5%

---


# 開始使用網路表單{#about-web-forms}

Adobe Campaign整合了圖形模組，用於定義和發佈Web表單，以建立包含輸入和選擇欄位的頁面，並可能包含資料在資料庫中。 這可讓您設計並張貼網頁，讓使用者可存取這些網頁以檢視或輸入資訊。

本章詳細說明Web表單的建立與管理、如何管理欄位和頁面，以及儲存與儲存模式。

>[!CAUTION]
>
>基於隱私權原因，我們建議對所有外部資源使用HTTPS。

## 建立Web表單的步驟{#steps-for-creating-a-web-form}

本章詳細說明在Adobe Campaign中設計&#x200B;**webForm**&#x200B;類型表單所需的步驟，以及可用的選項和設定。 Adobe Campaign可讓您將此Web表格提供給使用者，並收集和封存資料庫中的答案。

>[!CAUTION]
>
>在設定Web應用程式和Web表單時，您需要最低900像素的垂直解析度(例如：1600x900)。

您可透過&#x200B;**促銷活動**&#x200B;標籤的「Web應用程式」選單存取Web表格。 在Adobe Campaign樹狀結構中，這些變數會分組在&#x200B;**[!UICONTROL Resources > Online > Web Applications]**&#x200B;節點下。

要建立Web表單，請按一下Web應用程式清單上方的&#x200B;**[!UICONTROL Create]**&#x200B;按鈕。

![](assets/webapp_create_new.png)

選擇Web表單模板（預設情況下為&#x200B;**[!UICONTROL newWebForm]**）。

![](assets/s_ncs_admin_survey_select_template.png)

這會帶您進入表單的控制面板。

![](assets/webapp_empty_dashboard.png)

**[!UICONTROL Edit]**&#x200B;標籤可讓您建立內容。

![](assets/webapp_edit_tab.png)

要定義Web表單的配置和內容，請應用以下步驟：

* 首先，請建立必要的頁面和控制項：輸入欄位、下拉式清單、HTML內容等。

   此步驟在下面詳述。

* 定義頁面順序並設定顯示條件。

   此步驟在[定義網頁表單頁面順序](../../web/using/defining-web-forms-page-sequencing.md)中詳細說明。

* 視需要翻譯內容。

   此步驟在[轉換Web表單](../../web/using/translating-a-web-form.md)中有詳細說明。

## 關於設計的Web表單{#about-web-forms-designing}

表單的頁面是透過特定編輯器建立的，可讓您定義和設定輸入區域（文字）、選擇欄位（清單、核取方塊等） 和靜態元素（影像、HTLM內容等）。 您可將容器分組，並依您的需求變更其版面配置（如需詳細資訊，請參閱「建立容器[」）。](../../web/using/defining-web-forms-layout.md#creating-containers)

以下章節詳細說明如何定義表單畫面的內容和版面：

* [新增欄位至網路表單](../../web/using/adding-fields-to-a-web-form.md),
* [插入HTML內容](../../web/using/static-elements-in-a-web-form.md#inserting-html-content),
* [網路表單中的靜態元素](../../web/using/static-elements-in-a-web-form.md),
* [定義網路表單版面](../../web/using/defining-web-forms-layout.md).

>[!NOTE]
>
>* 在頁面設計期間，您可以在&#x200B;**[!UICONTROL Preview]**&#x200B;標籤中檢視最終演算。 若要檢視變更，請先儲存表單。 所有錯誤都會顯示在&#x200B;**[!UICONTROL Log]**&#x200B;標籤中。
>* 若要確保頁面顯示和資訊儲存以適當順序進行，請在Web表單中啟用除錯模式。 要執行此操作，請轉至&#x200B;**[!UICONTROL Preview]**&#x200B;子頁籤並選中&#x200B;**[!UICONTROL Enable debug mode]**&#x200B;框：所有收集的資訊和可能的執行錯誤都會顯示在每個頁面的底部。
>



### 使用工具欄中的表徵圖{#using-the-icons-in-the-toolbar}

您也可以使用工具列中的圖示，或按一下滑鼠右鍵以插入輸入區域。

![](assets/s_ncs_admin_webform_add_selection.png)

在這種情況下，首先選擇要添加的欄位類型並回答儲存模式。

![](assets/s_ncs_admin_webform_select_storage.png)

按一下&#x200B;**[!UICONTROL Ok]**&#x200B;以核准選擇。

![](assets/s_ncs_admin_webform_confirm_storage.png)

