---
title: 內容編輯器介面
seo-title: 內容編輯器介面
description: 內容編輯器介面
seo-description: null
page-status-flag: never-activated
uuid: b108ea74-ae2c-4e47-bee8-12070927ba89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
dc-title: </strong> and
discoiquuid: 20c64d31-c2ed-4bc9-9f0e-46f2e0c08c88
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# 內容編輯器介面{#content-editor-interface}

## 編輯窗口 {#editing-window}

DCE編輯窗口分為三個不同部分。 它們可讓您檢視、修改和檢查內容的狀態。

![](assets/dce_decoupe_window_nb.png)

1. 頂 **部** (top)區域是向用戶發送消息的顯示區域。 這些訊息會指出Web應用程式狀態或所建立的傳送狀態，以及與內容相關的警告和錯誤訊息。 如需詳細資訊，請參閱 [HTML內容狀態](../../web/using/content-editing-best-practices.md#html-content-statuses)。
1. 視窗左側 **的區** 域是編輯內容的區域。 在此區域，使用者可使用快顯工具列直接與內容互動：將連結插入影像、變更字型、刪除欄位等。 For more on this refer to [Editing forms](../../web/using/editing-content.md#editing-forms).
1. 窗口右側 **的部** 分是控制面板區域。 此區域將編輯器的不同選項分組，特別是與為塊配置頁面標題和常規選項相關的選項：新增邊框、連結資料庫欄位與輸入區域、存取網頁屬性等。 有關詳細資訊，請參閱「全 [域選項](#global-options) 」 [和「編輯內容](../../web/using/editing-content.md) 」部分。

## 全域選項 {#global-options}

編輯器的右上方部分可讓您存取全域選項，讓您控制目前建立的內容。

![](assets/dce_global_options.png)

它有四個圖示：

![](assets/dce_icons_sidebar.png)

* 「顯 **示／隱藏區塊** 」圖示可讓您在內容區塊周圍顯示藍色影格(與 `<div>` HTML標籤對應)。

* 「選 **擇其他內容** 」圖示可讓使用者從範本（現有範本或現成範本）載入新內容。

   ![](assets/dce_popup_templatechoice.png)

   >[!CAUTION]
   >
   >選取的內容會取代目前的內容。

* 「另 **存為範本** 」圖示可讓您將目前的內容儲存為範本。 您必須輸入範本的標籤和內部名稱。 模板儲存在節 **[!UICONTROL Resources > Templates > Content templates]** 點中。

   ![](assets/dce_popup_savetemplate.png)

   儲存後，範本就可供使用，並可在建立新內容時加以選取。

   ![](assets/dce_create_fromtemplate.png)

* 「頁 **面屬性** 」圖示可讓您選取HTML頁面頂端的內容資訊。

   ![](assets/dce_popup_headerhtml.png)

   >[!NOTE]
   >
   >此資訊對應至頁 **`<title>`** 面上 **`<meta>`** 的和HTML標籤。
   >
   >關鍵字必須以逗號分隔。

## 區塊選項 {#block-options}

編輯器右側的部分將允許您對內容採取行動的主要選項分組。 要顯示這些選項，必須選擇一個塊：這些選項的性質取決於所選塊。

![](assets/dce_right_section.png)

您可以：

* 確定一個或多個塊的顯示，請參閱定 [義可見性條件](../../web/using/editing-content.md#defining-a-visibility-condition),
* 定義邊框和框架，請參閱 [添加邊框和背景](../../web/using/editing-content.md#adding-a-border-and-background),
* 定義影像屬性（大小、標題），請參閱「編 [輯影像屬性](../../web/using/editing-content.md#editing-image-properties)」
* 將資料庫連結到表單元素（輸入區域、複選框），請參 [閱更改表單的資料屬性](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* 將表單的一部分設為強制，請參 [閱變更表單的資料屬性](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* 定義按鈕的操作，請參閱向 [按鈕添加操作](../../web/using/editing-content.md#adding-an-action-to-a-button)。

## 內容工具列 {#content-toolbar}

工具欄是DCE **介面的彈出式元素** ，它根據所選塊顯示不同的功能。

>[!CAUTION]
>
>某些工具列功能可讓您設定HTML內容的格式。 不過，如果頁面包含CSS樣式表，則樣 **式表中的說明** ，可能會優先於工具列中指 **定的說明** 。

