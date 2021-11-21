---
product: campaign
title: 指標計算
description: 指標計算
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2972'
ht-degree: 2%

---

# 指標計算 {#indicator-calculation}

![](../../assets/common.svg)

## 使用者活動 {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 開啟次數<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主鍵@totalClicks為1的所有加總。<br /> </td> 
   <td> sum(Iif([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL類型等於「電@totalClicks點按」的所有加總。<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL類型等於「交@totalClicks」的所有總和。<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

此報告以 **[!UICONTROL Consolidated tracking]** 表格(nms:trackingStats)。 此匯總表用於顯示報表時的效能原因，取代 **[!UICONTROL Recipient tracking logs]** 表(nms:trackingLogRcp)，且不會即時計算。 系統會在擷取追蹤記錄數後幾分鐘產生表格。 如果指標是最新的，則結果與指標的結果相同 **追蹤指標** 報表。 @totalclicks指示器表示在5分鐘期間的點按總數。

## 傳遞失敗和退回次數 {#non-deliverables-and-bounces-1}

**按錯誤類型劃分**

此報告以 **[!UICONTROL Delivery and tracking statistics]** 表格(nms:deliveryLogStats)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已處理郵件的總數<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> 狀態等於「就緒」、「已傳送」或「失敗」的訊息總和。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 用戶未知<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「使用者未知」的所有訊息計數。 <br /> </td> 
   <td> 計數(@status=2,msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> 無法聯繫 <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「無法聯繫」的所有郵件的計數。 <br /> </td> 
   <td> 計數(@status=2和msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 已拒絕<br /> </td> 
   <td> @refused<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「已拒絕」的所有訊息計數。 <br /> </td> 
   <td> 計數(@status=2,msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效域<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「無效域」的所有郵件的計數。 <br /> </td> 
   <td> 計數(@status=2和msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> 帳戶已停用<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「帳戶已停用」的所有訊息計數。<br /> </td> 
   <td> 計數(@status=2和msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件匣已滿<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「收件匣已滿」的所有郵件計數。 <br /> </td> 
   <td> 計數(@status=2和msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤<br /> </td> 
   <td> @value<br /> </td> 
   <td> 此類錯誤的失敗消息數。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason="錯誤類型的值")<br /> </td> 
  </tr> 
  <tr> 
   <td> 貢獻<br /> </td> 
   <td> -<br /> </td> 
   <td> 此類型的錯誤百分比與錯誤訊息總數之比。<br /> </td> 
   <td> 百分比(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 劃分<br /> </td> 
   <td> -<br /> </td> 
   <td> 此類型錯誤與已處理訊息總數的百分比。<br /> </td> 
   <td> 百分比(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**依網域劃分**

報告的第二部分詳細說明了按Internet域而非錯誤類型劃分的失敗消息。 連結至的公式 **錯誤** 指標(@value)在此情況下是：Count(@status=2 and @domain=&quot;域名的值&quot;)，即此域狀態為失敗的所有消息的計數。

## 瀏覽器 {#browsers-1}

此報告以 **[!UICONTROL Internet Browser Statistics]** 表(nms:userAgentsStats)。

**全局統計**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 訪客<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> 此瀏覽器中至少點擊一次傳遞的目標收件者總數。<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 頁面檢視<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> 使用此瀏覽器進行所有傳送的傳送連結點按總次數。<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此瀏覽器的訪客百分比與訪客總數之比。<br /> </td> 
   <td> 百分比(@totalVisitors，加總(@totalVisitors) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**每個瀏覽器的統計資訊**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 使用此瀏覽器的每日訪客數與在造訪次數最多的當天測量的訪客數量百分比。<br /> </td> 
   <td> 百分比(總和(@visitors)，最大(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 全域比率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的訪客百分比與使用所有瀏覽器的訪客總數。<br /> </td> 
   <td> 百分比(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相對權數<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的訪客百分比與使用此瀏覽器的訪客總數。<br /> </td> 
   <td> 百分比(@totalVisitors，加總(@totalVisitors) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 分享至社交網路 {#sharing-to-social-networks-1}

此報告以 **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats)和 **[!UICONTROL Web tracking]** (nms:webTrackingLog)表格。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 要傳送的訊息數<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 傳送分析期間處理的訊息總數。<br /> </td> 
   <td> sum([properties/@totalTarget]<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功傳送的次數<br /> </td> 
   <td> @success<br /> </td> 
   <td> 已成功處理的郵件數 <br /> </td> 
   <td> sum([indicators/@success]<br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL類別等@totalClicks於「電子郵件」的所有總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL類@totalClicks等於「facebook」的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL類@totalClicks等於「twitter」的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL類@totalClicks等於「可口」的所有總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL類別等@totalClicks於「digg」的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL類別等@totalClicks於「google」的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 林克丁<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL類別等@totalClicks於「linkedin」的所有總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**共用**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 分享次數<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 此社交網路上共用的訊息總數。<br /> </td> 
   <td> Sum(iIf([url/@category]="社交網路類型的值",@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 劃分<br /> </td> 
   <td> @percent<br /> </td> 
   <td> 此社交網路上分享次數與分享總數的百分比。<br /> </td> 
   <td> 百分比(@forward，加總(@forward)<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用率<br /> </td> 
   <td> @rate<br /> </td> 
   <td> 與要傳送的報文數相比，此網路上的共用數。<br /> </td> 
   <td> @forward / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

**開啟的郵件**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 開啟次數 <br /> </td> 
   <td> @open<br /> </td> 
   <td> Web追蹤表格中的追蹤行總數。<br /> </td> 
   <td> 計數<br /> </td> 
  </tr> 
  <tr> 
   <td> 劃分<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 此社交網路上開啟次數與開啟總數的百分比。<br /> </td> 
   <td> 百分比(@open，加總(@open)<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟率<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 此社交網路上的開啟次數與要傳送的訊息總數比較。<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 共用活動統計 {#statistics-on-sharing-activities-1}

此報告以 **[!UICONTROL Delivery]** (nms:delivery), **[!UICONTROL Consolidated tracking]** (nms:trackingStats)和 **[!UICONTROL Web tracking]** (nms:webTrackingLog)表格。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 新聯繫人<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> 連結至收件者的訪客數。<br /> </td> 
   <td> 公式：count(@id)<br /> 篩選：@recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟次數<br /> </td> 
   <td> @opened<br /> </td> 
   <td> URL類型等@ids於「開啟」的所有計數。<br /> </td> 
   <td> count(Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用<br /> </td> 
   <td> @shared<br /> </td> 
   <td> 包含在「電子郵件」、「facebook」、「twitter」、「可口」、「digg」、「google」、「linkedin」中的URL類別<br /> URL類別等於「電@totalClicks」、「facebook」、「twitter」、「可口」、「digg」、「google」或「linkedin」時，計算所有的URL。<br /> </td> 
   <td> count(Iif([url/@category] IN(email' 、 'facebook' 、 'twitter' 、 'delicious' 、 'digg' 、 'google' 、 'linkedin')、 @totalClicks、 0)<br /> </td> 
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
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 訪客<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> 作業系統鎖定的收件者總數的每日平均值，只要點進傳遞至少一次。<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 已檢視的頁面<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> 所有傳送中每個作業系統的傳送連結點按總次數的每日平均值。<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 依作業系統劃分的訪客數與訪客總數。<br /> </td> 
   <td> 百分比(@totalVisitors，加總(@totalVisitors)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**每個作業系統的統計資訊**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 此作業系統上每天的訪客數量與在造訪次數最多的當天測量的訪客數量百分比。<br /> </td> 
   <td> 百分比(總和(@visitors)，最大(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 全域比率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每個版本的訪客百分比，與所有作業系統上的訪客總數相比。<br /> </td> 
   <td> 百分比(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相對速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每個版本的訪客數與使用此作業系統的訪客總數之比百分比。<br /> </td> 
   <td> 百分比(@totalVisitors，加總(@totalVisitors)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 訂閱追蹤 {#subscription-tracking-1}

此報告以 **[!UICONTROL Services]** 表(nms:service)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已註冊<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> 前一天的註冊人數。<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(),(-1), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 訂閱<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> 前一天的訂閱計數(@action = 1)。<br /> </td> 
   <td> sum(Iif(@action = 1 and @date &gt; addDays(getDate(),(-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 取消訂閱<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> 前一天的取消訂閱計數（動作= 0）。<br /> </td> 
   <td> sum(Iif(@action = 0和@date &gt; addDays(getDate(),(-1)), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 進化<br /> </td> 
   <td> -<br /> </td> 
   <td> 訂閱數減去取消訂閱數。 比率是根據訂閱者總數計算。<br /> </td> 
   <td> Iif(數字(@_subscription)&gt;數字(@_unsubscription), '+', ")+格式(@_subscription - @_unsubscription, 'number', '# ##0')+ Iif(@_subscriber&gt;0,'(' + format(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.00')+ '%',')<br /> </td> 
  </tr> 
  <tr> 
   <td> 忠誠度<br /> </td> 
   <td> -<br /> </td> 
   <td> 相關期間的訂閱者忠誠度。<br /> </td> 
   <td> 1-percent(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 追蹤指標 {#tracking-indicators-1}

此報告以 **[!UICONTROL Delivery and tracking statistics]** (nms:deliveryLogStats)和 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)表格。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 要傳送的訊息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 目標分析後broadLogs的數量計數。<br /> </td> 
   <td> sum([properties/@toDeliver]<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> 「種子地址」欄位等於「否」且狀態等於「服務提供者已考慮」、「已傳送」或「行動裝置上已接收」的訊息計數。<br /> </td> 
   <td> sum([indicators/@success]<br /> </td> 
  </tr> 
  <tr> 
   <td> 達到的母體上不同開啟<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> 根據html格式電子郵件的不同開啟次數，外推所有電子郵件的不同開啟次數。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@recipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 達到的人口開啟總數<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> 根據html格式的電子郵件開啟總數外推所有電子郵件的開啟總數。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@totalRecipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按取消訂閱連結<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL類@ids等於「選擇退出」的所有計數。<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 按一下鏡像頁面的連結<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> URL類@ids等於「鏡像頁面」時的所有計數。<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 轉發估計<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 不重複訪客的數量與至少按一下電子郵件一次的不重複收件者數量之間的差異。<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> 「種子地址」欄位等於「否」且狀態等於「收件者已考慮」、「已傳送」或「在行動裝置上已接收」的訊息計數。<br /> </td> 
   <td> sum([indicators/@success]<br /> </td> 
  </tr> 
  <tr> 
   <td> 投訴<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「封鎖清單上的地址」的訊息計數。<br /> </td> 
   <td> 計數(@status=2,msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟次數<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 所有追@broadLog-ids記錄檔中的所有計數。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL類型等於「電子郵件@broadLog-ids」的不重複計數。 <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 原始反應性<br /> </td> 
   <td> -<br /> </td> 
   <td> 至少按一次傳遞的收件者人數與至少開啟一次傳遞的收件者人數百分比。<br /> </td> 
   <td> 百分比(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 達到母體的不重複點按<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL類別等@source-ids於「電子郵件點按」的所有計數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 累積點按次數<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> URL類別等於@ids「電子郵件點按」時的所有計數。<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件者點按次數<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL類型等於「電子郵件點按」@broadLog-ids的不同計數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 估計的反應性<br /> </td> 
   <td> -<br /> </td> 
   <td> 點按至少一次傳遞的收件者人數與開啟傳遞至少一次的收件者預估人數之比。<br /> </td> 
   <td> 百分比(@recipientClick,@estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> 已瀏覽頁面<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL類型等@ids於「Web」或「交易」的所有計數。<br /> </td> 
   <td> count(Iif([url/@type]=4或[url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL類型等@ids於「交易」的所有計數。<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 總金額<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL類型等於「交易」的webTrackingLog/@amounts總和。 <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 平均交易記錄金額<br /> </td> 
   <td> -<br /> </td> 
   <td> 總金額與交易數的比率。<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 項目<br /> </td> 
   <td> @article<br /> </td> 
   <td> URL類型等於「交易」的webTrackingLog/@articles總和。<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 每筆交易的平均項目數<br /> </td> 
   <td> -<br /> </td> 
   <td> 項目數與交易數的比率。<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 每條郵件的平均數量<br /> </td> 
   <td> -<br /> </td> 
   <td> 總量與要傳送的報文數量之比。<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL類別等於「電@totalClicks」的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL類@totalClicks等於"facebook"的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL類@totalClicks等於"twitter"的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL類別等於「可@totalClicks性」的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL類@totalClicks等於「digg」的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL類別等@totalClicks於「google」的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 林克丁<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL類別等於「linkedin」@totalClicks的全部總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL 和點擊流量 {#urls-and-click-streams-1}

此報告以 **[!UICONTROL Delivery]** 表格(nms:delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 反應性<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> 點按一次傳遞的目標收件者人數與至少開啟一次傳遞的目標收件者預估人數之比。<br /> </td> 
   <td> percent([指標/@recipientClick], [指標/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> 不重複點按<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 至少按一下傳送一次的不同訪客數量與成功傳送之訊息數量之比。<br /> </td> 
   <td> percent([指標/@personClick], [指標/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 累積點按次數<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 目標收件者點按總次數與成功傳送訊息總數之比。<br /> </td> 
   <td> percent([指標/@totalRecipientClick], [指標/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數<br /> </td> 
   <td> @_click<br /> </td> 
   <td> URL主鍵@totalClicks不同於1的所有計數<br /> </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數(%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 點按次數與累積點按總數的百分比。<br /> </td> 
   <td> 百分比(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳遞摘要 {#delivery-summary-1}

此報告以 **[!UICONTROL Delivery]** 表格(nms:delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 初始母體<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 傳遞鎖定的收件者總數。<br /> </td> 
   <td> sum([properties/@totalTarget]<br /> </td> 
  </tr> 
  <tr> 
   <td> 規則拒絕的訊息<br /> </td> 
   <td> @reject<br /> </td> 
   <td> 分析期間為符合類型規則而忽略的地址數：未指定的地址、隔離的地址、禁用清單上的地址等。<br /> </td> 
   <td> sum([properties/@reject]<br /> </td> 
  </tr> 
  <tr> 
   <td> 要傳送的訊息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 傳遞分析後要傳送的訊息總數。<br /> </td> 
   <td> sum([properties/@toDeliver]<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功處理的郵件數。<br /> </td> 
   <td> sum([indicators/@success]<br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤<br /> </td> 
   <td> @error<br /> </td> 
   <td> 傳送和自動退信處理期間累積的錯誤總數。<br /> </td> 
   <td> sum([indicators/@error]<br /> </td> 
  </tr> 
  <tr> 
   <td> 新隔離<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 傳送失敗後隔離的地址數（使用者未知、無效網域）。<br /> </td> 
   <td> sum([indicators/@newQuarantine]<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 熱點點擊 {#hot-clicks-1}

此報告以傳送(nms:delivery)和 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)表格。

此報表顯示訊息內容(HTML和/或文字)，在每個連結上包含點按連結的百分比。 個人化區塊取消訂閱連結和鏡像頁面連結會納入累積點按總數中，但不會顯示在報表中。

## 追蹤統計資料 {#tracking-statistics-1}

此報告以 **[!UICONTROL Delivery]** 表格(nms:delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL類型等於「交@totalClicks」的所有加總。<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL類型等於「電@totalClicks點按」的所有加總。<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主鍵@totalClicks為等於1的所有加總。<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳送統計資料 {#delivery-statistics-1}

此報告以 **[!UICONTROL Delivery and tracking statistics]** 表格(nms:deliveryLogStats)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已處理的電子郵件<br /> </td> 
   <td> @processed<br /> </td> 
   <td> 狀態等於「就緒」、「已傳送」或「失敗」的訊息總數。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳遞<br /> </td> 
   <td> @success<br /> </td> 
   <td> 已成功處理的郵件數。<br /> </td> 
   <td> 指標/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> 硬跳出數<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「使用者未知」的訊息總數。<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> 軟跳出數<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「無法聯繫」、「收件箱已滿」、「無效域」、「禁用帳戶」、「未連接」或「已拒絕」的所有郵件總數<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟次數<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 追蹤記錄@broadLog-ids的總數。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL類別等於「電@source-ids點按」的總數。 <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> 取消訂閱<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL類別等於「@ids退」的總數。<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 開啟次數劃分 {#breakdown-of-opens-1}

此報表以 **傳遞** (nms:delivery)和 **追蹤記錄** (nms:trackingLogRcp)表格。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指示器計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 開啟次數<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> URL主鍵@id等於1（開啟）的所有加總。 <br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他指標 {#other-indicators}

此 **已傳送** 指標(@sent)，透過 **傳送(nms:delivery)>指標** 節點對應於傳送給服務提供者的SMS總數。 此指標僅用於SMS傳送，不得用於其他類型的傳送(請勿與 **@success** 和 **@processed** 指標)。

## 指示器同步 {#indicator-synchronization}

如果您遇到某些指標的取消同步或不一致，請在Adobe Campaign檔案總管中選取相關傳送，按一下滑鼠右鍵並選擇 **[!UICONTROL Action>Recompute delivery and tracking indicators]**. 按一下 **[!UICONTROL Next]**，然後按一下 **[!UICONTROL Finish]**.

![](assets/s_ncs_user_recalculate_indicators.png)

## 追蹤開啟 {#tracking-opens-}

為了讓Adobe Campaign偵測開啟的訊息，收件者必須下載電子郵件中的影像。 HTML和多部分/替代電子郵件包含0像素影像，可讓您偵測已開啟的訊息。 由於文本格式的消息不包含任何影像，因此無法檢測它們是否已開啟。 根據訊息開啟次數計算的值一律會經過估計，因為連結至影像顯示的誤差範圍。

## 目標人員/收件者 {#targeted-persons---recipients}

在某些報表中，Adobe Campaign會區分目標人員和目標收件者。

目標收件者是傳送給的所有收件者。

人數包括目標接收者以及轉發電子郵件的所有人員。 每次在新瀏覽器中開啟或按一下（訊息尚未在中開啟）時，就會將另一個人新增至統計資料。

例如，若您在工作中收到電子郵件(由Adobe Campaign傳送)，並開啟或按一下，則會計為目標收件者（即收件者=1，人員=1）。 如果您將此電子郵件轉送給兩個朋友，目標收件者人數仍等於一，而人數則等於三。 值3與新瀏覽器中每次開啟/按一下的時間一致。
