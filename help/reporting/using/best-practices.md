---
product: campaign
title: 報告的最佳實務
description: Campaign報告最佳實務
badge: label="v7" type="資訊性" tooltip="僅適用於Campaign Classicv7"
feature: Reporting
exl-id: 0c7f00f3-b16d-41c5-a7b1-f5a59201bf8c
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 0%

---

# 報告最佳實務{#best-practices-reporting}



## 分析您的需求{#analyzing-needs}

使用報告工具取決於要處理的資料量、其複雜性以及要設定的報告型別。

若要最佳化報告的建立、使用及耐久性，您必須仔細檢視您想要滿足的需求。 第一個分析可讓您識別要建立的報告型別和最佳建立模式。 若要建立報表，請套用下列步驟：

1. 確定需求

   第一步是明確識別需求：您要在報告中顯示的內容及其目標（監控、分析、資料匯出等）。

   Adobe Campaign提供廣泛的報告容量。 請務必分析您的需求，以找出最適合的功能。

   例如，您可以：

   * 探索資料庫中的資料並定義測量。 瞭解更多 [在本節中](../../reporting/using/ac-cubes.md)
   * 新增指標至現有報表。 瞭解更多 [在本節中](../../reporting/using/about-reports-creation-in-campaign.md)
   * 檢視資料庫中的資料。 瞭解更多 [在本節中](../../reporting/using/about-descriptive-analysis.md)
   * 建立新的傳遞報告。 瞭解更多 [在本節中](../../reporting/using/about-reports-creation-in-campaign.md))，
   * 從Adobe Campaign資料庫匯出資料(透過工作流程，請參閱 [本節](../../workflow/using/about-workflows.md)
   * 建立樞紐分析表。 瞭解更多 [在本節中](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)
   * 探索彙總的資料。 瞭解更多 [在本節中](../../reporting/using/ac-cubes.md)
   * 使用精靈來分析資料。 瞭解更多 [在本節中](../../reporting/using/about-descriptive-analysis.md)
   * 分析大量資料。 瞭解更多 [在本節中](../../reporting/using/about-reports-creation-in-campaign.md)

1. 識別目標母體

   接著，您需要找出要建立報告的目標、瞭解將檢視報告的公眾型別以及報告顯示模式(在瀏覽器中、在Adobe Campaign中、針對特定物件、針對整個平台等)。

   您也可以為以下專案建立報表：

   * 所有Adobe Campaign運運算元、
   * 僅有權存取行銷活動的操作者，
   * 暫時使用的單一運運算元，
   * Web存取中的所有運運算元等

   這些考量事項也需要考量存取許可權和安全性相關的問題。

1. 定義內容

   之後，您需要找出要顯示的資料型別：傳遞指標、資料庫設定檔的報告等。

   您也需要瞭解此資料的性質（簡單、由計算、重大等造成）、其位置(在Adobe Campaign、在協力廠商系統中)、其定義計算週期性的更新頻率（每日、每週、即時），以及其數量。

   需要仔細審視與資料量及更新連結的問題，以避免報告顯示問題，尤其是時間方面的問題。 因此，我們建議建立彙總，以在報表外部預先計算某些資料。 包含追蹤和傳送記錄的表格可包含數百萬筆記錄：這表示資料需要透過工作流程加以彙總，才能用於報告中。

## 最佳化報表設計{#optimizing-report-creation}

### 資料量 {#data-volume}

為確保最佳效能，操作資料的量不能太大。

即：

* 報表的計算時間不得超過5分鐘。

   同樣地，在設計階段中，由於資料量較少，如果報表計算超過60秒，則需要變更計算方法。

* 使用Marketing Analytics模組時，報表資料不可超過1,000萬行。

我們也建議在夜間計算彙總，並直接在報告中使用此彙總資料。 這些彙總必須透過專用的資料管理工作流程（SQL查詢）建立。

您也可以在夜間計算報表，並自動建立歷史記錄，以便隨時檢視，而不會造成資料庫超載。

### 查詢 {#queries}

建議您儘可能使用SQL查詢，並避免JavaScript後續處理。 如有必要，請在工作流程中使用指令碼活動，並刪除用於計算的資料。 您也可以使用封存的資料來加快處理時間。

在此情況下，應使用下列語法：

```
if(string(ctx@_historyId)!==""))
```

可讓您收集報表中顯示資料的查詢不得過於複雜，尤其是套用至資料庫中所有資料時。 若要改善效能，在執行這些查詢之前篩選資料會很有用：這表示計算只會涉及部分資料。

### 效能 {#performances}

上述建議可讓您最佳化報表計算。

除此之外，Adobe Campaign還建議進行下列改善：

* 使用您的資料模型：索引欄位必須主要用於改進計算公式。

   若要快速尋找已編制索引的欄位，請在Adobe Campaign介面中檢視該欄的名稱：如果該欄位已編制索引，則排序箭頭會以紅色加底線。

   有關索引的詳細資訊，請參閱 [本節](../../configuration/using/data-model-best-practices.md#indexes).

* 確保報表可擴充：資料量可能會隨著時間大幅增加。

   同樣地，在測試階段處理的資料量可能與生產時的實際資料量不同。 這就是為什麼測試階段很重要。

   最後，需要知道資料清除延遲，並在必要時進行調整，以輕鬆操控資料。

   有關清理和資料保留的詳細資訊，請參閱 [本節](../../configuration/using/data-model-best-practices.md#data-retention).

### 匯出您的報告 {#exporting-reports}

有關匯出報告的特定Recommendations的詳情，請參閱 [本節](../../reporting/using/actions-on-reports.md#exporting-a-report).
