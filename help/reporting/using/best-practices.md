---
title: 報告的最佳實務
seo-title: 報告的最佳實務
description: 報告的最佳實務
seo-description: null
page-status-flag: never-activated
uuid: 09de6a17-b3a7-4543-b672-b0a21653aa75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: reporting-in-adobe-campaign
discoiquuid: 904961e0-7dff-4350-8d5d-e4bdd368b3ff
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0c41cf2f35495a1514642e47f0b7146d8dd50946

---


# 報告的最佳實務{#best-practices-reporting}

## 分析需求{#analyzing-needs}

使用報告工具取決於要操作的資料量、其複雜性以及要設定的報告類型。

若要最佳化報表的建立、使用和持久性，您必須深入瞭解您想要滿足的需求。 第一個分析可讓您識別要建立的報表類型和最佳建立模式。 若要建立報表，請套用下列步驟：

1. 識別需求

   第一步是明確識別需求：您要在報表中顯示的內容及其目標（監控、分析、資料匯出等）。

   Adobe Campaign提供多種報表功能。 分析您識別最合適功能的需求非常重要。

   例如，您可以：

   * 探索資料庫中的資料並定義測量(透過 [本節](../../reporting/using/about-cubes.md)),
   * 新增指標至現有報表(請參 [閱本節](../../reporting/using/about-reports-creation-in-campaign.md)),
   * 查看資料庫中的資料(通 [過本節](../../reporting/using/about-descriptive-analysis.md)),
   * 建立新的傳送報表(請參 [閱本節](../../reporting/using/about-reports-creation-in-campaign.md)),
   * 從Adobe Campaign資料庫匯出資料(透過工作流程，請參 [閱本節](../../workflow/using/about-workflows.md)),
   * 建立透視表(請參閱 [本節](../../reporting/using/creating-a-table.md#creating-a-breakdown-or-pivot-table)),
   * 探索匯整資料(透 [過本節](../../reporting/using/about-cubes.md)),
   * 使用精靈來分析資料(透過 [本節](../../reporting/using/about-descriptive-analysis.md)),
   * 分析大量資料(請參 [閱本節](../../reporting/using/about-reports-creation-in-campaign.md))等。

1. 識別目標人口

   然後，您需要找出您要建立的報表將鎖定的目標對象、知道將檢視報表的公開對象類型以及報表顯示模式（在瀏覽器、Adobe Campaign、特定物件、整個平台等）。

   您也可以建立下列報表：

   * 所有Adobe Campaign營運商、
   * 擁有僅存取行銷促銷活動之權限的營運商，
   * 一個用於臨時使用的運算子，
   * Web存取中的所有運算子等。
   這些考量也需要考慮與存取權及安全性相關的問題。

1. 定義內容

   然後，您需要瞭解要顯示的資料類型：傳送指標、資料庫描述檔報告等。

   您也需要瞭解此資料的性質（簡單、由計算產生、重要等）、其位置（在Adobe Campaign中，在協力廠商系統中）、其更新頻率以定義計算週期（每日、每週、即時），以及其音量。

   需要仔細檢查與資料量和更新相關的問題，以避免報告顯示問題，尤其是在時間方面。 因此，我們建議建立匯整，以預先計算報表外的部分資料。 包含追蹤和傳送記錄的表格可包含數百萬筆記錄：這表示資料需要透過要用於報表的工作流程進行匯總。

## 最佳化報表建立{#optimizing-report-creation}

### 資料卷 {#data-volume}

為了保證最佳效能，操作資料量不能太大。

即：

* 報表的計算時間不得超過5分鐘。

   同樣地，在設計階段，若資料量較小，如果報表計算超過60秒，則需要變更計算方法。

* 使用行銷分析時，操控的資料不得超過1000萬行。

我們也建議您在晚上計算匯總，並直接在報表中使用此匯總資料。 這些集合必須通過專用的資料管理工作流（SQL查詢）建立。

您也可以在夜間計算報表，並自動建立可隨時檢視的歷史記錄，而不會超過資料庫。

### 查詢 {#queries}

我們建議盡可能使用SQL查詢，並避免JavaScript後處理。 如有必要，請在工作流中使用指令碼活動並刪除用於計算的資料。 您也可以使用封存的資料來加速處理時間。

在這種情況下，應使用下列語法：

```
if(string(ctx@_historyId)!==""))
```

可讓您收集報表中顯示的資料的查詢不應太複雜，尤其是套用至資料庫中所有資料時。 為了改善效能，在執行這些查詢之前先過濾資料非常有用：這表示計算只涉及部分資料。

### 效能 {#performances}

上述建議可讓您最佳化報表計算。

除此之外，Adobe Campaign建議進行下列改進：

* 研究資料模型：索引欄位必須主要用於改進計算公式。

   若要快速尋找索引欄位，請查看Adobe Campaign介面中的欄名：如果對欄位編製索引，則排序箭頭將以紅色加底線。

* 請確定報表在長期有效：資料量可能會隨著時間而大幅增加。

   同樣地，在測試階段期間處理的資料量可能與生產中的實際資料量不同。 這就是為什麼測試階段很重要。

   最後，需要知道並調整資料清除延遲，以方便進行資料操作。

### 匯出報表 {#exporting-reports}

本節將詳述特定於匯出報表 [的建議](../../reporting/using/actions-on-reports.md#exporting-a-report)。
