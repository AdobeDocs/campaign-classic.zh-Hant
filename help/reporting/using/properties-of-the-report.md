---
product: campaign
title: 報吿屬性
description: 深入瞭解報表屬性設定
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Reporting, Monitoring
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---

# 報吿屬性{#properties-of-the-report}



您可以完全個人化並設定報表，以符合您的需求。 若要這麼做，請編輯其屬性。 透過活動序列圖表上方的&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕存取報告屬性。

![](assets/s_ncs_advuser_report_properties_01.png)

一般屬性說明如下。 在&#x200B;**[!UICONTROL Parameters]**、**[!UICONTROL Variables]**&#x200B;和&#x200B;**[!UICONTROL Scripts]**&#x200B;索引標籤中設定的進階功能在此區段[&#128279;](../../reporting/using/advanced-functionalities.md)中說明。

## 一般屬性 {#overall-properties}

在報告屬性的&#x200B;**[!UICONTROL General]**&#x200B;標籤中，您可以編輯下列設定：

* 報告的標籤和內部名稱。 **[!UICONTROL Internal name]**&#x200B;已用於報表最終URL。 在報告建立後不應加以變更。

* 報告&#x200B;**資料夾**&#x200B;是在報告建立期間選取的。 最佳實務是為自訂報告建立專用資料夾，以便不會與[內建報告](../../reporting/using/about-campaign-built-in-reports.md)混合。

* 建立報告時已選取&#x200B;**儲存體**。 若要變更報告的資料表，請按一下&#x200B;**[!UICONTROL Document type]**&#x200B;欄位右側的&#x200B;**[!UICONTROL Select link]**&#x200B;圖示。

  ![](assets/s_ncs_advuser_report_properties_02.png)

* **存取控制**&#x200B;引數。 這些設定說明如下。

## 控制對報告的存取 {#report-accessibility}

報表可在Adobe Campaign主控台中或透過網頁瀏覽器存取。 在此情況下，可能必須設定報表存取控制，如下所示。

![](assets/s_ncs_advuser_report_properties_02b.png)

可能的選項包括：

* **[!UICONTROL Anonymous access]**：此選項可啟用報表的無限制存取。 但是，無法進行任何操作。

  「webapp」技術運運算元的許可權用於顯示報表元素。 在本節[&#128279;](../../platform/using/access-management-operators.md)瞭解更多。

* **[!UICONTROL Access control]**：此選項可讓Adobe Campaign運運算元在登入後存取它。
* **[!UICONTROL Specific account]**：此選項可讓您使用在&#x200B;**[!UICONTROL Operator]**&#x200B;欄位中選取之運運算元的許可權來執行報告。

## 翻譯您的報告 {#report-localization}

您可以設定要將報表翻譯成哪些語言。 若要這麼做，請按一下&#x200B;**[!UICONTROL Localization]**&#x200B;標籤。

![](assets/s_ncs_advuser_report_properties_06.png)

編輯語言是您使用的語言。 新增語言時，子索引標籤會出現在報告編輯頁面中。

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>如需Campaign網頁本地化的詳細資訊，請參閱[本節](../../web/using/translating-a-web-form.md)。

## 個人化HTML呈現 {#personalizing-html-rendering}

在&#x200B;**[!UICONTROL Rendering]**&#x200B;標籤中，您可以個人化頁面的資料顯示模式。 您可以選擇：

* 報表中的導覽型別：透過按鈕或連結。
* 報表元素的標籤預設位置。 可針對每個元素多載此位置。
* 用於產生報表頁面的範本或主題。

![](assets/s_ncs_advuser_report_properties_08.png)

## 個人化錯誤頁面 {#personalizing-the-error-page}

**[!UICONTROL Error page]**&#x200B;索引標籤可讓您設定在報表顯示中發生錯誤時將顯示的訊息。

您可以定義文字並將其連結至特定識別碼，以管理報表本地化。 如需詳細資訊，請參閱[新增頁首和頁尾](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

![](assets/s_ncs_advuser_report_properties_11.png)
