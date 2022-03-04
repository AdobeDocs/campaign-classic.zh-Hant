---
product: campaign
title: 編輯內容
description: 編輯內容
feature: Web Apps, Web Forms, Landing Pages
exl-id: 968430d6-b1dd-47f8-8b31-39aaa18bc05c
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 1%

---

# 編輯內容{#editing-content}

![](../../assets/common.svg)

## 定義可見性條件 {#defining-a-visibility-condition}

可以在網頁元素上指定可視性條件：僅當符合條件時，此元素才可見。

要添加可見性條件，請選擇一個塊，然後在 **[!UICONTROL Visibility condition]** 欄位。

![](assets/dce_add_condition.png)

>[!NOTE]
>
>高級表達式編輯在 [此頁](../../platform/using/defining-filter-conditions.md#list-of-functions)。

![](assets/dce_popup_visibilitycondition.png)

這些條件採用XTK表達式語法(例如 **ctx.recipient。@電子郵件 !=「」** 或 **ctx.recipient。@status==&quot;0&quot;**)。 預設情況下，所有欄位都可見。

>[!NOTE]
>
>無法編輯不可見的動態塊（如下拉菜單）。

## 添加邊框和背景 {#adding-a-border-and-background}

可以添加 **邊界** 的子菜單。 邊框使用三個選項定義：樣式、大小和顏色。

![](assets/dce_popup_border.png)

也可以定義 **背景色** 從顏色圖表中選擇顏色。

![](assets/dce_popup_background.png)

## 編輯表單 {#editing-forms}

### 更改窗體的資料屬性 {#changing-the-data-properties-for-a-form}

可以將資料庫欄位與輸入區域、單選按鈕或複選框類型塊連結起來。

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>預設欄位是Web應用程式儲存架構中的欄位。

的 **場** 「輸入區域」(input zone)允許您選擇要與表單域連結的資料庫欄位。

預設情況下，提供的欄位是 **nms：收件人** 的子菜單。

![](assets/dce_field_selection.png)

的 **必填欄位** 選項，您只能在用戶已填寫該欄位時授權該頁的批准。 如果未填寫必填欄位，則會顯示錯誤消息。

對於單選按鈕和複選框， **需要其他配置**。

實際上，如果預設情況下使用的模板不包含值，則必須在編輯器中完成它。

操作步驟：

* 按一下 **[!UICONTROL Edit]** 表徵圖

   ![](assets/dce_sidebar_options.png)

* 將明細化清單值（由選定欄位定義）輸入 **[!UICONTROL Value]** 的子菜單。

   ![](assets/dce_sidebar_completeoptionradio.png)

### 修改表單域 {#modifying-form-fields}

表單域，如單選按鈕、輸入區域、下拉清單等。 可從其工具欄修改。

這意味著您可以：

* 使用 **[!UICONTROL Delete]** 表徵圖
* 使用 **[!UICONTROL Duplicate]** 表徵圖
* 編輯 **[!UICONTROL Form data]** 窗口，使用 **[!UICONTROL Edit]** 表徵圖

   ![](assets/dce_toolbar_formblock_edition.png)

## 向按鈕添加操作 {#adding-an-action-to-a-button}

當用戶按一下按鈕時，您可以定義關聯的操作。 為此，請從下拉清單中選擇要執行的操作。

![](assets/dce_sidebar_button.png)

可用操作如下：

* **[!UICONTROL Refresh]** :刷新當前頁面。
* **[!UICONTROL Next page]** :建立指向Web應用程式下一頁的連結。
* **[!UICONTROL Previous page]** :建立指向Web應用程式上一頁的連結。

>[!NOTE]
>
>的 **[!UICONTROL None]** 值允許您不激活按鈕。

您可以修改連結到相應欄位中按鈕的標籤。

## 添加連結 {#adding-a-link}

可以將連結插入任何頁元素：影像、單詞、單片語、文本塊等。

為此，請選擇元素，然後使用彈出式菜單中的第一個表徵圖。

![](assets/dce_insertlink_icon.png)

此表徵圖允許您訪問所有可用類型的連結。

![](assets/dce_insertlink_menu.png)

個性化塊和欄位只能插入到文本類型塊中。

>[!NOTE]
>
>對於每種類型的連結，可以配置開啟模式：選擇 **目標** 的子菜單。 此值與 **`<target>`** HTML標籤。
>
>可用清單 **目標** 如下所示：
>
>* 其他(IFrame)
>* 頂部窗口(_top)
>* 父窗口(_parent)
>* 新窗口(_blank)
>* 當前窗口(_self)
>* 預設瀏覽器行為
>


### 連結到URL {#link-to-a-url}

的 **連結到外部URL** 選項，可開啟源內容中的任何URL。

![](assets/dce_toolbar_imgblock_externallink.png)

在 **URL** 的子菜單。 URL欄位應輸入為： **https://www.myURL.com**。

### 連結到Web應用程式 {#link-to-a-web-application}

的 **連結到Web應用程式** 選項，您可以訪問Adobe CampaignWeb應用程式。

![](assets/dce_toolbar_imgblock_appweb.png)

從相應欄位中選擇Web應用程式。

建議的Web應用程式清單對應於 **[!UICONTROL Resources > Online > Web Applications]** 的下界。

### 連結到操作 {#link-to-an-action}

的 **定義操作的連結** 選項，可在按一下源元素時配置操作。

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
>
>有關可用操作的詳細資訊，請參閱 [向按鈕添加操作](#adding-an-action-to-a-button) 的子菜單。

### 刪除連結 {#delete-a-link}

插入連結後，工具欄提供兩個新表徵圖： **編輯連結** 和 **斷開連結** 即可與建立的連結交互。

* **[!UICONTROL Edit link]** 允許您顯示包含連結所有參數的窗口。
* **[!UICONTROL Break the link]** 允許您在確認後刪除連結和所有相關參數。

>[!NOTE]
>
>如果刪除連結，則仍保留內容。

## 更改字型屬性 {#changing-font-attributes}

選擇文本元素時，可以修改字型屬性（樣式、格式）。

![](assets/dce_toolbar_txt.png)

可用選項如下：

* **放大字型** 表徵圖：增加所選文本的大小(添加 `<span style="font size:">`)
* **減少字型** 表徵圖：減小選定文本的大小(添加 `<span style="font size:">`)
* **粗體** 表徵圖：將選定文本加粗(用文本換行 `<strong> </strong>` 標籤)
* **斜體** 表徵圖：使選定文本傾斜(用文本換行  `<em> </em>` 標籤)
* **下划線** 表徵圖：使所選文本帶下划線（用帶下划線的文字換行） `<span style="text-decoration: underline;">` 標籤)
* **左對齊** 表徵圖：將文本對齊到所選塊的左側(add style=&quot;text-align:左；」
* **居中** 表徵圖：將所選塊的文本居中(add style=&quot;text-align:中；」
* **右對齊** 表徵圖：將文本對齊到選定塊的右側(add style=&quot;text-align:右；」
* **更改背景顏色** 表徵圖：允許您更改所選塊的背景顏色(add style=&quot;background-color:rgba(170、86、255、0.87)
* **更改文本顏色** 表徵圖：允許您更改所選塊的文本顏色或僅更改所選文本(`<span style="color: #CODE">`)

>[!NOTE]
>
>* **刪除** 表徵圖：刪除塊及其所有內容。
>
>* **重複** 表徵圖：複製塊以及與塊相關的所有樣式。


## 管理影像和動畫 {#managing-images-and-animations}

數字內容編輯器允許您 **任何類型的影像** 與瀏覽器相容。

>[!CAUTION]
>
>您不得在 **指令碼** HTML頁的標籤。 這些檔案不會導入到Adobe Campaign伺服器上。

### 添加/刪除/複製映像 {#adding---deleting---duplicating-an-image}

要插入影像，請選擇「影像類型」塊，然後按一下 **影像** 表徵圖

![](assets/dce_insert_image.png)

選擇本地保存的映像檔案。

![](assets/dce_popup_imgupload.png)

的 **刪除** 表徵圖刪除 ![]() 包含影像的標籤。

的 **重複** 表徵圖複製 ![]() 標籤及其內容。

>[!CAUTION]
>
>複製影像時，與新影像相關的標識符將被刪除。

### 編輯影像屬性 {#editing-image-properties}

選擇包含影像的塊時，可訪問以下屬性：

* **標題** 用於定義連結到影像的標題(與 **按住** HTML屬性)。
* **Dimension** 允許您指定影像大小（以像素為單位）。

   ![](assets/dce_popup_imgsize.png)

## 添加個性化內容 {#adding-personalization-content}

### 插入個人化欄位 {#inserting-a-personalization-field}

的 **個性化欄位** 的子菜單。 此選項僅適用於文本類型塊。

![](assets/dce_toolbar_textblock_persofield.png)

預設情況下，提供的欄位來自 **[!UICONTROL Recipient]** 的子菜單。 如有必要，請編輯Web應用程式屬性以選擇另一個表。

欄位名稱顯示在編輯器中，以黃色突出顯示。 在生成個性化設定時（例如，預覽登錄頁時），它將被目標收件人的配置檔案替換。

在 [插入個性化欄位](creating-a-landing-page.md#inserting-a-personalization-field) 的子菜單。

### 插入個性化塊 {#inserting-a-personalization-block}

的 **個性化塊** 選項，可將動態和個性化塊插入內容。 例如，您可以添加徽標或問候語。 它不可用於文本類型塊。

![](assets/dce_toolbar_textblock_persoblock.png)

插入後，個性化塊名稱將顯示在編輯器中，並以黃色突出顯示。 當產生個性化時，它自動適應於接收者簡檔。

有關內置個性化塊以及如何定義自定義個性化塊的詳細資訊，請參閱 [此頁](../../delivery/using/personalization-blocks.md)。
