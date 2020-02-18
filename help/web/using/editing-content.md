---
title: 編輯內容
seo-title: 編輯內容
description: 編輯內容
seo-description: null
page-status-flag: never-activated
uuid: 2f51e848-1820-4bec-a0ea-63c9ddff05e0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: da66d640-8504-4dc7-bc4e-1c0ac1d37c37
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7a0d82dfc6dc50026214d7d3b1094d45ffadbc03

---


# 編輯內容{#editing-content}

## 定義可見性條件 {#defining-a-visibility-condition}

您可以在網頁元素上指定可見性條件：此元素只有在符合條件時才會顯示。

要添加可見性條件，請選擇一個塊，然後使用表達式編輯器 **[!UICONTROL Visibility condition]** 在欄位中輸入條件。

![](assets/dce_add_condition.png)

>[!NOTE]
>
>進階運算式編輯會顯示在 [此頁面上](../../platform/using/defining-filter-conditions.md#list-of-functions)。

![](assets/dce_popup_visibilitycondition.png)

這些條件採用XTK運算式語法(例如 **ctx.recipient)。@email != &quot;&quot;** 或 **ctx.recipient。@status=&quot;0&quot;**)。 依預設，所有欄位皆可顯示。

>[!NOTE]
>
>無法編輯非可見的動態區塊，例如下拉式功能表。

## 新增邊框和背景 {#adding-a-border-and-background}

您可以將邊框 **新增至** 選取的區塊。 邊框使用三個選項定義：樣式、大小和顏色。

![](assets/dce_popup_border.png)

您也可以從色 **彩圖表中** ，選取顏色來定義背景顏色。

![](assets/dce_popup_background.png)

## 編輯表格 {#editing-forms}

### 變更表單的資料屬性 {#changing-the-data-properties-for-a-form}

您可以將資料庫欄位與輸入區域、單選按鈕或複選框類型塊連結。

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>預設欄位是Web應用程式儲存架構中的欄位。

欄位 **輸入區** ，可讓您選取要與表單欄位連結的資料庫欄位。

預設情況下，提供的欄位是 **nms:recipient表中的欄位** 。

![](assets/dce_field_selection.png)

「必 **要欄位** 」選項可讓您僅在使用者已填入欄位時授權頁面的核准。 如果未填入必要欄位，則會出現錯誤訊息。

對於選項按鈕和複選框，需 **要進行其他配置**。

事實上，如果使用的範本預設不包含值，您必須在編輯器中完成。

操作步驟：

* 按一下 **[!UICONTROL Edit]** 圖示。

   ![](assets/dce_sidebar_options.png)

* 在欄位中輸入項目化清單值（由選取欄位定義）。 **[!UICONTROL Value]**

   ![](assets/dce_sidebar_completeoptionradio.png)

### 修改表單欄位 {#modifying-form-fields}

表單欄位，例如選項按鈕、輸入區域、下拉式清單等。 可從工具列修改。

這表示您可以：

* 使用圖示刪除包含表單欄位的 **[!UICONTROL Delete]** 區塊。
* 使用圖示建立新區塊，以複製選取的欄 **[!UICONTROL Duplicate]** 位。
* 使用圖 **[!UICONTROL Form data]** 標編輯窗口，將資料庫欄位連結到表單區 **[!UICONTROL Edit]** 域。

   ![](assets/dce_toolbar_formblock_edition.png)

## 新增動作至按鈕 {#adding-an-action-to-a-button}

當使用者按一下按鈕時，您可以定義相關的動作。 若要這麼做，請從下拉式清單中選取要執行的動作。

![](assets/dce_sidebar_button.png)

可用操作如下：

* **[!UICONTROL Refresh]** :重新整理目前頁面。
* **[!UICONTROL Next page]** :建立指向Web應用程式中下一頁的連結。
* **[!UICONTROL Previous page]** :在Web應用程式中建立上一頁的連結。

>[!NOTE]
>
>值 **[!UICONTROL None]** 允許您不激活按鈕。

您可以在對應欄位中修改連結至按鈕的標籤。

## 新增連結 {#adding-a-link}

您可以將連結插入任何頁面元素：影像、單詞、單片語、文本塊等。

若要這麼做，請選取元素，然後使用快顯功能表中的第一個圖示。

![](assets/dce_insertlink_icon.png)

此圖示可讓您存取所有可用的連結類型。

![](assets/dce_insertlink_menu.png)

個人化區塊和欄位只能插入文字類型區塊。

>[!NOTE]
>
>對於每種類型的連結，您可以設定開啟模式：在「目標」下拉式清單中 **選取目標** 視窗。 此值與 **`<target>`** HTML標籤相對應。
>
>可用目標 **清單** 如下：
>
>* 其他(IFrame)
>* 頂端視窗(_top)
>* 父窗口(_parent)
>* 新視窗(_blank)
>* 目前視窗(_self)
>* 預設瀏覽器行為
>



### 連結至URL {#link-to-a-url}

「連 **結至外部URL** 」選項可讓您從來源內容開啟任何URL。

![](assets/dce_toolbar_imgblock_externallink.png)

在 **URL欄位中輸入相關的連結** 位址。 URL欄位應輸入為： **https://www.myURL.com**。

### 連結至Web應用程式 {#link-to-a-web-application}

「連 **結至網頁應用程式** 」選項可讓您存取Adobe Campaign網頁應用程式。

![](assets/dce_toolbar_imgblock_appweb.png)

