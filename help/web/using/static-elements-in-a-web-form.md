---
product: campaign
title: 網路表單中的靜態元素
description: 網路表單中的靜態元素
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 364d90af-4b18-4104-8b6a-be80cfde3b0b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1266'
ht-degree: 4%

---

# 網路表單中的靜態元素{#static-elements-in-a-web-form}

您可以在表單的頁面中加入使用者沒有互動的元素；這些是靜態元素，例如影像、HTML內容、水準條或超文字連結。 這些元素是透過工具列中的第一個按鈕，透過選取&#x200B;**[!UICONTROL Static elements]**&#x200B;而建立。

![](assets/s_ncs_admin_survey_add_static_element.png)

可用的欄位類型如下：

* 值以先前提供的答案（在表單的上下文中）或資料庫為基礎。
* 超文字連結、HTML、橫條。 請參閱[插入HTML內容](#inserting-html-content)。
* 儲存在資源庫或使用者可存取之伺服器上的影像。 請參閱[插入影像](#inserting-images)。
* 在用戶端和/或伺服器端執行的指令碼。 它必須以JavaScript撰寫，且與大部分的瀏覽器相容，以確保在用戶端上正確執行。

   >[!NOTE]
   >
   >在伺服器端，指令碼可使用[Campaign JSAPI檔案](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)中定義的函式。

## 插入HTML內容{#inserting-html-content}

您可以在表單頁面中加入HTML內容：超文本連結、影像、格式化段落、視頻等。

HTML編輯器可讓您輸入要插入表單頁面的內容。 若要開啟編輯器，請按一下「**[!UICONTROL Static elements]** > **[!UICONTROL HTML]** 」。

您可以直接輸入內容並設定其格式，或顯示原始碼視窗以貼入某些外部內容。 若要切換為「原始碼」模式，請按一下工具列中的第一個圖示：

![](assets/s_ncs_admin_survey_html_editor.png)

若要插入資料庫欄位，請使用個人化按鈕。

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>只有在&#x200B;**[!UICONTROL Texts]**&#x200B;子索引標籤中定義了HTML編輯器中輸入的字串，才會進行翻譯。 否則將不會收集。 有關詳細資訊，請參閱[轉譯Web表單](../../web/using/translating-a-web-form.md)。

### 插入連結{#inserting-a-link}

填寫編輯視窗中的欄位，如下列範例所示：

若要新增超文字連結，請前往&#x200B;**[!UICONTROL Static elements]** > **[!UICONTROL Link]**。

![](assets/s_ncs_admin_survey_add_link.png)

* **[!UICONTROL Label]**&#x200B;是超文字連結的內容，將顯示在表單頁面上。
* **[!UICONTROL URL]**&#x200B;是所需地址，例如：網站的[https://www.adobe.com](https://www.adobe.com)，或傳送訊息的[info@adobe.com](mailto:info@adobe.com)。
* **[!UICONTROL Window]**&#x200B;欄位可讓您在網站的情況下選取連結的顯示模式。 您可以決定在新視窗、目前視窗或其他視窗中開啟連結。
* 您可以新增工具提示，如下所示：

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* 您可以選擇將連結顯示為按鈕或影像。 要執行此操作，請在&#x200B;**[!UICONTROL Type]**&#x200B;欄位中選取顯示類型。

### 連結類型{#types-of-links}

依預設，連結會與URL類型動作相關聯，以便在URL欄位中輸入連結目的地址。

![](assets/s_ncs_admin_survey_link_url.png)

您可以定義連結的其他動作，讓使用者可以按一下連結來執行下列動作：

* 重新整理頁面

   要執行此操作，請在&#x200B;**[!UICONTROL Action]**&#x200B;欄位的下拉式方塊中選取&#x200B;**[!UICONTROL Refresh page]**&#x200B;選項。

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* 顯示下一頁/上一頁

   要執行此操作，請在&#x200B;**[!UICONTROL Action]**&#x200B;欄位的下拉式方塊中選取&#x200B;**[!UICONTROL Next page]**&#x200B;或&#x200B;**[!UICONTROL Previous page]**&#x200B;選項。

   ![](assets/s_ncs_admin_survey_link_next.png)

   如果&#x200B;**[!UICONTROL Next]**&#x200B;和/或&#x200B;**[!UICONTROL Back]**&#x200B;按鈕要由連結替換，則可以隱藏這些按鈕。 請參閱此[page](../../web/using/defining-web-forms-page-sequencing.md)。

   該連結將替換預設使用的&#x200B;**[!UICONTROL Next]**&#x200B;按鈕。

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* 顯示其他頁面

   **[!UICONTROL Enable a transition]**&#x200B;選項可讓您顯示與在&#x200B;**[!UICONTROL Transition]**&#x200B;欄位中選取的出站轉變相關聯的特定頁面。

   ![](assets/s_ncs_admin_survey_link_viral.png)

   依預設，頁面只有一個輸出轉變。 若要建立新轉變，請選取頁面，然後按一下&#x200B;**[!UICONTROL Output transitions]**&#x200B;區段中的&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，如下所示：

   ![](assets/s_ncs_admin_survey_add_transition.png)

   在圖中，此新增項目看起來會像這樣：

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >如需Web表單中頁面排序的詳細資訊，請參閱[定義網頁表單頁面排序](../../web/using/defining-web-forms-page-sequencing.md)。

* 使用從Facebook設定檔擷取的資料預先載入表單欄位

   >[!CAUTION]
   >
   >只有在安裝了&#x200B;**[!UICONTROL Social Marketing]**&#x200B;應用程式時，此函式才可用。 若要使用此選項，您需要建立Facebook應用程式，並輸入&#x200B;**[!UICONTROL Facebook Connect]**&#x200B;外部帳戶。 有關詳細資訊，請參見[此頁面](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

   **[!UICONTROL Preload with Facebook]**&#x200B;選項可讓您將按鈕插入表單中，以使用Facebook設定檔資訊預先載入欄位。

   ![](assets/web_social_webapp_037.png)

   當使用者按一下&#x200B;**[!UICONTROL Fill in automatically]**&#x200B;按鈕時，會開啟Facebook的權限要求視窗。

   ![](assets/web_social_webapp_029.png)

   >[!NOTE]
   >
   >設定外部帳戶時，可以變更延伸權限清單。 如果您未輸入任何延伸權限，Facebook會依預設轉送基本設定檔資訊。\
   >若要檢視擴充權限清單及其語法，請按一下這裡：[https://developers.facebook.com/docs/reference/api/permissions/](https://developers.facebook.com/docs/reference/api/permissions/)

   如果使用者同意共用其資訊，表單的欄位會預先載入。

   ![](assets/web_social_webapp_030.png)

針對此使用案例，我們建立了由下列元素組成的Web應用程式：

* 包含表單的頁面
* **[!UICONTROL Record]** 活動
* **[!UICONTROL End]**&#x200B;活動

![](assets/social_webapp_031.png)

要添加預載入按鈕，請應用以下步驟：

1. 建立表單。

   ![](assets/social_webapp_032.png)

1. 移至表單中欄位的相同層級，並新增連結。

   ![](assets/social_webapp_033.png)

1. 輸入標籤並選擇&#x200B;**[!UICONTROL Button]**&#x200B;類型。

   ![](assets/social_webapp_034.png)

1. 轉到&#x200B;**[!UICONTROL Action]**&#x200B;欄位並選擇&#x200B;**[!UICONTROL Preload with Facebook]**。

   ![](assets/social_webapp_035.png)

1. 前往&#x200B;**[!UICONTROL Application]**&#x200B;欄位，並選取&#x200B;**[!UICONTROL Facebook Connect]**&#x200B;類型先前建立的外部帳戶。 有關詳細資訊，請參見[此頁面](../../social/using/creating-a-facebook-application.md#configuring-external-accounts)。

   ![](assets/social_webapp_036.png)

### 個人化HTML內容{#personalizing-html-content}

您可以使用上一頁記錄的資料，個人化表單頁面的HTML內容。 例如，您可以建立車險Web表單，其第一頁允許您提供聯繫資訊和車牌。

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

使用個人化欄位，將使用者名稱和選取的品牌重新插入至下一頁。 使用的語法取決於資訊儲存模式。 有關詳細資訊，請參閱[使用收集的資訊](../../web/using/web-forms-answers.md#using-collected-information)。

>[!NOTE]
>
>基於安全原因，**`<%=`**&#x200B;公式中輸入的值將替換為逸出字元。

在我們的範例中，收件者的名字和姓氏會儲存在資料庫的欄位中，而其車牌會儲存在變數中。 第2頁個人化訊息的語法如下：

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

這會產生下列結果：

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### 使用文本變數{#using-text-variables}

**[!UICONTROL Text]**&#x200B;索引標籤可讓您建立變數欄位，這些欄位可用於&lt;%=和%>字元之間的HTML中，使用下列語法：**$（識別碼）**。

使用此方法可輕鬆將字串本地化。 請參閱[轉譯網頁表單](../../web/using/translating-a-web-form.md)

例如，您可以建立&#x200B;**Contact**&#x200B;欄位，讓您將「上次連絡日期：」字串顯示到HTML內容。 要執行此操作，請遵循下列步驟：

1. 按一下HTML文字的&#x200B;**[!UICONTROL Text]**&#x200B;標籤。
1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;圖示。
1. 在&#x200B;**[!UICONTROL Identifier]**&#x200B;欄中，輸入變數的名稱
1. 在&#x200B;**[!UICONTROL Text]**&#x200B;欄中，輸入預設值。

   ![](assets/s_ncs_admin_survey_html_text.png)

1. 在HTML內容中，透過&#x200B;**&lt;%= $（連絡人）%>**&#x200B;語法插入此文字變數。

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >如果在HTML編輯器中輸入這些字元， ****&#x200B;和&#x200B;****&#x200B;欄位將替換為其逸出字元。 在這種情況下，您需要按一下HTML文本編輯器的&#x200B;**[!UICONTROL Display source code]**&#x200B;表徵圖來更正原始碼。

1. 開啟表單的&#x200B;**[!UICONTROL Preview]**&#x200B;標籤以檢視在HTML中輸入的值：

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

此作業模式可讓您僅定義一次網路表單的文字，並使用整合翻譯工具管理翻譯。 有關詳細資訊，請參閱[轉譯Web表單](../../web/using/translating-a-web-form.md)。

## 插入影像{#inserting-images}

若要將影像包含在表單中，必須將其儲存在可從外部存取的伺服器上。

選擇&#x200B;**[!UICONTROL Static elements]** > **[!UICONTROL Image]**&#x200B;菜單。

選擇要插入的影像源：它可以來自公共資源庫，或儲存在可從外部訪問的外部伺服器上。

![](assets/s_ncs_admin_survey_add_img.png)

如果這是資料庫中的影像，請在欄位的下拉式方塊中選取該影像；如果位於外部檔案中，請輸入訪問路徑。 標籤的顯示方式是將游標傳遞到影像上（與HTML中的ALT欄位一致），或影像未顯示時。

您可以在編輯器的中央區段中檢視影像。
