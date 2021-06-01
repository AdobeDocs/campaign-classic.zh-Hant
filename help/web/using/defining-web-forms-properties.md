---
product: campaign
title: 定義網路表單屬性
description: 定義網路表單屬性
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 37aaaa03-0656-4a9b-bcae-74de33e3737b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 1%

---

# 定義網路表單屬性{#defining-web-forms-properties}

Web表單可完全配置且可個性化，以滿足您的需求。 必須在屬性窗口中輸入參數。

可通過Web表單工具欄中的&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕訪問屬性窗口。 此視窗可讓您存取Web表單的特定設定範圍。 某些設定可能來自範本設定。

![](assets/s_ncs_admin_survey_properties_general.png)

## 整體表單屬性{#overall-form-properties}

在屬性窗口的&#x200B;**[!UICONTROL General]**&#x200B;頁簽中，可以修改表單的&#x200B;**標籤**。 強烈建議不要更改&#x200B;**內部名稱**。

![](assets/s_ncs_admin_survey_properties_general_tab.png)

表單建立期間會選擇表單範本。 以後無法更改。 有關建立和管理表單模板的詳細資訊，請參閱[使用Web表單模板](../../web/using/using-a-web-form-template.md)。

## 表單資料儲存{#form-data-storage}

預設情況下，網路表單的欄位會儲存在收件者表格中。 您可以從&#x200B;**[!UICONTROL Document type]**&#x200B;欄位中選取新表格，以變更所使用的表格。 **[!UICONTROL Zoom]**&#x200B;圖示可讓您檢視所選表格的內容。

預設情況下，答案儲存在&#x200B;**收件者表單**&#x200B;的回答表中。

## 設定錯誤頁{#setting-up-an-error-page}

您可以設定錯誤頁面：在表單執行期間發生錯誤時，會顯示此頁面。

錯誤頁面是在表單屬性視窗的對應索引標籤中定義。

依預設，它會顯示下列資訊：

![](assets/s_ncs_admin_survey_default_error_page.png)

顯示的字串內容在屬性窗口的&#x200B;**[!UICONTROL Error page]**&#x200B;頁簽中定義。 **[!UICONTROL HTML]**&#x200B;標籤會顯示呈現，而&#x200B;**[!UICONTROL Texts]**&#x200B;標籤可讓您修改文字字串，並視需要新增一些文字：

![](assets/s_ncs_admin_survey_error_page.png)

## 表單本地化{#form-localization}

**[!UICONTROL Localization]**&#x200B;標籤可讓您選取網頁表單的設計和顯示語言。

請參閱[轉譯網頁表單](../../web/using/translating-a-web-form.md)。

## 表單瀏覽和呈現{#form-browsing-and-rendering}

**[!UICONTROL Rendering]**&#x200B;索引標籤可讓您定義Web表單頁面之間的瀏覽類型和使用的呈現範本。

您可以選擇透過連結或按鈕導覽。

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

按鈕預設為導覽元素。 它們可讓您執行下列動作：

* 按一下&#x200B;**[!UICONTROL Next]**&#x200B;核准目前頁面並顯示下一頁。 此按鈕會顯示在除最後一個之外的所有頁面上。
* 按一下&#x200B;**[!UICONTROL Previous]**&#x200B;顯示上一頁。 此按鈕會顯示在除第一個按鈕外的所有頁面上。
* 按一下&#x200B;**[!UICONTROL Approve]**&#x200B;按鈕以儲存表單回應。 此按鈕只會顯示在最後一頁。

這些元素會顯示在每個頁面的底部。 他們的立場可以改變。 要執行此操作，必須修改樣式表。

>[!NOTE]
>
>可以隱藏某些頁面上的&#x200B;**[!UICONTROL Previous]**&#x200B;按鈕。 要執行此操作，請前往相關頁面並核取&#x200B;**[!UICONTROL Disallow returning to the previous page]**&#x200B;選項。 選取頁面樹的根時，即可存取此選項。

**[!UICONTROL Rendering]**&#x200B;標籤的&#x200B;**[!UICONTROL Template]**&#x200B;欄位可讓您從可用的主題中選取主題。

主題保存在樹的&#x200B;**[!UICONTROL Administration>Configuration>Form rendering]**&#x200B;節點中。 請參閱[選取表單呈現範本](../../web/using/form-rendering.md#selecting-the-form-rendering-template)

樣例呈現顯示在屬性窗口的下部。 **[!UICONTROL Edit link]**&#x200B;圖示可讓您檢視所選主題的設定。

![](assets/s_ncs_admin_survey_properties_render.png)

## 格式為{#texts-in-the-form}的文本

**[!UICONTROL Page]**&#x200B;標籤可讓您定義表單頁首和頁尾的內容。 請參閱[定義頁眉和頁腳](../../web/using/form-rendering.md#defining-headers-and-footers)。

您也可以管理翻譯。 請參閱[轉譯網頁表單](../../web/using/translating-a-web-form.md)。

