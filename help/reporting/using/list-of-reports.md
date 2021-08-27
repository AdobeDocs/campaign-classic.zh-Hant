---
product: campaign
title: 報告清單
description: 報告清單
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 1%

---

# 報告清單{#list-of-reports}

![](../../assets/common.svg)

## 傳遞報表 {#reports-on-deliveries}

Adobe Campaign提供的內建報表位於下表。

如需這些報表內容的詳細資訊，請參閱[此區段](../../reporting/using/delivery-reports.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>結構</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 使用者活動(recipientActivity)<br /> </td> 
   <td> 按時段劃分的開啟、點按和交易。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送吞吐量（吞吐量）<br /> </td> 
   <td> 傳送吞吐量圖表，以消息/小時和Mbit/s.<br />表示 </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 失敗和退信（錯誤）<br /> </td> 
   <td> 按原因和域列出的跳出和無法交付項。<br /> </td> 
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
   <td> 按一下訊息的收件者所使用的瀏覽器統計資料。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 分享至社交網路(deliveryForward)<br /> </td> 
   <td> 共用活動和郵件開啟統計資訊。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 熱點點按（霍特爾）<br /> </td> 
   <td> 顯示疊加的消息和點按率。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 假設報表(deliveryHexposition)<br /> </td> 
   <td> 顯示有關傳送假設的度量摘要。<br /> </td> 
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
   <td> 開啟，按一下，然後按交易率報表。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送摘要(deliverySending)<br /> </td> 
   <td> 交付指標摘要：target、排除和已傳送的訊息。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送摘要(deliveryStatistics)<br /> </td> 
   <td> 所選傳送的摘要表格：已發送目標、排除和消息。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> 作業系統(osStatistics)<br /> </td> 
   <td> 按一下訊息的收件者所使用的作業系統統計資料。<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> 反應率(deliveryFeedbackSocial)<br /> </td> 
   <td> 投遞反應率和反應分解。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> URL和點按輸送量(topUrlDelivery)<br /> </td> 
   <td> 最多反應URL和關聯的點按流。<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 行銷活動報表 {#reports-on-campaigns}

有關促銷活動的報表與&#x200B;**nms:operation**&#x200B;表格中的資料有關。

Adobe Campaign提供的內建報表位於下表。

如需這些報表內容的詳細資訊，請參閱[此區段](../../campaign/using/designing-marketing-campaigns.md)。

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
   <td> 傳送吞吐量(operationThroughput)<br /> </td> 
   <td> 以郵件/小時和Mbit/s表示的傳送吞吐量圖表取決於促銷活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 促銷活動費用(budgetOperationExpenses)<br /> </td> 
   <td> 詳細顯示促銷活動明細項目，取決於促銷活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 失敗和退信(operationErrors)<br /> </td> 
   <td> 退信和不可交付項（按原因和域）取決於Campaign。<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerOperation)<br /> </td> 
   <td> 成本行的描述性分析，取決於MRM.<br /> </td> 
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
   <td> 顯示促銷活動傳送的假設測量摘要，視促銷活動而定。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用活動統計資料(forwardActivityOpt)<br /> </td> 
   <td> 依據Campaign分析每個時段的共用活動、開啟次數和訂閱次數。<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送摘要(operationStatistics)<br /> </td> 
   <td> 促銷活動傳送的摘要圖表：已發送目標、排除和消息。<br /> </td> 
  </tr> 
  <tr> 
   <td> URL和點按輸送量(operationTopUrlDelivery)<br /> </td> 
   <td> 大部分的反應URL和相關的點按資料流取決於Campaign。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 服務報告 {#reports-on-services}

服務報告與&#x200B;**nms:service**&#x200B;表中的資料有關。

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
   <td> 訂閱的劃分(mobileAppDistribution)<br /> </td> 
   <td> 每個行動應用程式之作用中訂閱的劃分取決於行動應用程式頻道附加元件。<br /> </td> 
  </tr> 
  <tr> 
   <td> 訂閱追蹤(subscriptionsProgress)<br /> </td> 
   <td> 資訊服務訂閱的演變<br /> </td> 
  </tr> 
  <tr> 
   <td> 反應性率(socialReactionRate)<br /> </td> 
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

如需這些報表內容的詳細資訊，請參閱[此區段](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>結構</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 與方案(budgetProgramCost)相關的費用<br /> </td> 
   <td> 方案費用細目。<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> 預算演化(budgetEvolution)<br /> </td> 
   <td> 按承諾水準開列的預算費用的演變。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> 預算的累積演化(budgetCumulativeEvolution)<br /> </td> 
   <td> 按預算<br />部門級別劃分的累積預算費用的演變。 </td> 
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
   <td> 主要成本、費用類別和預算的快照。<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 模擬報告 {#reports-on-simulations}

模擬報告涉及&#x200B;**nms:simulation**&#x200B;表中的資料。

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
   <td> 排除所有原因的詳細表。<br /> </td> 
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
   <td> 重疊統計資訊(dlvSimuOverplaing)<br /> </td> 
   <td> 傳遞目標重疊卷。<br /> </td> 
  </tr> 
  <tr> 
   <td> 因模擬(dlvSimuLossSimu)而排除的摘要<br /> </td> 
   <td> 因模擬而排除的表。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 網路應用程式報告 {#reports-on-web-applications}

有關Web應用程式的報告涉及&#x200B;**nms:WebApp**&#x200B;表中的資料。

Adobe Campaign提供的內建報表位於下表。

如需這些報表內容的詳細資訊，請參閱[此區段](../../web/using/about-web-applications.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 檔案(surveyDictionary)<br /> </td> 
   <td> 調查結構的說明，取決於「調查管理員」附加元件。<br /> </td> 
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
   <td> <strong>結構</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 選件分析(offerAnalysis)<br /> </td> 
   <td> 根據日期和管道進行選件分析，取決於「互動」附加元件。<br /> </td> 
   <td> nms:offer<br /> </td> 
  </tr> 
  <tr> 
   <td> 再行銷效率（再行銷Effect）<br /> </td> 
   <td> 再行銷效率的測量<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> 社交潛在客戶贏取的歷史記錄(socialVisitorStatistics)<br /> </td> 
   <td> twitter和Facebook潛在客戶贏取的記錄，取決於Social行銷附加元件。<br /> </td> 
   <td> nms:visitor<br /> </td> 
  </tr> 
  <tr> 
   <td> 最近的命題跟蹤(recentPropositions)<br /> </td> 
   <td> 即時主張追蹤<br /> </td> 
   <td> nms:postitionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