從相應欄位中選擇Web應用程式。

建議的Web應用程式清單與節點中的可用應用程式相 **[!UICONTROL Resources > Online > Web Applications]** 對應。

### 連結至動作 {#link-to-an-action}

定義 **動作選項的連結** ，可讓您在按一下來源元素時設定動作。

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
>
>「將操作添加到按鈕」 [部分中詳細介紹了可用操作](#adding-an-action-to-a-button) 。

### 刪除連結 {#delete-a-link}

插入連結後，工具列會提供兩個新圖示：編 **輯連結** , **** 並中斷可讓您與建立之連結互動的連結。

* **[!UICONTROL Edit link]** 可讓您顯示包含連結所有參數的視窗。
* **[!UICONTROL Break the link]** 可讓您在確認後刪除連結和所有相關參數。

>[!NOTE]
>
>如果刪除連結，內容仍會保留。

## 變更字型屬性 {#changing-font-attributes}

選擇文本元素時，可以修改字型屬性（樣式、格式）。

![](assets/dce_toolbar_txt.png)

可用選項如下：

* **放大字型** 圖示：增加選取文字的大小(新增 `<span style="font size:">`)
* **減少字型** 圖示：減小選取文字的大小(新增 `<span style="font size:">`)
* **粗體圖示** :將選取的文字設為粗體(以標籤換 `<strong> </strong>` 行文字)
* **斜體圖** 示：使選取的文字變成斜體(以標籤包 `<em> </em>` 住文字)
* **下划線** 表徵圖：使選取的文字加上底線(以標籤換 `<span style="text-decoration: underline;">` 行文字)
* **左對齊圖示** :將文字對齊選定塊的左側(add style=&quot;text-align:左；」)
* **中心** 圖示：將選取區塊的文字置中(新增style=&quot;text-align:中；」)
* **右對齊圖示** :將文字對齊選定塊的右側(add style=&quot;text-align:權利；」)
* **變更背景顏色** 圖示：可讓您變更所選區塊的背景顏色(新增style=&quot;background-color:rgba(170、86、255、0.87)
* **變更文字顏色** 圖示：可讓您變更所選區塊的文字顏色，或僅變更所選取的文字(`<span style="color: #CODE">`)

>[!NOTE]
>
>* **刪除圖示** :刪除塊及其所有內容。
   >
   >
* **復製圖示** :複製塊以及與塊相關的所有樣式。


## 管理影像和動畫 {#managing-images-and-animations}

數位內容編輯器可讓您處理與 **瀏覽器相容的任** 何影像類型。

要與DCE相容， **必須以下列方式將** &quot;Flash&quot;類型動畫插入HTML頁面：

```
<object type="application/x-shockwave-flash" data="https://www.mydomain.com/flash/your_animation.swf" width="200" height="400">
 <param name="movie" value="https://www.mydomain.com/flash/your_animation.swf" />
 <param name="quality" value="high" />
 <param name="play" value="true"/>
 <param name="loop" value="true"/> 
</object>
```

>[!CAUTION]
>
>您不得在HTML頁面的指令碼標 **記中** ，呼叫外部檔案。 這些檔案不會匯入至Adobe Campaign伺服器。

### 添加／刪除／複製映像 {#adding---deleting---duplicating-an-image}

要插入影像，請選擇「影像類型」塊，然後按一下「圖 **像** 」表徵圖。

![](assets/dce_insert_image.png)

選取儲存在本機的影像檔案。

![](assets/dce_popup_imgupload.png)

「刪 **除** 」圖示會刪除 ![]() 包含影像的標籤。

「復 **制** 」圖示會復 ![]() 制標籤及其內容。

>[!CAUTION]
>
>複製影像時，與新影像相關的識別碼會被刪除。

### 編輯影像屬性 {#editing-image-properties}

當您選取包含影像的區塊時，可存取下列屬性：

* **標題** (Caption)可讓您定義連結至影像的標題(與 **alt** HTML屬性相對應)。
* **尺寸** (Dimensions)可讓您指定影像大小（以像素為單位）。

   ![](assets/dce_popup_imgsize.png)

## 新增個人化內容 {#adding-personalization-content}

### 插入個人化欄位 {#inserting-a-personalization-field}

插 **入圖示的** 「個人化」欄位選項可讓您在內容中新增資料庫欄位，例如收件者的名稱。 此選項僅適用於文本類型塊。

![](assets/dce_toolbar_textblock_persofield.png)

依預設，提供的欄位是表格 **[!UICONTROL Recipient]** 中。 如有必要，請編輯Web應用程式屬性以選擇另一個表。

欄位名稱會顯示在編輯器中，以黃色反白顯示。 當產生個人化時（例如，在預覽著陸頁面時），會由目標收件者的設定檔取代。

「插入個人化」欄 [位區段中顯示範例](../../web/using/creating-a-landing-page.md#inserting-a-personalization-field) 。

### 插入個人化區塊 {#inserting-a-personalization-block}

「個 **人化區塊** 」選項可讓您將動態和個人化區塊插入內容。 例如，您可以新增標誌或問候訊息。 它不適用於文本類型塊。

![](assets/dce_toolbar_textblock_persoblock.png)

插入後，個人化區塊名稱會出現在編輯器中，並以黃色反白顯示。 當產生個人化時，它會自動適應收件者描述檔。

如需有關內建個人化區塊以及如何定義自訂個人化區塊的詳細資訊，請參 [閱本頁](../../delivery/using/personalization-blocks.md)。
