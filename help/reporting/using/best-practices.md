---
product: campaign
title: 報告的最佳實務
description: Campaign報表最佳實務
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 0%

---

# 報告最佳實務{#best-practices-reporting}

![](../../assets/common.svg)

## 分析需求{#analyzing-needs}

使用報告工具取決於要處理的資料量、其複雜性，以及要設定的報告類型。

若要最佳化報表的建立、使用和持久性，您必須詳細了解您想要滿足的需求。 第一個分析可讓您識別要建立的報表類型，以及最佳建立模式。 若要建立報表，請套用下列步驟：

1. 確定需要

   第一步是明確確定需求：您要在報表中顯示的項目及其目標（監控、分析、資料匯出等）。

   Adobe Campaign提供多種報告功能。 必須分析您確定最合適功能的需求。

   例如，您可以：

   * 探索資料庫中的資料並定義測量。 了解更多[，請參閱本節](../../reporting/using/about-cubes.md)
   * 新增指標至現有報表。 了解更多[，請參閱本節](../../reporting/using/about-reports-creation-in-campaign.md)
   * 在資料庫中查看資料。 了解更多[，請參閱本節](../../reporting/using/about-descriptive-analysis.md)
   * 建立新的傳送報表。 了解更多[，請參閱本節](../../reporting/using/about-reports-creation-in-campaign.md)),
   * 從Adobe Campaign資料庫匯出資料(透過工作流程，請參閱[此區段](../../workflow/using/about-workflows.md)
   * 建立樞紐分析表。 了解更多[，請參閱本節](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * 探索匯總的資料。 了解更多[，請參閱本節](../../reporting/using/about-cubes.md)
   * 使用精靈分析資料。 了解更多[，請參閱本節](../../reporting/using/about-descriptive-analysis.md)
   * 分析大量資料。 了解更多[，請參閱本節](../../reporting/using/about-reports-creation-in-campaign.md)

1. 識別目標人口

   接著，您需要找出您要建立的報表將鎖定目標對象、知道要檢視報表的公開類型，以及報表顯示模式(在瀏覽器、Adobe Campaign、特定物件、整個平台等中)。

   您也可以建立報表：

   * 所有Adobe Campaign運算子，
   * 只具有存取行銷活動之權限的運算子，
   * 一個用於臨時的運算子，
   * Web訪問等中的所有操作員

   這些考慮因素還需要考慮與訪問權限和安全性相關的問題。

1. 定義內容

   接著，您必須找出您要顯示的資料類型：傳遞指標、資料庫設定檔報告等。

   您也需要了解此資料的性質（簡單、因計算而產生、顯著等）、其位置(在Adobe Campaign中，位於協力廠商系統)、其更新頻率以定義計算週期（每日、每週、即時），以及其數量。

   需要仔細研究與資料卷和更新相關的問題，以避免報告顯示問題，特別是在時間方面。 因此，建議您建立匯總，以預先計算報表外的部分資料。 包含追蹤和傳送記錄的表格可包含數百萬筆記錄：這表示需要透過工作流程匯總資料，才能用於報表。

## 最佳化報表建立{#optimizing-report-creation}

### 資料卷 {#data-volume}

為保證最佳效能，操作資料量不得過大。

即：

* 報表的計算時間不得超過5分鐘。

   同樣，在設計階段，若資料量很小，如果報表計算超過60秒，則需要變更計算方法。

* 使用Marketing Analytics模組時，報表資料不得超過1,000萬行。

我們也建議您在晚上計算匯總，並直接在報表中使用此匯總資料。 這些匯總必須透過專用的資料管理工作流程（SQL查詢）建立。

您也可以在夜間計算報表，並自動建立歷史記錄，以便隨時查看，而不會超出資料庫負載。

### 查詢 {#queries}

建議您盡可能使用SQL查詢，並避免進行JavaScript後置處理。 如有必要，請在工作流程中使用指令碼活動並刪除用於計算的資料。 您也可以使用封存的資料來加速處理時間。

在此情況下，應使用下列語法：

```
if(string(ctx@_historyId)!==""))
```

可讓您收集報表中顯示資料的查詢不得太複雜，尤其是如果已套用至資料庫中的所有資料。 為了改善效能，在執行這些查詢之前先篩選資料會很有幫助：這表示計算只涉及部分資料。

### 效能 {#performances}

上述建議可讓您將報表計算最佳化。

除此之外，Adobe Campaign還建議進行下列改善：

* 使用您的資料模型：索引欄位必須主要用於改進計算公式。

   若要快速找到索引欄位，請查看Adobe Campaign介面中的欄名稱：如果欄位已編列索引，排序箭頭會以紅色加底線。

   有關索引的詳細資訊，請參閱[此部分](../../configuration/using/data-model-best-practices.md#indexes)。

* 確認報表可擴充：資料量可能會隨著時間而顯著增加。

   同樣，在測試階段期間操作的資料量可能與生產中的實際資料量不同。 這就是為什麼測試階段很重要。

   最後，需要知道資料清除延遲並在必要時調整以便於資料操作。

   如需清理和資料保留的詳細資訊，請參閱[此區段](../../configuration/using/data-model-best-practices.md#data-retention)。

### 匯出報表 {#exporting-reports}

匯出報表專用的Recommendations在[本區段](../../reporting/using/actions-on-reports.md#exporting-a-report)中詳細說明。
