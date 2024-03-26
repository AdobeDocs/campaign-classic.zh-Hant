---
product: campaign
title: 需維護的表格
description: 需維護的表格
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 194f12de-4671-4a56-8cdc-cd5e3dac147b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1146'
ht-degree: 1%

---

# 需維護的表格{#tables-to-maintain}



要維護的表格清單取決於您的Adobe Campaign版本、使用方式以及資料模型設定。

下列清單只包含最容易分散的表格。 其影響如下：

* 磁碟空間過度消耗，進而影響資料庫存取，
* 尚未定期更新的索引，這會減慢查詢效能。

## Adobe Campaign表格 {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>表格名稱 </strong><br /> </th> 
   <th> <strong>大小</strong><br /> </th> 
   <th> <strong>主要活動型別</strong><br /> </th> 
   <th> <strong>註解</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每個傳遞動作會有一筆記錄。 單一記錄可以更新多次以反映傳送進度，因此此表上的索引傾向於快速分割。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> Medium<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 在傳遞準備期間插入記錄的工作表。 它們會在傳送期間更新，最後在傳送完成後刪除。<br /> 此表格的平均大小相當受限，卻傾向於快速分割。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 此表格包含產生個人化映象頁面所需的資訊。 它包含備忘錄(CLOB)欄位，因此可能會非常大。 磁碟區與映象頁面的保留歷史記錄成正比。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> Medium<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表格包含傳遞程式的統計資料。 其記錄會定期更新。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> Medium<br /> </td> 
   <td> 更新，插入<br /> </td> 
   <td> 此表格包含電子郵件地址的相關資訊。 在隔離程式中經常會更新（記錄會在第一次傳送錯誤時建立、在計數器變更時更新，並在傳送成功後刪除）。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每個工作流程例項只有一個記錄，因此記錄極少。 但表格會定期更新，以反映狀態和進度。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 每次執行工作流程活動都會導致在此表格中建立記錄。 清除機制會在它們過期之後將其刪除。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 在工作流程中的任務之間啟用的每個轉變，都會導致在此表格中建立記錄。 清除機制會在它們過期之後將其刪除。 <br /> </td> 
  </tr> 
  <tr> 
   <td> xtkworkflowjob<br /> </td> 
   <td> 非常小 <br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表格專用於工作流程引擎。 這可讓您將命令傳送至工作流程（例如，開始、停止、暫停）。 雖然此表格很小，但在清除連結至工作流程的異動表格時，會考慮使用此表格。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> 最大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 這是系統中最大的表格。 每封傳送的訊息有一筆記錄，這些記錄會插入、更新以追蹤傳遞狀態，並在清除歷史記錄時刪除。 <br /> </td> 
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
   <td> 此表格包含用於確認SMTP錯誤的資訊。 索引相當小，但會大幅更新，因此此表格上的索引傾向於快速分割。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> Medium<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表格包含依網域排序的SMTP錯誤彙總。 它最初包含詳細資訊，在清除任務過期後由清除任務彙總。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid （在中間來源執行個體上）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 只有在5.10 （或更新版本）執行個體用作中間來源執行個體時。 這是資料庫中最大的表格之一。 每封傳送的訊息有一筆記錄，這些記錄會插入、更新以追蹤傳遞狀態，並在清除歷史記錄時刪除。 使用中間來源時，建議限制歷史記錄（通常少於兩個月），因此此表格在大小方面維持合理（若60,000,000列，則小於30 Go，資料+索引），但時常重建非常重要。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp （使用NmsRecipient表格時） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 這是系統中最大的表格。 每封傳送的訊息有一筆記錄，這些記錄會插入、更新以追蹤傳遞狀態，並在清除歷史記錄時刪除。 請注意，在5.10中，此表格小於4.05 (NmsBroadLog)中的對應專案，因為5.10版的NmsBroadLogMsg表格會分解SMTP訊息文字。 不過，仍必須定期重新索引此表格（從開始每隔一週重新索引），並不時完全重建（每月一次，或效能受到影響時）。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyyBroadLogXxx （使用外部收件者表格時）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與NmsBroadLogRcp相同，但使用外部收件者表格。 請將Yyyy和Xxx調整為您傳送對應中的值。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp （使用NmsRecipient表格時） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 清除歷史記錄時會插入和刪除追蹤記錄，但不會更新。 磁碟區取決於資料保留的長度。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyyyTrackingLogXxx （使用外部收件者表格時）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 與NmsTrackingLogRcp相同，但使用外部收件者表格。 請將Yyyy和Xxx調整為您傳送對應中使用的值。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent （Message Center執行例項）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與其他broadlog表格類似，但使用NmsRtEvent而非NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent（ Message Center執行例項）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 與其他trackingLog表格類似，但使用NmsRtEvent表格而非NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent （Message Center執行例項）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 包含訊息中心事件佇列的表格。 這些事件的狀態會在處理時由訊息中心更新。 刪除會在整個清除期間執行。 建議您定期重新建立此資料表的索引並重新建置。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto （訊息中心控制執行個體）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與NmsRtEvent類似。 此表格會封存所有執行例項中的每個事件。 此變數僅供報告使用，不供即時程式使用。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMobileApp<br /> </td> 
   <td> 非常小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 包含行動應用程式及其設定的表格。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAppSubscriptionRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新<br /> </td> 
   <td> 此表格包含用來傳送通知的行動裝置（位址）識別碼（類似收件者表格）。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與其他broadlog表格類似，但使用NmsappSubscriptionRcp而非NmsRecipient。<br /> </td> 
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
   <td> 包含使用者工作階段的表格。 插入和刪除的數目非常重要。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 客戶表格 {#customer-tables}

除了上述清單，包含客戶(不存在於Adobe Campaign資料模型中)在平台設定期間建立的表格也可能遭到分割，尤其是在資料載入或同步程式期間經常更新這些表格時。 這些表格可以是預設Adobe Campaign資料模型的一部分(例如 **NmsRecipient**)。 在這種情況下，由Adobe Campaign平台的管理員負責稽核其特定的資料庫模型，以尋找這些自訂表格。 這些表格不一定會在我們的維護程式中明確提及。
