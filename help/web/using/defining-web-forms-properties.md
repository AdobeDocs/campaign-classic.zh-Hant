---
title: 定義Web表單屬性
seo-title: 定義Web表單屬性
description: 定義Web表單屬性
seo-description: null
page-status-flag: never-activated
uuid: 2fb0952a-5f73-48f5-b344-e3247cefca62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 36953eb5-3296-4796-9352-945121bbdc69
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 定義Web表單屬性{#defining-web-forms-properties}

Web表單可完全設定且可個人化，以符合您的需求。 參數必須在屬性窗口中輸入。

可通過Web表單工具欄 **[!UICONTROL Properties]** 中的按鈕訪問屬性窗口。 此視窗可讓您存取特定於Web表單的設定範圍。 某些設定可能源自範本設定。

![](assets/s_ncs_admin_survey_properties_general.png)

## 整體表單屬性 {#overall-form-properties}

在「屬 **[!UICONTROL General]** 性」窗口的頁籤中，可以修改 **表單的** 「標籤」。 強烈建議不要更改內部 **名稱**。

![](assets/s_ncs_admin_survey_properties_general_tab.png)

表單範本是在建立表單時選擇的。 以後不能更改。 有關建立和管理表單模板的詳細資訊，請 [參閱使用Web表單模板](../../web/using/using-a-web-form-template.md)。

## 表單資料儲存 {#form-data-storage}

預設情況下，Web表單的欄位儲存在收件人表中。 可以通過從欄位中選擇新表來更改所用 **[!UICONTROL Document type]** 表。 圖 **[!UICONTROL Zoom]** 示可讓您檢視所選表格的內容。

依預設，答案會儲存在表格 **[!UICONTROL Answer to a recipient form]** 中。

## 設定錯誤頁面 {#setting-up-an-error-page}

您可以設定錯誤頁面：在表單執行期間發生錯誤時，將顯示此頁。

錯誤頁是在表單屬性窗口的相應頁籤中定義的。

依預設，它會顯示下列資訊：

![](assets/s_ncs_admin_survey_default_error_page.png)

顯示的字串內容在屬性窗口的 **[!UICONTROL Error page]** 頁籤中定義。 此標 **[!UICONTROL HTML]** 簽會顯示轉譯，而此標 **[!UICONTROL Texts]** 簽可讓您修改文字字串，並視需要新增一些文字：

![](assets/s_ncs_admin_survey_error_page.png)

## 表單本地化 {#form-localization}

此標 **[!UICONTROL Localization]** 簽可讓您選取Web表單的設計和顯示語言。

請參 [閱轉換Web表格](../../web/using/translating-a-web-form.md)。

## 表單瀏覽與轉換 {#form-browsing-and-rendering}

此標 **[!UICONTROL Rendering]** 簽可讓您定義Web表單頁面與使用之轉換範本之間的瀏覽類型。

您可以選擇透過連結或按鈕來導覽。

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

按鈕是預設的導覽元素。 它們可讓您執行下列動作：

* 核准目前頁面，並按一下以顯示下一頁 **[!UICONTROL Next]**。 此按鈕會顯示在除最後一頁以外的所有頁面上。
* 按一下以顯示上一頁 **[!UICONTROL Previous]**。 除第一個按鈕外，此按鈕會顯示在所有頁面上。
* 按一下按鈕以儲存表格 **[!UICONTROL Approve]** 回應。 此按鈕僅顯示在最後一頁。

這些元素會顯示在每個頁面的底部。 他們的立場可以改變。 要執行此操作，必須修改樣式表。

>[!NOTE]
>
>有些頁面上的按鈕可 **[!UICONTROL Previous]** 以隱藏。 若要這麼做，請前往相關頁面並勾選 **[!UICONTROL Disallow returning to the previous page]** 選項。 當選取頁面樹的根目錄時，即可存取此選項。

標籤 **[!UICONTROL Template]** 的欄位可 **[!UICONTROL Rendering]** 讓您從可用主題中選取主題。

主題將保存在樹 **[!UICONTROL Administration>Configuration>Form rendering]** 的節點中。 請參 [閱選擇表單轉換範本](../../web/using/form-rendering.md#selecting-the-form-rendering-template)

屬性窗口的下半部會顯示示例渲染。 圖 **[!UICONTROL Edit link]** 示可讓您檢視所選主題的設定。

![](assets/s_ncs_admin_survey_properties_render.png)

## 格式文本 {#texts-in-the-form}

此標 **[!UICONTROL Page]** 簽可讓您定義表單頁首和頁尾的內容。 請參閱 [定義頁首和頁尾](../../web/using/form-rendering.md#defining-headers-and-footers)。

它也可讓您管理翻譯。 請參 [閱轉換Web表格](../../web/using/translating-a-web-form.md)。

## 表單的協助功能 {#accessibility-of-the-form}

如果網頁表單是，且目前日期在有效 **[!UICONTROL Online]** 期間內，使用者可存取該表單。 在發佈階段會修改表單的狀態(請參 [閱發佈表單](../../web/using/publishing-a-web-form.md#publishing-a-form))。 狀態顯示在屬性窗 **口的** 「項 **[!UICONTROL General]** 目」部分中。

有效期間從日期 **[!UICONTROL Start]** 到日期 **[!UICONTROL End date]**。 如果這些欄位中未指定日期，表單就具有永久有效性。

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>如果表單已關閉，因此其有效期尚未到達或已過期，或者如果表單由Adobe Campaign運算子關閉，當使用者嘗試存取表單時，會顯示訊息。 您可以按一下，將此訊息個人化 **[!UICONTROL Personalize the message displayed if the form is closed...]**。

## 表單存取控制 {#form-access-control}

依預設，Web表格的存取是以匿名模式進行：所有存取表單的運算子都會指派WebApp運算子權限。

您可以啟用表格顯示的存取控制，例如在內部網路網站上傳送表格以驗證使用者。 若要這麼做，請顯示相 **[!UICONTROL Properties]** 關表單的視窗，然後按一下 **[!UICONTROL Enable access control]** 選項，如下所示：

![](assets/s_ncs_admin_survey_access_ctrl.png)

存取頁面時，將會出現下列驗證表單：

![](assets/s_ncs_admin_survey_access_login.png)

登入和密碼是Adobe Campaign營運商使用的登入和密碼。 如需詳細資訊，請參閱[本小節](../../platform/using/access-management.md)。

選 **[!UICONTROL Use a specific account]** 項可讓您限制存取表單之運算子的讀取或寫入權限。 使用下拉式方塊來選取負責授與這些權限的運算元或運算元群組。

![](assets/s_ncs_admin_survey_access_op_select.png)

## 表單URL參數 {#form-url-parameters}

您可以在表單的URL中新增其他參數，以個人化其內容並初始化內容（語言、加密的收件者ID、公司、儲存在變數中的計算公式等）。 這可讓您透過數個不同的URL存取一個表單，並根據URL中指示之參數值個人化頁面內容。

依預設，Adobe Campaign會提供預覽表單和檢查錯誤的參數。 您可以建立連結至表單的新設定，這可能會使用資料庫中欄位或本機變數的值。

## 標準參數 {#standard-parameters}

下列參數預設可用：

* **id** ，指出加密的識別碼。
* **lang** ：更改顯示語言。
* **來源** ：指定回應者的來源。
* **_uuid** 可在發佈和錯誤追蹤之前啟用表單檢視。 此參數僅供內部使用（建立和調試）:當您透過此URL存取Web表格時，在追蹤（報表）中不會考慮建立的記錄。 原點被強制為 **[!UICONTROL Adobe Campaign]** 值。

   它可與 **_preview** 參數和／或** _debug**搭配使用：

   **_preview** ，以顯示上次儲存的版本。 此參數僅能用於測試階段。

   **_debug** ，顯示表單頁面中資料輸入或計算的追蹤。 這可用來取得更多錯誤的相關資訊，包括表單發佈後的錯誤資訊。

   >[!CAUTION]
   >
   >當透過具有 **_uuid參數的URL顯示表單時** ，會強制 **[!UICONTROL origin]** 將參數值顯示 **至Adobe Campaign**。

## 添加參數 {#adding-parameters}

可以通過表單的「屬 **[!UICONTROL Parameters...]** 性」(Properties)窗口中的頁籤添加參數。 可強制執行，如下所示：

![](assets/s_ncs_admin_survey_properties_param.png)

必須指定從中檢索參數值的儲存位置。 若要這麼做，請選取其中一個儲存選項，然後按一 **[!UICONTROL Storage]** 下標籤以選取欄位或相關變數。 「響應」儲存欄位中詳 [細介紹了儲存選項](../../web/using/web-forms-answers.md#response-storage-fields)。

回應者狀態（0、1或任何其他值）隨後可新增至URL以存取表單。 這些資訊可在表單的頁面或測試方塊中重複使用。 顯示的頁面可以根據上下文的值進行條件調整，如下所示：

1. 客戶首頁(**status=1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. 潛在客戶的首頁(**status=0**):

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. 其他設定檔的首頁(例如， **status=12**):

   ![](assets/s_ncs_admin_survey_test_other.png)

要配置此表單，請建立一個測試框並將其置於圖的開頭，如下所示：

![](assets/s_ncs_admin_survey_test.png)

測試方塊可讓您設定頁面順序條件：

![](assets/s_ncs_admin_survey_test_box.png)

