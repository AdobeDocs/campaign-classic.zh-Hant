---
product: campaign
title: 進階功能
description: 進階功能
audience: reporting
content-type: reference
topic-tags: creating-new-reports
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 5%

---

# 進階功能{#advanced-functionalities}

身為技術使用者，除了[一般屬性](../../reporting/using/properties-of-the-report.md)，您還可以運用進階功能來設定報表，例如：

* 建立複雜查詢以處理&#x200B;**Script**&#x200B;活動中的資料。 [瞭解更多](#script-activity)

* 新增要在伺服器端或用戶端上執行的外部指令碼。 [瞭解更多](#external-script)

* 呼叫具有&#x200B;**Jump**&#x200B;活動的報表。 [瞭解更多](#calling-up-another-report)

* 新增URL參數至報表，使其更方便存取。 [瞭解更多](#calling-up-another-report)

* 新增要在報表內容中使用的變數。 [瞭解更多](#adding-variables)

## 使用指令碼{#adding-a-script}

### 參考外部指令碼{#external-script}

您可以參考在呼叫報表頁面時，在用戶端和/或伺服器端執行的JavaScript程式碼。

操作步驟：

1. 編輯[報表屬性](../../reporting/using/properties-of-the-report.md) ，然後按一下&#x200B;**[!UICONTROL Scripts]**。
1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選取要參考的指令碼。
1. 然後選取執行模式。

   如果您新增數個指令碼，請使用工具列的箭頭來定義其執行順序。

   ![](assets/reporting_custom_js.png)

為了在用戶端正常執行，參考的指令碼必須以JavaScript寫入，且必須與一般瀏覽器相容。 如需詳細資訊，請參閱[本章節](../../web/using/web-forms-answers.md)。

### 新增指令碼活動{#script-activity}

當[設計您的報表](../../reporting/using/creating-a-new-report.md#modelizing-the-chart)時，請使用&#x200B;**[!UICONTROL Script]**&#x200B;活動來處理資料並輕鬆建立不啟用SQL語言的複雜查詢。 您可以直接在指令碼窗口中輸入查詢。

**[!UICONTROL Texts]**&#x200B;索引標籤可讓您定義文字字串。 然後，可搭配下列語法使用：**$（標識符）**。 有關使用文本的詳細資訊，請參閱[添加頁首和頁尾](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

>[!CAUTION]
>
>我們不建議使用JavaScript程式碼來建立匯總。

若要建立報表歷史記錄，請新增下列行至JavaScript查詢，以儲存已封存的資料：

```
if( ctx.@_historyId.toString().length == 0 )
```

否則，只會顯示目前的資料。

## 新增URL參數{#defining-additional-settings}

[報表屬性](../../reporting/using/properties-of-the-report.md)的&#x200B;**[!UICONTROL Parameters]**&#x200B;標籤可讓您定義報表的其他設定：這些設定會在呼叫期間傳遞至URL。

>[!CAUTION]
>
>出於安全原因，這些參數必須非常小心地使用。

要建立新設定：

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕並輸入設定的名稱。

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. 如有必要，請指定設定是否為強制設定。

1. 選取要建立的設定類型：**[!UICONTROL Filter]**&#x200B;或&#x200B;**[!UICONTROL Variable]**。

   **[!UICONTROL Filter entities]**&#x200B;選項可讓您使用資料庫的欄位作為參數。

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   直接在實體級別恢復資料：**ctx/recipient/@account**。

   **[!UICONTROL Variable]**&#x200B;選項可讓您建立或選取變數，該變數將作為URL的參數傳遞，並可用於篩選器。

**[!UICONTROL Response HTTP headers]**&#x200B;可讓您在使用iframe將報表的頁面納入HTML頁面時，防止點按劫持。 若要避免點按頂升，您可以選擇&#x200B;**[!UICONTROL X-Frame-options header]**&#x200B;行為：

* **[!UICONTROL None]**:報告沒有 **[!UICONTROL X-Frame-options header]**。
* **[!UICONTROL Same as origin]**:為新報表和重新發佈的報表預設設定。主機名稱與報表的URL相同。
* **[!UICONTROL Deny]**:報表無法包含在使用iframe的HTML頁面中。

![](assets/s_ncs_advuser_report_properties_09c.png)

## 新增變數{#adding-variables}

**[!UICONTROL Variables]**&#x200B;標籤包含報表中設定的變數清單。 這些變數會在報表內容中公開，並可用於計算。

按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以建立新變數。

若要檢視變數的定義，請選取變數，然後按一下&#x200B;**[!UICONTROL Detail...]**&#x200B;按鈕。

![](assets/s_ncs_advuser_report_properties_10.png)

## 使用案例：在報表中使用變數和參數

在以下影片範例中，您將了解如何新增「_type」參數，以根據此屬性的值，建立不同的報表檢視。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## 呼叫另一個報表{#calling-up-another-report}

**Jump**&#x200B;活動就像沒有箭頭的轉變：可讓您從一個活動移至另一個活動或存取其他報表。
