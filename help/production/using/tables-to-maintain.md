---
product: campaign
title: 需維護的表格
description: 需維護的表格
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 3%

---

# 需維護的表格{#tables-to-maintain}



要維護的表格清單取決於您的Adobe Campaign版本、使用方式和資料模型設定。

以下清單僅包含最易碎的表。 影響如下：

* 磁碟空間消耗過多，從而影響資料庫訪問，
* 未定期更新的索引，這會降低查詢效能。

## Adobe Campaign表 {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>表格名稱 </strong><br /> </th> 
   <th> <strong>大小</strong><br /> </th> 
   <th> <strong>活動的主要類型</strong><br /> </th> 
   <th> <strong>評論</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每個傳送動作有一筆記錄。 單一記錄可更新多次以反映傳送進度，因此此表格上的索引往往會快速分割。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 在傳送準備期間插入記錄的工作表。 然後在傳送期間更新，最後在傳送完成後刪除。<br /> 此表格雖然平均大小相當有限，但往往會迅速分割。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 此表包含生成個性化鏡像頁所需的資訊。 它包含備忘錄(CLOB)欄位，因此往往非常大。 該卷與保留的鏡像頁的歷史記錄成正比。 <br /> </td> 
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
   <td> 此表包含有關電子郵件地址的資訊。 它會隨著隔離程式而經常更新（記錄會在第一個傳送錯誤時建立，當計數器變更，並在傳送成功後刪除）。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每個工作流實例只有一個記錄，因此記錄非常少。 但定期更新表，以反映狀態和進展。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 工作流活動的每次執行都會導致在此表格中建立記錄。 清除機制會在過期後刪除它們。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 在工作流中的任務之間激活的每個轉變都會導致在此表中建立記錄。 清除機制會在過期後刪除它們。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> 很小 <br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表格是工作流程引擎專屬的表格。 它可讓命令傳送至工作流程（例如，開始、停止、暫停）。 雖然此表很小，但在清除連結到工作流的交易表時會考慮此表。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> 最大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 這是系統中最大的表。 每條郵件都有一條記錄，這些記錄會插入、更新以追蹤傳送狀態，並在清除歷史記錄時刪除。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLog<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 清除歷史記錄時會插入和刪除追蹤記錄，但不會更新。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 此表包含用於確認SMTP錯誤的資訊。 它相當小，但會大量更新，因此此表格上的索引往往會快速分割。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表包含按域排序的SMTP錯誤上的聚合。 它最初包含詳細資訊，一旦清理任務過期，該資訊將由清理任務匯總。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid（在中間來源執行個體上）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 僅當5.10（或更新版本）例項用作中間來源例項時。 這是資料庫中最大的表之一。 每條郵件都有一條記錄，這些記錄會插入、更新以追蹤傳送狀態，並在清除歷史記錄時刪除。 使用中間來源時，建議限制歷史記錄（通常少於兩個月），因此此表格在大小上仍然合理（6,000萬列少於30 Go，資料+索引），但必須不時重建表格。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp（使用NmsRecipient表時） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 這是系統中最大的表。 每條郵件都有一條記錄，這些記錄會插入、更新以追蹤傳送狀態，並在清除歷史記錄時刪除。 請注意，在5.10中，此表小於4.05(NmsBroadLog)中的等值項，因為SMTP消息文本在5.10版的NmsBroadLogMsg表中被分解。 但是，定期（每隔一週從開始）重新索引此表格，並不時（每月一次，或效能受到影響時）完全重建表格仍然至關重要。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx（當使用外部收件者表時）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與NmsBroadLogRcp相同，但與外部收件者表格相同。 請將Yyy和Xxx與您的傳送對應中的值調整。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp（使用NmsRecipient表時） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 清除歷史記錄時會插入和刪除追蹤記錄，但不會更新。 卷取決於資料保留的時間長度。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx（使用外部收件者表時）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 與NmsTrackingLogRcp相同，但與外部收件者表格相同。 請使用傳送映射中使用的值來調整Yyy和Xxx。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent（Message Center執行實例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與其他broadlog表類似，但使用NmsRtEvent而非NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent（Message Center執行實例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 與其他trackingLog表格類似，但使用NmsRtEvent表格而非NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent（消息中心執行實例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 包含「消息中心」事件隊列的表。 這些事件的狀態會在處理時由訊息中心更新。 清除期間執行刪除操作。 我們建議您定期重新建立此表的索引並重建它。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto（Message Center控制實例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 類似NmsRtEvent。 此表格會封存所有執行例項的每個事件。 它不供即時程式使用，僅供報表使用。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> 很小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 包含行動應用程式及其設定的表格。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新<br /> </td> 
   <td> 包含用於傳送通知的行動裝置（地址）識別碼的表格（類似於收件者表格）。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與其他broadlog表類似，但使用NmsappSubscriptionRcp而非NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 與其他trackingLog表格類似，但使用NmsappSubscriptionRcp表格而非NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 包括用戶會話的表。 插入和刪除的數量非常重要。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 客戶表 {#customer-tables}

除了上述清單外，在平台設定期間包含客戶建立(Adobe Campaign資料模型中不存在)的表格也可能會遭到分割，尤其是當資料載入或同步程式期間經常更新時。 這些表格可以是預設Adobe Campaign資料模型的一部分(例如 **NmsRecipient**)。 在這種情況下，由Adobe Campaign平台的管理員對其特定資料庫模型進行審核，以查找這些自定義表。 這些表不一定在我們的維護過程中明確提及。
