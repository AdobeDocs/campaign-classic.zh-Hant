---
product: campaign
title: 定義網路表單屬性
description: 定義網路表單屬性
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Forms
exl-id: 37aaaa03-0656-4a9b-bcae-74de33e3737b
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 1%

---

# 定義網路表單屬性{#defining-web-forms-properties}



您可以完全設定並個人化網路表單，以符合您的需求。 引數必須在屬性視窗中輸入。

屬性視窗可透過 **[!UICONTROL Properties]** 按鈕。 此視窗可讓您存取網路表單的特定設定範圍。 某些設定可能源自範本設定。

![](assets/s_ncs_admin_survey_properties_general.png)

## 整體表單屬性 {#overall-form-properties}

在 **[!UICONTROL General]** 標籤上，您可以修改 **標籤** 表單的。 強烈建議不要變更 **內部名稱**.

![](assets/s_ncs_admin_survey_properties_general_tab.png)

表單建立期間會選擇表單範本。 之後無法變更。 有關建立和管理表單範本的詳細資訊，請參閱 [使用網路表單範本](using-a-web-form-template.md).

## 表單資料儲存 {#form-data-storage}

依預設，Web表單的欄位會儲存在收件者表格中。 您可以透過選取新表格來變更所使用的表格 **[!UICONTROL Document type]** 欄位。 此 **[!UICONTROL Zoom]** 圖示可讓您檢視所選表格的內容。

依預設，答案會儲存在 **收件者表單的回覆** 表格。

## 設定錯誤頁面 {#setting-up-an-error-page}

您可以設定錯誤頁面：在執行表單期間發生錯誤時，將顯示此頁面。

錯誤頁面會在表單屬性視窗的對應標籤中定義。

依預設，它會顯示下列資訊：

![](assets/s_ncs_admin_survey_default_error_page.png)

顯示的字串內容定義於 **[!UICONTROL Error page]** 屬性視窗的標籤。 此 **[!UICONTROL HTML]** 索引標籤顯示呈現和 **[!UICONTROL Texts]** 索引標籤可讓您修改文字字串並在必要時新增一些文字：

![](assets/s_ncs_admin_survey_error_page.png)

## 表單本地化 {#form-localization}

此 **[!UICONTROL Localization]** 索引標籤可讓您選取網頁表單的設計和顯示語言。

另請參閱 [轉譯網路表單](translating-a-web-form.md).

## 表單瀏覽與轉譯 {#form-browsing-and-rendering}

此 **[!UICONTROL Rendering]** 索引標籤可讓您定義在網頁表單頁面與所使用的轉譯範本之間瀏覽的型別。

您可以選擇透過連結或按鈕導覽。

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

依預設，按鈕是導覽元素。 它們可讓您執行下列動作：

* 按一下「 」，核准目前頁面並顯示下一頁 **[!UICONTROL Next]**. 此按鈕會顯示在除最後一個頁面以外的所有頁面上。
* 按一下以顯示上一頁 **[!UICONTROL Previous]**. 此按鈕會顯示在第一個頁面以外的所有頁面上。
* 按一下「 」，儲存表單回應 **[!UICONTROL Approve]** 按鈕。 此按鈕只顯示在最後一頁。

這些元素會顯示在每個頁面的底部。 他們的位置可以變更。 要執行此操作，必須修改樣式表。

>[!NOTE]
>
>您可以隱藏 **[!UICONTROL Previous]** 按鈕。 若要這麼做，請前往相關頁面並核取 **[!UICONTROL Disallow returning to the previous page]** 選項。 選取頁面樹狀結構的根目錄時，此選項可供存取。

此 **[!UICONTROL Template]** 的欄位 **[!UICONTROL Rendering]** 索引標籤可讓您從可用的主題中選取主題。

