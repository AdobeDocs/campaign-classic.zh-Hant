---
product: campaign
title: 報告清單
description: 報告清單
feature: Reporting
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 2%

---

# 報告清單{#list-of-reports}

![](../../assets/common.svg)

## 傳遞報表 {#reports-on-deliveries}

Adobe Campaign提供的內置報告見下表。

有關這些報告內容的詳細資訊，請參閱 [此部分](../../reporting/using/delivery-reports.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>結構描述</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 用戶活動(recipientActivity)<br /> </td> 
   <td> 按時段分析開啟、按一下和交易記錄。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 交付吞吐量（吞吐量）<br /> </td> 
   <td> 以消息/小時和Mbit/s為單位的傳遞吞吐量圖表。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 故障和邊界（錯誤）<br /> </td> 
   <td> 按原因和域列出的邊界和非交付項。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟蹤指標(deliveryFeedback)<br /> </td> 
   <td> 用於跟蹤收件人行為的關鍵指標摘要。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟蹤指示器(mobileAppDeliveryFeedback)<br /> </td> 
   <td> 跟蹤向移動應用傳送的指示符。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 瀏覽器（瀏覽器統計資訊）<br /> </td> 
   <td> 按一下消息的收件人使用的瀏覽器的統計資訊。<br /> </td> 
   <td> xtk：無<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用到社交網路(deliveryForward)<br /> </td> 
   <td> 共用活動和郵件開啟統計資訊。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 熱點擊（滾動）<br /> </td> 
   <td> 顯示消息和疊加的按一下率。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 假設報告(deliveryHesphoit)<br /> </td> 
   <td> 顯示有關交付假設的度量摘要。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳遞統計資訊(statisticsPerDelivery)<br /> </td> 
   <td> 每個電子郵件域的統計資訊（已處理的郵件、已傳遞的郵件、硬邊界、軟邊界、按一下、取消訂閱）。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用活動統計資訊(forwardActivities)<br /> </td> 
   <td> 分析每個時間段的共用活動、開啟和訂閱。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟蹤統計資訊(trackingStatistics)<br /> </td> 
   <td> 開啟，按一下並交易費率報表。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 交貨摘要（交貨發送）<br /> </td> 
   <td> 交付指標摘要：目標、排除和發送的消息。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 交貨摘要(deliveryStatistics)<br /> </td> 
   <td> 所選交貨的匯總表：目標、排除項和發送的消息。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> 作業系統(osStatistics)<br /> </td> 
   <td> 按一下消息的收件人使用的作業系統的統計資訊。<br /> </td> 
   <td> xtk：無<br /> </td> 
  </tr> 
  <tr> 
   <td> 反應性率(deliveryFeedbackSocial)<br /> </td> 
   <td> 反應性率和反應破裂。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
  <tr> 
   <td> URL並按一下吞吐量(topUrlDelivery)<br /> </td> 
   <td> 大多數被動URL和關聯的按一下流。<br /> </td> 
   <td> nms：交付<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 市場活動報告 {#reports-on-campaigns}

有關市場活動的報告涉及 **nms：操作** 的子菜單。

Adobe Campaign提供的內置報告見下表。

有關這些報告內容的詳細資訊，請參閱 [此部分](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 用戶活動(operationRecipientActivity)<br /> </td> 
   <td> 按時段分列的開啟、按一下和事務處理的細分取決於市場活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳遞吞吐量(operationThroughput)<br /> </td> 
   <td> 以郵件/小時和Mbit/s為單位的交付吞吐量圖表取決於市場活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 市場活動費用(budgetOperationExpenses)<br /> </td> 
   <td> 詳細顯示市場活動行項目，這取決於市場活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 故障和邊界(operationErrors)<br /> </td> 
   <td> 按原因和域列出的退貨和非交付項取決於市場活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 正在查找成本行(budgetExplorerOperation)<br /> </td> 
   <td> 成本行的描述性分析取決於MRM。<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟蹤指示器(operationFeedback)<br /> </td> 
   <td> 主要跟蹤指標概述：開啟、按一下和事務處理取決於市場活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用到社交網路（操作轉發）<br /> </td> 
   <td> 共用活動和郵件開啟的統計資訊，取決於活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 假設報告（操作假設）<br /> </td> 
   <td> 顯示市場活動交付的假設度量匯總，取決於市場活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用活動統計資訊(forwardActivityOpt)<br /> </td> 
   <td> 每個時段的共用活動（開啟和訂閱）的分析取決於活動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 交貨摘要(operationStatistics)<br /> </td> 
   <td> 市場活動交貨的匯總圖表：目標、排除項和發送的消息。<br /> </td> 
  </tr> 
  <tr> 
   <td> URL並按一下吞吐量（操作TopUrlDelivery）<br /> </td> 
   <td> 大多數被動URL和關聯的點擊流都取決於市場活動。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 服務報告 {#reports-on-services}

有關服務的報告涉及 **nms：服務** 的子菜單。

Adobe Campaign提供的內置報告見下表。

有關這些報告內容的詳細資訊，請參閱相關指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 風扇收購(socialUncipationsByWebapp)<br /> </td> 
   <td> 哪些Web應用程式啟用了潛在客戶收購？ 取決於社交營銷附加項。<br /> </td> 
  </tr> 
  <tr> 
   <td> 訂閱細目(mobileAppDistribution)<br /> </td> 
   <td> 每個移動應用程式的活動訂閱的細分取決於移動應用通道載入項。<br /> </td> 
  </tr> 
  <tr> 
   <td> 訂閱跟蹤（預訂Progress）<br /> </td> 
   <td> 資訊服務訂閱的演變<br /> </td> 
  </tr> 
  <tr> 
   <td> 反應性率(socialReactionRate)<br /> </td> 
   <td> 最近交貨的反應性率是多少？ 取決於社交營銷附加項。<br /> </td> 
  </tr> 
  <tr> 
   <td> 反應性率(mobileAppRicjyctRate)<br /> </td> 
   <td> 最新交付的反應性率取決於移動應用通道附加項。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 預算報表 {#budget-reports}

Adobe Campaign提供的內置報告見下表。

有關這些報告內容的詳細資訊，請參閱 [此部分](../../campaign/using/designing-marketing-campaigns.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>結構描述</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 與方案相關的費用（預算方案費用）<br /> </td> 
   <td> 方案費用細目。<br /> </td> 
   <td> nms：程式<br /> </td> 
  </tr> 
  <tr> 
   <td> 預算演變（預算演變）<br /> </td> 
   <td> 按承付款額分列的預算費用變化。<br /> </td> 
   <td> nms：預算<br /> </td> 
  </tr> 
  <tr> 
   <td> 預算的累計演化(budgetCumulativeEvolution)<br /> </td> 
   <td> 按預算細分的累計預算費用的演變<br /> 檔案。 </td> 
   <td> nms：預算<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerBudget)<br /> </td> 
   <td> 成本行的說明性分析。<br /> </td> 
   <td> nms：預算<br /> </td> 
  </tr> 
  <tr> 
   <td> 瀏覽成本行(budgetExplorer)<br /> </td> 
   <td> 成本行的說明性分析。<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerPlan)<br /> </td> 
   <td> 成本行的說明性分析。<br /> </td> 
   <td> nms：計畫<br /> </td> 
  </tr> 
  <tr> 
   <td> 探索成本行(budgetExplorerProgram)<br /> </td> 
   <td> 成本行的說明性分析。<br /> </td> 
   <td> nms：程式<br /> </td> 
  </tr> 
  <tr> 
   <td> 預算摘要（預算）<br /> </td> 
   <td> 主要成本、支出類別和預算的快照。<br /> </td> 
   <td> nms：預算<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 模擬報告 {#reports-on-simulations}

有關模擬的報告涉及 **nms：模擬** 的子菜單。

Adobe Campaign提供的內置報告見下表。

有關這些報告內容的詳細資訊，請參閱相關指南。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 模擬排除的詳細資訊(dlvSimuLossDetail)<br /> </td> 
   <td> 所有排除原因的詳細表。<br /> </td> 
  </tr> 
  <tr> 
   <td> 按級別列出的優惠細目(offerSimulationRanking)<br /> </td> 
   <td> 模擬中按級別列出的報價的細分。<br /> </td> 
  </tr> 
  <tr> 
   <td> 模擬摘要(dlvSimuLossSummary)<br /> </td> 
   <td> 模擬卷和排除的摘要。<br /> </td> 
  </tr> 
  <tr> 
   <td> 重疊統計(dlvSimuOverlaping)<br /> </td> 
   <td> 傳遞目標重疊卷。<br /> </td> 
  </tr> 
  <tr> 
   <td> 因模擬(dlvSimuLossSimu)而排除的概要<br /> </td> 
   <td> 因模擬而排除的表。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Web應用程式報告 {#reports-on-web-applications}

有關Web應用程式的報告涉及 **nms:WebApp** 的子菜單。

Adobe Campaign提供的內置報告見下表。

有關這些報告內容的詳細資訊，請參閱 [此部分](../../web/using/about-web-applications.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 文檔(surveyDictionary)<br /> </td> 
   <td> 調查結構的說明取決於調查管理器載入項。<br /> </td> 
  </tr> 
  <tr> 
   <td> 主要(surveyProperties)<br /> </td> 
   <td> 調查屬性<br /> </td> 
  </tr> 
  <tr> 
   <td> 答復分類（調查分佈）<br /> </td> 
   <td> 對問題的答復的細目。<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他ootb報告 {#other-ootb-reports}

還提供了以下內置報告。 有關此內容的詳細資訊，請參閱有關其所關心功能的文檔。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤和內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
   <td> <strong>結構描述</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 優惠分析（優惠分析）<br /> </td> 
   <td> 根據日期和渠道提供分析，這取決於「交互」附加項。<br /> </td> 
   <td> nms：提供<br /> </td> 
  </tr> 
  <tr> 
   <td> 再營銷效率（再營銷效果）<br /> </td> 
   <td> 再營銷效率的度量<br /> </td> 
   <td> nms:web事件<br /> </td> 
  </tr> 
  <tr> 
   <td> 社會前景獲取歷史記錄(socialVisitorStatistics)<br /> </td> 
   <td> twitter和Facebook的潛在收購歷史取決於社會營銷附加功能。<br /> </td> 
   <td> nms：訪問者<br /> </td> 
  </tr> 
  <tr> 
   <td> 最近的命題跟蹤（最近的命題）<br /> </td> 
   <td> 即時命題跟蹤<br /> </td> 
   <td> nms：命題Rcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
