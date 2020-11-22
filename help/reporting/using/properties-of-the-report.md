---
solution: Campaign Classic
product: campaign
title: 報表屬性
description: 進一步瞭解報表屬性設定
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 2%

---


# 報表屬性{#properties-of-the-report}

您可以完全個人化並設定您的報表，以符合您的需求。 若要這麼做，請編輯其屬性。 報表屬性可透過活動順序 **[!UICONTROL Properties]** 圖表上方的按鈕存取。

![](assets/s_ncs_advuser_report_properties_01.png)

一般屬性說明如下。 本節將介紹在中配 **[!UICONTROL Parameters]**&#x200B;置的 **[!UICONTROL Variables]** 高 **[!UICONTROL Scripts]** 級功能，以 [及頁籤](../../reporting/using/advanced-functionalities.md)。

## 一般屬性 {#overall-properties}

在報表 **[!UICONTROL General]** 屬性的標籤中，您可以編輯下列設定：

* 報表的標籤和內部名稱。 報 **[!UICONTROL Internal name]** 表最終URL中使用。 在建立報表後不應變更。

* 在建立報 **表時** ，會選取報表資料夾。 最佳實務是為自訂報表建立專屬的資料夾，以避免與內建 [報表混用](../../reporting/using/about-campaign-built-in-reports.md)。

* 建立 **報告時** ，將選擇「儲存」。 若要變更報表的資料表格，請按一 **[!UICONTROL Select link]** 下欄位右側的圖 **[!UICONTROL Document type]** 示。

   ![](assets/s_ncs_advuser_report_properties_02.png)

* 存取 **控制參數** 。 以下說明這些設定。

## Controlling access to the report {#report-accessibility}

報表可在Adobe Campaign主控台或網頁瀏覽器中存取。 在此情況下，您必須設定報表存取控制，如下所示。

![](assets/s_ncs_advuser_report_properties_02b.png)

可能的選項包括：

* **[!UICONTROL Anonymous access]**:此選項可讓您不受限制地存取報表。 但是，不可能操縱。

   「webapp」技術營運商的權利可用來顯示報表元素。 在本節 [中進一步瞭解](../../platform/using/access-management.md#default-operators)。

* **[!UICONTROL Access control]**:此選項可讓Adobe Campaign營運商在登入後加以存取。
* **[!UICONTROL Specific account]**:此選項可讓您在欄位中選取運算子的權限下執行報 **[!UICONTROL Operator]** 表。

## 管理報告本地化 {#managing-report-localization}

您可以設定要將報表翻譯為的語言。 若要這麼做，請按一下標 **[!UICONTROL Localization]** 簽。

![](assets/s_ncs_advuser_report_properties_06.png)

編輯語言是您所用的語言。 新增語言時，子標籤會出現在報表編輯頁面中。

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>如需Campaign中網頁本地化的詳細資訊，請參 [閱本節](../../web/using/translating-a-web-form.md)。

## 個人化HTML演算 {#personalizing-html-rendering}

在標籤 **[!UICONTROL Rendering]** 中，您可以個人化頁面的資料顯示模式。 您可以選擇：

* 圖表轉換引擎：Adobe Campaign提供兩種不同的模式來產生圖表轉換。 依預設，演算引擎為HTML 5。 如有必要，您可以選取Flash演算。
* 報表中的導覽類型：按鈕或連結。
* 報表元素的標籤預設位置。 此位置可以為每個元素過載。
* 用於產生報表頁面的範本或主題。

![](assets/s_ncs_advuser_report_properties_08.png)

## 個人化錯誤頁面 {#personalizing-the-error-page}

此標 **[!UICONTROL Error page]** 簽可讓您設定在報表顯示中發生錯誤時會顯示的訊息。

您可以定義文字，並將它們連結至特定識別碼，以管理報表本地化。 有關詳細資訊，請參 [閱添加頁眉和頁腳](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

![](assets/s_ncs_advuser_report_properties_11.png)
