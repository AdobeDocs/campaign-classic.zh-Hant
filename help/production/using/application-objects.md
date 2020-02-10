---
title: 應用程式物件
seo-title: 應用程式物件
description: 應用程式物件
seo-description: null
page-status-flag: never-activated
uuid: 84fbad0f-872d-4aca-8ea9-007577be076d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 24d4875b-81fa-4bf3-8cf0-e6998bec4949
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e1937c1ddcbde092a22f4fe8c50d3d72b02cfeed

---


# 應用程式物件{#application-objects}

內建物件應受到監控，防止其增長過多非常重要。

## ID順序 {#sequence-of-ids}

Adobe Campaign會使用必須據以使用的ID序列： **xtkNewId**。 如果序列的使用速度非常快（即每天100,000次），您必須確認它符合您的業務需求，例如每天傳送數百萬封電子郵件。 可以為特定表定義專用序列。 您可以設定工作流程來監控ID使用情況。

當序列達到20多億（確切數字是2,147,483,648）時，它會回到零。 必須避免並產生問題，因此必須監控此序列。

若要防止在大型表格中出現此情況，請考慮使用特定序列。 這可以使用架構中 **的pkSequence** 屬性來完成。

建立大量記錄檔的高頻率工作流程會耗用大量ID。 因此強烈建議您避免工作流程中記錄檔過多和高頻率。

如果序列已經循環，最佳解決方案是切換至負ID，從-2,147,483,648開始。

## 資料夾 {#folders}

任何實例上都應少於1000個資料夾。 資料夾數量超過此數目，可能會造成促銷活動用戶端的效能問題。 您可以設定監控工作來計算資料夾、工作流程等數目，並定期向回報。

此方法也會反白顯示建立過多物件的使用者。

## 交貨 {#deliveries}

在任何時間，例項上應少於1000個傳送。 大量傳送會佔用資料庫空間並造成問題。 必鬚根據業務需求檢查每天建立10個以上交貨的實例。 請考慮使用持續傳送來建立較少的傳送。 如需詳細資訊，請參閱[本小節](../../workflow/using/continuous-delivery.md)。

應從實例中清除兩年以上的交貨。

## 檔案 {#files}

應用程式伺服器磁碟上的檔案數不應無限增加。

匯入工作流程會建立檔案，因此會造成磁碟擴充。 使用標準的「檔案」( [File)收集器活動可以防止](../../workflow/using/file-collector.md) 此情況。 檔案收集器將檔案移動到臨時資料夾並自動清除它們。

如果工作流導入檔案而未使用標準功能，則需要清除它，以將磁碟空間保持在最小。

## 交易資料和記錄檔 {#transactional-data-and-logs}

將資 [料匯入](../../workflow/using/executing-a-workflow.md#work-table) Adobe Campaign的每個工作流程都會使資料庫的大小增加。

檢查清除或清除工作流是否正在運行並有效清除記錄。 必須清除所有事務性資料和日誌。 清除任務僅清除標準表：追蹤和廣泛的記錄檔。 特定表必須由特定工作流清除。 Refer to [this section](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

檢查記錄的最舊建立日期，以查看事務資料的老化。
