---
product: campaign
title: 報吿屬性
description: 進一步了解報表屬性設定
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 2%

---

# 報吿屬性{#properties-of-the-report}

您可以完全個人化並設定報表以符合您的需求。 要執行此操作，請編輯其屬性。 報表屬性可透過活動順序圖上方的&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕存取。

![](assets/s_ncs_advuser_report_properties_01.png)

以下說明一般屬性。 在&#x200B;**[!UICONTROL Parameters]**、**[!UICONTROL Variables]**&#x200B;和&#x200B;**[!UICONTROL Scripts]**&#x200B;標籤中配置的高級功能在本部分](../../reporting/using/advanced-functionalities.md)中有描述。[

## 一般屬性{#overall-properties}

在報表屬性的&#x200B;**[!UICONTROL General]**&#x200B;標籤中，您可以編輯下列設定：

* 報表的標籤和內部名稱。 **[!UICONTROL Internal name]**&#x200B;用於報表最終URL。 報表建立後不應變更。

* 報表建立期間會選取報表&#x200B;**資料夾**。 最佳作法是為自訂報表建立專用資料夾，使其不與[內建報表](../../reporting/using/about-campaign-built-in-reports.md)混合。

* 建立報表時會選取&#x200B;**Storage**。 若要變更報表的資料表格，請按一下&#x200B;**[!UICONTROL Document type]**&#x200B;欄位右側的&#x200B;**[!UICONTROL Select link]**&#x200B;圖示。

   ![](assets/s_ncs_advuser_report_properties_02.png)

* **訪問控制**&#x200B;參數。 以下說明這些設定。

## 控制對報告{#report-accessibility}的訪問

報表可在Adobe Campaign控制台或網頁瀏覽器中存取。 在此情況下，可能需要設定報表存取控制，如下所示。

![](assets/s_ncs_advuser_report_properties_02b.png)

可能的選項包括：

* **[!UICONTROL Anonymous access]**:此選項可允許不受限制地訪問報告。但是，不可能操縱。

   「webapp」技術運算子的權限用於顯示報表元素。 了解更多[，請參閱本節](../../platform/using/access-management-operators.md)。

* **[!UICONTROL Access control]**:此選項可讓Adobe Campaign運算子在登入後加以存取。
* **[!UICONTROL Specific account]**:此選項可讓您以在欄位中選取運算子的權限執行報 **[!UICONTROL Operator]** 表。

## 管理報表本地化{#managing-report-localization}

您可以設定要將報表翻譯成的語言。 要執行此操作，請按一下&#x200B;**[!UICONTROL Localization]**&#x200B;標籤。

![](assets/s_ncs_advuser_report_properties_06.png)

編輯語言是您所撰寫的語言。 新增語言時，子索引標籤會出現在報表編輯頁面中。

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>如需Campaign中網頁本地化的詳細資訊，請參閱[此區段](../../web/using/translating-a-web-form.md)。

## 個人化HTML呈現{#personalizing-html-rendering}

在&#x200B;**[!UICONTROL Rendering]**&#x200B;標籤中，您可以個人化頁面的資料顯示模式。 您可以選擇：

* 圖表呈現引擎：預設情況下，呈現引擎為HTML 5。
* 報表中的導覽類型：透過按鈕或連結。
* 報表元素的標籤預設位置。 每個元素的此位置都可能超載。
* 用於產生報表頁面的範本或主題。

![](assets/s_ncs_advuser_report_properties_08.png)

## 個人化錯誤頁面{#personalizing-the-error-page}

**[!UICONTROL Error page]**&#x200B;標籤可讓您設定在報表顯示中發生錯誤時將顯示的訊息。

您可以定義文字並將文字連結至特定識別碼，以管理報表本地化。 有關詳細資訊，請參閱[新增頁首和頁尾](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

![](assets/s_ncs_advuser_report_properties_11.png)
