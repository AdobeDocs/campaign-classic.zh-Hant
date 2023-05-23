---
product: campaign
title: 需維護的表格
description: 需維護的表格
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 3%

---

# 需維護的表格{#tables-to-maintain}



要維護的表清單取決於您的Adobe Campaign版本、使用方式和資料模型配置。

以下清單僅包含最受碎片影響的表。 影響如下：

* 磁碟空間消耗過大，從而影響資料庫訪問，
* 未定期更新的索引，這會降低查詢效能。

## Adobe Campaign表 {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>表格名稱 </strong><br /> </th> 
   <th> <strong>大小</strong><br /> </th> 
   <th> <strong>主要活動類型</strong><br /> </th> 
   <th> <strong>評論</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Nms交付<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每個傳遞操作有一條記錄。 單個記錄可以多次更新以反映交付進度，因此此表上的索引往往會快速分解。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 在交付準備期間插入記錄的工作表。 然後，在交付期間更新它們，最後在交付完成後將其刪除。<br /> 儘管該表的平均大小相當有限，但它往往會迅速分裂。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入，刪除<br /> </td> 
   <td> 此表包含生成個性化鏡像頁所需的資訊。 它包含一個備忘錄(CLOB)欄位，因此它往往非常大。 卷與保留的鏡像頁的歷史記錄成正比。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表包含有關傳遞過程的統計資訊。 其記錄會定期更新。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NMS地址<br /> </td> 
   <td> 中<br /> </td> 
   <td> 更新，插入<br /> </td> 
   <td> 此表包含有關電子郵件地址的資訊。 它經常作為隔離過程的一部分進行更新（記錄在第一次傳送錯誤時建立，在計數器更改時更新，並在傳送成功後刪除）。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每個工作流實例有一條記錄，因此記錄很少。 但是，定期更新表，以反映現狀和進展。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 工作流活動的每次執行都會導致在此表中建立記錄。 清除機制會在它們過期後將其刪除。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 在工作流中的任務之間激活的每個轉換都會導致在此表中建立記錄。 清除機制會在它們過期後將其刪除。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> 很小 <br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表特定於工作流引擎。 它允許將命令發送到工作流（例如，啟動、停止、暫停）。 儘管該表很小，但在清除連結到工作流的事務表時會考慮此表。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> 最大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 這是系統中最大的表。 每條消息都有一條記錄，這些記錄將被插入、更新以跟蹤傳送狀態，並在清除歷史記錄時被刪除。 <br /> </td> 
  </tr> 
  <tr> 
   <td> Nms跟蹤日誌<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入，刪除<br /> </td> 
   <td> 在清除歷史記錄時，將插入和刪除跟蹤日誌，但不會更新它們。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadlogMsg <br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 此表包含用於限定SMTP錯誤的資訊。 它相當小，但會大量更新，因此此表上的索引往往會快速分解。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表包含按域排序的SMTP錯誤聚合。 它最初包含詳細資訊，一旦清理任務過時，該資訊將由該任務聚合。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid（在中間採購實例上）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 僅當5.10（或更高版本）實例用作中間採購實例時。 這是資料庫中最大的表之一。 每條消息都有一條記錄，這些記錄將被插入、更新以跟蹤傳送狀態，並在清除歷史記錄時被刪除。 使用中間來源補充時，建議限制歷史記錄（通常不到兩個月），因此此表在大小上保持合理（6000萬行少於30Go，資料+索引），但是，不時重建它非常重要。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp（使用NmsRecipient表時） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 這是系統中最大的表。 每條消息都有一條記錄，這些記錄將被插入、更新以跟蹤傳送狀態，並在清除歷史記錄時被刪除。 請注意，在5.10中，此表小於4.05(NmsBroadLog)中的等效值，因為SMTP消息文本在5.10版本的NmsBroadLogMsg表中被分解。 但是，定期（每隔一週開始）重新編製此表的索引，並不時（每月一次，或當效能受到影響時）完全重建它仍然至關重要。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyBroadLogXxx（使用外部收件人表時）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與NmsBroadLogRcp相同，但與外部收件人表相同。 請將Yyy和Xxx與交貨映射中的值進行調整。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp（使用NmsRecipient表時） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入，刪除<br /> </td> 
   <td> 在清除歷史記錄時，將插入和刪除跟蹤日誌，但不會更新它們。 卷取決於資料保留的長度。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyTrackingLogXxx（使用外部收件人表時）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入，刪除<br /> </td> 
   <td> 與NmsTrackingLogRcp相同，但與外部收件人表相同。 請將Yyy和Xxx與在交付映射中使用的值進行調整。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent（消息中心執行實例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與其他廣播表類似，但使用NmsRtEvent而不是NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent（消息中心執行實例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入，刪除<br /> </td> 
   <td> 與其他trackingLog表類似，但與NmsRtEvent表而不是NmsRecipient表類似。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent（消息中心執行實例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 包含消息中心事件隊列的表。 這些事件的狀態由消息中心在處理時更新。 清除期間執行刪除操作。 我們建議您定期重新建立此表的索引並重建它。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto（消息中心控制實例）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與NmsRtEvent類似。 此表將存檔所有執行實例中的每個事件。 它不由即時進程使用，只由報告使用。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> 很小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 包括移動應用程式及其配置的表。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新<br /> </td> 
   <td> 包括用於發送通知的移動設備（地址）的標識符的表（類似於收件人表）。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與其他廣播表類似，但使用NmsappSubscriptionRcp而不是NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogAppSubRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入，刪除<br /> </td> 
   <td> 與其他trackingLog表類似，但與NmsappSubscriptionRcp表而不是NmsRecipient表類似。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkSessionInfo<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入，刪除<br /> </td> 
   <td> 包括用戶會話的表。 插入和刪除的次數非常重要。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 客戶表 {#customer-tables}

除上面的清單外，在平台設定期間包含客戶建立的表(在Adobe Campaign資料模型中不存在)也可能受到碎片的影響，特別是在資料載入或同步過程中經常更新這些表時。 這些表可以是預設Adobe Campaign資料模型的一部分(例如 **Nms收件人**)。 在這種情況下，Adobe Campaign平台的管理員應對其特定資料庫模型進行審計，以找到這些自定義表。 這些表不一定在維護過程中明確提及。
