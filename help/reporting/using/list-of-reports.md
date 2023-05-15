---
product: campaign
title: 報告清單
description: 報告清單
badge: label="v7" type="Informity" tooltip="僅適用於Campaign Classicv7"
feature: Reporting
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 2%

---

# 報告清單{#list-of-reports}



## 傳遞報表 {#reports-on-deliveries}

Adobe Campaign提供的內建報表位於下表。

如需這些報表內容的詳細資訊，請參閱 [本節](../../reporting/using/delivery-reports.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>結構描述</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 使用者活動(recipientActivity)<br /> </td> 
   <td> 依時段劃分開啟、點按和交易。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送總處理量（輸送量）<br /> </td> 
   <td> 傳送吞吐量圖表，以報文/小時和Mbit/s為單位。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 失敗和退信（錯誤）<br /> </td> 
   <td> 退信和不可交付項（按原因和域）。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 追蹤指標(deliveryFeedback)<br /> </td> 
   <td> 追蹤收件者行為的關鍵指標摘要。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 追蹤指標(mobileAppDeliveryFeedback)<br /> </td> 
   <td> 追蹤傳送至行動應用程式的指標。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 瀏覽器(browserStatistics)<br /> </td> 
   <td> 按一下訊息之收件者所使用之瀏覽器的統計資料。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 分享至社交網路(deliveryForward)<br /> </td> 
   <td> 共用活動和郵件開啟統計資訊。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 熱點點按（捲動）<br /> </td> 
   <td> 顯示疊加的消息和點按率。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 假設報表(deliveryHexposition)<br /> </td> 
   <td> 顯示有關交付假設的測量摘要。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送統計資料(statisticsPerDelivery)<br /> </td> 
   <td> 每個電子郵件網域的統計資料（已處理的訊息、已傳送的訊息、硬退信、軟退信、點按、取消訂閱）。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用活動統計資料(forwardActivities)<br /> </td> 
   <td> 分析每個時段的共用活動、開啟和訂閱。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 追蹤統計資料(trackingStatistics)<br /> </td> 
   <td> 開啟，按一下「和」交易率報表。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送摘要(deliverySending)<br /> </td> 
   <td> 交付指標摘要：目標、排除和已傳送的訊息。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送摘要(deliveryStatistics)<br /> </td> 
   <td> 所選傳送的摘要表格：已傳送目標、排除和訊息。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 作業系統(osStatistics)<br /> </td> 
   <td> 按一下訊息的收件者所使用作業系統的統計資料。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 反應率(deliveryFeedbackSocial)<br /> </td> 
   <td> 輸送反應率和反應分解。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> URL和點按輸送量(topUrlDelivery)<br /> </td> 
   <td> 反應性最強的URL和相關的點按資料流。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 行銷活動報表 {#reports-on-campaigns}

行銷活動報表與 **nms:operation** 表格。

Adobe Campaign提供的內建報表位於下表。

如需這些報表內容的詳細資訊，請參閱 [本節](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 使用者活動(operationRecipientActivity)<br /> </td> 
   <td> 依時段劃分的開啟、點按和交易次數，取決於促銷活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送總處理能力(operationThroughput)<br /> </td> 
   <td> 以郵件/小時和Mbit/s為單位的傳送吞吐量圖表取決於Campaign。<br /> </td> 
  </tr> 
  <tr> 
   <td> 促銷活動費用(budgetOperationExpenses)<br /> </td> 
   <td> 根據促銷活動顯示詳細的促銷活動明細項目。<br /> </td> 
  </tr> 
  <tr> 
   <td> 失敗和退信(operationErrors)<br /> </td> 
   <td> 退信和不可交付項目（依原因和網域）取決於Campaign。<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerOperation)<br /> </td> 
   <td> 成本行的描述性分析取決於MRM。<br /> </td> 
  </tr> 
  <tr> 
   <td> 追蹤指標(operationFeedback)<br /> </td> 
   <td> 關鍵追蹤指標的概觀：開啟、點按和交易，取決於促銷活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用至社交網路(operationForward)<br /> </td> 
   <td> 共用活動和郵件開啟統計資料，取決於促銷活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 假設報表(operationHexposition)<br /> </td> 
   <td> 根據促銷活動顯示促銷活動傳送的假設測量摘要。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用活動統計資料(forwardActivityOpt)<br /> </td> 
   <td> 依據Campaign分析每個時段的共用活動、開啟次數和訂閱次數。<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送摘要(operationStatistics)<br /> </td> 
   <td> 促銷活動傳送的摘要圖表：已傳送目標、排除和訊息。<br /> </td> 
  </tr> 
  <tr> 
   <td> URL和點按輸送量(operationTopUrlDelivery)<br /> </td> 
   <td> 大部分的反應式URL和相關的點按資料流取決於Campaign。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 服務報告 {#reports-on-services}

有關服務的報告涉及 **nms:service** 表格。

Adobe Campaign提供的內建報表位於下表。

如需這些報表內容的詳細資訊，請參閱相關指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 粉絲贏取(socialUbcripationsByWebapp)<br /> </td> 
   <td> 哪些Web應用程式使潛在客戶獲得成功？ 取決於社交行銷附加元件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 訂閱劃分(mobileAppDistribution)<br /> </td> 
   <td> 依行動應用程式頻道附加元件，劃分每個行動應用程式的作用中訂閱。<br /> </td> 
  </tr> 
  <tr> 
   <td> 訂閱追蹤(subscriptionsProgress)<br /> </td> 
   <td> 資訊服務訂閱的演變<br /> </td> 
  </tr> 
  <tr> 
   <td> 反應率(socialReactionRate)<br /> </td> 
   <td> 最新傳送的再活動率為何？ 取決於社交行銷附加元件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 反應率(mobileAppReciblyRate)<br /> </td> 
   <td> 最新傳送的再活動率取決於行動應用程式通道附加元件。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 預算報表 {#budget-reports}

Adobe Campaign提供的內建報表位於下表。

如需這些報表內容的詳細資訊，請參閱 [本節](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>結構描述</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 與方案有關的費用（預算方案費用）<br /> </td> 
   <td> 方案費用細目。<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 預算演變(budgetEvolution)<br /> </td> 
   <td> 按承諾水準開列的預算費用演變。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 預算的累積演變(budgetCumulativeEvolution)<br /> </td> 
   <td> 按預算細分的累積預算費用的演變<br /> 部門級別。 </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerBudget)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorer)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerPlan)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerProgram)<br /> </td> 
   <td> 成本行的描述性分析。<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 預算（預算）匯總<br /> </td> 
   <td> 主要成本、支出類別和預算的快照。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 模擬報告 {#reports-on-simulations}

模擬報表與 **nms：模擬** 表格。

Adobe Campaign提供的內建報表位於下表。

如需這些報表內容的詳細資訊，請參閱相關指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 模擬排除的詳細資訊(dlvSimuLossDetail)<br /> </td> 
   <td> 排除所有原因的詳細表格。<br /> </td> 
  </tr> 
  <tr> 
   <td> 依排名劃分優惠方案(offerSimulationRanking)<br /> </td> 
   <td> 模擬中選件的劃分（依排名）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 模擬摘要(dlvSimuLossSummary)<br /> </td> 
   <td> 模擬卷和排除的摘要。<br /> </td> 
  </tr> 
  <tr> 
   <td> 重疊統計(dlvSimuOverplaing)<br /> </td> 
   <td> 傳遞目標重疊卷。<br /> </td> 
  </tr> 
  <tr> 
   <td> 因模擬而排除的摘要(dlvSimuLossSimu)<br /> </td> 
   <td> 因模擬而排除的表格。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 網路應用程式報告 {#reports-on-web-applications}

Web應用程式報告與 **nms:WebApp** 表格。

Adobe Campaign提供的內建報表位於下表。

如需這些報表內容的詳細資訊，請參閱 [本節](../../web/using/about-web-applications.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 檔案(surveyDictionary)<br /> </td> 
   <td> 調查結構的說明取決於「調查管理員」附加元件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 主要(surveyProperties)<br /> </td> 
   <td> 調查屬性<br /> </td> 
  </tr> 
  <tr> 
   <td> 回應的劃分(surveyDistribution)<br /> </td> 
   <td> 問題回應的劃分。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他ootb報告 {#other-ootb-reports}

也提供下列內建報表。 有關詳細資訊，請參閱相關功能的文檔。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>結構描述</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 優惠方案分析(offerAnalysis)<br /> </td> 
   <td> 根據日期和管道進行選件分析，取決於互動附加元件。<br /> </td> 
   <td> nms:offer<br /> </td> 
  </tr> 
  <tr> 
   <td> 再行銷效率（再行銷效果）<br /> </td> 
   <td> 再行銷效率的測量<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> 社交潛在客戶贏取歷史記錄(socialVisitorStatistics)<br /> </td> 
   <td> twitter和Facebook潛在客戶贏取的歷史，取決於Social行銷附加元件。<br /> </td> 
   <td> nms:visitor<br /> </td> 
  </tr> 
  <tr> 
   <td> 最近的主張跟蹤（最近的主張）<br /> </td> 
   <td> 即時主張追蹤<br /> </td> 
   <td> nms:positionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
