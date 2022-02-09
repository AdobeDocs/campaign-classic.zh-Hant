---
product: campaign
title: 報告的最佳實務
description: 市場活動報告最佳做法
feature: Reporting
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---

# 報告最佳做法{#best-practices-reporting}

![](../../assets/common.svg)

## 分析您的需求{#analyzing-needs}

使用報告工具取決於要處理的資料量、其複雜性以及要設定的報告類型。

要優化報告的建立、使用和持久性，您需要仔細瞭解您想要滿足的需求。 第一個分析將使您能夠確定要建立的報告類型和最佳建立模式。 要建立報告，請應用以下步驟：

1. 確定需要

   第一步是明確確定需求：您希望在報告中顯示的內容及其目標（監視、分析、資料導出等）。

   Adobe Campaign提供了廣泛的報告能力。 分析您確定最合適功能的需要非常重要。

   例如，您可以：

   * 瀏覽資料庫中的資料並定義測量。 瞭解更多資訊 [此部分](../../reporting/using/about-cubes.md)
   * 將指標添加到現有報告。 瞭解更多資訊 [此部分](../../reporting/using/about-reports-creation-in-campaign.md)
   * 查看資料庫中的資料。 瞭解更多資訊 [此部分](../../reporting/using/about-descriptive-analysis.md)
   * 新建交貨報表。 瞭解更多資訊 [此部分](../../reporting/using/about-reports-creation-in-campaign.md))
   * 從Adobe Campaign資料庫導出資料(通過工作流，請參閱 [此部分](../../workflow/using/about-workflows.md)
   * 建立透視表。 瞭解更多資訊 [此部分](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * 瀏覽聚合資料。 瞭解更多資訊 [此部分](../../reporting/using/about-cubes.md)
   * 使用嚮導分析資料。 瞭解更多資訊 [此部分](../../reporting/using/about-descriptive-analysis.md)
   * 分析大量資料。 瞭解更多資訊 [此部分](../../reporting/using/about-reports-creation-in-campaign.md)

1. 確定目標人口

   然後，您需要瞭解您要建立的報告將針對誰，瞭解將查看報告的公眾類型以及報告顯示模式(在瀏覽器中，在Adobe Campaign，針對特定對象，針對整個平台，等等)。

   您還可以為以下項目建立報告：

   * 所有Adobe Campaign運營商，
   * 僅有權參與營銷活動的運營商，
   * 一個用於臨時使用的運算子，
   * Web訪問中的所有運算子等。

   這些考慮因素還需要考慮與訪問權和安全有關的問題。

1. 定義內容

   然後，您需要瞭解要顯示的資料類型：交付指標、資料庫概要檔案報告等。

   您還需要瞭解此資料的性質（簡單，由計算、重要等所導致）、其位置(在Adobe Campaign，在第三方系統中)、其更新頻率以定義計算週期（每日、每週、即時）以及其體積。

   需要仔細檢查與資料卷和更新相關的問題，以避免報告顯示問題，特別是在時間方面。 因此，我們建議建立聚合，以預計報表外的一些資料。 包含跟蹤和傳遞日誌的表可以包含數百萬條記錄：這意味著需要通過工作流聚合資料以在報告中使用。

## 優化報表設計{#optimizing-report-creation}

### 資料卷 {#data-volume}

為了保證最佳效能，操作資料量不能太大。

即：

* 報告的計算時間不得超過5分鐘。

   同樣，在設計階段，如果報告計算超過60秒，則需要更改計算方法。

* 使用市場營銷分析模組時，報告資料不能超過1000萬行。

我們還建議在夜間計算匯總，並直接在報告中使用此匯總資料。 這些聚合必須通過專用資料管理工作流（SQL查詢）建立。

您還可以在夜間計算報告，並自動建立可隨時查看的歷史記錄，而不會使資料庫超負荷。

### 查詢 {#queries}

我們建議盡可能使用SQL查詢，並避免JavaScript後處理。 如有必要，請在工作流中使用指令碼活動並刪除用於計算的資料。 您還可以使用歸檔資料來加快處理時間。

在這種情況下，應使用以下語法：

```
if(string(ctx@_historyId)!==""))
```

使您能夠收集報告中顯示的資料的查詢不能過於複雜，尤其是如果應用於資料庫中的所有資料。 為了提高效能，在執行以下查詢之前過濾資料會非常有用：這意味著計算只涉及部分資料。

### 效能 {#performances}

以上建議使您能夠優化報表計算。

除此之外，Adobe Campaign還建議改進以下措施：

* 處理資料模型：索引欄位必須主要用於改進計算公式。

   要快速查找索引欄位，請查看Adobe Campaign介面中列的名稱：如果已對欄位編製索引，則排序箭頭的下划線為紅色。

   有關索引的詳細資訊，請參閱 [此部分](../../configuration/using/data-model-best-practices.md#indexes)。

* 確保報告可擴展：資料量可能會隨著時間的推移而顯著增加。

   同樣，在test階段期間處理的資料量可能與生產中的實際資料量不同。 這就是test階段很重要的原因。

   最後，需要知道資料清除延遲並在必要時加以調整，以便於進行資料操作。

   有關清理和資料保留的詳細資訊，請參閱 [此部分](../../configuration/using/data-model-best-practices.md#data-retention)。

### 導出報告 {#exporting-reports}

Recommendations的出口報告詳見 [此部分](../../reporting/using/actions-on-reports.md#exporting-a-report)。
