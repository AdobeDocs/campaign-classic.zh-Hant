---
solution: Campaign Classic
product: campaign
title: 報表屬性
description: 進一步瞭解報表屬性設定
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 2%

---


# 報表屬性{#properties-of-the-report}

您可以完全個人化並設定您的報表，以符合您的需求。 若要這麼做，請編輯其屬性。 報表屬性可透過活動順序圖表上方的&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕存取。

![](assets/s_ncs_advuser_report_properties_01.png)

一般屬性說明如下。 在&#x200B;**[!UICONTROL Parameters]**、**[!UICONTROL Variables]**&#x200B;和&#x200B;**[!UICONTROL Scripts]**&#x200B;標籤中配置的高級功能在本節[中有說明。](../../reporting/using/advanced-functionalities.md)

## 一般屬性{#overall-properties}

在報表屬性的&#x200B;**[!UICONTROL General]**&#x200B;標籤中，您可以編輯下列設定：

* 報表的標籤和內部名稱。 **[!UICONTROL Internal name]**&#x200B;用於報告最終URL。 在建立報表後不應變更。

* 在建立報告時，會選擇報告&#x200B;**資料夾**。 最佳實務是為自訂報表建立專屬的資料夾，以避免與[內建報表](../../reporting/using/about-campaign-built-in-reports.md)混用。

* 建立報告時選擇&#x200B;**儲存**。 若要變更報表的資料表格，請按一下&#x200B;**[!UICONTROL Document type]**&#x200B;欄位右側的&#x200B;**[!UICONTROL Select link]**&#x200B;圖示。

   ![](assets/s_ncs_advuser_report_properties_02.png)

* **訪問控制**&#x200B;參數。 以下說明這些設定。

## 控制對報告{#report-accessibility}的訪問

報表可在Adobe Campaign主控台或網頁瀏覽器中存取。 在此情況下，您必須設定報表存取控制，如下所示。

![](assets/s_ncs_advuser_report_properties_02b.png)

可能的選項包括：

* **[!UICONTROL Anonymous access]**:此選項可讓您不受限制地存取報表。但是，不可能操縱。

   「webapp」技術營運商的權限可用來顯示報表元素。 瞭解本節](../../platform/using/access-management-operators.md)的更多資訊。[

* **[!UICONTROL Access control]**:此選項可讓Adobe Campaign運算子在登入後加以存取。
* **[!UICONTROL Specific account]**:此選項可讓您以在欄位中選取之運算子的權限執行 **[!UICONTROL Operator]** 報表。

## 管理報告本地化{#managing-report-localization}

您可以設定要將報表翻譯為的語言。 要執行此操作，請按一下&#x200B;**[!UICONTROL Localization]**&#x200B;頁籤。

![](assets/s_ncs_advuser_report_properties_06.png)

編輯語言是您所用的語言。 新增語言時，子標籤會出現在報表編輯頁面中。

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>有關Campaign中網頁本地化的詳細資訊，請參閱[本節](../../web/using/translating-a-web-form.md)。

## 個人化HTML演算{#personalizing-html-rendering}

在&#x200B;**[!UICONTROL Rendering]**&#x200B;標籤中，您可以個人化頁面的資料顯示模式。 您可以選擇：

* 圖表轉換引擎：依預設，演算引擎為HTML 5。
* 報表中的導覽類型：按鈕或連結。
* 報表元素的標籤預設位置。 此位置可以為每個元素過載。
* 用於產生報表頁面的範本或主題。

![](assets/s_ncs_advuser_report_properties_08.png)

## 個人化錯誤頁面{#personalizing-the-error-page}

**[!UICONTROL Error page]**&#x200B;標籤可讓您設定在報告顯示中發生錯誤時會顯示的訊息。

您可以定義文字，並將它們連結至特定識別碼，以管理報表本地化。 有關詳細資訊，請參閱[添加頁眉和頁腳](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

![](assets/s_ncs_advuser_report_properties_11.png)
