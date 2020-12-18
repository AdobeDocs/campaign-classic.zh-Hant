---
solution: Campaign Classic
product: campaign
title: 進階功能
description: 進階功能
audience: reporting
content-type: reference
topic-tags: creating-new-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 4%

---


# 進階功能{#advanced-functionalities}

身為技術使用者，除了[一般屬性](../../reporting/using/properties-of-the-report.md)外，您還可運用進階功能來設定報表，例如：

* 建立複雜查詢以處理&#x200B;**Script**&#x200B;活動中的資料。 [進一步瞭解](#script-activity)

* 新增要在伺服器或用戶端上執行的外部指令碼。 [進一步瞭解](#external-script)

* 呼叫具有&#x200B;**Jump**&#x200B;活動的報表。 [進一步瞭解](#calling-up-another-report)

* 新增URL參數至報表，讓其更易於存取。 [進一步瞭解](#calling-up-another-report)

* 新增要用於報表內容的變數。 [進一步瞭解](#adding-variables)

## 使用指令碼{#adding-a-script}

### 參考外部指令碼{#external-script}

您可以參考在呼叫報表頁面時，在用戶端和／或伺服器端執行的JavaScript代碼。

操作步驟：

1. 編輯[報表屬性](../../reporting/using/properties-of-the-report.md)，然後按一下&#x200B;**[!UICONTROL Scripts]**。
1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選擇要引用的指令碼。
1. 然後選擇執行模式。

   如果添加了多個指令碼，請使用工具欄的箭頭來定義其執行順序。

   ![](assets/reporting_custom_js.png)

為了在用戶端上正常執行，參考的指令碼必須以JavaScript編寫，而且必須與一般瀏覽器相容。 如需詳細資訊，請參閱[本章節](../../web/using/web-forms-answers.md)。

### 添加指令碼活動{#script-activity}

當[設計報表](../../reporting/using/creating-a-new-report.md#modelizing-the-chart)時，請使用&#x200B;**[!UICONTROL Script]**&#x200B;活動來處理資料並輕鬆建立不啟用SQL語言的複雜查詢。 您可以直接在指令碼窗口中輸入查詢。

**[!UICONTROL Texts]**&#x200B;標籤可讓您定義文字字串。 然後可搭配下列語法使用：**$（識別碼）**。 有關使用文本的詳細資訊，請參閱[添加頁眉和頁腳](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

>[!CAUTION]
>
>我們不建議使用JavaScript程式碼來建立匯整。

若要建立報表的歷史記錄，請新增下列行至JavaScript查詢，以儲存已封存的資料：

```
if( ctx.@_historyId.toString().length == 0 )
```

否則，只會顯示目前的資料。

## 新增URL參數{#defining-additional-settings}

[報表屬性](../../reporting/using/properties-of-the-report.md)的&#x200B;**[!UICONTROL Parameters]**&#x200B;標籤可讓您定義報表的其他設定：這些設定會在呼叫期間傳遞至URL。

>[!CAUTION]
>
>出於安全考慮，這些參數必須非常小心地使用。

要建立新設定：

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕並輸入設定的名稱。

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. 如有必要，請指定是否必須設定。

1. 選擇要建立的設定類型：**[!UICONTROL Filter]**&#x200B;或&#x200B;**[!UICONTROL Variable]**。

   **[!UICONTROL Filter entities]**&#x200B;選項可讓您使用資料庫的欄位作為參數。

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   資料直接在實體級別恢復：**ctx/recipient/@account**。

   **[!UICONTROL Variable]**&#x200B;選項可讓您建立或選取變數，此變數將作為URL的參數傳遞，並可用於篩選器中。

**[!UICONTROL Response HTTP headers]**&#x200B;可讓您在使用iframe將報表的頁面加入HTML頁面時，防止點按劫持。 若要避免點按劫持，您可以選擇&#x200B;**[!UICONTROL X-Frame-options header]**&#x200B;行為：

* **[!UICONTROL None]**:報告將不提供 **[!UICONTROL X-Frame-options header]**。
* **[!UICONTROL Same as origin]**:依預設設定新報表和重新發佈的報表。主機名稱與報表的URL相同。
* **[!UICONTROL Deny]**:使用iframe時，報表無法包含在HTML頁面中。

![](assets/s_ncs_advuser_report_properties_09c.png)

## 新增變數{#adding-variables}

**[!UICONTROL Variables]**&#x200B;標籤包含報表中設定的變數清單。 這些變數會在報表的上下文中公開，並可用於計算。

按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以建立新變數。

要查看變數的定義，請選擇該變數並按一下&#x200B;**[!UICONTROL Detail...]**&#x200B;按鈕。

![](assets/s_ncs_advuser_report_properties_10.png)

## 使用案例：在報表中使用變數和參數

在以下視訊範例中，您將學習如何新增&quot;_type&quot;參數，以根據此屬性的值來建立報表的不同檢視。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## 呼叫另一個報告{#calling-up-another-report}

**Jump**&#x200B;活動就像沒有箭頭的轉場：它可讓您從一個活動移至另一個活動，或存取另一個報表。