主題會儲存在 **[!UICONTROL Administration>Configuration>Form rendering]** 樹狀結構的節點。 另請參閱 [選取表單轉譯範本](form-rendering.md#selecting-the-form-rendering-template)

範例演算會顯示在屬性視窗的下方。 此 **[!UICONTROL Edit link]** 圖示可讓您檢視所選主題的設定。

![](assets/s_ncs_admin_survey_properties_render.png)

## 表單中的文字 {#texts-in-the-form}

此 **[!UICONTROL Page]** tab可讓您定義表單頁首與頁尾的內容。 另請參閱 [定義頁首與頁尾](form-rendering.md#defining-headers-and-footers).

它也可讓您管理翻譯。 另請參閱 [轉譯網路表單](translating-a-web-form.md).

## 表單的協助工具 {#accessibility-of-the-form}

網路表單若符合下列條件，則可供使用者存取 **[!UICONTROL Online]** 以及目前日期是否在有效期內。 表單的狀態會在發佈階段期間修改(請參閱 [發佈表單](publishing-a-web-form.md#publishing-a-form))。 狀態會顯示在 **專案** 部分 **[!UICONTROL General]** 屬性視窗的標籤。

有效期從 **[!UICONTROL Start]** 結束日期 **[!UICONTROL End date]**. 如果這些欄位中未指定日期，則表單具有永久有效性。

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>如果表單已關閉，因此其有效期尚未到達或已過期，或者Adobe Campaign運運算元已關閉表單，則當使用者嘗試存取該表單時，會顯示一則訊息。 您可以按一下「 」，將此訊息個人化 **[!UICONTROL Personalize the message displayed if the form is closed...]**.

## 表單存取控制 {#form-access-control}

依預設，存取網路表單會以匿名模式執行：存取表單的所有運運算元都會被指派為WebApp運運算元許可權。

您可以啟用表單顯示的存取控制，例如在內部網路網站上傳送表單時，以便驗證使用者。 若要這麼做，請顯示 **[!UICONTROL Properties]** 窗體，然後按一下 **[!UICONTROL Enable access control]** 選項，如下所示：

![](assets/s_ncs_admin_survey_access_ctrl.png)

存取頁面時，將會出現下列驗證表單：

![](assets/s_ncs_admin_survey_access_login.png)

登入和密碼是Adobe Campaign操作員所使用的專案。 如需詳細資訊，請參閱[本章節](../../platform/using/access-management.md)。

此 **[!UICONTROL Use a specific account]** 選項可讓您限制存取表單之操作員的讀取或寫入許可權。 使用下拉式方塊來選取將負責授與這些許可權的運運算元或運運算元群組。

![](assets/s_ncs_admin_survey_access_op_select.png)

## 表單URL引數 {#form-url-parameters}

您可以在表單的URL中新增其他引數，以個人化其內容並初始化內容（語言、加密的收件者ID、公司、儲存在變數中的計算公式等）。 這可讓您透過數個不同的URL來授予一個表單的存取權，並根據URL中指出的引數值來個人化頁面內容。

依預設，Adobe Campaign會提供引數來預覽表單和檢查錯誤。 您可以建立連結至表單的新設定，這些設定可能會使用資料庫中欄位的值或本機變數的值。

## 標準引數 {#standard-parameters}

預設可使用下列引數：

* **id** 表示加密的識別碼。
* **lang** 以變更顯示語言。
* **來源** 指定回應者的來源。
* **_uuid** 啟用發佈前的表單檢視和錯誤追蹤。 此引數供內部使用（建立與偵錯）：當您透過此URL存取網路表單時，所建立的記錄不會納入追蹤（報表）的考量。 來源會強製為 **[!UICONTROL Adobe Campaign]** 值。

   此變數會與 **預覽(_P)** 引數和/或 **偵錯(_D)**：

   **預覽(_P)** 以顯示上次儲存的版本。 此引數僅能用於測試階段。

   **偵錯(_D)** 顯示表單頁面中資料輸入或計算的追蹤。 這可用來取得錯誤的詳細資訊，包括發佈表單後。

   >[!CAUTION]
   >
   >透過具有的URL顯示表單時 **_uuid** 引數，值 **[!UICONTROL origin]** 引數被強製為 **Adobe Campaign**.

## 新增引數 {#adding-parameters}

引數可透過以下方式新增： **[!UICONTROL Parameters...]** 標籤（在表單的「屬性」視窗中）。 可以將變數設為強制性，如下所示：

![](assets/s_ncs_admin_survey_properties_param.png)

您必須指定將從中擷取引數值的儲存位置。 若要這麼做，請選取其中一個儲存選項，然後按一下 **[!UICONTROL Storage]** 索引標籤來選取相關欄位或變數。 儲存選項詳見 [回應儲存欄位](web-forms-answers.md#response-storage-fields).

回應者狀態（0、1或任何其他值）可接著新增至URL以存取表單。 此資訊可在表單頁面或測試方塊中重複使用。 顯示的頁面可根據內容的值設定條件，如下所示：

1. 客戶首頁(**status=1**)：

   ![](assets/s_ncs_admin_survey_test_client.png)

1. 潛在客戶首頁(**status=0**)：

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. 其他設定檔的首頁(例如 **status=12**)：

   ![](assets/s_ncs_admin_survey_test_other.png)

若要設定此表單，請建立測試方塊並將其放在圖表的開頭，如下所示：

![](assets/s_ncs_admin_survey_test.png)

測試方塊可讓您設定頁面排序條件：

![](assets/s_ncs_admin_survey_test_box.png)
