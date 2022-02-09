---
product: campaign
title: 指標計算
description: 指標計算
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '2972'
ht-degree: 2%

---

# 指標計算 {#indicator-calculation}

![](../../assets/common.svg)

## 用戶活動 {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 開啟次數<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主鍵@totalClicks等於1的所有總和。<br /> </td> 
   <td> sum(Iif([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 按一下<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL類型等於「電子郵件按一下」的@totalClicks總和。<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易記錄<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL類型等於「事@totalClicks」的所有URL的總和。<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

此報告以 **[!UICONTROL Consolidated tracking]** 表(nms:trackingStats)。 此聚合表用於顯示報表時的效能原因，代替 **[!UICONTROL Recipient tracking logs]** 表(nms:trackingLogRcp)，並且它不是即時計算的。 在檢索跟蹤日誌後幾分鐘內生成表。 如果指標是最新的，則結果與指標相同 **跟蹤指標** 報告。 @totalclicks指示器表示在5分鐘內的點擊總數。

## 傳遞失敗和退回次數 {#non-deliverables-and-bounces-1}

**按錯誤類型分析**

此報告以 **[!UICONTROL Delivery and tracking statistics]** 表(nms:deliveryLogStats)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已處理郵件總數<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> 狀態等於「就緒」、「已發送」或「失敗」的消息總和。<br /> </td> 
   <td> @prepared + @error @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 用戶未知<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 狀態為「失敗」且原因為「用戶未知」的所有消息的計數。 <br /> </td> 
   <td> 計數(@status=2和msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> 無法訪問 <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 狀態為「失敗」且原因為「無法訪問」的所有消息的計數。 <br /> </td> 
   <td> 計數(@status=2和msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 已拒絕<br /> </td> 
   <td> @refused<br /> </td> 
   <td> 狀態為「失敗」且原因為「已拒絕」的所有消息的計數。 <br /> </td> 
   <td> 計數(@status=2和msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效域<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 狀態為「失敗」且原因為「無效域」的所有消息的計數。 <br /> </td> 
   <td> 計數(@status=2和msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> 帳戶已禁用<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 狀態為「失敗」且原因為「帳戶已禁用」的所有消息的計數。<br /> </td> 
   <td> 計數(@status=2和msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件箱已滿<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> 狀態為「失敗」且原因為「收件箱已滿」的所有郵件的計數。 <br /> </td> 
   <td> 計數(@status=2和msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤<br /> </td> 
   <td> @value<br /> </td> 
   <td> 此類錯誤的失敗消息數。<br /> </td> 
   <td> 計數(@status=2和msg/@failureReason="錯誤類型的值")<br /> </td> 
  </tr> 
  <tr> 
   <td> 貢獻<br /> </td> 
   <td> -<br /> </td> 
   <td> 與錯誤消息總數相比，此類型的錯誤百分比。<br /> </td> 
   <td> 百分比(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 細分<br /> </td> 
   <td> -<br /> </td> 
   <td> 與已處理郵件總數相比，此類型的錯誤百分比。<br /> </td> 
   <td> 百分比(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**按域細分**

報告的第二部分按Internet域（而不是錯誤類型）詳細列出故障消息的細目。 連結到的公式 **錯誤** 指示符(@value):Count(@status=2和@domain=&quot;域名的值&quot;)，即此域狀態失敗的所有消息的計數。

## 瀏覽器 {#browsers-1}

此報告以 **[!UICONTROL Internet Browser Statistics]** 表(nms:userAgentsStats)。

**全局統計**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 訪問者<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> 此瀏覽器中按一下至少一次傳遞的目標收件人總數。<br /> </td> 
   <td> 總和(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 頁面視圖<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> 使用此瀏覽器對所有交貨在交貨連結上按一下的總次數。<br /> </td> 
   <td> 總和(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此瀏覽器的訪問者百分比與訪問者總數之比。<br /> </td> 
   <td> 百分比(@totalVisitors，總計(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**每個瀏覽器的統計資訊**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 使用此瀏覽器的每日訪問者數量與訪問次數最多的當天測量訪問者數量的百分比。<br /> </td> 
   <td> 百分比(總和(@visitors)，最大值(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局比率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的訪問者百分比與使用所有瀏覽器的訪問者總數之比。<br /> </td> 
   <td> 百分比(@totalVisitors、@globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相對權重<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的訪問者百分比與使用此瀏覽器的訪問者總數之比。<br /> </td> 
   <td> 百分比(@totalVisitors，總計(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 共用到社交網路 {#sharing-to-social-networks-1}

此報告以 **[!UICONTROL Delivery]** （nms：交付）, **[!UICONTROL Consolidated tracking]** (nms:trackingStats)，和 **[!UICONTROL Web tracking]** (nms:webTrackingLog)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 要傳遞的郵件數<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 在傳遞分析期間處理的郵件總數。<br /> </td> 
   <td> sum([屬性/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功交貨的數量<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功處理的消息數 <br /> </td> 
   <td> sum([指示符/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL類別等於「email」@totalClicks的所有總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL類別等於「facebook」的所有@totalClicks的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL類別等於「twitter」的所有@totalClicks的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL類別等於「delicious」@totalClicks的所有總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicios',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 迪格<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL類別等於「digg」的所@totalClicks總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL類別等於「google」的@totalClicks總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 林克丁<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL類別等於「linkedin」的所@totalClicks總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**股份**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 股份數<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 此社交網路上共用的消息總數。<br /> </td> 
   <td> Sum(iIf([url/@category]="社交網路類型的值",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 細分<br /> </td> 
   <td> @percent<br /> </td> 
   <td> 此社交網路上的股份數與股份總數之比百分比。<br /> </td> 
   <td> 百分比(@forward，總計(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用率<br /> </td> 
   <td> @rate<br /> </td> 
   <td> 與要傳遞的消息數相比，此網路上的共用數。<br /> </td> 
   <td> @forward / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**開啟的郵件**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 開啟的數 <br /> </td> 
   <td> @open<br /> </td> 
   <td> Web跟蹤表中的跟蹤行總數。<br /> </td> 
   <td> 計數<br /> </td> 
  </tr> 
  <tr> 
   <td> 細分<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 此社交網路上的開啟次數與開啟總數之比的百分比。<br /> </td> 
   <td> 百分比(@open，總計(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟率<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 與要傳遞的消息總數相比，此社交網路上的開啟數。<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 關於共用活動的統計 {#statistics-on-sharing-activities-1}

此報告以 **[!UICONTROL Delivery]** （nms：交付）, **[!UICONTROL Consolidated tracking]** (nms:trackingStats)，和 **[!UICONTROL Web tracking]** (nms:webTrackingLog)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 新聯繫人<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> 連結到收件人的訪問者數。<br /> </td> 
   <td> 公式：計數(@id)<br /> 篩選器：@recipientid != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟次數<br /> </td> 
   <td> @opened<br /> </td> 
   <td> URL類型等於「Open」的@ids全部計數。<br /> </td> 
   <td> count(Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 股份<br /> </td> 
   <td> @shared<br /> </td> 
   <td> 包含在「email」、「facebook」、「twitter」、「delicious」、「digg」、「google」、「linkedin」中的URL類別<br /> URL類別等於「email」、「facebook」、「twitter」、「delicious」、「digg」、「google」或「linkedin」的@totalClicks全部計數。<br /> </td> 
   <td> count(Iif([url/@category] IN(email', 'facebook', 'twitter', 'delicios', 'digg', 'google', 'linkedin'), @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 作業系統 {#operating-systems-1}

此報告以 **[!UICONTROL Internet Browser Statistics]** 表(nms:userAgentsStats)。

**全局統計**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 訪問者<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> 在遞送中按一下至少一次的作業系統目標收件人總數的每日平均值。<br /> </td> 
   <td> 總和(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 已查看的頁面<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> 每個作業系統上所有交貨的交貨連結的每日平均點擊次數。<br /> </td> 
   <td> 總和(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 按作業系統列出的訪問者數與訪問者總數之比。<br /> </td> 
   <td> 百分比(@totalVisitors，總計(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**每個作業系統的統計資訊**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 此作業系統中每天訪問者數量與每天訪問次數最多的訪問者數量相比的百分比。<br /> </td> 
   <td> 百分比(總和(@visitors)，最大(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局比率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每個版本的訪問者百分比與所有作業系統上訪問者總數之比。<br /> </td> 
   <td> 百分比(@totalVisitors、@globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相對速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每個版本的訪問者百分比與使用此作業系統的訪問者總數之比。<br /> </td> 
   <td> 百分比(@totalVisitors，總計(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 訂閱跟蹤 {#subscription-tracking-1}

此報告以 **[!UICONTROL Services]** 表(nms:service)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已註冊<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> 前一天的註冊人員數。<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(),(-1), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 訂閱<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> 上一天的訂閱計數(@action = 1)。<br /> </td> 
   <td> sum(Iif(@action = 1和@date &gt; addDays(getDate(),(-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 取消訂閱<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> 前一天未訂閱的計數（操作= 0）。<br /> </td> 
   <td> sum(Iif(@action = 0和@date &gt; addDays(getDate(),(-1), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 進化<br /> </td> 
   <td> -<br /> </td> 
   <td> 訂閱數減去未訂閱數。 該速率是按訂戶總數計算的。<br /> </td> 
   <td> Iif(number(@_subscription)&gt; number(@_unsubscription), '+', ")+格式(@_subscription - @_unsubscription, 'number', '# ##0')+ Iif(@_subscriber&gt;0,'(' + format(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.00')+ '%',")<br /> </td> 
  </tr> 
  <tr> 
   <td> 忠誠<br /> </td> 
   <td> -<br /> </td> 
   <td> 相關期間的訂戶忠誠度。<br /> </td> 
   <td> 1%(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 追蹤指標 {#tracking-indicators-1}

此報告以 **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats)和 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 要傳遞的消息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 目標分析後broadLogs的數量計數。<br /> </td> 
   <td> sum([屬性/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> 「種子地址」欄位等於「否」且狀態等於「服務提供商考慮」、「發送」或「在移動設備上接收」的郵件計數。<br /> </td> 
   <td> sum([指示符/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 對已到達的人口開啟明顯<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> 根據html格式電子郵件的不同開啟次數，推斷所有電子郵件的不同開啟次數。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@recipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 已到達人口的開戶總數<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> 根據以html格式開啟的電子郵件總數推斷所有電子郵件的開啟總數。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@totalRecipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 按一下取消訂閱連結<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL類別等於「Opt-out」的@ids全部計數。<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 按一下指向鏡像頁面的連結<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> URL類別等於「鏡像頁」的@ids全部計數。<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 前向估計<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 在電子郵件中按一下至少一次的不同人數與不同收件人的數目之間的差異。<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> 發送<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> 「種子地址」欄位等於「否」且狀態等於「接收者考慮」、「發送」或「移動時接收」的郵件計數。<br /> </td> 
   <td> sum([指示符/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 投訴<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> 狀態為「失敗」且原因為「denylist上的地址」的郵件計數。<br /> </td> 
   <td> 計數(@status=2和msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟次數<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 所有跟蹤日誌@broadLog所有ID的計數。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 按一下<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL類型等於「電子郵件按一下」的@broadLog-id的不同計數。 <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 原反應性<br /> </td> 
   <td> -<br /> </td> 
   <td> 在傳遞中按一下至少一次的收件人數與開啟傳遞至少一次的收件人數的百分比。<br /> </td> 
   <td> 百分比(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 對人口的不同點擊<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL類別等於「E-mail click」的所有@source-id的計數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 累計點擊量<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> URL類別等於「電子郵件按一下」的@ids全部計數。<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件人按一下<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL類型等於「電子郵件按一下」的@broadLog-id的非重複計數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 估計反應性<br /> </td> 
   <td> -<br /> </td> 
   <td> 在遞送中按一下至少一次的收件人數與至少開啟遞送一次的收件人的估計數之比。<br /> </td> 
   <td> 百分比(@recipientClick,@estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> 訪問的頁面<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL類型等於「Web」或「事務」的所@ids計數。<br /> </td> 
   <td> count(Iif([url/@type]=4或[url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易記錄<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL類型等於@ids「事務處理」的所有計數。<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 總額<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL類型等於"Transaction"的WebTrackingLog/@amounts總和。 <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 平均交易記錄金額<br /> </td> 
   <td> -<br /> </td> 
   <td> 總金額與交易記錄數之比。<br /> </td> 
   <td> div(@amount、@transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 項目<br /> </td> 
   <td> @article<br /> </td> 
   <td> URL類型等於"Transaction"的WebTrackingLog/@articles的總和。<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 每個交易記錄的平均物料數<br /> </td> 
   <td> -<br /> </td> 
   <td> 項目數與交易記錄數之比。<br /> </td> 
   <td> div(@article、@transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 每封郵件的平均金額<br /> </td> 
   <td> -<br /> </td> 
   <td> 總金額與要傳遞的消息數之比。<br /> </td> 
   <td> div(@amount、@toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL類別等於「email」的@totalClicks總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL類別等於「@totalClicks」的所有URL的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL類別等於「@totalClicks」的所有URL的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL類別等於「delicious」的@totalClicks總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicios',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 迪格<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL類別等於「digg」的@totalClicks總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL類別等於「google」的@totalClicks總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 林克丁<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL類別等於「linkedin」的@totalClicks總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL 和點擊流量 {#urls-and-click-streams-1}

此報告以 **[!UICONTROL Delivery]** 表(nms:delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 反應性<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> 在遞送中至少按一下一次的目標收件人數與至少開啟遞送一次的目標收件人的估計數之比。<br /> </td> 
   <td> 百分比([指標/@recipientClick],[指標/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> 不同的點擊<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 在傳遞中按一下至少一次的不同人數與成功傳遞的消息數之比。<br /> </td> 
   <td> 百分比([指標/@personClick],[指標/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 累計點擊量<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 目標收件人點擊總數與成功傳遞的郵件數之比。<br /> </td> 
   <td> 百分比([指標/@totalRecipientClick],[指標/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 按一下<br /> </td> 
   <td> @_click<br /> </td> 
   <td> URL主鍵不@totalClicks於1的所有計數<br /> </td> 
   <td> count(Iif([@url-id]] != 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 按一下(%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 與累計點擊總數相比的點擊次數百分比。<br /> </td> 
   <td> 百分比(@_click、@_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳遞摘要 {#delivery-summary-1}

此報告以 **[!UICONTROL Delivery]** 表(nms:delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 初始人口<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 傳遞目標的收件人總數。<br /> </td> 
   <td> sum([屬性/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 規則拒絕的郵件<br /> </td> 
   <td> @reject<br /> </td> 
   <td> 在分析過程中根據類型規則忽略的地址數：未指定地址、隔離地址、拒絕清單等。<br /> </td> 
   <td> sum([屬性/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> 要傳遞的消息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 傳遞分析後要傳遞的郵件總數。<br /> </td> 
   <td> sum([屬性/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功處理的郵件數。<br /> </td> 
   <td> sum([指示符/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤<br /> </td> 
   <td> @error<br /> </td> 
   <td> 在交貨和自動彈出處理期間累積的錯誤總數。<br /> </td> 
   <td> sum([指示符/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> 新隔離<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 傳遞失敗後隔離的地址數（用戶未知，無效域）。<br /> </td> 
   <td> sum([指示符/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 熱點點擊 {#hot-clicks-1}

此報告基於交付（nms：交付）和 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)表。

此報表顯示每個連結上的HTML百分比（和/或文本）。 個性化塊未訂閱連結和鏡像頁面連結在累計點擊總數中被考慮在內，但不會顯示在報告中。

## 跟蹤統計 {#tracking-statistics-1}

此報告以 **[!UICONTROL Delivery]** 表(nms:delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 交易記錄<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL類型等於「事務」的@totalClicks總和。<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 按一下<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL類型等於「電子郵件按一下」的@totalClicks總和。<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主鍵@totalClicks等於1的所有總和。<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳遞統計 {#delivery-statistics-1}

此報告以 **[!UICONTROL Delivery and tracking statistics]** 表(nms:deliveryLogStats)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已處理電子郵件<br /> </td> 
   <td> @processed<br /> </td> 
   <td> 狀態為「就緒」、「已發送」或「失敗」的郵件總數。<br /> </td> 
   <td> @prepared + @error @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 已交付<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功處理的消息數。<br /> </td> 
   <td> 指標/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> 硬邊界<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「用戶未知」的郵件總數。<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> 軟邊界<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「unreachable」、「inbox full」、「invalid domain」、「disabled account」、「not connected」或「rejected」的所有郵件總數<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟次數<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 跟蹤日誌中@broadLog-id的總數。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 按一下<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL類別等於「電子郵件按一下」的@source-id總數。 <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> 取消訂閱<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL類別等於「Opt-out」的@ids總數。<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 開啟的細目 {#breakdown-of-opens-1}

此報告基於 **交貨** （nms：交付）和 **跟蹤日誌** (nms:trackingLogRcp)表。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 開啟次數<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> URL主鍵等於1（開啟）的@id總和。 <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他指標 {#other-indicators}

的 **已發送** 指示符(@sent)，通過 **交貨（nms：交貨）>指示器** 節點對應於發送到服務提供商的SMS總數。 此指示器僅用於SMS遞送，不得用於其他類型的遞送(不要與 **@success** 和 **@processed** 指標)。

## 指示器同步 {#indicator-synchronization}

如果您遇到某些指標的不同步或不一致，請在Adobe Campaign瀏覽器中選擇相關的傳遞，按一下右鍵並選擇 **[!UICONTROL Action>Recompute delivery and tracking indicators]**。 按一下 **[!UICONTROL Next]**，然後按一下 **[!UICONTROL Finish]**。

![](assets/s_ncs_user_recalculate_indicators.png)

## 跟蹤開啟 {#tracking-opens-}

為了Adobe Campaign檢測郵件開啟，收件人必須下載電子郵件中的影像。 HTML和多部件/替代電子郵件包含0像素影像，使您能夠檢測已開啟的郵件。 由於文本格式的消息不包含任何影像，因此無法檢測它們是否已開啟。 基於消息開啟計算的值總是由於連結到影像顯示的誤差範圍而估計。

## 目標人員/收件人 {#targeted-persons---recipients}

在一些報告中，Adobe Campaign區分了目標人和目標接收人。

目標收件人是將傳遞發送給的所有收件人。

人數包括目標收件人加上轉發電子郵件的所有人。 每次在新瀏覽器中開啟或按一下（消息尚未在中開啟）時，都會向統計資訊中添加另一個人。

例如，如果您在工作時收到一封電子郵件(由Adobe Campaign發送)並開啟或按一下，則您將被視為目標收件人（即收件人=1，人員=1）。 如果您將此電子郵件轉發給兩個朋友，則目標收件人的數量仍為1，而人數則為3。 值3與在新瀏覽器中開啟/按一下的每個值重合。
