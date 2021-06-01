---
product: campaign
title: 應用程式物件
description: 應用程式物件
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 4%

---

# 應用程式物件{#application-objects}

應監控內建物件，並防止其過量成長，這很重要。

## ID序列{#sequence-of-ids}

Adobe Campaign會使用必須據以使用的ID序列：**xtkNewId**。 如果快速使用序列（即每天100,000個序列），您必須確認其符合您的業務需求，例如每天傳送數百萬封電子郵件。 可以為特定表定義專用序列。 您可以設定工作流程以監控ID使用情形。

當序列達到20多億（確切數字為2,147,483,648）時，就會回到零。 這必須避免並造成問題，因此必須監控此序列。

若要在大型表格中防止發生此情況，請考慮使用特定序列。 這可以使用架構中的&#x200B;**pkSequence**&#x200B;屬性來完成。

建立大量記錄的高頻率工作流程將耗用大量ID。 因此，強烈建議您避免工作流程中記錄過多和高頻率。

如果序列已經循環，最佳解決方案是從–2,147,483,648開始切換為負ID。

## 資料夾 {#folders}

任何執行個體上都應少於1000個資料夾。 資料夾數量超過此上限，可能會造成Campaign用戶端的效能問題。 您可以設定監控工作來計算資料夾、工作流程等的數量，並定期回報。

此方法也會反白顯示建立過多物件的使用者。

## 傳遞 {#deliveries}

執行個體上隨時應少於1000個傳送。 大量傳送會佔用資料庫空間並造成問題。 每天建立10個以上傳送的例項，必鬚根據業務需求進行檢查。 請考慮使用持續傳送來建立較少的傳送。 如需詳細資訊，請參閱[本章節](../../workflow/using/continuous-delivery.md)。

超過兩年的傳送應從執行個體清除。

## 檔案 {#files}

應用程式伺服器磁碟上的檔案數不應無限增加。

導入工作流建立檔案，因此導致磁碟擴展。 使用標準[檔案收集器](../../workflow/using/file-collector.md)活動可以防止此情況。 檔案收集器將檔案移動到臨時資料夾並自動清除它們。

如果工作流導入了檔案，但未使用標準功能，則需要清除它，以將磁碟空間保持在最小。

## 交易資料和日誌{#transactional-data-and-logs}

將資料匯入Adobe Campaign的每個[工作流程](../../workflow/using/data-life-cycle.md#work-table)都會導致資料庫的大小增加。

檢查清除或清除工作流是否正在運行，並有效清除記錄。 必須清除所有交易資料和記錄檔。 清除任務僅清除標準表：追蹤和廣泛記錄檔。 特定表必須由特定工作流清除。 請參閱[本節](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs)。

檢查記錄最舊的建立日期，以觀察交易資料的時效性。
