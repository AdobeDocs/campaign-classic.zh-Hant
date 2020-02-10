---
title: 要維護的表
seo-title: 要維護的表
description: 要維護的表
seo-description: null
page-status-flag: never-activated
uuid: 1085e929-65cc-48fa-9c31-0508a14b4704
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 6ec4e566-7116-4d7f-835d-cb0f3c3a6a7a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 要維護的表{#tables-to-maintain}

要維護的表格清單取決於您的Adobe Campaign版本、使用方式和資料模型設定。

以下清單僅包含最受碎片影響的表。 影響如下：

* 過度佔用磁碟空間，從而影響資料庫訪問，
* 未定期更新的索引，這會降低查詢效能。

## Adobe Campaign表格 {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>表名 </strong><br /> </th> 
   <th> <strong>大小</strong><br /> </th> 
   <th> <strong>主要活動類型</strong><br /> </th> 
   <th> <strong>注釋</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每個傳送動作有一個記錄。 單一記錄可多次更新以反映傳遞進度，因此此表格上的索引往往會快速分割。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 在交付準備期間插入記錄的工作表。 然後在傳送期間更新，最後在傳送完成後刪除。<br /> 儘管平均大小相當有限，但這張表格往往會迅速分割。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 此表包含生成個性化鏡像頁面所需的資訊。 它包含一個備忘錄(CLOB)欄位，因此通常很大。 卷與保留的鏡像頁的歷史記錄直接成比例。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表包含傳送程式的統計資料。 其記錄會定期更新。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> 中<br /> </td> 
   <td> 更新、插入<br /> </td> 
   <td> 此表包含有關電子郵件地址的資訊。 它經常作為隔離過程的一部分進行更新（記錄在第一次傳送錯誤時建立，當計數器更改並在傳送成功時刪除）。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每個工作流程例項有一個記錄，因此記錄很少。 不過，會定期更新表格，以反映狀態和進度。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 工作流活動的每次執行都會導致在此表中建立記錄。 清除機制會在過期後將其刪除。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 工作流中任務之間激活的每個過渡都會導致在此表中建立記錄。 清除機制會在過期後將其刪除。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> 非常小 <br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表格是工作流引擎專用的。 它可將命令發送到工作流（例如，「開始」、「停止」、「暫停」）。 雖然它很小，但在清除連結至工作流的事務表時會考慮此表。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> 最大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 這是系統中最大的表。 每條消息發送一條記錄，這些記錄將被插入、更新以跟蹤傳送狀態，並在清除歷史記錄時被刪除。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 追蹤記錄在清除歷史記錄時會插入和刪除，但不會更新。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 此表包含用於確定SMTP錯誤的資訊。 它相當小，但會大幅更新，因此此表上的索引往往會快速分解。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表包含按域排序的SMTP錯誤上的聚合。 它最初包含詳細資訊，當清除任務過時時，該資訊將由清除任務匯總。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid（在中間採購實例上）<br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 僅當5.10（或更新版本）例項用作中間採購例項時。 這是資料庫中最大的表之一。 每條消息發送一條記錄，這些記錄將被插入、更新以跟蹤傳送狀態，並在清除歷史記錄時被刪除。 使用中間採購時，建議限制歷史記錄（通常少於兩個月），因此此表格在大小上仍屬合理（6000萬列小於30 Go，資料+索引），但是必須不時重建它。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp（使用NmsRecipient表時） <br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 這是系統中最大的表。 每條消息發送一條記錄，這些記錄將被插入、更新以跟蹤傳送狀態，並在清除歷史記錄時被刪除。 請注意，在5.10中，此表比4.05中的等效表(NmsBroadLog)小，因為5.10版的NmsBroadLogMsg表中分解了SMTP消息文本。 不過，定期（每隔一週開始）重新索引此表格，並不時（每月一次，或效能受到影響時）完全重建表格，仍然很重要。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx（使用外部收件者表時）<br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與NmsBroadLogRcp相同，但具有外部收件者表。 請將Yyy和Xxx與您的傳送映射中的值相適配。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp（使用NmsRecipient表時） <br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 追蹤記錄在清除歷史記錄時會插入和刪除，但不會更新。 卷取決於資料保留的長度。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx（使用外部收件者表時）<br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 與NmsTrackingLogRcp相同，但與外部收件者表相同。 請將Yyy和Xxx與傳送映射中使用的值進行調整。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent（消息中心執行實例）<br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與其他廣播表類似，但使用NmsRtEvent而不是NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent（消息中心執行實例）<br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 與其他trackingLog表類似，但與NmsRtEvent表相似，而不與NmsRecipient相同。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent（消息中心執行實例）<br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 包含消息中心事件隊列的表。 這些事件的狀態由消息中心在處理時更新。 刪除在清除期間執行。 我們建議您定期重新建立此表的索引並重建該索引。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto（消息中心控制實例）<br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 類似於NmsRtEvent。 此表會封存所有執行例項中的每個事件。 它不會由即時程式使用，只會由報表使用。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> 非常小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 包含行動應用程式及其組態的表格。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、更新<br /> </td> 
   <td> 包含用於傳送通知的行動裝置（地址）識別碼的表格（類似於收件者表格）。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與其他廣播表類似，但使用NmsappSubscriptionRcp而非NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> 大型<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 與其他trackingLog表類似，但NmsappSubscriptionRcp表而非NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 包含用戶會話的表。 插入和刪除的數量非常重要。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 客戶表 {#customer-tables}

除了上述清單外，在平台設定期間包含客戶建立（Adobe Campaign資料模型中不存在）的表格也可能會遭到分割，尤其是當資料載入或同步程式期間經常更新時。 這些表格可以是預設Adobe Campaign資料模型(例如 **NmsRecipient**)的一部分。 在這種情況下，Adobe Campaign平台的管理員必須對其特定資料庫模型進行稽核，才能找到這些自訂表格。 這些表格不一定在我們的維護程式中明確提及。
