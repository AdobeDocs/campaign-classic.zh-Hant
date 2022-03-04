---
product: campaign
title: 進階功能
description: 瞭解有關使用報告時高級功能的更多資訊
feature: Reporting
exl-id: 8b51d0fc-1692-41cd-9aa8-3bb8f4ee454e
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 4%

---

# 進階功能{#advanced-functionalities}

![](../../assets/common.svg)

作為技術用戶，除 [一般屬性](../../reporting/using/properties-of-the-report.md)，您可以利用高級功能來配置報告，例如：

* 建立複雜查詢以處理 **指令碼** 的子菜單。 [了解更多](#script-activity)

* 添加要在伺服器或客戶端上執行的外部指令碼。 [了解更多](#external-script)

* 使用 **跳** 的子菜單。 [了解更多](#calling-up-another-report)

* 將URL參數添加到報表，使其更易訪問。 [了解更多](#calling-up-another-report)

* 添加要在報表上下文中使用的變數。 [了解更多](#adding-variables)

## 使用指令碼 {#adding-a-script}

### 引用外部指令碼 {#external-script}

您可以引用在調用報告頁時將在客戶端和/或伺服器端執行的JavaScript代碼。

操作步驟：

1. 編輯 [報表屬性](../../reporting/using/properties-of-the-report.md) 並按一下 **[!UICONTROL Scripts]**。
1. 按一下 **[!UICONTROL Add]** 並選擇要引用的指令碼。
1. 然後選擇執行模式。

   如果添加了多個指令碼，請使用工具欄的箭頭來定義其執行順序。

   ![](assets/reporting_custom_js.png)

要在客戶端上正常執行，引用的指令碼必須用JavaScript編寫，並且需要與常用瀏覽器相容。 如需詳細資訊，請參閱[本章節](../../web/using/web-forms-answers.md)。

### 添加指令碼活動 {#script-activity}

當 [設計報告](../../reporting/using/creating-a-new-report.md#modelizing-the-chart)，使用 **[!UICONTROL Script]** 活動：處理資料並輕鬆建立不啟用SQL語言的複雜查詢。 您可以直接在指令碼窗口中輸入查詢。

的 **[!UICONTROL Texts]** 頁籤中，您可以定義文本字串。 然後，可以使用以下語法使用它們： **$（標識符）**。 有關使用文本的詳細資訊，請參閱 [添加頁眉和頁腳](../../reporting/using/element-layout.md#adding-a-header-and-a-footer)。

>[!CAUTION]
>
>我們不建議使用JavaScript代碼建立聚合。

要建立報表的歷史記錄，請將以下行添加到JavaScript查詢中以保存存檔的資料：

```
if( ctx.@_historyId.toString().length == 0 )
```

否則，將只顯示當前資料。

## 添加URL參數 {#defining-additional-settings}

的 **[!UICONTROL Parameters]** 頁籤 [報表屬性](../../reporting/using/properties-of-the-report.md) 允許您為報告定義其他設定：這些設定將在調用期間傳遞到URL。

>[!CAUTION]
>
>出於安全原因，這些參數必須非常謹慎地使用。

建立新設定：

1. 按一下 **[!UICONTROL Add]** 按鈕並輸入設定的名稱。

   ![](assets/s_ncs_advuser_report_properties_09a.png)

1. 如有必要，請指定設定是否為強制設定。

1. 選擇要建立的設定類型： **[!UICONTROL Filter]** 或 **[!UICONTROL Variable]**。

   的 **[!UICONTROL Filter entities]** 選項，可將資料庫的欄位用作參數。

   ![](assets/s_ncs_advuser_report_properties_09b.png)

   資料直接在實體級別恢復： **ctx/recipient/@account**。

   的 **[!UICONTROL Variable]** 的子菜單。

的 **[!UICONTROL Response HTTP headers]** 允許您在使用iframe將報表的頁面包含在HTML頁面中時防止點擊。 為避免點擊劫持，您可以選擇 **[!UICONTROL X-Frame-options header]** 行為：

* **[!UICONTROL None]**:報告沒有 **[!UICONTROL X-Frame-options header]**。
* **[!UICONTROL Same as origin]**:預設為新報告和重新發佈的報告設定。 主機名與報告的URL相同。
* **[!UICONTROL Deny]**:無法使用iframe將報表包含在HTML頁中。

![](assets/s_ncs_advuser_report_properties_09c.png)

## 添加變數 {#adding-variables}

的 **[!UICONTROL Variables]** 頁籤包含在報告中配置的變數清單。 這些變數在報告的上下文中顯示，可用於計算。

按一下 **[!UICONTROL Add]** 按鈕

要查看變數的定義，請選擇變數，然後按一下 **[!UICONTROL Detail...]** 按鈕

![](assets/s_ncs_advuser_report_properties_10.png)

## 用例：在報告中使用變數和參數

在下面的視頻示例中，您將學習如何添加「_type」參數，以基於此屬性的值建立報表的不同視圖。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](https://helpx.adobe.com/campaign/classic/how-to/add-url-parameter-in-acv6.html?playlist=/ccx/v1/collection/product/campaign/classic/segment/business-practitioners/explevel/intermediate/applaunch/how-to-4/collection.ccx.js&amp;ref=helpx.adobe.com)


## 調用另一個報告 {#calling-up-another-report}

A **跳** 活動就像沒有箭頭的過渡：它允許您從一個活動轉到另一個活動或訪問另一個報告。
