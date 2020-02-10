---
title: 定義Web表單頁面順序
seo-title: 定義Web表單頁面順序
description: 定義Web表單頁面順序
seo-description: null
page-status-flag: never-activated
uuid: 297fad62-d806-4bd8-9b8c-313c20344ab0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 85bf3244-6896-43e7-96b8-84c45c282fec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 定義Web表單頁面順序{#defining-web-forms-page-sequencing}

表單可包含一或多個頁面。 它是透過圖表建立的，可讓您對頁面進行排序、測試、指令碼執行和頁面跳轉錄制階段。 圖結構模式與工作流模式相同。

## 關於上一頁和下一頁 {#about-previous-page-and-next-page}

您可以針對每個頁面刪除 **[!UICONTROL Next]** 或按 **[!UICONTROL Previous]** 鈕。 若要這麼做，請選取相關頁面，然後選取選 **[!UICONTROL Disable next page]** 項或 **[!UICONTROL Disallow returning to the previous page]** 。

![](assets/s_ncs_admin_survey_no_next_page.png)

您可以用連結來取代這些按鈕。 請參 [閱插入HTML內容](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)。

## 插入跳轉 {#inserting-a-jump}

當使 **[!UICONTROL Jump]** 用者點按時，物件可存取其他頁面或其他表格 **[!UICONTROL Next]**。

目標可以是：

* 表單的另一頁。 若要這麼做，請選 **[!UICONTROL Internal activity]** 取並指定所要的頁面，如下所示：

   ![](assets/s_ncs_admin_jump_param1.png)

* 另一種形式。 若要這麼做，請選取選 **[!UICONTROL Explicit]** 項並指定目標表單。

   ![](assets/s_ncs_admin_jump_param2.png)

* 目標可以儲存在變數中。 在此情況下，請從下拉式清單中選取它，如下所示：

   ![](assets/s_ncs_admin_jump_param3.png)

* 該選 **[!UICONTROL Comment]** 項卡可讓您輸入操作員在按一下圖中的對象時將顯示的資訊。

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## 範例：根據URL的參數存取其他表單 {#example--accessing-another-form-according-to-a-parameter-of-the-url}

在下列範例中，我們要設定Web表格，當核准後，該表格將顯示由URL參數指定的其他表格。 若要這麼做，請套用下列步驟：

1. 在表單結尾插入跳轉：這會取代方 **[!UICONTROL End]** 塊。

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. 在表單屬性中，新增儲存在本&#x200B;**機變數**(下一&#x200B;**步**)的參數。 局部變數在將資料儲 [存於局部變數中有詳細說明](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable)。

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. 編輯 **[!UICONTROL Jump]** 物件，選取 **[!UICONTROL Stored in a variable]** 選項，並從下 **拉式方塊中選** 取下一個變數。

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. 傳送URL必須包含目標表單的內部名稱，例如：

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   當使用者按一下按 **[!UICONTROL Approve]** 鈕時，會顯 **示表單APP22** 。

## 插入到表單另一頁的連結 {#inserting-a-link-to-another-page-of-the-form}

您可以插入表單中其他頁面的連結。 若要這麼做，請新增 **[!UICONTROL Link]** 文字靜態元素至頁面。 有關詳細資訊，請參閱 [插入連結](../../web/using/static-elements-in-a-web-form.md#inserting-a-link)。

## 條件式頁面顯示 {#conditional-page-display}

### 根據回應顯示 {#display-based-on-responses}

此方 **[!UICONTROL Test]** 塊可讓您在表單中設定頁面順序。 它可讓您根據測試結果定義各種分支線。 這可讓您根據使用者提供的答案顯示不同的頁面。

例如，您可以針對已線上訂購的客戶顯示不同的頁面，或針對已下訂超過10份的客戶顯示另一個頁面。 若要這麼做，請在表單的第一頁中插入 **[!UICONTROL Number]** 文字輸入欄位，讓使用者指出已下多少訂單。

![](assets/s_ncs_admin_survey_test_ex0.png)

您可以將此資訊儲存在資料庫的欄位中，或使用本機變數。

>[!NOTE]
>
>「響應」儲存欄位中詳細 [介紹了儲存模式](../../web/using/web-forms-answers.md#response-storage-fields)。

在我們的範例中，我們想使用變數：

![](assets/s_ncs_admin_survey_test_ex1.png)

在表單的圖表中，插入測試方塊以定義條件。 對於每個條件，在測試盒的輸出處都會新增一個分支。

![](assets/s_ncs_admin_survey_test_ex2.png)

選取 **[!UICONTROL Activate the default branching]** 選項，以新增無任何條件的轉場。 如果所定義的條件涵蓋了所有可能的情況，則此選項是不必要的。

接著，在其中一個或其他條件為true時定義頁面順序，例如：

![](assets/s_ncs_admin_survey_test_ex3.png)

### 根據參數顯示 {#display-based-on-parameters}

您也可以根據Web表單的初始化參數或根據資料庫中儲存的值個性化頁面排序。 請參 [閱表單URL參數](../../web/using/defining-web-forms-properties.md#form-url-parameters)。

## 添加指令碼 {#adding-scripts}

此物 **[!UICONTROL Script]** 件可讓您直接輸入JavaScript指令碼，例如修改欄位值、從資料庫擷取資料或呼叫Adobe Campaign API。

## 個人化結束頁面 {#personalizing-the-end-page}

必須在圖的末尾放置一個結束頁。 當使用者按一下Web表單中的按鈕時， **[!UICONTROL Approve]** 會顯示結束頁面。

若要個人化此頁面，請連按兩 **[!UICONTROL End]** 下並在中央編輯器中輸入頁面內容。

![](assets/s_ncs_admin_survey_end_page_edit.png)

* 您可以複製和貼上現有的HTML內容。 若要這麼做，請按一 **[!UICONTROL Display source code]** 下並插入HTML程式碼。
* 您可使用外部URL;若要這麼做，請選取對應的選項，並輸入要顯示之頁面的URL。

