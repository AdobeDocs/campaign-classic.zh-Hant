---
title: 報表的屬性
seo-title: 報表的屬性
description: 報表的屬性
seo-description: null
page-status-flag: never-activated
uuid: 56163f53-d115-45b8-94a5-c173ac4c6533
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: 5ec88743-be51-438c-9064-dd0196fdd7d3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b2222b2997105801164f930428c7b05ae7d11336

---


# 報表的屬性{#properties-of-the-report}

## 概觀 {#overview}

您可以完全個人化並設定您的報表，以符合您的需求。 若要這麼做，請編輯其屬性。 報表屬性可透過活動順序圖上方的「屬性」按鈕存取。

![](assets/s_ncs_advuser_report_properties_01.png)

## 整體屬性 {#overall-properties}

此標 **[!UICONTROL General]** 簽可讓您檢視或變更報表所關注的標籤和架構。 這些元素是在建立報表時輸入的。

我們不建議變更 **[!UICONTROL Internal name]** :這會用於報表存取URL。

報表範本是在報表建立期間選取的，以後無法變更。

若要變更報表所關注的表格，請按一 **[!UICONTROL Select link]** 下欄位右側的圖 **[!UICONTROL Document type]** 示。 要查看所選表格中的可用欄位，請按一下該 **[!UICONTROL Magnifier]** 表徵圖。

![](assets/s_ncs_advuser_report_properties_02.png)

## 報告協助功能 {#report-accessibility}

報表可從Adobe Campaign主控台以外的位置存取，例如透過網頁瀏覽器。 在此情況下，您必須設定報表存取控制，如下所示。

![](assets/s_ncs_advuser_report_properties_02b.png)

總體原則是：

* 此選 **[!UICONTROL Anonymous access]** 項可讓您不受限制地存取報表。 但是，不可能操縱。

   預設(&#39;webapp&#39;)報表運算子的權限可用來顯示報表元素。

* 此選 **[!UICONTROL Access control]** 項可讓Adobe Campaign營運商在登入後加以存取。
* 選 **[!UICONTROL Specific account]** 項可讓您在欄位中選取運算子的權限下執行報 **[!UICONTROL Operator]** 表。

本頁將詳述Web表 [單屬性](../../web/using/about-web-forms.md)。

## 管理報告本地化 {#managing-report-localization}

您可以設定要將報表翻譯為的語言。 若要這麼做，請按一下標 **[!UICONTROL Localization]** 簽。

![](assets/s_ncs_advuser_report_properties_06.png)

編輯語言是您所用的語言。 新增語言時，子標籤會出現在報表編輯頁面中。

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>有關此內容的詳細資訊，請參閱本節的相 [應章節](../../web/using/translating-a-web-form.md)。

## 個人化HTML演算 {#personalizing-html-rendering}

在標籤 **[!UICONTROL Rendering]** 中，您可以個人化頁面的資料顯示模式。 您可以選擇：

* 圖表轉換引擎：Adobe Campaign提供兩種不同的模式來產生圖表轉換。 依預設，演算引擎為HTML 5。 如有必要，您可以選取Flash演算。
* 報表中的導覽類型：按鈕或連結。
* 報表元素的標籤預設位置。 此位置可以為每個元素過載。
* 用於產生報表頁面的範本或主題。

本頁將詳述Web表 [單屬性](../../web/using/about-web-forms.md)。

![](assets/s_ncs_advuser_report_properties_08.png)

## 定義其他設定 {#defining-additional-settings}

此標 **[!UICONTROL Parameters]** 簽可讓您為報表建立其他設定：這些設定會在呼叫期間傳遞至URL。

本頁將詳述Web表 [單屬性](../../web/using/about-web-forms.md)。

>[!CAUTION]
>
>出於安全考慮，這些參數必須非常小心地使用。

要建立新設定：

1. 按一下 **[!UICONTROL Add]** 按鈕，然後輸入設定的名稱。

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. 如有必要，請指定是否必須設定。
1. 選擇要建立的設定類型：或 **[!UICONTROL Filter]** 者 **[!UICONTROL Variable]**。

   選 **[!UICONTROL Filter entities]** 項可讓您使用資料庫的欄位做為參數。

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   資料直接在實體級別恢復： **ctx/recipient/@account**。

   選 **[!UICONTROL Variable]** 項可讓您建立或選取變數，此變數將作為URL的參數傳遞，並可用於篩選器中。

使用 **[!UICONTROL Response HTTP headers]** iframe，可讓您在將報表的頁面加入HTML頁面時，防止點按劫持。 若要避免點按劫持，您可以選擇 **[!UICONTROL X-Frame-options header]** 行為：

* **[!UICONTROL None]**:報告將不提供 **[!UICONTROL X-Frame-options header]**。
* **[!UICONTROL Same as origin]**:依預設設定新報表和重新發佈的報表。 主機名稱與報表的URL相同。
* **[!UICONTROL Deny]**:使用iframe時，報表無法包含在HTML頁面中。

![](assets/s_ncs_advuser_report_properties_09c.png)

## 新增變數 {#adding-variables}

此標 **[!UICONTROL Variables]** 簽包含報表中設定的變數清單。 這些變數會在報表的上下文中公開，並可用於計算。

按一下 **[!UICONTROL Add]** 按鈕以建立新變數。

若要檢視變數的定義，請選取該變數，然後按一下 **[!UICONTROL Detail...]** 按鈕。

![](assets/s_ncs_advuser_report_properties_10.png)

## 引用指令碼 {#referencing-scripts}

此標 **[!UICONTROL Scripts]** 簽可讓您參考在呼叫報表頁面時，將在用戶端和／或伺服器端執行的JavaScript代碼。

為了在用戶端上正常執行，參考的指令碼必須以JavaScript編寫，而且必須與大部分的瀏覽器相容。 如需詳細資訊，請參閱[本小節](../../web/using/web-forms-answers.md)。

## 個人化錯誤頁面 {#personalizing-the-error-page}

此標 **[!UICONTROL Error page]** 簽可讓您設定在報表顯示中發生錯誤時會顯示的訊息。

您可以定義文字，並將它們連結至特定識別碼，以管理報表本地化。 有關詳細資訊，請參 [閱添加頁眉和頁腳](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

![](assets/s_ncs_advuser_report_properties_11.png)

