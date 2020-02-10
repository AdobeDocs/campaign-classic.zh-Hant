---
title: 報告清單
seo-title: 報告清單
description: 報告清單
seo-description: null
page-status-flag: never-activated
uuid: 79a914d0-7828-4fe1-b1b7-b055d4bf1f82
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: 3e593527-5580-44ea-93dc-9084d862537e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f7655cd93a7dc8ecd35cd379da350ad279cae725

---


# 報告清單{#list-of-reports}

## 交貨報告 {#reports-on-deliveries}

Adobe Campaign提供的內建報表可在下表中找到。

如需這些報表內容的詳細資訊，請參閱 [本節](../../reporting/using/delivery-reports.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>架構</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 使用者活動(recipientActivity)<br /> </td> 
   <td> 依時段劃分的開啟、點按和交易。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送總處理能力（總處理能力）<br /> </td> 
   <td> 傳送吞吐量圖表，以消息／小時和Mbit/s為單位。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 失敗與彈回數（錯誤）<br /> </td> 
   <td> 彈回數和非交付項（依原因和領域區分）。<br /> </td> 
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
   <td> 點按訊息之收件者使用之瀏覽器的統計資料。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用至社交網路(deliveryForward)<br /> </td> 
   <td> 共用活動和郵件開啟統計資訊。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 熱點點按（熱點按）<br /> </td> 
   <td> 顯示疊加的訊息和點按率。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 假設報告(deliveryHoxtions)<br /> </td> 
   <td> 顯示有關交付假設的測量摘要。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送統計資料(statisticsPerDelivery)<br /> </td> 
   <td> 每個電子郵件網域的統計資料（已處理的訊息、已傳送的訊息、硬彈回數、軟彈回數、點按、取消訂閱）。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用活動統計資料(forwardActivity)<br /> </td> 
   <td> 分析每個時段的共用活動、開啟和訂閱。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 追蹤統計資料(trackingStatistics)<br /> </td> 
   <td> 開啟、點按和交易費率報表。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送摘要(deliverySending)<br /> </td> 
   <td> 交付指標摘要：目標、排除和傳送的訊息。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送摘要(deliveryStatistics)<br /> </td> 
   <td> 選定交貨的匯總表：目標、排除和傳送的訊息。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 作業系統(osStatistics)<br /> </td> 
   <td> 點選訊息之收件者所使用之作業系統的統計資料。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 反應率(deliveryFeedbackSocial)<br /> </td> 
   <td> 輸送反應性率和反應擊穿。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> URL和按一下總處理能力(topUrlDelivery)<br /> </td> 
   <td> 最常反應的URL和關聯的點按串流。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 促銷活動的報表 {#reports-on-campaigns}

有關促銷活動的報表涉及 **nms:operation表中的資料** 。

Adobe Campaign提供的內建報表可在下表中找到。

如需這些報表內容的詳細資訊，請參閱 [本節](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 使用者活動(operationRecipientActivity)<br /> </td> 
   <td> 依時段劃分的開啟、點按和交易，視促銷活動而定。<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送總處理能力(operationThroughput)<br /> </td> 
   <td> 傳送吞吐量圖表（以電子郵件／小時和Mbit/s為單位）取決於促銷活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 促銷活動費用(budgetOperationExpenses)<br /> </td> 
   <td> 詳細顯示促銷活動明細項目，視促銷活動而定。<br /> </td> 
  </tr> 
  <tr> 
   <td> 失敗與彈回數(operationErrors)<br /> </td> 
   <td> 彈回數和非可交付項目（依原因和網域而定）取決於促銷活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerOperation)<br /> </td> 
   <td> 成本行的說明性分析取決於MRM。<br /> </td> 
  </tr> 
  <tr> 
   <td> 追蹤指標(operationFeedback)<br /> </td> 
   <td> 主要追蹤指標概述：開啟、點按和交易取決於促銷活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用至社交網路(operationForward)<br /> </td> 
   <td> 共用活動和郵件開啟統計資料，取決於促銷活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 假設報告（操作假設）<br /> </td> 
   <td> 顯示促銷活動傳送之假設測量摘要，視促銷活動而定。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用活動統計資料(forwardActivityOpt)<br /> </td> 
   <td> 依據促銷活動分析每個時段的共用活動、開啟和訂閱。<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送摘要(operationStatistics)<br /> </td> 
   <td> 促銷活動傳送的摘要圖表：目標、排除和傳送的訊息。<br /> </td> 
  </tr> 
  <tr> 
   <td> URL和按一下總處理能力(operationTopUrlDelivery)<br /> </td> 
   <td> 大多數反應式URL和關聯的點按串流都取決於促銷活動。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 服務報告 {#reports-on-services}

有關服務的報告涉及 **nms:service表中的資料** 。

Adobe Campaign提供的內建報表可在下表中找到。

如需這些報表內容的詳細資訊，請參閱相關指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 粉絲收購(socialUnbrecipationsByWebapp)<br /> </td> 
   <td> 哪些Web應用程式可讓潛在客戶獲取產品？ 視Social行銷附加元件而定。<br /> </td> 
  </tr> 
  <tr> 
   <td> 訂閱的劃分(mobileAppDistribution)<br /> </td> 
   <td> 依行動應用程式的作用中訂閱劃分，取決於行動應用程式頻道附加元件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 訂閱追蹤（訂閱進度）<br /> </td> 
   <td> 資訊服務訂閱的演變<br /> </td> 
  </tr> 
  <tr> 
   <td> 反應率(socialReactionRate)<br /> </td> 
   <td> 最新交貨的反應率是多少？ 視Social行銷附加元件而定。<br /> </td> 
  </tr> 
  <tr> 
   <td> 反應性率(mobileAppRyctimeRate)<br /> </td> 
   <td> 最新傳送的反應率取決於行動應用程式頻道附加元件。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 預算報表 {#budget-reports}

Adobe Campaign提供的內建報表可在下表中找到。

如需這些報表內容的詳細資訊，請參閱 [本節](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>架構</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 與方案有關的費用（預算方案費用）<br /> </td> 
   <td> 方案成本細目。<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 預算演變(budgetEvolution)<br /> </td> 
   <td> 預算成本依承諾層次的演變。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 預算的累計演變(budgetCumulativeEvolution)<br /> </td> 
   <td> 按預算層次劃分的累計預算成本<br /> 。 </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerBudget)<br /> </td> 
   <td> 成本行的說明性分析。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorer)<br /> </td> 
   <td> 成本行的說明性分析。<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerPlan)<br /> </td> 
   <td> 成本行的說明性分析。<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerProgram)<br /> </td> 
   <td> 成本行的說明性分析。<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 預算（預算）概要<br /> </td> 
   <td> 主要成本、費用類別和預算的快照。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 模擬報告 {#reports-on-simulations}

有關模擬的報告涉及 **nms:simulation表中的資料** 。

Adobe Campaign提供的內建報表可在下表中找到。

如需這些報表內容的詳細資訊，請參閱相關指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 模擬排除的詳細資訊(dlvSimuLossDetail)<br /> </td> 
   <td> 所有排除原因的詳細表格。<br /> </td> 
  </tr> 
  <tr> 
   <td> 依排名劃分選件(offerSimulationRanking)<br /> </td> 
   <td> 模擬中選件的劃分，依排名。<br /> </td> 
  </tr> 
  <tr> 
   <td> 模擬摘要(dlvSimuLossSummary)<br /> </td> 
   <td> 模擬卷和排除的摘要。<br /> </td> 
  </tr> 
  <tr> 
   <td> 重疊統計(dlvSimuOverplaing)<br /> </td> 
   <td> 傳送目標重疊卷。<br /> </td> 
  </tr> 
  <tr> 
   <td> 因模擬而排除的摘要(dlvSimuLossSimu)<br /> </td> 
   <td> 因模擬而排除的表格。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web應用程式報告 {#reports-on-web-applications}

有關Web應用程式的報告涉及 **nms:WebApp表中的資料** 。

Adobe Campaign提供的內建報表可在下表中找到。

如需這些報表內容的詳細資訊，請參閱 [本節](../../web/using/about-web-applications.md)。

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

也提供下列內建報表。 有關此內容的詳細資訊，請參閱檔案中有關其所關注之功能的說明。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>架構</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 選件分析(offerAnalysis)<br /> </td> 
   <td> 依據日期和渠道的選件分析，視互動附加元件而定。<br /> </td> 
   <td> nms:offer<br /> </td> 
  </tr> 
  <tr> 
   <td> 再行銷效率（再行銷效果）<br /> </td> 
   <td> 再行銷效率的衡量<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> 社交潛在客戶贏取記錄(socialVisitorStatistics)<br /> </td> 
   <td> Twitter和Facebook潛在客戶收購的歷史，取決於Social行銷附加元件。<br /> </td> 
   <td> nms:visitor<br /> </td> 
  </tr> 
  <tr> 
   <td> 最近的提案追蹤（最近的提案）<br /> </td> 
   <td> 即時提案追蹤<br /> </td> 
   <td> nms：命題Rcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

