---
product: campaign
title: 定義網路表單頁面排序
description: 定義網路表單頁面排序
audience: web
content-type: reference
topic-tags: web-forms
exl-id: c5b5c398-c13b-4ebe-88b2-8ff84741422e
source-git-commit: 360fd1ed8970c17c0687eaca0a4c1960d6f5838c
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 2%

---

# 定義網路表單頁面排序{#defining-web-forms-page-sequencing}

表單可包含一或多個頁面。 它是透過圖表建置，可讓您排序頁面、測試、指令碼執行、頁面跳轉和記錄步驟。 全域圖表設計模式與Campaign工作流程的模式相同。

## 關於上一頁和下一頁 {#about-previous-page-and-next-page}

對於每個頁面，您可以刪除&#x200B;**[!UICONTROL Next]**&#x200B;或&#x200B;**[!UICONTROL Previous]**&#x200B;按鈕。 若要這麼做，請選取相關頁面，然後選取選項&#x200B;**[!UICONTROL Disable next page]**&#x200B;或&#x200B;**[!UICONTROL Disallow returning to the previous page]** 。

![](assets/s_ncs_admin_survey_no_next_page.png)

您可以用連結取代這些按鈕。 請參閱[插入HTML內容](static-elements-in-a-web-form.md#inserting-html-content)。

## 插入跳轉 {#inserting-a-jump}

當使用者點按&#x200B;**[!UICONTROL Next]**&#x200B;時，**[!UICONTROL Jump]**&#x200B;物件可供存取其他頁面或其他表單。

目的地可以是：

* 表單的另一頁。 要執行此操作，請選取&#x200B;**[!UICONTROL Internal activity]**，然後指定所需頁面，如下所示：

   ![](assets/s_ncs_admin_jump_param1.png)

* 另一種形式。 要執行此操作，請選擇&#x200B;**[!UICONTROL Explicit]**&#x200B;選項並指定目標表單。

   ![](assets/s_ncs_admin_jump_param2.png)

* 目的地可儲存在變數中。 在此情況下，請從下拉式清單中選取它，如下所示：

   ![](assets/s_ncs_admin_jump_param3.png)

* **[!UICONTROL Comment]**&#x200B;索引標籤可讓您輸入當運算子按一下圖表中的物件時，將顯示的資訊。

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## 範例：根據URL的參數存取其他表單 {#example--accessing-another-form-according-to-a-parameter-of-the-url}

在以下範例中，我們要設定Web表單，在核准後，該表單將顯示URL參數指定的其他表單。 若要這麼做，請套用下列步驟：

1. 在表單結尾處插入跳轉：這會取代&#x200B;**[!UICONTROL End]**&#x200B;方塊。

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. 在表單屬性中，新增儲存在本機變數(**next**)中的參數(**next**)。 在[將資料儲存在本地變數](web-forms-answers.md#storing-data-in-a-local-variable)中會詳細說明本地變數。

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. 編輯&#x200B;**[!UICONTROL Jump]**&#x200B;物件，選取&#x200B;**[!UICONTROL Stored in a variable]**&#x200B;選項，然後從下拉式方塊選取&#x200B;**next**&#x200B;變數。

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. 傳送URL必須包含目的地表單的內部名稱，例如：

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   當使用者按一下&#x200B;**[!UICONTROL Approve]**&#x200B;按鈕時，會顯示表單&#x200B;**APP22**。

## 插入到表單的其他頁面的連結 {#inserting-a-link-to-another-page-of-the-form}

您可以插入表單中其他頁面的連結。 若要這麼做，請將&#x200B;**[!UICONTROL Link]**&#x200B;類型靜態元素新增至頁面。 有關詳細資訊，請參閱[插入連結](static-elements-in-a-web-form.md#inserting-a-link)。

## 條件式頁面顯示 {#conditional-page-display}

### 根據回應顯示 {#display-based-on-responses}

**[!UICONTROL Test]**&#x200B;方塊可讓您條件表單中的頁面順序。 它可讓您根據測試結果定義各種分支線。 這可讓您根據使用者提供的答案，顯示不同的頁面。

例如，您可以為已線上訂購的客戶顯示不同的頁面，而為已訂購超過10個的客戶顯示另一個頁面。 要執行此操作，請在表單的第一頁插入&#x200B;**[!UICONTROL Number]**&#x200B;類型輸入欄位，讓使用者指出已下了多少訂單。

![](assets/s_ncs_admin_survey_test_ex0.png)

您可以將此資訊儲存在資料庫的欄位中，或使用本機變數。

>[!NOTE]
>
>在[響應儲存欄位](web-forms-answers.md#response-storage-fields)中詳細說明儲存模式。

在我們的範例中，我們想使用變數：

![](assets/s_ncs_admin_survey_test_ex1.png)

在表單的圖表中，插入測試方塊以定義條件。 對於每個條件，測試方塊的輸出將新增一個新分支。

![](assets/s_ncs_admin_survey_test_ex2.png)

選取&#x200B;**[!UICONTROL Activate the default branching]**&#x200B;選項，以針對無條件的情況新增轉變。 如果定義的條件涵蓋所有可能的情況，則不需要此選項。

接著，當其中一個或其他條件為true時，定義頁面排序，例如：

![](assets/s_ncs_admin_survey_test_ex3.png)

### 根據參數顯示 {#display-based-on-parameters}

您也可以根據Web表單的初始化參數或根據資料庫中儲存的值來個人化頁面排序。 請參閱[表單URL參數](defining-web-forms-properties.md#form-url-parameters)。

## 新增指令碼 {#adding-scripts}

**[!UICONTROL Script]**&#x200B;物件可讓您直接輸入JavaScript指令碼，例如修改欄位值、從資料庫擷取資料，或呼叫Adobe Campaign API。

## 個人化結束頁面 {#personalizing-the-end-page}

必須在圖的結尾處放置結束頁。 當用戶按一下Web表單中的&#x200B;**[!UICONTROL Approve]**&#x200B;按鈕時，將顯示結束頁。

若要個人化此頁面，請連按兩下&#x200B;**[!UICONTROL End]**，然後在中央編輯器中輸入頁面內容。

![](assets/s_ncs_admin_survey_end_page_edit.png)

* 您可以複製並貼上現有的HTML內容。 要執行此操作，請按一下&#x200B;**[!UICONTROL Display source code]**&#x200B;並插入HTML代碼。
* 您可以使用外部URL;若要這麼做，請選取對應的選項，然後輸入要顯示的頁面URL。
