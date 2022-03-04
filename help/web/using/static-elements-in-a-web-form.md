---
product: campaign
title: 網路表單中的靜態元素
description: 網路表單中的靜態元素
feature: Web Forms
exl-id: 364d90af-4b18-4104-8b6a-be80cfde3b0b
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 3%

---

# 網路表單中的靜態元素{#static-elements-in-a-web-form}

![](../../assets/common.svg)

在表單的頁面中可以包含用戶沒有交互的元素；這些是靜態元素，如影像、HTML內容、水準條或超文本連結。 這些元素是通過工具欄中的第一個按鈕通過選擇 **[!UICONTROL Static elements]**。

![](assets/s_ncs_admin_survey_add_static_element.png)

以下類型的欄位可用：

* 值基於先前提供的答案（在表單上下文中）或資料庫。
* 超文本連結、HTML、水準條。 請參閱 [插入HTML內容](#inserting-html-content)。
* 保存在資源庫或用戶可訪問的伺服器上的映像。 請參閱 [插入影像](#inserting-images)。
* 在客戶端和/或伺服器端執行的指令碼。 它必須用JavaScript編寫，並且與大多數瀏覽器相容，以確保在客戶端正確執行。

   >[!NOTE]
   >
   >在伺服器端，指令碼可以使用中定義的函式 [市場活動JSAPI文檔](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant)。

## 插入HTML內容 {#inserting-html-content}

您可以在表單頁中包括HTML內容：超文本連結、影像、格式化段落、視頻等。

HTML編輯器允許您輸入要插入表單頁面的內容。 要開啟編輯器，請按一下 **[!UICONTROL Static elements]** > **[!UICONTROL HTML]** 。

您可以直接輸入和格式化內容，或顯示原始碼窗口以貼上到某些外部內容中。 要切換到「原始碼」模式，請按一下工具欄中的第一個表徵圖：

![](assets/s_ncs_admin_survey_html_editor.png)

要插入資料庫欄位，請使用個性化按鈕。

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>只有在HTML編輯器中定義字串時，才會轉換這些字串 **[!UICONTROL Texts]** 的子菜單。 否則，將不收集。 有關此內容的詳細資訊，請參閱 [翻譯Web表單](translating-a-web-form.md)。

### 插入連結 {#inserting-a-link}

在編輯窗口中填寫欄位，如下例所示：

要添加超文本連結，請轉到 **[!UICONTROL Static elements]** > **[!UICONTROL Link]**。

![](assets/s_ncs_admin_survey_add_link.png)

* 的 **[!UICONTROL Label]** 是超文本連結的內容，它將顯示在表單頁面上。
* 的 **[!UICONTROL URL]** 是所需地址，例如： [https://www.adobe.com](https://www.adobe.com) 或 [info@adobe.com](mailto:info@adobe.com) 發送消息。
* 的 **[!UICONTROL Window]** 欄位中，您可以選擇站點情況下連結的顯示模式。 您可以決定在新窗口、當前窗口或其他窗口中開啟連結。
* 可以添加工具提示，如下所示：

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* 您可以選擇將連結顯示為按鈕或影像。 要執行此操作，請在 **[!UICONTROL Type]** 的子菜單。

### 連結類型 {#types-of-links}

預設情況下，連結與URL類型操作相關聯，以便可以在URL欄位中輸入連結目標地址。

![](assets/s_ncs_admin_survey_link_url.png)

您可以為連結定義其他操作，以便用戶按一下該連結可執行以下操作：

* 刷新頁面

   要執行此操作，請選擇 **[!UICONTROL Refresh page]** 的子菜單。 **[!UICONTROL Action]** 的子菜單。

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* 顯示下一頁/上一頁

   要執行此操作，請選擇 **[!UICONTROL Next page]** 或 **[!UICONTROL Previous page]** 的子菜單。 **[!UICONTROL Action]** 的子菜單。

   ![](assets/s_ncs_admin_survey_link_next.png)

   你可以隱藏 **[!UICONTROL Next]** 和/或 **[!UICONTROL Back]** 按鈕。 請參閱此 [頁](defining-web-forms-page-sequencing.md)。

   連結將替換 **[!UICONTROL Next]** 按鈕

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* 顯示另一頁

   的 **[!UICONTROL Enable a transition]** 選項，您可以顯示與在 **[!UICONTROL Transition]** 的子菜單。

   ![](assets/s_ncs_admin_survey_link_viral.png)

   預設情況下，頁面只有一個輸出轉換。 要建立新過渡，請選擇該頁，然後按一下 **[!UICONTROL Add]** 按鈕 **[!UICONTROL Output transitions]** ，如下所示：

   ![](assets/s_ncs_admin_survey_add_transition.png)

   在圖中，此添加內容將如下所示：

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >有關Web表單中頁面排序的詳細資訊，請參閱 [定義Web表單頁排序](defining-web-forms-page-sequencing.md)。

### 個性化HTML內容 {#personalizing-html-content}

您可以個性化表單頁的HTML內容，並記錄上一頁中的資料。 例如，您可以建立汽車保險Web表單，其第一頁允許您提供聯繫資訊和汽車品牌。

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

使用個性化欄位將用戶名和所選品牌重新注入到下一頁。 要使用的語法取決於資訊儲存模式。 有關此內容的詳細資訊，請參閱 [使用收集的資訊](web-forms-answers.md#using-collected-information)。

>[!NOTE]
>
>出於安全原因，在 **`<%=`** 公式將替換為轉義字元。

在我們的示例中，收件人的名字和姓氏儲存在資料庫的欄位中，而其汽車的品牌儲存在變數中。 第2頁上個性化消息的語法如下：

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

這將產生以下結果：

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### 使用文本變數 {#using-text-variables}

的 **[!UICONTROL Text]** 頁籤用於建立可用於&lt;%=和%>字元之間的HTML的變數欄位，其語法如下： **$（標識符）**。

使用此方法可輕鬆將字串本地化。 請參閱 [翻譯Web表單](translating-a-web-form.md)

例如，您可以建立 **聯繫人** 欄位，您可以在HTML內容中顯示「上次聯繫人的日期：」字串。 要執行此操作，請遵循下列步驟：

1. 按一下 **[!UICONTROL Text]** 的子菜單。
1. 按一下 **[!UICONTROL Add]** 表徵圖
1. 在 **[!UICONTROL Identifier]** 列，輸入變數的名稱
1. 在 **[!UICONTROL Text]** 列，輸入預設值。

   ![](assets/s_ncs_admin_survey_html_text.png)

1. 在HTML內容中，通過 **&lt;%= $（聯繫人）%>** 語法。

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >如果在HTML編輯器中輸入這些字元， **&lt;** 和 **>** 欄位將替換為其轉義字元。 在這種情況下，您需要通過按一下 **[!UICONTROL Display source code]** 表徵圖。

1. 開啟 **[!UICONTROL Preview]** 標籤，以查看在HTML中輸入的值：

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

此操作模式允許您僅定義一次Web表單的文本，並使用整合翻譯工具管理翻譯。 有關此內容的詳細資訊，請參閱 [翻譯Web表單](translating-a-web-form.md)。

## 插入影像 {#inserting-images}

要在表單中包含影像，必須將其保存在可從外部訪問的伺服器上。

選擇 **[!UICONTROL Static elements]** > **[!UICONTROL Image]** 的子菜單。

選擇要插入的影像的源：它可以來自公共資源庫，也可以儲存在外部可訪問的外部伺服器上。

![](assets/s_ncs_admin_survey_add_img.png)

如果這是庫中的影像，請在欄位的組合框中選擇它；如果它位於外部檔案中，則輸入訪問路徑。 標籤將通過將游標傳遞到影像(與HTML中的ALT欄位一致)或影像未顯示來顯示。

可以在編輯器的中心部分查看影像。
