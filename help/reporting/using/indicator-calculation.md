---
product: campaign
title: 指標計算
description: 指標計算
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '2972'
ht-degree: 1%

---

# 指標計算 {#indicator-calculation}

## 用戶活動{#user-activities-1}

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
   <td> 開啟的郵件<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主鍵@totalClicks為1的全部總和。<br /> </td> 
   <td> sum(Iif([@url-id]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL類型等於「Email click」@totalClicks的所有加總。<br /> </td> 
   <td> sum(Iif([url/@type]=1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 事務<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL類型等於「Transaction」@totalClicks的全部總和。<br /> </td> 
   <td> sum(Iif([url/@type]=5, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

此報表以&#x200B;**[!UICONTROL Consolidated tracking]**&#x200B;表格(nms:trackingStats)為基礎。 此匯總表用於顯示報表時的效能原因，取代&#x200B;**[!UICONTROL Recipient tracking logs]**&#x200B;表(nms:trackingLogRcp)，且不會即時計算。 系統會在擷取追蹤記錄數後幾分鐘產生表格。 如果指標是最新的，則結果與&#x200B;**追蹤指標**&#x200B;報告的指標相同。 @totalclicks指示器表示在5分鐘期間的點按總數。

## 傳送失敗和退回的郵件 {#non-deliverables-and-bounces-1}

**按錯誤類型劃分**

此報表以&#x200B;**[!UICONTROL Delivery and tracking statistics]**&#x200B;表格(nms:deliveryLogStats)為基礎。

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
   <td> 已處理郵件總數<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> 狀態等於「就緒」、「已發送」或「失敗」的消息總和。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 用戶未知<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「使用者未知」的所有訊息計數。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> 無法訪問<br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「無法聯繫」的所有郵件的計數。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 已拒絕<br /> </td> 
   <td> @refused<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「已拒絕」的所有訊息計數。<br /> </td> 
   <td> Count(@status=2, msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效的域<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「無效域」的所有郵件的計數。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> 帳戶已禁用<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 狀態為「失敗」且原因為等於「帳戶已禁用」的所有郵件的計數。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件箱已滿<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「收件匣已滿」的所有郵件計數。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤<br /> </td> 
   <td> @value<br /> </td> 
   <td> 此類錯誤的失敗消息數。<br /> </td> 
   <td> Count(@status=2 and msg/@failureReason="錯誤類型的值")<br /> </td> 
  </tr> 
  <tr> 
   <td> 貢獻<br /> </td> 
   <td> -<br /> </td> 
   <td> 與錯誤消息總數相比，此類型的錯誤百分比。<br /> </td> 
   <td> 百分比(@value,@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 劃分<br /> </td> 
   <td> -<br /> </td> 
   <td> 與已處理郵件總數相比，此類型的錯誤百分比。<br /> </td> 
   <td> 百分比(@value,@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**依網域劃分**

報告的第二部分詳細說明了按Internet域而非錯誤類型劃分的失敗消息。 在本例中，連結到&#x200B;**Error**&#x200B;指示器(@value)的公式為：Count(@status=2 and @domain=&quot;域名的值&quot;)，即此域狀態為失敗的所有消息的計數。

## 瀏覽器 {#browsers-1}

此報表以&#x200B;**[!UICONTROL Internet Browser Statistics]**&#x200B;表格(nms:userAgentsStats)為基礎。

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
   <td> Sum(@pages)<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此瀏覽器的訪客數與訪客總數的百分比。<br /> </td> 
   <td> 百分比(@totalVisitors，總和(@totalVisitors)<br /> </td> 
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
   <td> 使用此瀏覽器的每日訪客數與在造訪次數最多的當天測量的訪客數百分比。<br /> </td> 
   <td> 百分比(總和(@visitors)，最大(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的訪客數與使用所有瀏覽器的訪客總數的百分比。<br /> </td> 
   <td> 百分比(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相對重量<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的訪客數與使用此瀏覽器的訪客總數的百分比。<br /> </td> 
   <td> 百分比(@totalVisitors，總和(@totalVisitors)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 共用至社交網路{#sharing-to-social-networks-1}

此報表以&#x200B;**[!UICONTROL Delivery]**(nms:delivery)、**[!UICONTROL Consolidated tracking]**(nms:trackingStats)和&#x200B;**[!UICONTROL Web tracking]**(nms:webTrackingLog)表格為基礎。

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
   <td> 要傳送的消息數<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 傳遞分析期間處理的郵件總數。<br /> </td> 
   <td> sum([properties/@totalTarget]<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功傳送的次數<br /> </td> 
   <td> @success<br /> </td> 
   <td> 已成功處理的郵件數<br /> </td> 
   <td> sum([indicators/@success]<br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL類別等於「email」@totalClicks的所有加總。<br /> </td> 
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
   <td> 美味的<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL類別等於「可@totalClicks性」的所有值的總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL類別等於「digg」@totalClicks的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL類@totalClicks等於"google"。<br />的所有加總 </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL類別等於「linkedin」@totalClicks的所有加總。<br /> </td> 
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
   <td> 此社交網路上分享次數與分享總數之比的百分比。<br /> </td> 
   <td> percent(@forward, sum(@forward)<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用率<br /> </td> 
   <td> @rate<br /> </td> 
   <td> 與要傳送的消息數相比，此網路上的共用數。<br /> </td> 
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
   <td> 開啟次數<br /> </td> 
   <td> @open<br /> </td> 
   <td> Web跟蹤表中的跟蹤行總數。<br /> </td> 
   <td> 計數<br /> </td> 
  </tr> 
  <tr> 
   <td> 劃分<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 此社交網路上開啟次數與開啟總數的百分比。<br /> </td> 
   <td> percent(@open, sum(@open)<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟率<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 此社交網路上的開啟次數與要傳送的訊息總數相比。<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 共用活動統計資料{#statistics-on-sharing-activities-1}

此報表以&#x200B;**[!UICONTROL Delivery]**(nms:delivery)、**[!UICONTROL Consolidated tracking]**(nms:trackingStats)和&#x200B;**[!UICONTROL Web tracking]**(nms:webTrackingLog)表格為基礎。

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
   <td> 連結至收件者的訪客數目。<br /> </td> 
   <td> 公式：count(@id)<br />篩選器：@recipient-id != 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟的郵件<br /> </td> 
   <td> @opened<br /> </td> 
   <td> URL類型等於「Open」@ids的所有計數。<br /> </td> 
   <td> count(Iif([url/@type] = 2, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用<br /> </td> 
   <td> @shared<br /> </td> 
   <td> 包含在「電子郵件」、「facebook」、「twitter」、「delicious」、「digg」、「google」、「linkedin」<br />所有@totalClicks的URL類別計數，其URL類別等於「email」、「facebook」、「twitter」、「delicious」、「digg」、「google」或「linkedin」。<br /> </td> 
   <td> count(Iif([url/@category] IN(email' 、 'facebook' 、 'twitter' 、 'delicious' 、 'digg' 、 'google' 、 'linkedin'), @totalClicks, 0)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 作業系統 {#operating-systems-1}

此報表以&#x200B;**[!UICONTROL Internet Browser Statistics]**&#x200B;表格(nms:userAgentsStats)為基礎。

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
   <td> 作業系統定位的收件者總數的每日平均值，這些收件者至少按一下一次傳遞。<br /> </td> 
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
   <td> percent(@totalVisitors, sum(@totalVisitors)<br /> </td> 
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
   <td> 此作業系統上每天的訪客數量，與瀏覽次數最多的當天所測量的訪客數量百分比。<br /> </td> 
   <td> 百分比(總和(@visitors)，最大(@visitorsOfTheDay)<br /> </td> 
  </tr> 
  <tr> 
   <td> 全局速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每個版本的訪客數與所有作業系統上的訪客總數之比百分比。<br /> </td> 
   <td> 百分比(@totalVisitors, @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相對速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每個版本的訪客數與使用此作業系統的訪客總數之比百分比。<br /> </td> 
   <td> percent(@totalVisitors, sum(@totalVisitors)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 訂閱追蹤{#subscription-tracking-1}

此報告以&#x200B;**[!UICONTROL Services]**&#x200B;表(nms:service)為基礎。

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
   <td> sum(Iif(@action = 1 and @date &gt; addDays(getDate(),(-1), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 取消訂閱<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> 前一天的取消訂閱（動作= 0）計數。<br /> </td> 
   <td> sum(Iif(@action = 0 and @date &gt; addDays(getDate(),(-1), 1, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 進化<br /> </td> 
   <td> -<br /> </td> 
   <td> 訂閱數減去取消訂閱數。 此比率是根據訂閱者總數來計算。<br /> </td> 
   <td> Iif(數字(@_subscription)&gt;數字(@_unsubscription), '+', ")+格式(@_subscription - @_unsubscription, 'number', '# ##0')+ Iif(@_subscriber&gt;0,'(' + format(100*percent)(@_subscription - @_unsubscription, @_subscriber), 'number', '#,##0.00')+ '%',")<br /> </td> 
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

此報告以&#x200B;**[!UICONTROL Delivery and tracking statistics]**(nms:deliveryLogStats)和&#x200B;**[!UICONTROL Consolidated tracking]**(nms:trackingStats)表格為基礎。

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
   <td> 目標分析後broadLogs的數目。<br /> </td> 
   <td> sum([properties/@toDeliver]<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> 「種子地址」欄位等於「否」且狀態等於「服務提供者已考慮」、「已發送」或「在行動裝置上已接收」的郵件計數。<br /> </td> 
   <td> sum([indicators/@success]<br /> </td> 
  </tr> 
  <tr> 
   <td> 達到<br />的母體上不同開啟 </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> 根據html格式電子郵件的不同開啟次數外推所有電子郵件的不同開啟次數。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@recipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 達到的母體上的開啟總和<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> 根據html格式的電子郵件開啟總數外推所有電子郵件的開啟總數。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text])= 0, 0, round(toDouble(@totalRecipientOpen)* [@toDeliver] /([@toDeliver] - [@text]), 0)<br /> </td> 
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
   <td> URL類@ids等於「鏡像頁面」的所有計數。<br /> </td> 
   <td> count(Iif([url/@type]=6, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 轉發的估計<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 不重複訪客的數量與至少點擊一次電子郵件的不重複收件者的數量之間的差異。<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> 「種子地址」欄位等於「否」且狀態等於「收件者考慮」、「已發送」或「在行動裝置上接收」的郵件計數。<br /> </td> 
   <td> sum([indicators/@success]<br /> </td> 
  </tr> 
  <tr> 
   <td> 投訴<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「封鎖清單上的地址」的郵件計數。<br /> </td> 
   <td> Count(@status=2和msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟的郵件<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 所有追@broadLog-ids記錄檔中的所有計數。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL類型等於「電子郵件@broadLog-ids」的不重複計數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 原始反應性<br /> </td> 
   <td> -<br /> </td> 
   <td> 點按至少一次傳遞的收件者人數與開啟傳遞至少一次的收件者人數之百分比。<br /> </td> 
   <td> 百分比(@recipientClick,@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 達到<br />的母體上的不重複點按 </td> 
   <td> @personClick<br /> </td> 
   <td> URL類別等於「電@source-ids點按」的所有計數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 累積點按<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> URL類別等於「電@ids點按」時的所有計數。<br /> </td> 
   <td> count(Iif([url/@type]=1, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件者點按<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL類型等於「電子郵件點按」@broadLog-ids的不重複計數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @broadLog-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 估計反應性<br /> </td> 
   <td> -<br /> </td> 
   <td> 點按至少一次傳遞的收件者人數與開啟傳遞至少一次的收件者預估人數之比。<br /> </td> 
   <td> 百分比(@recipientClick, @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> 已瀏覽頁面<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL類型等於「Web」或「交易」@ids的所有計數。<br /> </td> 
   <td> count(Iif([url/@type]=4或[url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 事務<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL類型等於「Transaction」@ids的所有計數。<br /> </td> 
   <td> count(Iif([url/@type]=5, @id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 總金額<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL類型等於「交易」的webTrackingLog/@amounts總和。<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@amount, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 平均事務金額<br /> </td> 
   <td> -<br /> </td> 
   <td> 總金額與事務數的比率。<br /> </td> 
   <td> div(@amount, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 項目<br /> </td> 
   <td> @article<br /> </td> 
   <td> URL類型等於"Transaction"的webTrackingLog/@articles的總和。<br /> </td> 
   <td> Sum(Iif([url/@type]=5, webTrackingLog/@article, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 每個事務的平均項數<br /> </td> 
   <td> -<br /> </td> 
   <td> 項目數與事務處理數之比。<br /> </td> 
   <td> div(@article, @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 每條消息的平均數量<br /> </td> 
   <td> -<br /> </td> 
   <td> 總量與要傳送的報文數的比率。<br /> </td> 
   <td> div(@amount, @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL類別等於「email」@totalClicks的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='email',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL類別等於"facebook"的@totalClicks總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL類別等於"twitter"的@totalClicks總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味的<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL類@totalClicks等於「delicious」的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL類別等於「digg」@totalClicks的全部加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL類別等於"google"的@totalClicks總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google',@totalClicks,0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL類別等於「linkedin」@totalClicks的所有加總。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin',@totalClicks,0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL 和點按流 {#urls-and-click-streams-1}

此報表以&#x200B;**[!UICONTROL Delivery]**&#x200B;表格(nms:delivery)為基礎。

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
   <td> 點按至少一次傳遞的目標收件者人數與至少開啟一次傳遞的目標收件者預估人數之比。<br /> </td> 
   <td> percent([indicators/@recipientClick], [indicators/@estimatedRecipientOpen]<br /> </td> 
  </tr> 
  <tr> 
   <td> 不重複點按<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 至少按一次傳遞的不同訪客數量與成功傳遞的訊息數量之比。<br /> </td> 
   <td> percent([indicators/@personClick], [indicators/@success]<br /> </td> 
  </tr> 
  <tr> 
   <td> 累積點按<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 目標收件者點按總次數與成功傳送之訊息次數的比率。<br /> </td> 
   <td> percent([indicators/@totalRecipientClick], [indicators/@success]<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按<br /> </td> 
   <td> @_click<br /> </td> 
   <td> URL主鍵與@totalClicks 1<br />不同的所有計數 </td> 
   <td> count(Iif([@url-id] != 1, @totalClicks, 0)<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按(%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 點按次數與累積點按總數的百分比。<br /> </td> 
   <td> 百分比(@_click, @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳送摘要 {#delivery-summary-1}

此報表以&#x200B;**[!UICONTROL Delivery]**&#x200B;表格(nms:delivery)為基礎。

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
   <td> 傳遞目標的收件者總數。<br /> </td> 
   <td> sum([properties/@totalTarget]<br /> </td> 
  </tr> 
  <tr> 
   <td> 規則<br />拒絕的消息 </td> 
   <td> @reject<br /> </td> 
   <td> 分析期間為符合類型規則而忽略的地址數：未指定、隔離、封鎖清單等地址。<br /> </td> 
   <td> sum([properties/@reject]<br /> </td> 
  </tr> 
  <tr> 
   <td> 要傳送的訊息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 傳遞分析後要傳遞的郵件總數。<br /> </td> 
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
   <td> 傳遞和自動退信處理期間累積的錯誤總數。<br /> </td> 
   <td> sum([indicators/@error]<br /> </td> 
  </tr> 
  <tr> 
   <td> 新隔離<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 傳送失敗後的隔離地址數（用戶未知，無效域）。<br /> </td> 
   <td> sum([indicators/@newQuarantine]<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 熱點點按 {#hot-clicks-1}

此報告以「傳送」(nms:delivery)和&#x200B;**[!UICONTROL Consolidated tracking]**(nms:trackingStats)表格為基礎。

此報表顯示每個連結上含有點按百分比的訊息內容（HTML和/或文字）。 個人化區塊取消訂閱連結和鏡像頁面連結會納入累積點按總數中，但不會顯示在報表中。

## 跟蹤統計資料{#tracking-statistics-1}

此報表以&#x200B;**[!UICONTROL Delivery]**&#x200B;表格(nms:delivery)為基礎。

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
   <td> 事務<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL類型等於"Transaction"的@totalClicks總和。<br /> </td> 
   <td> sum(Iif([url/@type] = 5, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL類型等於「電@totalClicks點按」的所有加總。<br /> </td> 
   <td> sum(Iif([url/@type] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主鍵@totalClicks等於1.<br />的全部總和 </td> 
   <td> sum(Iif([@url-id] = 1, @totalClicks, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳送統計資料{#delivery-statistics-1}

此報表以&#x200B;**[!UICONTROL Delivery and tracking statistics]**&#x200B;表格(nms:deliveryLogStats)為基礎。

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
   <td> 狀態等於「就緒」、「已發送」或「失敗」的郵件總數。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 已傳送<br /> </td> 
   <td> @success<br /> </td> 
   <td> 已成功處理的郵件數。<br /> </td> 
   <td> indicators/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> 硬跳出數<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「用戶未知」的郵件總數。<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> 軟跳出數<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「無法聯繫」、「收件箱已滿」、「無效域」、「禁用帳戶」、「未連接」或「已拒絕」的所有郵件總數<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟的郵件<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 追蹤記錄@broadLog-ids的總數。<br /> </td> 
   <td> Countdistinct([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL類別等於「電@source-ids點按」的總數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1, @source-id, 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 取消訂閱<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL類別等於「選@ids退出」的總數。<br /> </td> 
   <td> count(Iif([url/@type]=3, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 開啟次數{#breakdown-of-opens-1}

此報告以&#x200B;**Deliversions**(nms:delivery)和&#x200B;**Tracking logs**(nms:trackingLogRcp)表格為基礎。

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
   <td> 開啟的郵件<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> URL主鍵@id等於1（開啟）的所有加總。<br /> </td> 
   <td> count(Iif([@url-id] = 1, @id, 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他指標{#other-indicators}

**已傳送**&#x200B;指示器(@sent)，經由&#x200B;**傳送(nms:delivery)>指示器**&#x200B;節點存取，對應於傳送至服務提供者的SMS總數。 此指標僅用於SMS傳送，不得用於其他類型的傳送(不得與&#x200B;**@success**&#x200B;和&#x200B;**@processed**&#x200B;指標混淆)。

## 指示器同步{#indicator-synchronization}

如果您遇到某些指標的取消同步或不一致，請在Adobe Campaign檔案總管中選取相關傳送，按一下滑鼠右鍵並選擇&#x200B;**[!UICONTROL Action>Recompute delivery and tracking indicators]**。 按一下&#x200B;**[!UICONTROL Next]**，然後按一下&#x200B;**[!UICONTROL Finish]**。

![](assets/s_ncs_user_recalculate_indicators.png)

## 追蹤開啟{#tracking-opens-}

為了讓Adobe Campaign偵測開啟的訊息，收件者必須下載電子郵件中的影像。 HTML和多部分/替代電子郵件包含0像素影像，可讓您偵測已開啟的訊息。 由於文本格式的消息不包含任何影像，因此無法檢測它們是否已開啟。 根據訊息開啟次數計算的值一律會經過估計，因為連結至影像顯示的誤差範圍。

## 目標人員/收件者{#targeted-persons---recipients}

在某些報表中，Adobe Campaign會區分目標人員和目標收件者。

目標收件者是傳送給的所有收件者。

人數包括目標接收者以及轉發電子郵件的所有人員。 每次在新瀏覽器中開啟或按一下（訊息尚未在中開啟）時，就會將另一個人新增至統計資料。

例如，若您在工作中收到電子郵件(由Adobe Campaign傳送)，並開啟或按一下，則會計為目標收件者（即收件者=1，人員=1）。 如果您將此電子郵件轉送給兩個朋友，目標收件者人數仍等於一，而人數則等於三。 值3與新瀏覽器中每次開啟/按一下的時間一致。
