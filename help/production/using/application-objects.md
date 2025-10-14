---
product: campaign
title: 應用程式物件
description: 應用程式物件
feature: Monitoring
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: fb4798d7-0a2c-455b-86b6-3dcb5fd25c82
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 1%

---

# 應用程式物件{#application-objects}



應該監控內建物件，並防止它們過度成長，這點很重要。

## ID序列 {#sequence-of-ids}

Adobe Campaign使用的ID序列必須據此使用： **xtkNewId**。 如果序列使用非常快（即每天超過100,000），您必須驗證它是否符合您的業務要求，例如每天傳送數百萬封電子郵件。 您可以為特定表格定義專用序列。 您可以設定工作流程以監控ID使用情形。

當序列達到超過20億（2,147,483,648是確切數字）時，就會回到零。 這必須避免並產生問題，因此必須監控此順序。

若要防止大型表格發生這種情況，請考慮使用特定順序。 您可以透過結構描述中的&#x200B;**pkSequence**&#x200B;屬性完成此操作。

建立大量記錄的高頻率工作流程將消耗大量ID。 因此，強烈建議避免在工作流程中記錄太多且頻率較高。

如果序列已經循環，最好的解決方案是切換到負ID，從 — 2,147,483,648開始。

## 資料夾 {#folders}

任何執行個體上的資料夾都應少於1000個。 資料夾數量超過此上限可能會導致Campaign使用者端的效能問題。 您可以設定監視工作，以計算資料夾、工作流程等數量，並定期回報。

此方法也會反白建立太多物件的使用者。

## 傳遞 {#deliveries}

執行個體上隨時應該有少於1000個傳遞。 大量的傳遞會消耗資料庫空間並產生問題。 每天建立超過10個傳遞的執行個體必須根據業務需求進行檢查。 請考慮使用連續傳遞來建立較少的傳遞。 如需詳細資訊，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/continuous-delivery.html?lang=zh-Hant){target="_blank"}。

應從執行個體中清除超過兩年的傳遞。

## 檔案 {#files}

應用程式伺服器磁碟上的檔案數不應無限增加。

匯入工作流程會建立檔案，因此造成磁碟擴充。 使用標準[檔案收集器](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-collector.html?lang=zh-Hant){target="_blank"}活動可避免此問題。 檔案收集器會將檔案移至暫存資料夾，並自動將其清除。

如果工作流程匯入檔案但未使用標準功能，則需要清除該工作流程以將磁碟空間維持在最低限度。

## 異動資料和記錄 {#transactional-data-and-logs}

每個將資料匯入Adobe Campaign的工作流程都會導致資料庫大小增加。 請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/use-workflow-data.html?lang=zh-Hant){target="_blank"}。

檢查清除或永久刪除工作流程是否正在執行並有效永久刪除記錄。 必須清除所有交易式資料和記錄檔。 清理工作只會清除標準表格：追蹤和廣泛記錄。 特定表格必須由特定工作流程清除。 請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=zh-Hant){target="_blank"}。

檢查記錄的最舊建立日期，以觀察交易式資料是否過時。
