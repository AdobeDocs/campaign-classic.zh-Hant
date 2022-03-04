---
product: campaign
title: 內容編輯器介面
description: 內容編輯器介面
feature: Web Apps, Web Forms, Landing Pages
exl-id: cb76f3dc-7f3a-49de-89cb-c106865ecb17
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 3%

---

# 內容編輯器介面{#content-editor-interface}

![](../../assets/common.svg)

## 編輯窗口 {#editing-window}

DCE編輯窗口分為三個不同的部分。 它們允許您查看、修改和檢查內容的狀態。

![](assets/dce_decoupe_window_nb.png)

1. 的 **頂** section是向用戶發送消息的顯示區域。 這些消息指示Web應用程式狀態或正在建立的傳遞的狀態以及與內容相關的警告和錯誤消息。 有關此內容的詳細資訊，請參閱 [HTML內容狀態](content-editing-best-practices.md#html-content-statuses)。
1. 到 **左** 窗口的「 」區域。 在此區域中，用戶可以使用彈出工具欄直接與內容交互：將連結插入影像、更改字型、刪除欄位等。 有關詳細資訊，請參閱 [編輯表單](editing-content.md#editing-forms)。
1. 到 **右** 窗口的控制面板區域。 此區域將編輯器的不同選項分組，特別是與為塊配置頁面標題和常規選項相關的選項：添加邊框、將資料庫欄位與輸入區域連結、訪問網頁屬性等。 有關詳細資訊，請參閱 [全局選項](#global-options) 和 [編輯內容](editing-content.md) 的下界。

## 全局選項 {#global-options}

編輯器右上部分允許您訪問全局選項，以便控制當前建立的內容。

![](assets/dce_global_options.png)

它有四個表徵圖：

![](assets/dce_icons_sidebar.png)

* 的 **顯示/隱藏塊** 表徵圖允許您在內容塊周圍顯示藍色幀(對應於 `<div>` HTML標籤)。

* 的 **選擇其他內容** 表徵圖允許用戶從模板（現有模板或現成模板）載入新內容。

   ![](assets/dce_popup_templatechoice.png)

   >[!CAUTION]
   >
   >所選內容將替換當前內容。

* 的 **另存為模板** 表徵圖，您可以將當前內容另存為模板。 必須輸入模板的標籤和內部名稱。 模板儲存在 **[!UICONTROL Resources > Templates > Content templates]** 的下界。

   ![](assets/dce_popup_savetemplate.png)

   保存後，模板可用，在建立新內容時可以選擇。

   ![](assets/dce_create_fromtemplate.png)

* 的 **頁面屬性** 表徵圖，用於選擇HTML頁頂部的內容資訊。

   ![](assets/dce_popup_headerhtml.png)

   >[!NOTE]
   >
   >此資訊對應於 **`<title>`** 和 **`<meta>`** HTML頁面上的標籤。
   >
   >關鍵字必須用逗號分隔。

## 阻止選項 {#block-options}

編輯器右側的部分將允許您對內容執行操作的主要選項分組。 要顯示這些選項，必須選擇一個塊：這些選項的性質取決於所選的塊。

![](assets/dce_right_section.png)

您可以：

* 確定一個或多個塊的顯示，請參閱 [定義可見性條件](editing-content.md#defining-a-visibility-condition)。
* 定義邊框和框架，請參閱 [添加邊框和背景](editing-content.md#adding-a-border-and-background)。
* 定義影像屬性（大小、標題），請參閱 [編輯影像屬性](editing-content.md#editing-image-properties)。
* 將資料庫連結到表單元素（輸入區域、複選框），請參閱 [更改窗體的資料屬性](editing-content.md#changing-the-data-properties-for-a-form)。
* 將表單的一部分設定為強制，請參閱 [更改窗體的資料屬性](editing-content.md#changing-the-data-properties-for-a-form)。
* 定義按鈕的操作，請參閱 [向按鈕添加操作](editing-content.md#adding-an-action-to-a-button)。

## 內容工具欄 {#content-toolbar}

工具欄是 **彈出元素** DCE介面的DCE介面，它根據選定的塊顯示不同的功能。

>[!CAUTION]
>
>特定工具列功能可讓您設定 HTML 內容的格式。但是，如果頁面包含CSS樣式表， **說明** 從樣式表中 **優先順序** 指定的說明。
