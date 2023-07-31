---
product: campaign
title: 進階功能
description: 進一步瞭解使用報告時的進階功能
feature: Reporting, Monitoring
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 4%

---

# 進階功能{#advanced-functionalities}



除了作為技術使用者外， [一般屬性](../../reporting/using/properties-of-the-report.md)，您可以利用進階功能來設定報表，例如：

* 建立複雜查詢以在 **指令碼** 活動。 [了解更多](#script-activity)

* 新增要在伺服器或使用者端執行的外部指令碼。 [了解更多](#external-script)

* 呼叫具有下列專案的報表： **跳轉** 活動。 [了解更多](#calling-up-another-report)

* 新增URL引數至報表，讓使用者更容易存取。 [了解更多](#calling-up-another-report)

* 新增用於報告內容的變數。 [了解更多](#adding-variables)

## 使用指令碼 {#adding-a-script}

### 參考外部指令碼 {#external-script}

您可以參照呼叫報表頁面時將在使用者端和/或伺服器端執行的JavaScript程式碼。

操作步驟：

1. 編輯 [報告屬性](../../reporting/using/properties-of-the-report.md) 並按一下 **[!UICONTROL Scripts]**.
1. 按一下 **[!UICONTROL Add]** 並選取要參照的指令碼。
1. 然後選取執行模式。

   如果您新增多個指令碼，請使用工具列的箭頭來定義其執行順序。

   ![](assets/reporting_custom_js.png)

若要在使用者端正常執行，參照的指令碼必須以JavaScript撰寫，且必須和一般瀏覽器相容。 如需詳細資訊，請參閱[本章節](../../web/using/web-forms-answers.md)。

### 新增指令碼活動 {#script-activity}

時間 [設計您的報表](../../reporting/using/creating-a-new-report.md#modelizing-the-chart)，使用 **[!UICONTROL Script]** 處理資料並輕鬆建立無法啟用SQL語言的複雜查詢的活動。 您可以在指令碼視窗中直接輸入查詢。

此 **[!UICONTROL Texts]** 定位字元可讓您定義文字字串。 然後可搭配下列語法使用： **$（識別碼）**. 有關使用文字的詳細資訊，請參閱 [新增頁首和頁尾](../../reporting/using/element-layout.md#adding-a-header-and-a-footer).

>[!CAUTION]
>
>我們不建議使用JavaScript程式碼來建立彙總。

若要建立報表歷史記錄，請將下列行新增至JavaScript查詢，以儲存已封存的資料：

```
if( ctx.@_historyId.toString().length == 0 )
```

否則，只會顯示目前的資料。

## 新增URL引數 {#defining-additional-settings}

此 **[!UICONTROL Parameters]** 的標籤 [報告屬性](../../reporting/using/properties-of-the-report.md) 可讓您定義報表的其他設定：這些設定將在呼叫期間傳遞至URL。

>[!CAUTION]
>
>基於安全考量，使用這些引數時必須格外小心。

若要建立新設定：

1. 按一下 **[!UICONTROL Add]** 按鈕並輸入設定的名稱。

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. 如有必要，請指定此設定是否為必要。

1. 選取您要建立的設定型別： **[!UICONTROL Filter]** 或 **[!UICONTROL Variable]**.

   此 **[!UICONTROL Filter entities]** 選項可讓您將資料庫的欄位用作引數。

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   資料會直接在實體層級復原： **ctx/recipient/@account**.

   此 **[!UICONTROL Variable]** 選項可讓您建立或選取變數，該變數將作為URL的引數傳遞，並可在篩選中使用。

此 **[!UICONTROL Response HTTP headers]** 可讓您在使用iframe將報表頁面納入HTML頁面時，防止點選劫持。 若要避免點選劫持，您可以選擇 **[!UICONTROL X-Frame-options header]** 行為：

* **[!UICONTROL None]**：報告將沒有 **[!UICONTROL X-Frame-options header]**.
* **[!UICONTROL Same as origin]**：新報表和重新發佈報表的預設值。 主機名稱將與報表的URL相同。
* **[!UICONTROL Deny]**：該報告不可包含在使用iframe的HTML頁面中。

![](assets/s_ncs_advuser_report_properties_09c.png)

## 新增變數 {#adding-variables}

此 **[!UICONTROL Variables]** 索引標籤包含報表中設定的變數清單。 這些變數會顯示在報表內容中，且可用於計算。

按一下 **[!UICONTROL Add]** 按鈕以建立新變數。

若要檢視變數的定義，請選取變數並按一下 **[!UICONTROL Detail...]** 按鈕。

![](assets/s_ncs_advuser_report_properties_10.png)

## 使用案例：在報表中使用變數和引數

在以下影片範例中，您將瞭解如何新增「_type」引數，以根據此屬性的值建立不同的報告檢視。

<!--
![](assets/do-not-localize/how-to-video.png) [Discover this feature in video](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&ref=helpx.adobe.com)-->


## 呼叫其他報表 {#calling-up-another-report}

A **跳轉** 活動就像一個沒有箭頭的轉變：它可讓您從一個活動移至另一個活動或存取另一個報表。
