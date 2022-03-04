---
product: campaign
title: 定義Web表單頁排序
description: 定義Web表單頁排序
feature: Web Forms
exl-id: c5b5c398-c13b-4ebe-88b2-8ff84741422e
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 0%

---

# 定義Web表單頁排序{#defining-web-forms-page-sequencing}

![](../../assets/common.svg)

表單可以包含一個或多個頁面。 它通過圖形構建，您可以對頁面進行排序、測試、指令碼執行、頁面跳轉和記錄步驟。 全局圖設計模式與市場活動工作流模式相同。

## 關於上一頁和下一頁 {#about-previous-page-and-next-page}

對於每個頁面，可以刪除 **[!UICONTROL Next]** 或 **[!UICONTROL Previous]** 按鈕。 要執行此操作，請選擇相關頁面並選擇選項 **[!UICONTROL Disable next page]** 或 **[!UICONTROL Disallow returning to the previous page]** 。

![](assets/s_ncs_admin_survey_no_next_page.png)

可以用連結替換這些按鈕。 請參閱 [插入HTML內容](static-elements-in-a-web-form.md#inserting-html-content)。

## 插入跳轉 {#inserting-a-jump}

的 **[!UICONTROL Jump]** 當用戶按一下時，對象可訪問其他頁面或其他表單 **[!UICONTROL Next]**。

目標可以是：

* 窗體的另一頁。 要執行此操作，請選擇 **[!UICONTROL Internal activity]** 然後指定所需頁，如下所示：

   ![](assets/s_ncs_admin_jump_param1.png)

* 另一種形式。 要執行此操作，請選擇 **[!UICONTROL Explicit]** 的子菜單。

   ![](assets/s_ncs_admin_jump_param2.png)

* 目標可以儲存在變數中。 在這種情況下，請從下拉清單中選擇它，如下所示：

   ![](assets/s_ncs_admin_jump_param3.png)

* 的 **[!UICONTROL Comment]** 頁籤中，您可以輸入操作員在圖中按一下對象時可見的資訊。

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## 示例：根據URL的參數訪問另一個窗體 {#example--accessing-another-form-according-to-a-parameter-of-the-url}

在以下示例中，我們要配置一個Web表單，在批准後，該表單將顯示由URL的參數指定的另一個表單。 若要這麼做，請套用下列步驟：

1. 在表單末尾插入跳轉：這將取代 **[!UICONTROL End]** 框。

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. 在表單屬性中，添加參數(**下**)儲存在本地變數(**下**)。 本地變數詳見 [將資料儲存在局部變數中](web-forms-answers.md#storing-data-in-a-local-variable)。

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. 編輯 **[!UICONTROL Jump]** 對象，選擇 **[!UICONTROL Stored in a variable]** 的 **下** 的下界。

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. 傳遞URL必須包括目標表單的內部名稱，例如：

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   當用戶按一下 **[!UICONTROL Approve]** 按鈕 **APP22** 的上界。

## 插入指向窗體另一頁的連結 {#inserting-a-link-to-another-page-of-the-form}

可以插入指向窗體其他頁面的連結。 為此，請添加 **[!UICONTROL Link]** 在頁面中鍵入static element。 有關此內容的詳細資訊，請參閱 [插入連結](static-elements-in-a-web-form.md#inserting-a-link)。

## 條件頁顯示 {#conditional-page-display}

### 基於響應顯示 {#display-based-on-responses}

的 **[!UICONTROL Test]** 框中，您可以定義窗體中頁的順序。 它允許您根據test結果定義各種分支行。 這使您能夠根據用戶提供的答案顯示不同的頁面。

例如，您可以為已線上訂購的客戶顯示不同的頁面，為已下達超過十個訂單的客戶顯示另一個頁面。 為此，在表單的第一頁中，插入 **[!UICONTROL Number]** 為用戶鍵入輸入欄位，以說明已下達的訂單數。

![](assets/s_ncs_admin_survey_test_ex0.png)

您可以將此資訊儲存在資料庫的欄位中，或使用本地變數。

>[!NOTE]
>
>儲存模式在 [響應儲存欄位](web-forms-answers.md#response-storage-fields)。

在我們的示例中，我們希望使用變數：

![](assets/s_ncs_admin_survey_test_ex1.png)

在表單的圖中，插入一個test框以定義條件。 對於每個條件，將在test框的輸出處添加新分支。

![](assets/s_ncs_admin_survey_test_ex2.png)

選擇 **[!UICONTROL Activate the default branching]** 的雙曲餘切值。 如果定義的條件涵蓋了所有可能的情況，則不必使用此選項。

接下來，在其中一個或其他條件為true時定義頁排序，例如：

![](assets/s_ncs_admin_survey_test_ex3.png)

### 基於參數顯示 {#display-based-on-parameters}

您還可以根據Web表單的初始化參數或資料庫中儲存的值個性化頁面排序。 請參閱 [表單URL參數](defining-web-forms-properties.md#form-url-parameters)。

## 添加指令碼 {#adding-scripts}

的 **[!UICONTROL Script]** object允許您直接輸入JavaScript指令碼，例如修改欄位值、從資料庫檢索資料或調用Adobe CampaignAPI。

## 個性化結束頁 {#personalizing-the-end-page}

必須在圖的末尾放置結束頁。 當用戶按一下 **[!UICONTROL Approve]** 按鈕。

要個性化此頁面，請按兩下 **[!UICONTROL End]** 在中央編輯器中輸入頁面內容。

![](assets/s_ncs_admin_survey_end_page_edit.png)

* 您可以複製和貼上現有HTML內容。 要執行此操作，請按一下 **[!UICONTROL Display source code]** 並插入HTML。
* 可以使用外部URL;為此，請選擇相應選項並輸入要顯示的頁面的URL。