## 表單{#accessibility-of-the-form}的輔助功能

如果網路表單&#x200B;**[!UICONTROL Online]**，且目前日期在有效期內，使用者便可存取該表單。 在發佈階段期間會修改表單的狀態（請參閱[發佈表單](../../web/using/publishing-a-web-form.md#publishing-a-form)）。 狀態顯示在屬性窗口&#x200B;**[!UICONTROL General]**&#x200B;頁簽的&#x200B;**Project**&#x200B;部分中。

有效期從&#x200B;**[!UICONTROL Start]**&#x200B;日期到&#x200B;**[!UICONTROL End date]**。 如果未在這些欄位中指定日期，表單將具有永久有效性。

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>如果表單已關閉，且因此其有效期未達到或已過期，或者如果表單已由Adobe Campaign運算子關閉，則當使用者嘗試存取表單時，會顯示訊息。 您可以按一下&#x200B;**[!UICONTROL Personalize the message displayed if the form is closed...]**&#x200B;以個人化此訊息。

## 表單訪問控制{#form-access-control}

依預設，會以匿名模式存取網路表單：所有存取表單的運算子都會獲派WebApp運算子權限。

您可以啟用表單顯示的存取控制，例如在內部網站上傳送表單時，以驗證使用者。 要執行此操作，請顯示相關表單的&#x200B;**[!UICONTROL Properties]**&#x200B;窗口，然後按一下&#x200B;**[!UICONTROL Enable access control]**&#x200B;選項，如下所示：

![](assets/s_ncs_admin_survey_access_ctrl.png)

存取頁面時，會出現下列驗證表單：

![](assets/s_ncs_admin_survey_access_login.png)

登入和密碼是Adobe Campaign運算子使用的。 如需詳細資訊，請參閱[本章節](../../platform/using/access-management.md)。

**[!UICONTROL Use a specific account]**&#x200B;選項可讓您限制存取表單之運算子的讀取或寫入權限。 使用下拉式方塊，選取將負責授予這些權限的運算子或運算子群組。

![](assets/s_ncs_admin_survey_access_op_select.png)

## 表單URL參數{#form-url-parameters}

您可以在表單的URL中新增其他參數，以個人化其內容並初始化內容（語言、加密的收件者ID、公司、儲存在變數中的計算公式等）。 這可讓您透過數個不同的URL存取一個表單，並根據URL中指出之參數的值個人化頁面內容。

依預設，Adobe Campaign會提供參數以預覽表單和檢查錯誤。 您可以建立連結到表單的新設定，該設定可能會使用資料庫中某個欄位或本地變數的值。

## 標準參數{#standard-parameters}

預設可使用下列參數：

* **** id表示加密的識別碼。
* **** lang以變更顯示語言。
* **** 指定回應者的來源。
* **在發佈** 和錯誤追蹤之前檢視表單(_U)。此參數供內部使用（建立和除錯）:當您透過此URL存取Web表單時，在追蹤（報表）中不會考慮已建立的記錄。 原點會強制為&#x200B;**[!UICONTROL Adobe Campaign]**&#x200B;值。

   它可與&#x200B;**_preview**&#x200B;參數和/或&#x200B;**_debug**&#x200B;搭配使用：

   **_** previewo顯示上次保存的版本。此參數只能在測試階段中使用。

   **_** debugto顯示表單頁面中輸入或計算的資料跟蹤。這可用來取得錯誤的詳細資訊，包括表單發佈後的資訊。

   >[!CAUTION]
   >
   >透過具有&#x200B;**_uuid**&#x200B;參數的URL顯示表單時， **[!UICONTROL origin]**&#x200B;參數的值會強制為&#x200B;**Adobe Campaign**。

## 添加參數{#adding-parameters}

您可以透過表單「屬性」視窗的&#x200B;**[!UICONTROL Parameters...]**&#x200B;標籤來新增參數。 可強制使用，如下所示：

![](assets/s_ncs_admin_survey_properties_param.png)

必須指定要從中檢索參數值的儲存位置。 要執行此操作，請選取其中一個儲存選項，然後按一下&#x200B;**[!UICONTROL Storage]**&#x200B;標籤以選取相關欄位或變數。 在[響應儲存欄位](../../web/using/web-forms-answers.md#response-storage-fields)中詳細說明了儲存選項。

回應者狀態（0、1或任何其他值）隨後可新增至URL以存取表單。 此資訊可在表單的頁面或測試方塊中重複使用。 顯示的頁面可根據內容的值進行條件調整，如下所示：

1. 客戶首頁(**status=1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. 潛在客戶首頁(**status=0**):

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. 其他設定檔的首頁（例如&#x200B;**status=12**）:

   ![](assets/s_ncs_admin_survey_test_other.png)

若要設定此表單，請建立測試方塊並將其置於圖表的開頭，如下所示：

![](assets/s_ncs_admin_survey_test.png)

測試方塊可讓您設定頁面排序條件：

![](assets/s_ncs_admin_survey_test_box.png)
