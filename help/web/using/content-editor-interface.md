---
product: campaign
title: 內容編輯器介面
description: 內容編輯器介面
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Apps, Web Forms, Landing Pages
exl-id: cb76f3dc-7f3a-49de-89cb-c106865ecb17
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 3%

---

# 內容編輯器介面{#content-editor-interface}



## 編輯視窗 {#editing-window}

DCE編輯窗口可分為三個不同部分。 它們可讓您檢視、修改及檢查內容的狀態。

![](assets/dce_decoupe_window_nb.png)

1. 此 **top** section是傳送給使用者的訊息顯示區域。 這些訊息會指出Web應用程式狀態或正在建立的傳送狀態，以及與內容相關的警告和錯誤訊息。 有關詳細資訊，請參閱 [HTML內容狀態](content-editing-best-practices.md#html-content-statuses).
1. 區段 **lef** 窗口的是編輯內容的區域。 在此區域中，使用者可使用快顯工具列直接與內容互動：將連結插入影像、變更字型、刪除欄位等。 如需詳細資訊，請參閱 [編輯表單](editing-content.md#editing-forms).
1. 區段 **右** 窗口是控制面板區域。 此區域會為編輯器分組不同的選項，尤其是與設定頁面標題和區塊一般選項相關的選項：添加邊框、將資料庫欄位與輸入區域連結、訪問Web頁屬性等。 有關詳細資訊，請參閱 [全域選項](#global-options) 和 [編輯內容](editing-content.md) 區段。

## 全域選項 {#global-options}

編輯器的右上角區段可讓您存取全域選項，以便您控制目前建立的內容。

![](assets/dce_global_options.png)

它有四個表徵圖：

![](assets/dce_icons_sidebar.png)

* 此 **顯示/隱藏區塊** 圖示可讓您在內容區塊周圍顯示藍格(對應至 `<div>` HTML標籤)。

* 此 **選擇其他內容** 圖示可讓使用者從範本（現有範本或現成可用的範本）載入新內容。

   ![](assets/dce_popup_templatechoice.png)

   >[!CAUTION]
   >
   >選取的內容會取代目前的內容。

* 此 **另存為範本** 圖示可讓您將目前的內容儲存為範本。 您必須輸入範本的標籤和內部名稱。 範本儲存在 **[!UICONTROL Resources > Templates > Content templates]** 節點。

   ![](assets/dce_popup_savetemplate.png)

   儲存後，範本即可使用，並可在建立新內容時加以選取。

   ![](assets/dce_create_fromtemplate.png)

* 此 **頁面屬性** 圖示可讓您選取HTML頁面頂端的內容資訊。

   ![](assets/dce_popup_headerhtml.png)

   >[!NOTE]
   >
   >此資訊對應至 **`<title>`** 和 **`<meta>`** HTML頁面上的標籤。
   >
   >關鍵字必須以逗號分隔。

## 封鎖選項 {#block-options}

編輯器右側的區段會將可讓您對內容採取動作的主要選項分組。 若要顯示這些選項，您必須選取區塊：這些選項的性質取決於所選塊。

![](assets/dce_right_section.png)

您可以：

* 確定一個或多個塊的顯示，請參閱 [定義可見性條件](editing-content.md#defining-a-visibility-condition),
* 定義邊框和框架，請參閱 [新增邊框和背景](editing-content.md#adding-a-border-and-background),
* 定義影像屬性（大小、註解），請參閱 [編輯影像屬性](editing-content.md#editing-image-properties),
* 將資料庫連結到表單元素（輸入區域、核取方塊），請參閱 [變更表單的資料屬性](editing-content.md#changing-the-data-properties-for-a-form),
* 將表單的一部分設為強制項目，請參閱 [變更表單的資料屬性](editing-content.md#changing-the-data-properties-for-a-form),
* 定義按鈕的動作，請參閱 [新增動作至按鈕](editing-content.md#adding-an-action-to-a-button).

## 內容工具列 {#content-toolbar}

工具列是 **快顯元素** DCE介面的介面，該介面根據所選塊顯示不同的功能。

>[!CAUTION]
>
>特定工具列功能可讓您設定 HTML 內容的格式。不過，如果頁面包含CSS樣式表，則 **說明** 從樣式表上可以看出 **優先順序** 在工具列中指定的指示上。
