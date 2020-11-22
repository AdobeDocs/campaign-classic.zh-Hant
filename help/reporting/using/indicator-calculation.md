---
solution: Campaign Classic
product: campaign
title: 指示器計算
description: 指示器計算
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2972'
ht-degree: 1%

---


# 指示器計算 {#indicator-calculation}

## 使用者活動 {#user-activities-1}

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 開啟的郵件<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主鍵等於1時，所有@totalClicks的總和。<br /> </td> 
   <td> sum(If([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL類型等於「電子郵件點按」的所有@totalClicks的總和。<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL類型等於「交易」時，所有@totalClicks的總和。<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

此報告以表格(nms:trackingStats) **[!UICONTROL Consolidated tracking]** 為基礎。 此匯總表用於顯示報表時的效能原因，而代表表 **[!UICONTROL Recipient tracking logs]** (nms:trackingLogRcp)，且不會即時計算。 在擷取追蹤記錄數分鐘後，就會產生表格。 如果指標是最新的，則結果與追蹤指標報表的指標 **相同** 。 @totalclicks指示符表示在5分鐘時段內的點按總數。

## 傳送失敗和退回的郵件 {#non-deliverables-and-bounces-1}

**依錯誤類型劃分**

此報告以表格( **[!UICONTROL Delivery and tracking statistics]** nms:deliveryLogStats)為基礎。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已處理的消息總數<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> 狀態為「就緒」、「已發送」或「失敗」的消息總和。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 用戶未知<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「使用者未知」的所有訊息計數。 <br /> </td> 
   <td> Count（@status=2和msg/@failureReason=1）<br /> </td> 
  </tr> 
  <tr> 
   <td> 無法訪問 <br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 狀態為「失敗」且原因為「無法聯繫」的所有消息的計數。 <br /> </td> 
   <td> Count（@status=2和msg/@failureReason=3）<br /> </td> 
  </tr> 
  <tr> 
   <td> 已拒絕<br /> </td> 
   <td> @resubed<br /> </td> 
   <td> 狀態為「失敗」且原因為「已拒絕」的所有消息計數。 <br /> </td> 
   <td> Count（@status=2和msg/@failureReason=20）<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效的域<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 狀態為「失敗」且原因為等於「無效網域」的所有訊息計數。 <br /> </td> 
   <td> Count（@status=2和msg/@failureReason=2）<br /> </td> 
  </tr> 
  <tr> 
   <td> 帳戶已停用<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 狀態為「失敗」且原因為「帳戶已停用」的所有訊息計數。<br /> </td> 
   <td> Count（@status=2和msg/@failureReason=4）<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件匣已滿<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> 狀態為「失敗」且原因為「收件箱已滿」的所有郵件的計數。 <br /> </td> 
   <td> Count（@status=2和msg/@failureReason=5）<br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤<br /> </td> 
   <td> @value<br /> </td> 
   <td> 此類錯誤的失敗消息數。<br /> </td> 
   <td> Count（@status=2和msg/@failureReason="錯誤類型的值"）<br /> </td> 
  </tr> 
  <tr> 
   <td> 貢獻<br /> </td> 
   <td> -<br /> </td> 
   <td> 此類型的錯誤與錯誤消息總數的百分比。<br /> </td> 
   <td> percent(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 劃分<br /> </td> 
   <td> -<br /> </td> 
   <td> 此類型的錯誤與已處理郵件總數的百分比。<br /> </td> 
   <td> percent(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**依網域劃分**

報告的第二部分詳細說明按Internet網域（而非錯誤類型）劃分失敗訊息的詳細資訊。 在本例中，連結至 **Error** indicator(@value)的公式為：Count（@status=2和@domain=&quot;域名的值&quot;），即對此域狀態失敗的所有消息的計數。

## 瀏覽器 {#browsers-1}

此報告基於表( **[!UICONTROL Internet Browser Statistics]** nms:userAgentsStats)。

**全域統計資料**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 訪客<br /> </td> 
   <td> @totalVisitors<br /> </td> 
   <td> 此瀏覽器中點按傳送至少一次的目標收件者總數。<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> Page views<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> 使用此瀏覽器傳送連結（所有傳送）的點按總數。<br /> </td> 
   <td> Sum(@pages) <br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此瀏覽器的訪客數與訪客總數之比例。<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

**每個瀏覽器的統計資料**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 使用此瀏覽器的每日訪客數量與在瀏覽次數最多的一天所測量的訪客數量的百分比。<br /> </td> 
   <td> percent(sum(@visitors),max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 全域比率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的訪客數與使用所有瀏覽器的訪客總數的百分比。<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相對重量<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的訪客數與使用此瀏覽器的訪客總數之比例。<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 分享至社交網路 {#sharing-to-social-networks-1}

此報告以 **[!UICONTROL Delivery]** (nms:delivery)、 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)和 **[!UICONTROL Web tracking]** (nms:webTrackingLog)表為基礎。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Number of messages to deliver<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 傳送分析期間處理的訊息總數。<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功遞送的次數<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功處理的消息數 <br /> </td> 
   <td> sum([indicator/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL類別等於「電子郵件」的所有@totalClicks的總和。<br /> </td> 
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
   <td> 美味可口<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL類別等於「可口性」的所有@totalClicks的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL類別等於「digg」的所有@totalClicks的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL類別等於「google」的所有@totalClicks的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL類別等於「linkedin」的所有@totalClicks的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**分享**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 股份數<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 此社交網路上共用的訊息總數。<br /> </td> 
   <td> Sum(iIf（[url/@category]="社交網路類型的值",@totalClicks,0）)<br /> </td> 
  </tr> 
  <tr> 
   <td> 劃分<br /> </td> 
   <td> @percent<br /> </td> 
   <td> 此社交網路上的分享次數與分享總數之百分比。<br /> </td> 
   <td> percent(@forward, sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> 分享率<br /> </td> 
   <td> @rate<br /> </td> 
   <td> 與要發送的消息數相比，此網路上的共用數。<br /> </td> 
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
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 開啟次數 <br /> </td> 
   <td> @open<br /> </td> 
   <td> 網頁追蹤表格中的追蹤行總數。<br /> </td> 
   <td> Count<br /> </td> 
  </tr> 
  <tr> 
   <td> 劃分<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 此社交網路的開啟次數與開啟總數的百分比。<br /> </td> 
   <td> percent(@open, sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟率<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 此社交網路上的開啟次數與要傳送的訊息總數相比。<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 分享活動統計 {#statistics-on-sharing-activities-1}

此報告以 **[!UICONTROL Delivery]** (nms:delivery)、 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)和 **[!UICONTROL Web tracking]** (nms:webTrackingLog)表為基礎。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 新連絡人<br /> </td> 
   <td> @newContacts<br /> </td> 
   <td> 連結至收件者的訪客數目計數。<br /> </td> 
   <td> 公式：count(@id)<br /> Filter:@recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟的郵件<br /> </td> 
   <td> @opened<br /> </td> 
   <td> URL類型等於「Open」的所有@id的計數。<br /> </td> 
   <td> count(If([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 分享<br /> </td> 
   <td> @shared<br /> </td> 
   <td> URL類別包含在「電子郵件」、「facebook」、「twitter」、「diciol」、「digg」、「google」、「linkedin'<br /> Count of all @totalClicks，其URL類別等於「email」、「facebook」、「twitter」、「diciol」、「digg」或「linkedin」。<br /> </td> 
   <td> count(Iif([url/@category] IN(email', 'facebook', 'twitter', 'delicious', 'digg', 'google', 'linkedin'), @totalClicks, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 作業系統 {#operating-systems-1}

此報告基於表( **[!UICONTROL Internet Browser Statistics]** nms:userAgentsStats)。

**全域統計資料**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 訪客<br /> </td> 
   <td> @totalVisitors / @days<br /> </td> 
   <td> 作業系統所定位且點按傳送至少一次之收件者總數的每日平均值。<br /> </td> 
   <td> Sum(@visitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 已檢視的頁面<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> 所有傳送中，每個作業系統對傳送連結的每日點按總數平均值。<br /> </td> 
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 依作業系統劃分的訪客數量與訪客總數之比較。<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

**每個作業系統的統計資料**

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> @visitors<br /> </td> 
   <td> 此作業系統每天的訪客數量與在瀏覽次數最多的當天測量的訪客數量之比例。<br /> </td> 
   <td> percent(sum(@visitors), max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 全域比率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每個版本的訪客數與所有作業系統的訪客總數之比。<br /> </td> 
   <td> percent(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相對速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每個版本的訪客數與使用此作業系統的訪客總數的百分比。<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 訂閱追蹤 {#subscription-tracking-1}

此報告基於表( **[!UICONTROL Services]** nms:service)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 已註冊<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> 前一天的註冊人數。<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate(),(-1)),1,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 訂閱<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> 前一天的訂閱計數(@action = 1)。<br /> </td> 
   <td> sum(Iif(@action = 1和@date &gt; addDays(getDate(),(-1)), 1, 0))<br /> </td> 
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
   <td> 訂閱數減去取消訂閱數。 該比率是按用戶總數計算的。<br /> </td> 
   <td> 如果(number(@_subscription)&gt; number(@_unsubscription), '+', ")+format(@_subscription - @_unsubscription, 'number', '###0')+ Iif(@_subscriber&gt;0,'(' + format(100*percent(@_usbscription, @_subscriber)), 'number'), '#0'), '#0', '#0', '#0')+ '%',")<br /> </td> 
  </tr> 
  <tr> 
   <td> 忠誠度<br /> </td> 
   <td> -<br /> </td> 
   <td> 相關期間的訂閱者忠誠度比率。<br /> </td> 
   <td> 1-percent(@_unsubscription,@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 追蹤指標 {#tracking-indicators-1}

此報告以(nms:deliveryLogStats) **[!UICONTROL Delivery and tracking statistics]** 和(nms:trackingStats) **[!UICONTROL Consolidated tracking]** 表格為基礎。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 要傳遞的訊息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 目標分析後broadLogs的計數。<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> 「種子地址」欄位等於「否」且狀態等於「服務提供商考慮」、「已發送」或「在行動裝置上接收」的消息計數。<br /> </td> 
   <td> sum([indicator/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> Distinct opens on the pobulet of the receand<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> 根據HTML格式電子郵件的不同開啟次數，推斷所有電子郵件的不同開啟次數。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@recipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 已到達人口的開啟總和<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> 根據html格式電子郵件開啟總數，推斷所有電子郵件的開啟總數。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@totalRecipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按取消訂閱連結<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL類別等於「退出」的所有@id的計數。<br /> </td> 
   <td> count(If([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 按一下指向鏡像頁面的連結<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> URL類別等於「鏡像頁面」的所有@id的計數。<br /> </td> 
   <td> count(If([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 前向估計<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 不同人數與至少點擊一次電子郵件的不同收件者人數之間的差異。<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> 發送<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> 「種子地址」欄位等於「否」且狀態等於「收件者已考慮」、「已傳送」或「行動裝置已接收」的訊息計數。<br /> </td> 
   <td> sum([indicator/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 投訴<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「登入清單的位址」的訊息計數。<br /> </td> 
   <td> Count（@status=2和msg/@failureReason=8）<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟的郵件<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 所有追蹤記錄檔中所有@broadLog-id的計數。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL類型等於「電子郵件點按」的@broadLog-id的不同計數。 <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 原始反應性<br /> </td> 
   <td> -<br /> </td> 
   <td> 點選至少一次傳送的收件者人數與開啟至少一次傳送的收件者人數的百分比。<br /> </td> 
   <td> percent(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 已觸及人口的不同點按次數<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL類別等於「電子郵件點按」的所有@source-id計數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 累積的點按次數<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> URL類別等於「電子郵件點按」的所有@id的計數。<br /> </td> 
   <td> count(If([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件者點按<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL類型等於「電子郵件點按」的@broadLog-id的不同計數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 估計反應性<br /> </td> 
   <td> -<br /> </td> 
   <td> 點選至少一次遞送的接收者人數與開啟遞送至少一次的接收者估計數的比率。<br /> </td> 
   <td> percent(@recipientClick, @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> 已瀏覽頁面<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL類型等於「Web」或「交易」的所有@id的計數。<br /> </td> 
   <td> count(If（[url/@type]=4或[url/@type]=5, @id, 0）)<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL類型等於「交易」的所有@id的計數。<br /> </td> 
   <td> count(If([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 總金額<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL類型等於「交易」的webTrackingLog/@amounts的總和。 <br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 平均交易金額<br /> </td> 
   <td> -<br /> </td> 
   <td> 總金額與交易數之比率。<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 項目<br /> </td> 
   <td> @article<br /> </td> 
   <td> URL類型等於"Transaction"的webTrackingLog/@articles總和。<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 每筆交易的項目平均數<br /> </td> 
   <td> -<br /> </td> 
   <td> 項目數與事務處理數的比率。<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 每則訊息的平均金額<br /> </td> 
   <td> -<br /> </td> 
   <td> 總金額與要傳送之訊息數目之比例。<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件<br /> </td> 
   <td> @email<br /> </td> 
   <td> 所有@totalClicks與等於「電子郵件」的URL類別的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> 所有@totalClicks與等於"facebook"的URL類別的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> 所有@totalClicks與等於"twitter"的URL類別的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味可口<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> 所有@totalClicks與URL類別的總和等於「可口」。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> 所有@totalClicks與等於"digg"的URL類別的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL類別等於「google」時，所有@totalClicks的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> 所有@totalClicks與等於"linkedin"的URL類別的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL 和點按流 {#urls-and-click-streams-1}

此報告基於表( **[!UICONTROL Delivery]** nms:delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 反應性<br /> </td> 
   <td> @反應性<br /> </td> 
   <td> 點選至少一次傳送的目標接收者數目與至少開啟一次傳送的目標接收者數目的估計數目之比。<br /> </td> 
   <td> percent([indicator/@recipientClick], [indicators/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> 不同的點按次數<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 至少點選一次傳送的不同訪客數量與成功傳送之訊息數量之比。<br /> </td> 
   <td> percent([indicator/@personClick], [indicator/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 累積的點按次數<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 目標收件者點按總次數與成功傳送訊息次數的比率。<br /> </td> 
   <td> percent([indicator/@totalRecipientClick], [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數<br /> </td> 
   <td> @_click<br /> </td> 
   <td> URL主鍵與1不同的所有@totalClicks計數<br /> </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數(%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 點按次數與累計點按總數的百分比。<br /> </td> 
   <td> 百分比(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳送摘要 {#delivery-summary-1}

此報告基於表( **[!UICONTROL Delivery]** nms:delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 初始人口<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 傳送所定位的收件者總數。<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 規則拒絕的訊息<br /> </td> 
   <td> @reject<br /> </td> 
   <td> 在分析期間根據分類規則忽略的地址數：未指定的地址、隔離的地址、拒絕清單上的地址等。<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> 要傳遞的訊息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 傳送分析後要傳送的訊息總數。<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功處理的消息數。<br /> </td> 
   <td> sum([indicator/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤<br /> </td> 
   <td> @error<br /> </td> 
   <td> 傳送和自動彈回處理期間累積的錯誤總數。<br /> </td> 
   <td> sum([indicator/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> 新隔離<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 傳送失敗後隔離的地址數（用戶未知，無效域）。<br /> </td> 
   <td> sum([indicators/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 熱點點按 {#hot-clicks-1}

此報告以「傳送」(nms:delivery)和 **[!UICONTROL Consolidated tracking]** (nms:trackingStats)表格為基礎。

此報表顯示訊息內容（HTML和／或文字），在每個連結上包含點按連結的百分比。 個人化會封鎖未訂閱的連結，並在累計的點按總次數中考慮鏡像頁面連結，但不會顯示在報表中。

## 追蹤統計資料 {#tracking-statistics-1}

此報告基於表( **[!UICONTROL Delivery]** nms:delivery)。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL類型等於「交易」時，所有@totalClicks的總和。<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL類型等於「電子郵件點按」時，所有@totalClicks的總和。<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟<br /> </td> 
   <td> @opens<br /> </td> 
   <td> 所有@totalClicks與URL主鍵等於1的總和。<br /> </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳送統計資料 {#delivery-statistics-1}

此報告以表格( **[!UICONTROL Delivery and tracking statistics]** nms:deliveryLogStats)為基礎。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 處理的電子郵件<br /> </td> 
   <td> @processed<br /> </td> 
   <td> 狀態為「就緒」、「已發送」或「失敗」的消息總數。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 交付<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功處理的消息數。<br /> </td> 
   <td> 指示符/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> 硬彈回數<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> 狀態為「失敗」和原因為「使用者未知」的訊息總數。<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> 柔和彈回數<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> 狀態為「失敗」且原因等於「無法訪問」、「收件箱已滿」、「無效域」、「禁用帳戶」、「未連接」或「已拒絕」的所有郵件總數<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @resubled<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟的郵件<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 追蹤記錄檔中的@broadLog-id總數。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL類別等於「電子郵件點按」的@source-id總數。 <br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> 取消訂閱<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL類別等於「退出」的@ids總數。<br /> </td> 
   <td> count(If([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 開啟次數劃分 {#breakdown-of-opens-1}

此報告以「傳送 **」** (nms:delivery)和「 **追蹤記錄檔** 」(nms:trackingLogRcp)表格為基礎。

<table> 
 <thead> 
  <tr> 
   <th> <strong>標籤</strong> <br /> </th> 
   <th> <strong>欄位名稱</strong> <br /> </th> 
   <th> <strong>指標說明</strong> <br /> </th> 
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 開啟的郵件<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> URL主鍵等於1（開啟）的所有@id的總和。 <br /> </td> 
   <td> count(If([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他指標 {#other-indicators}

通過 **Deliveries(nms:delivery)> Indicators** (指示符 **** )節點訪問的Sent指示符(@sent)對應於發送給服務提供商的SMS總數。 此指標僅用於SMS傳送，不得用於其他類型的傳送(不要與 **@success****和@processed** 指示符混淆)。

## 指示器同步 {#indicator-synchronization}

如果您遇到某些指標的不同步或不一致，請在Adobe Campaign檔案總管中選取相關的傳送，按一下滑鼠右鍵並選擇 **[!UICONTROL Action>Recompute delivery and tracking indicators]**。 按一 **[!UICONTROL Next]**&#x200B;下，然後按一 **[!UICONTROL Finish]**&#x200B;下。

![](assets/s_ncs_user_recalculate_indicators.png)

## 追蹤開啟 {#tracking-opens-}

為了讓Adobe Campaign偵測訊息開啟，收件者必須下載電子郵件中的影像。 HTML和多部分／替代電子郵件包含0像素影像，可讓您偵測已開啟的訊息。 由於文字格式的訊息不包含任何影像，因此無法偵測到訊息是否已開啟。 根據訊息開啟次數計算的值一律是估計值，因為連結至影像顯示的錯誤邊界。

## 目標人員／收件者 {#targeted-persons---recipients}

在某些報表中，Adobe Campaign會區分目標人員和目標收件者。

目標收件者是傳送遞送給的所有收件者。

人數包括目標收件人，以及轉寄電子郵件給的所有人。 每當新瀏覽器中出現開啟或點按（訊息尚未在中開啟）時，就會將另一個人加入統計資料中。

例如，如果您在工作中收到電子郵件（由Adobe Campaign傳送）並開啟或按一下，就會被計為目標收件者（即收件者=1，人員=1）。 如果您將此電子郵件轉寄給兩位朋友，則目標收件者數目仍為一，而人數則為三。 值3與新瀏覽器中每次開啟／點按時間一致。
