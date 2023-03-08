---
product: campaign
title: 定義網路表單屬性
description: 定義網路表單屬性
feature: Web Forms
exl-id: 37aaaa03-0656-4a9b-bcae-74de33e3737b
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 1%

---

# 定義網路表單屬性{#defining-web-forms-properties}

![](../../assets/common.svg)

您可以完全配置和個性化網路表單，以滿足您的需求。 必須在屬性窗口中輸入參數。

可透過 **[!UICONTROL Properties]** 按鈕。 此視窗可讓您存取Web表單的特定設定範圍。 某些設定可能來自範本設定。

![](assets/s_ncs_admin_survey_properties_general.png)

## 整體表單屬性 {#overall-form-properties}

在 **[!UICONTROL General]** 頁簽，您可以修改 **標籤** 表單的。 強烈建議不要變更 **內部名稱**.

![](assets/s_ncs_admin_survey_properties_general_tab.png)

表單建立期間會選擇表單範本。 以後無法更改。 有關建立和管理表單模板的詳細資訊，請參閱 [使用網路表單範本](using-a-web-form-template.md).

## 表單資料儲存 {#form-data-storage}

預設情況下，網路表單的欄位會儲存在收件者表格中。 您可以變更表格，方法是從 **[!UICONTROL Document type]** 欄位。 此 **[!UICONTROL Zoom]** 圖示可讓您檢視所選表格的內容。

依預設，答案會儲存在 **收件者表單的回覆** 表格。

## 設定錯誤頁面 {#setting-up-an-error-page}

您可以設定錯誤頁面：在表單執行期間發生錯誤時，會顯示此頁面。

錯誤頁面是在表單屬性視窗的對應索引標籤中定義。

依預設，它會顯示下列資訊：

![](assets/s_ncs_admin_survey_default_error_page.png)

顯示的字串內容定義於 **[!UICONTROL Error page]** 頁簽。 此 **[!UICONTROL HTML]** 索引標籤會顯示呈現和 **[!UICONTROL Texts]** 索引標籤可讓您修改文字字串，並視需要新增一些文字：

![](assets/s_ncs_admin_survey_error_page.png)

## 表單本地化 {#form-localization}

此 **[!UICONTROL Localization]** 頁簽，您可以選擇Web表單的設計和顯示語言。

請參閱 [轉譯網路表單](translating-a-web-form.md).

## 表單瀏覽和轉譯 {#form-browsing-and-rendering}

此 **[!UICONTROL Rendering]** 索引標籤可讓您定義Web表單的頁面之間的瀏覽類型和使用的呈現範本。

您可以選擇透過連結或按鈕導覽。

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

按鈕預設為導覽元素。 它們可讓您執行下列動作：

* 核准目前頁面並顯示下一頁，方法是按一下 **[!UICONTROL Next]**. 此按鈕會顯示在除最後一個之外的所有頁面上。
* 按一下 **[!UICONTROL Previous]**. 此按鈕會顯示在除第一個按鈕外的所有頁面上。
* 按一下 **[!UICONTROL Approve]** 按鈕。 此按鈕只會顯示在最後一頁。

這些元素會顯示在每個頁面的底部。 他們的立場可以改變。 要執行此操作，必須修改樣式表。

>[!NOTE]
>
>可以隱藏 **[!UICONTROL Previous]** 按鈕。 若要這麼做，請前往相關頁面並檢查 **[!UICONTROL Disallow returning to the previous page]** 選項。 選取頁面樹的根時，即可存取此選項。

此 **[!UICONTROL Template]** 欄位 **[!UICONTROL Rendering]** 標籤中，您可以從可用主題中選取主題。

