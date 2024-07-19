---
product: campaign
title: 編輯內容
description: 編輯內容
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: 968430d6-b1dd-47f8-8b31-39aaa18bc05c
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1227'
ht-degree: 0%

---

# 編輯內容{#editing-content}



## 定義可見度條件 {#defining-a-visibility-condition}

您可以在網頁元素上指定可見性條件：只有在符合條件時，才會顯示此元素。

若要新增可見度條件，請選取區塊並使用運算式編輯器在&#x200B;**[!UICONTROL Visibility condition]**&#x200B;欄位中輸入條件。

![](assets/dce_add_condition.png)

>[!NOTE]
>
>在[此頁面](../../platform/using/defining-filter-conditions.md#list-of-functions)上顯示進階運算式編輯。

![](assets/dce_popup_visibilitycondition.png)

這些條件採用XTK運算式語法（例如&#x200B;**ctx.recipient）。@email！= &quot;**&#x200B;或&#x200B;**ctx.recipient。@status==&quot;0&quot;**)。 依預設，所有欄位都是可見的。

>[!NOTE]
>
>無法編輯無法顯示的動態區塊，例如下拉式功能表。

## 新增邊框和背景 {#adding-a-border-and-background}

您可以將&#x200B;**邊框**&#x200B;新增至選取的區塊。 使用下列三個選項來定義框線：樣式、大小和顏色。

![](assets/dce_popup_border.png)

您也可以從色彩表中選取一種顏色，以定義&#x200B;**背景顏色**。

![](assets/dce_popup_background.png)

## 編輯表單 {#editing-forms}

### 變更表單的資料屬性 {#changing-the-data-properties-for-a-form}

您可以將資料庫欄位與輸入區域、單選按鈕或核取方塊型別區塊連結。

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>預設欄位是Web應用程式儲存結構描述中的欄位。

**欄位**&#x200B;輸入區域可讓您選取要與表單欄位連結的資料庫欄位。

依預設，提供的欄位是&#x200B;**nms：recipient**&#x200B;表格中的欄位。

![](assets/dce_field_selection.png)

**必填欄位**&#x200B;選項可讓您僅在使用者已填入欄位時，授權頁面的核准。 如果未填入必填欄位，則會出現錯誤訊息。

對於選項按鈕和核取方塊，**需要其他設定**。

事實上，如果使用的範本預設不包含值，您必須在編輯器中完成它。

操作步驟：

* 按一下&#x200B;**[!UICONTROL Edit]**&#x200B;圖示。

  ![](assets/dce_sidebar_options.png)

* 在&#x200B;**[!UICONTROL Value]**&#x200B;欄位中輸入分項清單值（由選取的欄位定義）。

  ![](assets/dce_sidebar_completeoptionradio.png)

### 修改表單欄位 {#modifying-form-fields}

表單欄位，例如選項按鈕、輸入區域、下拉式清單等。 可使用其工具列進行修改。

這表示您可以：

* 使用&#x200B;**[!UICONTROL Delete]**&#x200B;圖示刪除包含表單欄位的區塊。
* 使用&#x200B;**[!UICONTROL Duplicate]**&#x200B;圖示建立新區塊，以複製選取的欄位。
* 使用&#x200B;**[!UICONTROL Edit]**&#x200B;圖示編輯&#x200B;**[!UICONTROL Form data]**&#x200B;視窗以將資料庫欄位連結至表單區域。

  ![](assets/dce_toolbar_formblock_edition.png)

## 將動作新增至按鈕 {#adding-an-action-to-a-button}

當使用者按一下按鈕時，您可以定義關聯的動作。 要執行此操作，請從下拉式清單中選取要執行的動作。

![](assets/dce_sidebar_button.png)

可用的動作如下：

* **[!UICONTROL Refresh]** ：重新整理目前頁面。
* **[!UICONTROL Next page]** ：建立指向Web應用程式中下一頁的連結。
* **[!UICONTROL Previous page]** ：建立指向Web應用程式中上一頁的連結。

>[!NOTE]
>
>**[!UICONTROL None]**&#x200B;值可讓您不啟動按鈕。

您可以在對應欄位中修改連結至按鈕的標籤。

## 新增連結 {#adding-a-link}

您可以將連結插入任何頁面元素中：影像、單字、字群組、文字區塊等。

要執行此操作，請選取元素，然後使用躍現式選單中的第一個圖示。

![](assets/dce_insertlink_icon.png)

此圖示可讓您存取所有可用的連結型別。

![](assets/dce_insertlink_menu.png)

個人化區塊和欄位只能插入文字型別區塊中。

>[!NOTE]
>
>對於每種型別的連結，您可以設定開啟模式：在&#x200B;**目標**&#x200B;下拉式清單中選取目標視窗。 此值對應至&#x200B;**`<target>`** HTML標籤。
>
>可用的&#x200B;**目標**&#x200B;清單如下：
>
>* 其他(IFrame)
>* 頂端視窗(_top)
>* 父視窗(_parent)
>* 新視窗(_blank)
>* 目前視窗(_self)
>* 預設瀏覽器行為
>

### 連結至URL {#link-to-a-url}

**連結至外部URL**&#x200B;選項可讓您從來源內容開啟任何URL。

![](assets/dce_toolbar_imgblock_externallink.png)

在&#x200B;**URL**&#x200B;欄位中輸入相關連結位址。 URL欄位應該輸入為： **https://www.myURL.com**。

### 連結至Web應用程式 {#link-to-a-web-application}

**連結至網頁應用程式**&#x200B;選項可讓您存取Adobe Campaign網頁應用程式。

![](assets/dce_toolbar_imgblock_appweb.png)

從對應的欄位中選取Web應用程式。

建議的Web應用程式清單對應至&#x200B;**[!UICONTROL Resources > Online > Web Applications]**&#x200B;節點中的可用應用程式。

### 連結至動作 {#link-to-an-action}

定義動作&#x200B;**選項的**&#x200B;連結可讓您在按一下來源元素時設定動作。

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
>
>可用的動作在[新增動作至按鈕](#adding-an-action-to-a-button)區段中詳細說明。

### 刪除連結 {#delete-a-link}

插入連結後，工具列會提供兩個新圖示： **編輯連結**&#x200B;和&#x200B;**中斷連結**，讓您與建立的連結互動。

* **[!UICONTROL Edit link]**&#x200B;可讓您顯示包含連結所有引數的視窗。
* **[!UICONTROL Break the link]**&#x200B;可讓您在確認後刪除連結及所有相關引數。

>[!NOTE]
>
>如果刪除連結，內容仍會保留。

## 變更字型屬性 {#changing-font-attributes}

當您選取文字元素時，可以修改字型屬性（樣式、格式）。

![](assets/dce_toolbar_txt.png)

可用的選項如下：

* **放大字型**&#x200B;圖示：增加選取文字的大小（新增`<span style="font size:">`）
* **縮小字型**&#x200B;圖示：縮小選取文字的大小（新增`<span style="font size:">`）
* **粗體**&#x200B;圖示：將選取的文字變為粗體（以`<strong> </strong>`標籤括住文字）
* **斜體**&#x200B;圖示：將選取的文字變為斜體（以`<em> </em>`標籤括住文字）
* **加底線**&#x200B;圖示：將選取的文字加底線（以`<span style="text-decoration: underline;">`標籤括住文字）
* **靠左對齊**&#x200B;圖示：將文字對齊所選取區塊的左側（新增style=&quot;text-align： left；&quot;）
* **置中**&#x200B;圖示：將所選取區塊的文字置中（新增style=&quot;text-align： center；&quot;）
* **靠右對齊**&#x200B;圖示：將文字對齊所選取區塊的右側（新增style=&quot;text-align： right；&quot;）
* **變更背景顏色**&#x200B;圖示：可讓您變更所選取區塊的背景顏色(新增style=&quot;background-color： rgba(170， 86， 255， 0.87))
* **變更文字色彩**&#x200B;圖示：可讓您變更所選區塊的文字色彩，或僅變更所選文字(`<span style="color: #CODE">`)

>[!NOTE]
>
>* **刪除**&#x200B;圖示：刪除區塊及其所有內容。
>
>* **複製**&#x200B;圖示：複製區塊以及與區塊相關的所有樣式。

## 管理影像和動畫 {#managing-images-and-animations}

數位內容編輯器可讓您處理與瀏覽器相容的&#x200B;**任何型別的影像**。

>[!CAUTION]
>
>您不得在HTML頁面的&#x200B;**指令碼**&#x200B;標籤中呼叫外部檔案。 這些檔案將不會匯入至Adobe Campaign伺服器。

### 新增/刪除/複製影像 {#adding---deleting---duplicating-an-image}

若要插入影像，請選取影像型別區塊，然後按一下&#x200B;**影像**&#x200B;圖示。

![](assets/dce_insert_image.png)

選取本機儲存的影像檔案。

![](assets/dce_popup_imgupload.png)

**Delete**&#x200B;圖示會刪除包含影像的標籤。

**重複**&#x200B;圖示會重複標籤及其內容。

>[!CAUTION]
>
>當您複製影像時，與新影像相關的識別碼會被刪除。

### 編輯影像屬性 {#editing-image-properties}

當您選取包含影像的區塊時，可以存取下列屬性：

* **註解**&#x200B;可讓您定義連結至影像的註解(對應至&#x200B;**alt** HTML屬性)。
* **Dimension**&#x200B;可讓您指定影像大小（畫素）。

  ![](assets/dce_popup_imgsize.png)

## 新增個人化內容 {#adding-personalization-content}

### 插入個人化欄位 {#inserting-a-personalization-field}

插入圖示的&#x200B;**Personalization欄位**&#x200B;選項可讓您新增資料庫欄位至內容，例如收件者的名稱。 此選項僅適用於文字型別區塊。

![](assets/dce_toolbar_textblock_persofield.png)

依預設，提供的欄位來自&#x200B;**[!UICONTROL Recipient]**&#x200B;表格。 必要時，編輯Web應用程式屬性以選取其他表格。

欄位名稱會顯示在編輯器中，以黃色反白顯示。 產生個人化時（例如，預覽登入頁面時），目標收件者的設定檔會取代此設定檔。

在[插入個人化欄位](creating-a-landing-page.md#inserting-a-personalization-field)區段中會顯示範例。

### 插入個人化區塊 {#inserting-a-personalization-block}

**Personalization區塊**&#x200B;選項可讓您在內容中插入動態和個人化的區塊。 例如，您可以新增標誌或問候語。 它不適用於文字型別區塊。

![](assets/dce_toolbar_textblock_persoblock.png)

插入後，個人化區塊名稱會顯示在編輯器中，並以黃色反白顯示。 產生個人化時，會自動調整成適合收件者設定檔。

如需內建個人化區塊以及如何定義自訂個人化區塊的詳細資訊，請參閱[此頁面](../../delivery/using/personalization-blocks.md)。
