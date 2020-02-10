---
title: Web表單中的靜態元素
seo-title: Web表單中的靜態元素
description: Web表單中的靜態元素
seo-description: null
page-status-flag: never-activated
uuid: 628e2252-16a2-4c8a-a178-60a9441d3198
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: ca3377c6-a120-4cd0-aaf4-80248f4f5918
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Web表單中的靜態元素{#static-elements-in-a-web-form}

在表單頁面中，您可以加入使用者沒有互動的元素；這些是靜態元素，例如影像、HTML內容、水準列或超文字連結。 這些元素是透過工具列的第一個按鈕，按一下功能表來建 **[!UICONTROL Add static element]** 立。

![](assets/s_ncs_admin_survey_add_static_element.png)

可用欄位類型如下：

* 值基於先前提供的答案（在表單上）或資料庫。
* 超文字連結、HTML、水準列。 請參 [閱插入HTML內容](#inserting-html-content)。
* 儲存在資源庫或使用者可存取之伺服器上的影像。 請參 [閱插入影像](#inserting-images)。
* 在用戶端和／或伺服器端執行的指令碼。 它必須以JavaScript編寫，並且與大部分的瀏覽器相容，以確保在用戶端執行正確。

   >[!NOTE]
   >
   >在伺服器端，指令碼可使用 [Campaign JSAPI檔案中定義的函式](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)。

## 插入HTML內容 {#inserting-html-content}

您可以在表單頁面中加入HTML內容：超文字連結、影像、格式化段落、視訊或Flash物件等。

HTML編輯器可讓您輸入要插入表單頁面的內容。 若要開啟編輯器，請前往 **[!UICONTROL Static elements>HTML]** 。

您可以直接輸入內容並設定其格式，或顯示原始碼視窗以貼入某些外部內容。 若要切換至「原始碼」模式，請按一下工具列中的第一個圖示：

![](assets/s_ncs_admin_survey_html_editor.png)

要插入資料庫欄位，請使用個性化按鈕。

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>在HTML編輯器中輸入的字串只有在子標籤中定義時才 **[!UICONTROL Texts]** 會轉換。 否則將不會收集這些資料。 如需詳細資訊，請參 [閱轉換Web表格](../../web/using/translating-a-web-form.md)。

### 插入連結 {#inserting-a-link}

填寫編輯視窗中的欄位，如下列範例所示：

要添加超文本連結，請轉至 **[!UICONTROL Static elements>Link]**。

![](assets/s_ncs_admin_survey_add_link.png)

* 超 **[!UICONTROL Label]** 文本連結的內容將顯示在表單頁面上。
* 該 **[!UICONTROL URL]** 地址是所需地址，例如：https://www.adobe.com [(](https://www.adobe.com) 網站)或mailto:info@adobe.com(網 [站](mailto:info@adobe.com) )傳送訊息。
* 欄位 **[!UICONTROL Window]** 可讓您在網站的情況下，選取連結的顯示模式。 您可以決定在新視窗、目前視窗或其他視窗中開啟連結。
* 您可以新增工具提示，如下所示：

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* 您可以選擇將連結顯示為按鈕或影像。 若要這麼做，請在欄位中選取顯示的類 **[!UICONTROL Type]** 型。

### 連結類型 {#types-of-links}

依預設，連結會與URL類型動作相關聯，以便在URL欄位中輸入連結目標位址。

![](assets/s_ncs_admin_survey_link_url.png)

您可以定義連結的其他動作，讓使用者按一下連結即可執行下列動作：

* 重新整理頁面

   若要這麼做，請 **[!UICONTROL Refresh page]** 在欄位的下拉式方塊中選取 **[!UICONTROL Action]** 選項。

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* 顯示下一頁／上一頁

   若要這麼做，請在欄 **[!UICONTROL Next page]** 位的 **[!UICONTROL Previous page]** 下拉式方塊中選取或 **[!UICONTROL Action]** 選項。

   ![](assets/s_ncs_admin_survey_link_next.png)

   如果要由連 **[!UICONTROL Next]** 結取代和/ **[!UICONTROL Back]** 或按鈕，您可以隱藏這些按鈕。 Refer to this [page](../../web/using/defining-web-forms-page-sequencing.md).

   此連結將取代預 **[!UICONTROL Next]** 設使用的按鈕。

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* 顯示另一頁

   選 **[!UICONTROL Enable a transition]** 項可讓您顯示與欄位中選取之傳出轉場相關聯的特定 **[!UICONTROL Transition]** 頁面。

   ![](assets/s_ncs_admin_survey_link_viral.png)

   依預設，頁面只有一個輸出轉場。 若要建立新的轉場效果，請選取頁面，然後按一 **[!UICONTROL Add]** 下區段中的 **[!UICONTROL Output transitions]** 按鈕，如下所示：

   ![](assets/s_ncs_admin_survey_add_transition.png)

   在圖中，此添加項的外觀如下：

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >有關Web表單中頁面排序的詳細資訊，請參閱定 [義Web表單頁面排序](../../web/using/defining-web-forms-page-sequencing.md)。

* 使用從Facebook設定檔取得的資料預先載入表單欄位

   >[!CAUTION]
   >
   >只有在您安裝了應用程式時，此函式才 **[!UICONTROL Social Marketing]** 可用。 若要使用此選項，您必須建立Facebook應用程式以及類型 **[!UICONTROL Facebook Connect]** 外部帳戶。 有關詳細資訊，請參見[此頁面](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

   選 **[!UICONTROL Preload with Facebook]** 項可讓您將按鈕插入表單，以使用Facebook設定檔資訊預先載入欄位。

   ![](assets/web_social_webapp_037.png)

   當使用者按一下按 **[!UICONTROL Fill in automatically]** 鈕時，Facebook會開啟權限要求視窗。

   ![](assets/web_social_webapp_029.png)

   >[!NOTE]
   >
   >在設定外部帳戶時，可變更擴充權限的清單。 如果您未輸入任何延伸權限，Facebook會依預設轉送基本設定檔資訊。\
   >若要檢視擴充權限的清單及其語法，請按一下這裡： [https://developers.facebook.com/docs/reference/api/permissions/](https://developers.facebook.com/docs/reference/api/permissions/)

   如果使用者同意分享其資訊，表單的欄位會預先載入。

   ![](assets/web_social_webapp_030.png)

針對此使用案例，我們建立了由下列元素組成的Web應用程式：

* 包含表單的頁面
* 活 **[!UICONTROL Record]** 動
* 活 **[!UICONTROL End]** 動

![](assets/social_webapp_031.png)

若要新增預先載入按鈕，請套用下列步驟：

1. 建立表格。

   ![](assets/social_webapp_032.png)

1. 移至表單中欄位的相同層級，並新增連結。

   ![](assets/social_webapp_033.png)

1. 輸入標籤並選擇 **[!UICONTROL Button]** 類型。

   ![](assets/social_webapp_034.png)

1. 轉至欄位 **[!UICONTROL Action]** 並選取 **[!UICONTROL Preload with Facebook]**。

   ![](assets/social_webapp_035.png)

1. 前往欄位並 **[!UICONTROL Application]** 選取先前建立 **[!UICONTROL Facebook Connect]** 的外部帳戶類型。 有關詳細資訊，請參見[此頁面](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

   ![](assets/social_webapp_036.png)

### 個人化HTML內容 {#personalizing-html-content}

您可以使用上一頁記錄的資料個人化表單頁面的HTML內容。 例如，您可以建立汽車保險Web表單，其第一頁可讓您提供聯絡資訊和汽車品牌。

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

使用個人化欄位，將使用者名稱和選取的品牌重新插入下一頁。 要使用的語法取決於資訊儲存模式。 如需詳細資訊，請參閱「使 [用收集的資訊](../../web/using/web-forms-answers.md#using-collected-information)」。

>[!NOTE]
>
>出於安全原因，在公式中輸入的值 **`<%=`** 將替換為轉義字元。 若要避免此情況，而且只有在必要時，請使用下列語法： **`<%=`**。

在我們的範例中，收件者的名字和姓氏會儲存在資料庫的欄位中，而其汽車品牌則會儲存在變數中。 第2頁個人化訊息的語法如下：

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

這會產生下列結果：

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### 使用文字變數 {#using-text-variables}

此標 **[!UICONTROL Text]** 簽可讓您建立變數欄位，這些欄位可在HTML中使用&lt;%=和%>字元，並使用以下語法： **$（識別碼）**。

使用此方法可輕鬆將字串本土化。 請參 [閱轉換Web表格](../../web/using/translating-a-web-form.md)

例如，您可以建立 **Contact** 欄位，讓您在HTML內容中顯示「上次連絡日期：」字串。 要執行此操作，請遵循下列步驟：

1. 按一下HTML **[!UICONTROL Text]** 文字的標籤。
1. 按一下 **[!UICONTROL Add]** 圖示。
1. 在欄 **[!UICONTROL Identifier]** 中，輸入變數的名稱
1. 在列中 **[!UICONTROL Text]** 輸入預設值。

   ![](assets/s_ncs_admin_survey_html_text.png)

1. 在HTML內容中，透過 **&lt;%= $(Contact)%>語法插入此文字變數** 。

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >如果您在HTML編輯器中輸入這些字元， **則&lt;** and **>** （和）欄位將被轉義字元取代。 在這種情況下，您需要按一下HTML文字編輯器的圖示， **[!UICONTROL Display source code]** 以修正原始碼。

1. 開啟表 **[!UICONTROL Preview]** 單標籤，以檢視在HTML中輸入的值：

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

此操作模式可讓您對Web表單的文本進行分解，並使用整合翻譯工具管理翻譯。 如需詳細資訊，請參 [閱轉換Web表格](../../web/using/translating-a-web-form.md)。

## 插入影像 {#inserting-images}

若要將影像包含在表單中，必須將其儲存在可從外部存取的伺服器上。

選擇菜 **[!UICONTROL Static elements>Image]** 單。

選擇要插入的影像源：它可以來自公共資源庫，也可以儲存在外部可訪問的外部伺服器上。

![](assets/s_ncs_admin_survey_add_img.png)

如果這是圖庫中的影像，請在欄位的組合方塊中選取；如果它位於外部檔案中，請輸入訪問路徑。 標籤將通過將游標傳遞到影像上（與HTML中的ALT欄位一致）或影像未顯示時顯示。

您可在編輯器的中央區段檢視影像。