主題會儲存在 **[!UICONTROL Administration>Configuration>Form rendering]** 樹的節點。 請參閱 [選取表單呈現範本](form-rendering.md#selecting-the-form-rendering-template)

樣例呈現顯示在屬性窗口的下部。 此 **[!UICONTROL Edit link]** 圖示可讓您檢視所選主題的設定。

![](assets/s_ncs_admin_survey_properties_render.png)

## 格式文本 {#texts-in-the-form}

此 **[!UICONTROL Page]** 索引標籤可讓您定義表單頁首和頁尾的內容。 請參閱 [定義頁首和頁尾](form-rendering.md#defining-headers-and-footers).

您也可以管理翻譯。 請參閱 [轉譯網路表單](translating-a-web-form.md).

## 表單的協助工具 {#accessibility-of-the-form}

使用者可存取網路表單（若有） **[!UICONTROL Online]** 如果目前日期在有效期內。 在發佈階段期間會修改表單的狀態(請參閱 [發佈表單](publishing-a-web-form.md#publishing-a-form))。 狀態會顯示在 **專案** 區段 **[!UICONTROL General]** 頁簽。

有效期從 **[!UICONTROL Start]** 日期至 **[!UICONTROL End date]**. 如果未在這些欄位中指定日期，表單將具有永久有效性。

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>如果表單已關閉，且因此其有效期未達到或已過期，或者如果表單已由Adobe Campaign運算子關閉，則當使用者嘗試存取表單時，會顯示訊息。 您可以按一下 **[!UICONTROL Personalize the message displayed if the form is closed...]**.

## 表單存取控制 {#form-access-control}

依預設，會以匿名模式存取網路表單：所有存取表單的運算子都會獲派WebApp運算子權限。

您可以啟用表單顯示的存取控制，例如在內部網站上傳送表單時，以驗證使用者。 若要這麼做，請顯示 **[!UICONTROL Properties]** 窗口，然後按一下 **[!UICONTROL Enable access control]** 選項，如下所示：

![](assets/s_ncs_admin_survey_access_ctrl.png)

存取頁面時，會出現下列驗證表單：

![](assets/s_ncs_admin_survey_access_login.png)

登入和密碼是Adobe Campaign運算子使用的。 如需詳細資訊，請參閱[本章節](../../platform/using/access-management.md)。

此 **[!UICONTROL Use a specific account]** 選項可讓您限制存取表單之運算子的讀取或寫入權限。 使用下拉式方塊，選取將負責授予這些權限的運算子或運算子群組。

![](assets/s_ncs_admin_survey_access_op_select.png)

## 表單URL參數 {#form-url-parameters}

您可以在表單的URL中新增其他參數，以個人化其內容並初始化內容（語言、加密的收件者ID、公司、儲存在變數中的計算公式等）。 這可讓您透過數個不同的URL存取一個表單，並根據URL中指出之參數的值個人化頁面內容。

依預設，Adobe Campaign會提供參數以預覽表單和檢查錯誤。 您可以建立連結到表單的新設定，該設定可能會使用資料庫中某個欄位或本地變數的值。

## 標準參數 {#standard-parameters}

預設可使用下列參數：

* **id** 以指出加密的識別碼。
* **朗** 來更改顯示語言。
* **來源** 指定回應者的來源。
* **_uuid** 可在發佈和錯誤追蹤前啟用表單檢視。 此參數供內部使用（建立和除錯）:當您透過此URL存取Web表單時，在追蹤（報表）中不會考慮已建立的記錄。 來源會強制 **[!UICONTROL Adobe Campaign]** 值。

   它與 **_預覽** 參數和/或 **_debug**:

   **_預覽** 顯示上次保存的版本。 此參數只能在測試階段中使用。

   **_debug** 顯示在表單頁面中輸入或計算的資料跟蹤。 這可用來取得錯誤的詳細資訊，包括表單發佈後的資訊。

   >[!CAUTION]
   >
   >透過URL顯示表單時， **_uuid** 參數， **[!UICONTROL origin]** 參數強制為 **Adobe Campaign**.

## 新增參數 {#adding-parameters}

參數可透過 **[!UICONTROL Parameters...]** 頁簽。 可強制使用，如下所示：

![](assets/s_ncs_admin_survey_properties_param.png)

必須指定要從中檢索參數值的儲存位置。 要執行此操作，請選取其中一個儲存選項，然後按一下 **[!UICONTROL Storage]** 索引標籤來選取欄位或相關變數。 儲存選項在 [回應儲存欄位](web-forms-answers.md#response-storage-fields).

回應者狀態（0、1或任何其他值）隨後可新增至URL以存取表單。 此資訊可在表單的頁面或測試方塊中重複使用。 顯示的頁面可根據內容的值進行條件調整，如下所示：

1. 客戶首頁(**status=1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. 潛在客戶首頁(**狀態=0**):

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. 其他設定檔的首頁(例如 **status=12**):

   ![](assets/s_ncs_admin_survey_test_other.png)

若要設定此表單，請建立測試方塊並將其置於圖表的開頭，如下所示：

![](assets/s_ncs_admin_survey_test.png)

測試方塊可讓您設定頁面排序條件：

![](assets/s_ncs_admin_survey_test_box.png)
