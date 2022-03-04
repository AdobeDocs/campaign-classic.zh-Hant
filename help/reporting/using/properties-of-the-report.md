---
product: campaign
title: 報吿屬性
description: 瞭解有關報告屬性設定的詳細資訊
feature: Reporting
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 2%

---

# 報吿屬性{#properties-of-the-report}

![](../../assets/common.svg)

您可以完全個性化並配置報告以滿足您的需要。 為此，請編輯其屬性。 通過 **[!UICONTROL Properties]** 按鈕。

![](assets/s_ncs_advuser_report_properties_01.png)

一般屬性如下所述。 在 **[!UICONTROL Parameters]**。 **[!UICONTROL Variables]** 和 **[!UICONTROL Scripts]** 頁籤 [此部分](../../reporting/using/advanced-functionalities.md)。

## 常規屬性 {#overall-properties}

在 **[!UICONTROL General]** 頁籤中，可以編輯下面列出的設定：

* 報表的標籤和內部名稱。 的 **[!UICONTROL Internal name]** 在報告最終URL中使用。 報告建立後不應更改。

* 報告 **資料夾** 在建立報表期間選中。 最佳做法是為自定義報告建立專用資料夾，以便不會與 [內置報告](../../reporting/using/about-campaign-built-in-reports.md)。

* 的 **儲存** 的子菜單。 要更改報表的資料表，請按一下 **[!UICONTROL Select link]** 表徵圖 **[!UICONTROL Document type]** 的子菜單。

   ![](assets/s_ncs_advuser_report_properties_02.png)

* 的 **訪問控制** 參數。 下面介紹了這些設定。

## 控制對報告的訪問 {#report-accessibility}

可以在Adobe Campaign控制台或Web瀏覽器中訪問報告。 在這種情況下，必須配置報告訪問控制，如下所示。

![](assets/s_ncs_advuser_report_properties_02b.png)

可能的選項包括：

* **[!UICONTROL Anonymous access]**:此選項允許無限制地訪問報表。 但是，不可能操縱。

   「webapp」技術操作員的權限用於顯示報表元素。 瞭解更多資訊 [此部分](../../platform/using/access-management-operators.md)。

* **[!UICONTROL Access control]**:此選項使Adobe Campaign操作員在登錄後可以訪問它。
* **[!UICONTROL Specific account]**:此選項允許您使用在 **[!UICONTROL Operator]** 的子菜單。

## 翻譯報告 {#report-localization}

您可以配置要將報告翻譯成的語言。 要執行此操作，請按一下 **[!UICONTROL Localization]** 頁籤。

![](assets/s_ncs_advuser_report_properties_06.png)

編輯語言是您所用的語言。 添加語言時，子頁籤將出現在報告編輯頁面中。

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>有關「市場活動」中網頁本地化的詳細資訊，請參閱 [此部分](../../web/using/translating-a-web-form.md)。

## 個性化HTML呈現 {#personalizing-html-rendering}

在 **[!UICONTROL Rendering]** 頁籤。 您可以選擇：

* 報表中的導航類型：按鈕或連結。
* 報表元素標籤的預設位置。 此位置可為每個元素重載。
* 用於生成報表頁的模板或主題。

![](assets/s_ncs_advuser_report_properties_08.png)

## 個性化錯誤頁 {#personalizing-the-error-page}

的 **[!UICONTROL Error page]** 頁籤，用於配置在報告顯示中出錯時將顯示的消息。

您可以定義文本並將其連結到特定標識符以管理報表本地化。 有關此內容的詳細資訊，請參閱 [添加頁眉和頁腳](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

![](assets/s_ncs_advuser_report_properties_11.png)
