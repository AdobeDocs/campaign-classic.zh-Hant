---
product: campaign
title: 編輯內容
description: 編輯內容
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Apps, Web Forms, Landing Pages
exl-id: 968430d6-b1dd-47f8-8b31-39aaa18bc05c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 1%

---

# 編輯內容{#editing-content}



## 定義可見性條件 {#defining-a-visibility-condition}

您可以在網頁元素上指定可見性條件：只有接受條件時，此元素才會顯示。

若要新增可見性條件，請選取區塊並在 **[!UICONTROL Visibility condition]** 欄位。

![](assets/dce_add_condition.png)

>[!NOTE]
>
>進階運算式編輯會顯示在 [本頁](../../platform/using/defining-filter-conditions.md#list-of-functions).

![](assets/dce_popup_visibilitycondition.png)

這些條件採用XTK運算式語法(例如 **ctx.recipient。@電子郵件 != &quot;&quot;** 或 **ctx.recipient。@status==「0」**)。 依預設，所有欄位皆會顯示。

>[!NOTE]
>
>無法編輯不可見的動態區塊（例如下拉式功能表）。

## 新增邊框和背景 {#adding-a-border-and-background}

您可以新增 **邊框** 到選定塊。 邊框使用三個選項來定義：樣式、大小和顏色。

![](assets/dce_popup_border.png)

您也可以定義 **背景顏色** 從顏色圖中選取顏色。

![](assets/dce_popup_background.png)

## 編輯表單 {#editing-forms}

### 變更表單的資料屬性 {#changing-the-data-properties-for-a-form}

您可以將資料庫欄位與輸入區域、單選按鈕或核取方塊類型區塊連結。

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>預設欄位是Web應用程式儲存架構中的欄位。

此 **欄位** 輸入區域可讓您選取要與表單欄位連結的資料庫欄位。

依預設，提供的欄位為 **nms:recipient** 表格。

![](assets/dce_field_selection.png)

此 **必填欄位** 選項可讓您僅在使用者已填入欄位時，授權頁面的核准。 如果未填入必填欄位，則會顯示錯誤訊息。

對於選項按鈕和複選框， **需要其他配置**.

事實上，如果使用的範本預設不含值，您必須在編輯器中完成它。

操作步驟：

* 按一下 **[!UICONTROL Edit]** 表徵圖。

   ![](assets/dce_sidebar_options.png)

* 在 **[!UICONTROL Value]** 欄位。

   ![](assets/dce_sidebar_completeoptionradio.png)

### 修改表單欄位 {#modifying-form-fields}

表單欄位，例如選項按鈕、輸入區域、下拉式清單等。 可從其工具欄修改。

這表示您可以：

* 使用刪除包含表單欄位的區塊 **[!UICONTROL Delete]** 表徵圖。
* 使用建立新區塊以複製選取的欄位 **[!UICONTROL Duplicate]** 表徵圖。
* 編輯 **[!UICONTROL Form data]** 窗口，使用 **[!UICONTROL Edit]** 表徵圖。

   ![](assets/dce_toolbar_formblock_edition.png)

## 新增動作至按鈕 {#adding-an-action-to-a-button}

當使用者按一下按鈕時，您可以定義相關的動作。 若要這麼做，請從下拉式清單中選取要執行的動作。

![](assets/dce_sidebar_button.png)

可用的動作如下：

* **[!UICONTROL Refresh]** :重新整理目前的頁面。
* **[!UICONTROL Next page]** :建立指向Web應用程式中的下一頁的連結。
* **[!UICONTROL Previous page]** :建立指向Web應用程式中上一頁的連結。

>[!NOTE]
>
>此 **[!UICONTROL None]** 值可讓您不啟動按鈕。

您可以在對應欄位中修改連結至按鈕的標籤。

## 新增連結 {#adding-a-link}

您可以將連結插入任何頁面元素中：影像、字、字組、文字區塊等。

若要這麼做，請選取元素，然後從快顯功能表中使用第一個圖示。

![](assets/dce_insertlink_icon.png)

此圖示可讓您存取所有可用的連結類型。

![](assets/dce_insertlink_menu.png)

個人化區塊和欄位只能插入文字類型區塊中。

>[!NOTE]
>
>對於每種類型的連結，您可以設定開啟模式：在 **目標** 下拉式清單。 此值對應至 **`<target>`** HTML標籤。
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


### 連結至URL {#link-to-a-url}

此 **連結至外部URL** 選項可讓您從來源內容開啟任何URL。

![](assets/dce_toolbar_imgblock_externallink.png)

在 **URL** 欄位。 URL欄位應輸入為： **https://www.myURL.com**.

### 連結到Web應用程式 {#link-to-a-web-application}

此 **連結到Web應用程式** 選項，即可存取Adobe Campaign Web應用程式。

![](assets/dce_toolbar_imgblock_appweb.png)

從相應欄位中選擇Web應用程式。

建議的Web應用程式清單與 **[!UICONTROL Resources > Online > Web Applications]** 節點。

### 動作連結 {#link-to-an-action}

此 **定義動作的連結** 選項可讓您在按一下來源元素時設定動作。

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
>
>在 [新增動作至按鈕](#adding-an-action-to-a-button) 區段。

### 刪除連結 {#delete-a-link}

插入連結後，工具列會提供兩個新圖示： **編輯連結** 和 **中斷連結** 可讓您與建立的連結互動。

* **[!UICONTROL Edit link]** 可讓您顯示包含連結所有參數的視窗。
* **[!UICONTROL Break the link]** 可讓您在確認後刪除連結和所有相關參數。

>[!NOTE]
>
>如果刪除連結，內容仍會保留。

## 更改字型屬性 {#changing-font-attributes}

選取文字元素時，可以修改字型屬性（樣式、格式）。

![](assets/dce_toolbar_txt.png)

可用選項如下：

* **放大字型** 圖示：增加所選取文字的大小(新增 `<span style="font size:">`)
* **縮小字型** 圖示：縮小所選取文字的大小(新增 `<span style="font size:">`)
* **粗體** 圖示：將選取的文字設為粗體(以「繞排文字」 `<strong> </strong>` 標籤)
* **斜體** 圖示：使選取的文字變斜(以「繞排」文字  `<em> </em>` 標籤)
* **畫底線** 圖示：使選定文本帶下划線(用「換行」文本 `<span style="text-decoration: underline;">` 標籤)
* **靠左對齊** 圖示：將文字對齊所選取區塊的左側(add style=&quot;text-align:左；」
* **中心** 圖示：將選取區塊的文字置中對齊(新增style=&quot;text-align:中心；」
* **靠右對齊** 圖示：將文字對齊所選取區塊的右側(add style=&quot;text-align:右；」
* **變更背景顏色** 圖示：可讓您變更所選取區塊的背景顏色(新增style=&quot;background-color:rgba(170, 86, 255, 0.87)
* **變更文字顏色** 圖示：可讓您變更所選取區塊的文字顏色，或僅變更所選取的文字(`<span style="color: #CODE">`)

>[!NOTE]
>
>* **刪除** 圖示：刪除區塊及其所有內容。
>
>* **複製** 圖示：複製區塊以及與區塊相關的所有樣式。


## 管理影像和動畫 {#managing-images-and-animations}

數位內容編輯器可讓您 **任何類型的影像** 與瀏覽器相容。

>[!CAUTION]
>
>您不得在 **指令碼** 標籤。 這些檔案將不會匯入Adobe Campaign伺服器。

### 新增/刪除/複製影像 {#adding---deleting---duplicating-an-image}

若要插入影像，請選取影像類型區塊，然後按一下 **影像** 表徵圖。

![](assets/dce_insert_image.png)

選取儲存於本機的影像檔案。

![](assets/dce_popup_imgupload.png)

此 **刪除** 圖示會刪除包含影像的標籤。

此 **複製** 圖示會複製標籤及其內容。

>[!CAUTION]
>
>複製影像時，會刪除與新影像相關的識別碼。

### 編輯影像屬性 {#editing-image-properties}

選取包含影像的區塊時，您會存取下列屬性：

* **註解** 可讓您定義連結至影像的註解(與 **alt** HTML屬性)。
* **Dimension** 可讓您以像素為單位指定影像大小。

   ![](assets/dce_popup_imgsize.png)

## 新增個人化內容 {#adding-personalization-content}

### 插入個人化欄位 {#inserting-a-personalization-field}

此 **個人化欄位** 「插入」圖示的選項可讓您將資料庫欄位新增至內容，例如收件者的名稱。 此選項僅適用於文本類型塊。

![](assets/dce_toolbar_textblock_persofield.png)

依預設，提供的欄位來自 **[!UICONTROL Recipient]** 表格。 如有必要，請編輯Web應用程式屬性以選擇其他表。

欄位名稱會顯示在編輯器中，並以黃色強調顯示。 在產生個人化時（例如，預覽登錄頁面時），會由目標收件者的設定檔取代。

範例如 [插入個人化欄位](creating-a-landing-page.md#inserting-a-personalization-field) 區段。

### 插入個人化區塊 {#inserting-a-personalization-block}

此 **個人化區塊** 選項可讓您將動態和個人化區塊插入內容中。 例如，您可以新增標誌或問候語訊息。 它不適用於文本類型塊。

![](assets/dce_toolbar_textblock_persoblock.png)

插入後，個人化區塊名稱會顯示在編輯器中，並以黃色強調顯示。 系統會在產生個人化時自動調整至收件者設定檔。

如需內建個人化區塊以及如何定義自訂個人化區塊的詳細資訊，請參閱 [本頁](../../delivery/using/personalization-blocks.md).
