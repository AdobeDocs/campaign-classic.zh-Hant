---
product: campaign
title: 報吿屬性
description: 深入瞭解報表屬性設定
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Reporting, Monitoring
exl-id: dfa9d329-1086-4f6d-9d03-df159cad5495
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 3%

---

# 報吿屬性{#properties-of-the-report}



您可以完全個人化並設定報表，以符合您的需求。 若要這麼做，請編輯其屬性。 報表屬性可透過以下方式存取： **[!UICONTROL Properties]** 活動序號圖表上方的按鈕。

![](assets/s_ncs_advuser_report_properties_01.png)

一般屬性說明如下。 在中設定的進階功能 **[!UICONTROL Parameters]**， **[!UICONTROL Variables]** 和 **[!UICONTROL Scripts]** 標籤已說明 [在本節中](../../reporting/using/advanced-functionalities.md).

## 一般屬性 {#overall-properties}

在 **[!UICONTROL General]** 標籤中，您可以編輯下列設定：

* 報告的標籤和內部名稱。 此 **[!UICONTROL Internal name]** 用於報表最終URL。 在報告建立後不應加以變更。

* 報告 **資料夾** 在建立報告期間選取。 最佳實務是為自訂報表建立專用資料夾，以免與混合 [內建報告](../../reporting/using/about-campaign-built-in-reports.md).

* 此 **儲存** 在建立報告時選取「 」。 若要變更報表的資料表，請按一下 **[!UICONTROL Select link]** 圖示右側 **[!UICONTROL Document type]** 欄位。

  ![](assets/s_ncs_advuser_report_properties_02.png)

* 此 **存取控制** 引數。 這些設定說明如下。

## 控制對報告的存取 {#report-accessibility}

報表可在Adobe Campaign主控台中或透過網頁瀏覽器存取。 在此情況下，可能必須設定報表存取控制，如下所示。

![](assets/s_ncs_advuser_report_properties_02b.png)

可能的選項包括：

* **[!UICONTROL Anonymous access]**：此選項可讓您不受限制地存取報表。 但是，無法進行任何操作。

  「webapp」技術運運算元的許可權用於顯示報表元素。 瞭解更多 [在本節中](../../platform/using/access-management-operators.md).

* **[!UICONTROL Access control]**：此選項可讓Adobe Campaign運運算元在登入後存取它。
* **[!UICONTROL Specific account]**：此選項可讓您使用在中選取之運運算元的許可權執行報表 **[!UICONTROL Operator]** 欄位。

## 翻譯您的報告 {#report-localization}

您可以設定要將報表翻譯成哪些語言。 若要這麼做，請按一下 **[!UICONTROL Localization]** 標籤。

![](assets/s_ncs_advuser_report_properties_06.png)

編輯語言是您使用的語言。 新增語言時，子索引標籤會出現在報告編輯頁面中。

![](assets/s_ncs_advuser_report_properties_05a.png)

>[!NOTE]
>
>如需Campaign網頁本地化的詳細資訊，請參閱 [本節](../../web/using/translating-a-web-form.md).

## 個人化HTML呈現 {#personalizing-html-rendering}

在 **[!UICONTROL Rendering]** 標籤，您可以個人化頁面的資料顯示模式。 您可以選擇：

* 報表中的導覽型別：透過按鈕或連結。
* 報表元素的標籤預設位置。 可針對每個元素多載此位置。
* 用於產生報表頁面的範本或主題。

![](assets/s_ncs_advuser_report_properties_08.png)

## 個人化錯誤頁面 {#personalizing-the-error-page}

此 **[!UICONTROL Error page]** 索引標籤可讓您設定在報表顯示錯誤時顯示的訊息。

您可以定義文字並將其連結至特定識別碼，以管理報表本地化。 有關詳細資訊，請參閱 [新增頁首和頁尾](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

![](assets/s_ncs_advuser_report_properties_11.png)
