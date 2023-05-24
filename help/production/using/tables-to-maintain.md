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



要維護的表格清單取決於您的Adobe Campaign版本、使用方式以及資料模型設定。

下列清單僅包含最容易發生片段化的表格。 其影響如下：

* 磁碟空間過度消耗，進而影響資料庫存取，
* 尚未定期更新的索引，這會減慢查詢效能。

## Adobe Campaign表格 {#adobe-campaign-tables}

<table> 
 <thead> 
  <tr> 
   <th> <strong>表格名稱 </strong><br /> </th> 
   <th> <strong>大小</strong><br /> </th> 
   <th> <strong>活動的主要型別</strong><br /> </th> 
   <th> <strong>評論</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> NmsDelivery<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每個傳遞動作都有一個記錄。 單一記錄可以更新數次以反映傳送進度，因此此表上的索引傾向於快速分割。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryPart<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 在傳遞準備期間插入記錄的工作表。 它們隨後會在傳送期間更新，並最終在傳送完成後刪除。<br /> 此表格的平均大小相當受限，但碎片化速度卻很快。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsMirrorPageInfo<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 此表格包含產生個人化映象頁面所需的資訊。 它包含備忘錄(CLOB)欄位，因此會非常大。 磁碟區與映象頁面的保留歷史記錄成正比。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsDeliveryStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表格包含傳遞程式的統計資料。 其記錄會定期更新。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsAddress<br /> </td> 
   <td> 中<br /> </td> 
   <td> 更新，插入<br /> </td> 
   <td> 此表格包含電子郵件地址的相關資訊。 它經常在隔離程式中更新（記錄會在第一次傳送錯誤時建立，並在計數器中變更時更新，並在傳送成功後刪除）。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflow<br /> </td> 
   <td> 小<br /> </td> 
   <td> 更新<br /> </td> 
   <td> 每個工作流程例項都有一個記錄，因此記錄非常少。 但表格會定期更新，以反映狀態和進度。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowTask<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 每次執行工作流程活動都會導致在此表格中建立記錄。 清除機制會在它們過期後將其刪除。<br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowEvent<br /> </td> 
   <td> 小<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 在工作流程中的任務之間啟用的每個轉變，都會導致在此表格中建立記錄。 清除機制會在它們過期後將其刪除。 <br /> </td> 
  </tr> 
  <tr> 
   <td> XtkWorkflowJob<br /> </td> 
   <td> 非常小 <br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表格專屬於工作流程引擎。 它可讓您將命令傳送至工作流程（例如「開始」、「停止」、「暫停」）。 雖然此表格很小，但在清除連結至工作流程的異動表格時，會考慮使用此表格。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLog<br /> </td> 
   <td> 最大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 這是系統中最大的表格。 每封傳送的訊息都有一筆記錄，這些記錄會插入、更新以追蹤傳遞狀態，並在清除歷史記錄時刪除。 <br /> </td> 
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
   <td> 此表格包含用於確認SMTP錯誤的資訊。 索引相當小，但會大幅更新，因此此表上的索引傾向於快速分割。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEmailErrorStat<br /> </td> 
   <td> 中<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 此表格包含依網域排序的SMTP錯誤彙總。 它最初包含詳細資訊，一旦清除任務過時就會彙總這些資訊。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogMid （在中間來源執行個體上）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 只有當5.10 （或更新版本）例項作為中間來源例項時。 這是資料庫中最大的表格之一。 每封傳送的訊息都有一筆記錄，這些記錄會插入、更新以追蹤傳遞狀態，並在清除歷史記錄時刪除。 使用中間來源時，建議限制歷史記錄（通常少於兩個月），因此此表格的尺寸保持合理（6000萬列小於30 Go，資料+索引），但偶爾重建非常重要。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRcp （使用NmsRecipient表格時） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 這是系統中最大的表格。 每封傳送的訊息都有一筆記錄，這些記錄會插入、更新以追蹤傳遞狀態，並在清除歷史記錄時刪除。 請注意，在5.10中，此表格比4.05中的對應表格(NmsBroadLog)小，因為5.10版的NmsBroadLogMsg表格會分解SMTP訊息文字。 不過，請務必定期重新索引此表格（從開始每隔一週重新索引），並不時完全重建表格（每月一次，或是在效能受到影響時）。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyybroadLogXxx （使用外部收件者表格時）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與NmsBroadLogRcp相同，但使用外部收件者表格。 請將Yyyy和Xxx調整為您的傳遞對應中的值。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRcp （使用NmsRecipient表格時） <br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 清除歷史記錄時會插入和刪除追蹤記錄，但不會更新。 磁碟區取決於資料保留的長度。 <br /> </td> 
  </tr> 
  <tr> 
   <td> YyytrackingLogXxx （使用外部收件者表格時）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 與NmsTrackingLogRcp相同，但使用外部收件者表格。 請將Yyyy和Xxx調整為您傳遞對應中使用的值。 <br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogRtEvent （訊息中心執行例項）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 類似於其他broadlog表格，但使用NmsRtEvent而非NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsTrackingLogRtEvent（訊息中心執行例項）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、刪除<br /> </td> 
   <td> 與其他trackingLog表格類似，但使用NmsRtEvent表格而非NmsRecipient。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsRtEvent （訊息中心執行例項）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 包含「訊息中心」事件佇列的表格。 這些事件的狀態會在處理時由訊息中心更新。 刪除會在整個清除期間執行。 建議您定期重新建立此資料表的索引並重新建置。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsEventHisto （訊息中心控制執行個體）<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 與NmsRtEvent類似。 此表格會封存所有執行例項中的每個事件。 此變數僅供報告使用，無法即時使用。<br /> </td> 
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
   <td> 此表格包含用來傳送通知的行動裝置（位址）識別碼（類似於收件者表格）。<br /> </td> 
  </tr> 
  <tr> 
   <td> NmsBroadLogAppSubRcp<br /> </td> 
   <td> 大<br /> </td> 
   <td> 插入、更新、刪除<br /> </td> 
   <td> 類似於其他broadlog表格，但使用NmsappSubscriptionRcp而非NmsRecipient。<br /> </td> 
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

除了上述清單，包含客戶(不存在於Adobe Campaign資料模型中)在平台設定期間建立的表格也可能遭到分割，尤其是如果這些表格在資料載入或同步程式期間經常更新。 這些表格可以是預設Adobe Campaign資料模型的一部分(例如 **NmsRecipient**)。 在這種情況下，Adobe Campaign平台的管理員需要對其特定資料庫模型進行稽核，以找到這些自訂表格。 我們的維護程式中不一定會明確提及這些表格。
