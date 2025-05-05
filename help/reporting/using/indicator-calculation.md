---
product: campaign
title: 指標計算
description: 指標計算
badge: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Reporting, Monitoring
exl-id: 52ca1595-16b3-4323-9122-d1ac13c08147
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '3049'
ht-degree: 3%

---

# 指標計算 {#indicator-calculation}



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
   <td> 開啟<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主索引鍵等於1的所有@totalClicks數總和。<br /> </td> 
   <td> sum(Iif([@url-id]=1， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL型別等於「Email click」的所有@totalClicks數總和。<br /> </td> 
   <td> sum(Iif([url/@type]=1， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transactions<br /> </td> 
   <td> URL型別等於「Transaction」的所有@totalClicks案總和。<br /> </td> 
   <td> sum(Iif([url/@type]=5， @totalClicks， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

此報表以&#x200B;**[!UICONTROL Consolidated tracking]**&#x200B;資料表(nms：trackingStats)為基礎。 此彙總表格是因效能原因在顯示報表時使用，取代&#x200B;**[!UICONTROL Recipient tracking logs]**&#x200B;表格(nms：trackingLogRcp)，而且不會即時計算。 表格會在擷取追蹤記錄後的幾分鐘內產生。 如果指標是最新的，則結果將與&#x200B;**追蹤指標**&#x200B;報告的指標相同。 @totalclicks指標表示5分鐘內的點選總數。

## 傳遞失敗和退回次數 {#non-deliverables-and-bounces-1}

**依錯誤型別劃分**

此報表以&#x200B;**[!UICONTROL Delivery and tracking statistics]**&#x200B;資料表(nms：deliveryLogStats)為基礎。

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
   <td> 已處理的訊息總數<br /> </td> 
   <td> @totalProcessed<br /> </td> 
   <td> 狀態等於「就緒」、「已傳送」或「失敗」的訊息總數。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用者不明<br /> </td> 
   <td> @unknownUser<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「使用者未知」的所有訊息計數。<br /> </td> 
   <td> Count(@status=2且msg/@failureReason=1)<br /> </td> 
  </tr> 
  <tr> 
   <td> 無法連線<br /> </td> 
   <td> @unreachable<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「無法聯絡」的所有訊息計數。<br /> </td> 
   <td> Count(@status=2且msg/@failureReason=3)<br /> </td> 
  </tr> 
  <tr> 
   <td> 已拒絕<br /> </td> 
   <td> @refused<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「已拒絕」的所有訊息計數。<br /> </td> 
   <td> Count(@status=2且msg/@failureReason=20)<br /> </td> 
  </tr> 
  <tr> 
   <td> 無效的網域<br /> </td> 
   <td> @invalidDomain<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「無效網域」的所有訊息計數。<br /> </td> 
   <td> Count(@status=2且msg/@failureReason=2)<br /> </td> 
  </tr> 
  <tr> 
   <td> 帳戶已停用<br /> </td> 
   <td> @disabled<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「帳戶已停用」的所有訊息計數。<br /> </td> 
   <td> Count(@status=2且msg/@failureReason=4)<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件匣已滿<br /> </td> 
   <td> @mailBoxFull<br /> </td> 
   <td> 狀態為「失敗」且原因等於「收件匣已滿」的所有郵件計數。<br /> </td> 
   <td> Count(@status=2且msg/@failureReason=5)<br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤<br /> </td> 
   <td> @value<br /> </td> 
   <td> 此錯誤型別的失敗訊息數。<br /> </td> 
   <td> Count(@status=2且msg/@failureReason="錯誤型別的值")<br /> </td> 
  </tr> 
  <tr> 
   <td> 貢獻<br /> </td> 
   <td> -<br /> </td> 
   <td> 與錯誤訊息總數相較之下，此型別的錯誤百分比。<br /> </td> 
   <td> percent(@value，@totalErrors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 劃分<br /> </td> 
   <td> -<br /> </td> 
   <td> 與已處理訊息總數相較之下，此型別的錯誤百分比。<br /> </td> 
   <td> percent(@value，@totalProcessed)<br /> </td> 
  </tr> 
 </tbody> 
</table>

**依網域**&#x200B;劃分

報表的第二部分詳細列出依網際網路網域而非錯誤型別的失敗訊息劃分。 在此案例中，連結至&#x200B;**Error**&#x200B;指示器(@value)的公式為： Count(@status=2和@domain=&quot;Value of the domain name&quot;)，也就是此網域所有狀態為失敗之訊息的計數。

## 瀏覽器 {#browsers-1}

此報表以&#x200B;**[!UICONTROL Internet Browser Statistics]**&#x200B;資料表(nms：userAgentsStats)為基礎。

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
   <td> 此瀏覽器中至少點按一次傳遞的目標收件者總數。<br /> </td> 
   <td> 總@visitors<br /> </td> 
  </tr> 
  <tr> 
   <td> 頁面檢視<br /> </td> 
   <td> @totalPages<br /> </td> 
   <td> 針對所有傳遞，使用此瀏覽器的傳遞連結點選總數。<br /> </td> 
   <td> 總@pages<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 此瀏覽器的訪客相對於訪客總數的百分比。<br /> </td> 
   <td> percent(@totalVisitors， sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

每個瀏覽器的&#x200B;**統計資料**

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
   <td> 每日使用此瀏覽器的訪客數與當天測量最多造訪的訪客數的百分比。<br /> </td> 
   <td> percent(sum(@visitors)，max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 全域速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 相較於使用所有瀏覽器的訪客總數，此版本的訪客百分比。<br /> </td> 
   <td> percent(@totalVisitors， @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相對權數<br /> </td> 
   <td> -<br /> </td> 
   <td> 此版本的訪客與使用此瀏覽器的訪客總數相比的百分比。<br /> </td> 
   <td> percent(@totalVisitors， sum(@totalVisitors)) <br /> </td> 
  </tr> 
 </tbody> 
</table>

## 分享至社交網路 {#sharing-to-social-networks-1}

此報表是以&#x200B;**[!UICONTROL Delivery]** (nms：delivery)、**[!UICONTROL Consolidated tracking]** (nms：trackingStats)和&#x200B;**[!UICONTROL Web tracking]** (nms：webTrackingLog)表格為基礎。

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
   <td> 要傳遞的訊息數<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 傳遞分析期間處理的訊息總數。<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功的傳遞數目<br /> </td> 
   <td> @success<br /> </td> 
   <td> 已成功處理的訊息數<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL類別等於「電子郵件」的所有@totalClicks案總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL類別等於「facebook」的所有@totalClicks數總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL類別等於「twitter」的所有@totalClicks數總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL類別等於「delicious」的所有@totalClicks數總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL類別等於"digg"的所有@totalClicks數總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL類別等於「google」的所有@totalClicks數總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL類別等於「linkedin」的所有@totalClicks數總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin'，@totalClicks，0))<br /> </td> 
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
   <th> <strong>指標計算公式</strong> <br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 共用數目<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 在此社交網路上共用的訊息總數。<br /> </td> 
   <td> Sum(iIf([url/@category]="社交網路型別的值"，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 劃分<br /> </td> 
   <td> @percent<br /> </td> 
   <td> 此社交網路上的分享數目與分享總數相較的百分比。<br /> </td> 
   <td> percent(@forward， sum(@forward))<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用率<br /> </td> 
   <td> @rate<br /> </td> 
   <td> 此網路上的共用數目與要傳送的訊息數目比較。<br /> </td> 
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
   <td> 開啟次數<br /> </td> 
   <td> @open<br /> </td> 
   <td> 網路追蹤資料表中的追蹤行總數。<br /> </td> 
   <td> 計數<br /> </td> 
  </tr> 
  <tr> 
   <td> 劃分<br /> </td> 
   <td> @percentOpen<br /> </td> 
   <td> 此社交網路上的開啟次數與開啟總數的百分比。<br /> </td> 
   <td> percent(@open， sum(@open))<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟率<br /> </td> 
   <td> @rateOpen<br /> </td> 
   <td> 相較於要傳遞的訊息總數，此社交網路上的開啟次數。<br /> </td> 
   <td> @open / @totalTarget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 共用活動的統計資料 {#statistics-on-sharing-activities-1}

此報表是以&#x200B;**[!UICONTROL Delivery]** (nms：delivery)、**[!UICONTROL Consolidated tracking]** (nms：trackingStats)和&#x200B;**[!UICONTROL Web tracking]** (nms：webTrackingLog)表格為基礎。

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
   <td> 連結至收件者的訪客計數。<br /> </td> 
   <td> 公式： count(@id)<br />篩選器： @recipient-id！= 0<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟<br /> </td> 
   <td> @opened<br /> </td> 
   <td> URL型別等於「Open」的所有@ids數計數。<br /> </td> 
   <td> count (Iif([url/@type] = 2， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 共用<br /> </td> 
   <td> @shared<br /> </td> 
   <td> 包含在「電子郵件」、「facebook」、「twitter」、「delicious」、「digg」、「google」、「linkedin」中的URL類別數<br />所有URL類別等於「email」、「facebook」、「twitter」、「delicious」、「digg」、「google」或「linkedin」的@totalClicks數。<br /> </td> 
   <td> count (Iif([url/@category] IN (email' ， 'facebook' ， 'twitter' ， 'delicious' ， 'digg' ， 'google' ， 'linkedin')， @totalClicks， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 作業系統 {#operating-systems-1}

此報表以&#x200B;**[!UICONTROL Internet Browser Statistics]**&#x200B;資料表(nms：userAgentsStats)為基礎。

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
   <td> 作業系統所定位且已至少點按一次傳遞的收件者總數每日平均值。<br /> </td> 
   <td> 總@visitors<br /> </td> 
  </tr> 
  <tr> 
   <td> 已檢視的頁面<br /> </td> 
   <td> @totalPages / @days<br /> </td> 
   <td> 所有傳遞之每個作業系統的傳遞連結的每日平均點按總數。<br /> </td> 
   <td> 總@pages<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每個作業系統的訪客劃分與訪客總數比較。<br /> </td> 
   <td> percent(@totalVisitors， sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

每個作業系統的&#x200B;**統計資料**

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
   <td> 此作業系統上的每日訪客數與當天測量的最大造訪數之間的百分比。<br /> </td> 
   <td> percent(sum(@visitors)， max(@visitorsOfTheDay))<br /> </td> 
  </tr> 
  <tr> 
   <td> 全域速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 相較於所有作業系統上的訪客總數，每個版本的訪客百分比。<br /> </td> 
   <td> percent(@totalVisitors， @globalVisitors)<br /> </td> 
  </tr> 
  <tr> 
   <td> 相對速率<br /> </td> 
   <td> -<br /> </td> 
   <td> 每個版本的訪客數與使用此作業系統的訪客總數相比的百分比。<br /> </td> 
   <td> percent(@totalVisitors， sum(@totalVisitors))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 訂閱追蹤 {#subscription-tracking-1}

此報表以&#x200B;**[!UICONTROL Services]**&#x200B;資料表(nms：service)為基礎。

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
   <td> 已登入<br /> </td> 
   <td> @_subscriber<br /> </td> 
   <td> 前一天已註冊的人數。<br /> </td> 
   <td> sum(Iif(@created &lt; addDays(getDate()， (-1))， 1， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 訂閱<br /> </td> 
   <td> @_subscription<br /> </td> 
   <td> 前一天的訂閱計數(@action = 1)。<br /> </td> 
   <td> sum(Iif(@action = 1和@date &gt; addDays(getDate()， (-1))， 1， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 取消訂閱<br /> </td> 
   <td> @_unsubscription<br /> </td> 
   <td> 前一天取消訂閱的計數（動作= 0）。<br /> </td> 
   <td> sum(Iif(@action = 0且@date &gt; addDays(getDate()， (-1))， 1， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 演化<br /> </td> 
   <td> -<br /> </td> 
   <td> 訂閱數減去取消訂閱數。 此比率是根據訂閱者總數所計算。<br /> </td> 
   <td> Iif(number(@_subscription) &gt; number(@_unsubscription)， '+'， ")+format(@_subscription - @_unsubscription， 'number'， '# ##0')+ Iif(@_subscriber&gt;0，' (' +格式(100*percent(@_subscription - @_unsubscription， @_subscriber)， 'number'， '#，##0.00')+ '%)'，")<br /> </td> 
  </tr> 
  <tr> 
   <td> 熟客方案<br /> </td> 
   <td> -<br /> </td> 
   <td> 相關期間的訂閱者忠誠度比率。<br /> </td> 
   <td> 1%(@_unsubscription，@_subscriber+@_subscription-@_unsubscription)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 追蹤指標 {#tracking-indicators-1}

此報表以&#x200B;**[!UICONTROL Delivery and tracking statistics]** (nms：deliveryLogStats)和&#x200B;**[!UICONTROL Consolidated tracking]** (nms：trackingStats)表格為基礎。

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
   <td> 目標分析之後的broadLogs數目計數。<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> 「種子地址」欄位等於「否」且狀態等於「服務提供者已考慮」、「已傳送」或「行動裝置上已接收」的訊息計數。<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 到達的母體上的不同開啟次數<br /> </td> 
   <td> @estimatedRecipientOpen<br /> </td> 
   <td> 根據html格式的電子郵件不同開啟次數，推斷所有電子郵件的不同開啟次數。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0， 0， round(toDouble(@recipientOpen) * [@toDeliver] / ([@toDeliver] - [@text])， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 已達母體的開啟總和<br /> </td> 
   <td> @estimatedTotalRecipientOpen<br /> </td> 
   <td> 根據html格式的電子郵件開啟總數推斷所有電子郵件的開啟總數。<br /> </td> 
   <td> Iif(([@toDeliver] - [@text]) = 0， 0， round(toDouble(@totalRecipientOpen) * [@toDeliver] / ([@toDeliver] - [@text])， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 按一下取消訂閱連結<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL類別等於「選擇退出」的所有@ids數計數。<br /> </td> 
   <td> count(Iif([url/@type]=3， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 按一下映象頁面的連結<br /> </td> 
   <td> @mirrorPage<br /> </td> 
   <td> URL類別等於「映象頁面」的所有@ids戶計數。<br /> </td> 
   <td> count(Iif([url/@type]=6， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 轉送的預估<br /> </td> 
   <td> @forward<br /> </td> 
   <td> 不同收件者的數目與至少在電子郵件中點按一次的不同收件者數目之間的差異。<br /> </td> 
   <td> @personClick - @recipientClick<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送<br /> </td> 
   <td> @successWithoutSeeds<br /> </td> 
   <td> 「種子地址」欄位等於「否」，且狀態等於「收件者已考慮」、「已傳送」或「行動上已接收」的訊息計數。<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 投訴<br /> </td> 
   <td> @complaints<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「封鎖清單上的位址」的訊息計數。<br /> </td> 
   <td> Count(@status=2且msg/@failureReason=8)<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 所有追蹤記錄檔中的所有@broadLog-ids數。<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL型別等於「Email click」的@broadLog-ids案不重複計數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1， @broadLog-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 原始反應性<br /> </td> 
   <td> -<br /> </td> 
   <td> 與開啟傳遞至少一次的收件者人數相較之下，至少點選一次傳遞的收件者人數的百分比。<br /> </td> 
   <td> percent(@recipientClick，@recipientOpen)<br /> </td> 
  </tr> 
  <tr> 
   <td> 已到達母體的不同點按次數<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL類別等於「Email click」的所有@source-ids戶計數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1， @source-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 累計點按次數<br /> </td> 
   <td> @totalRecipientClick<br /> </td> 
   <td> URL類別等於「電子郵件點選」的所有@ids戶計數。<br /> </td> 
   <td> count(Iif([url/@type]=1， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件者點按<br /> </td> 
   <td> @recipientClick<br /> </td> 
   <td> URL型別等於「Email click」的資@broadLog-ids的相異計數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1， @broadLog-id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 預估的反應性<br /> </td> 
   <td> -<br /> </td> 
   <td> 至少點選一次傳遞的收件者人數與至少開啟傳遞一次的收件者預估人數的比率。<br /> </td> 
   <td> 百分比(@recipientClick， @estimatedRecipientOpen<br /> </td> 
  </tr> 
  <tr> 
   <td> 造訪的頁面<br /> </td> 
   <td> @totalWebPage<br /> </td> 
   <td> URL型別等於「Web」或「Transaction」的所有@ids案計數。<br /> </td> 
   <td> count(Iif([url/@type]=4或[url/@type]=5， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 交易<br /> </td> 
   <td> @transaction<br /> </td> 
   <td> URL型別等於「Transaction」的所有@ids案計數。<br /> </td> 
   <td> count(Iif([url/@type]=5， @id， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 總金額<br /> </td> 
   <td> @amount<br /> </td> 
   <td> URL型別等於「交易」的webTrackingLog/@amounts總和。<br /> </td> 
   <td> Sum(Iif([url/@type]=5， webTrackingLog/@amount， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 平均交易金額<br /> </td> 
   <td> -<br /> </td> 
   <td> 總金額與交易數的比率。<br /> </td> 
   <td> div(@amount， @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 專案<br /> </td> 
   <td> @article<br /> </td> 
   <td> URL型別等於「交易」的webTrackingLog/@articles總和。<br /> </td> 
   <td> Sum(Iif([url/@type]=5， webTrackingLog/@article， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 每筆交易的平均專案數<br /> </td> 
   <td> -<br /> </td> 
   <td> 專案數目與交易數目的比率。<br /> </td> 
   <td> div(@article， @transaction)<br /> </td> 
  </tr> 
  <tr> 
   <td> 每則訊息的平均數量<br /> </td> 
   <td> -<br /> </td> 
   <td> 總金額與要傳遞的訊息數之比。<br /> </td> 
   <td> div(@amount， @toDeliver)<br /> </td> 
  </tr> 
  <tr> 
   <td> 電子郵件<br /> </td> 
   <td> @email<br /> </td> 
   <td> URL類別等於「email」的所有@totalClicks案總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='email'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> facebook<br /> </td> 
   <td> @facebook<br /> </td> 
   <td> URL類別等於「facebook」的所有@totalClicks數總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='facebook'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> twitter<br /> </td> 
   <td> @twitter<br /> </td> 
   <td> URL類別等於「twitter」的所有@totalClicks數總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='twitter'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 美味<br /> </td> 
   <td> @delicious<br /> </td> 
   <td> URL類別等於「delicious」的所有@totalClicks數總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='delicious'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Digg<br /> </td> 
   <td> @digg<br /> </td> 
   <td> URL類別等於"digg"的所有@totalClicks數總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='digg'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Google<br /> </td> 
   <td> @google<br /> </td> 
   <td> URL類別等於"google"的所有@totalClicks數總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='google'，@totalClicks，0))<br /> </td> 
  </tr> 
  <tr> 
   <td> Linkedin<br /> </td> 
   <td> @linkedin<br /> </td> 
   <td> URL類別等於「linkedin」的所有@totalClicks數總和。<br /> </td> 
   <td> Sum(iIf([url/@category]='linkedin'，@totalClicks，0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## URL 和點擊流量 {#urls-and-click-streams-1}

此報表以&#x200B;**[!UICONTROL Delivery]**&#x200B;資料表(nms：delivery)為基礎。

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
   <td> 反應<br /> </td> 
   <td> @reactivity<br /> </td> 
   <td> 至少點選一次傳遞的目標收件者人數，與至少開啟傳遞一次的目標收件者預估人數的比率。<br /> </td> 
   <td> percent([indicators/@recipientClick]， [indicators/@estimatedRecipientOpen])<br /> </td> 
  </tr> 
  <tr> 
   <td> 不同點按<br /> </td> 
   <td> @distinctClicks<br /> </td> 
   <td> 與成功傳遞的訊息數相比至少點選一次傳遞的不同人數比率。<br /> </td> 
   <td> percent([indicators/@personClick]， [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 累計點按次數<br /> </td> 
   <td> @totalClicks<br /> </td> 
   <td> 目標收件者的點按總數與成功傳遞的訊息數之比。<br /> </td> 
   <td> percent([indicators/@totalRecipientClick]， [indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按<br /> </td> 
   <td> @_click<br /> </td> 
   <td> URL主索引鍵與1<br />不同的所有@totalClicks數 </td> 
   <td> count(Iif([@url-id]&rbrack; ！= 1， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按次數(%)<br /> </td> 
   <td> -<br /> </td> 
   <td> 與累計點按總數相比的點按次數百分比。<br /> </td> 
   <td> percent(@_click， @_total)<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳遞摘要 {#delivery-summary-1}

此報表以&#x200B;**[!UICONTROL Delivery]**&#x200B;資料表(nms：delivery)為基礎。

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
   <td> 初始母體<br /> </td> 
   <td> @totalTarget<br /> </td> 
   <td> 傳遞所定位的收件者總數。<br /> </td> 
   <td> sum([properties/@totalTarget])<br /> </td> 
  </tr> 
  <tr> 
   <td> 規則<br />拒絕的訊息 </td> 
   <td> @reject<br /> </td> 
   <td> 分析期間根據型別規則忽略的位址數目：未指定位址、已隔離、已加入封鎖清單等。<br /> </td> 
   <td> sum([properties/@reject])<br /> </td> 
  </tr> 
  <tr> 
   <td> 要傳遞的訊息<br /> </td> 
   <td> @toDeliver<br /> </td> 
   <td> 傳遞分析後要傳遞的訊息總數。<br /> </td> 
   <td> sum([properties/@toDeliver])<br /> </td> 
  </tr> 
  <tr> 
   <td> 成功<br /> </td> 
   <td> @success<br /> </td> 
   <td> 成功處理的訊息數。<br /> </td> 
   <td> sum([indicators/@success])<br /> </td> 
  </tr> 
  <tr> 
   <td> 錯誤<br /> </td> 
   <td> @error<br /> </td> 
   <td> 傳遞和自動退回處理期間累積的錯誤總數。<br /> </td> 
   <td> sum([indicators/@error])<br /> </td> 
  </tr> 
  <tr> 
   <td> 新隔離<br /> </td> 
   <td> @newQuarantine<br /> </td> 
   <td> 傳送失敗（使用者不明，網域無效）後的隔離位址數目。<br /> </td> 
   <td> sum([indicators/@newQuarantine])<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 熱點點擊 {#hot-clicks-1}

此報告以Delivery(nms：delivery)和&#x200B;**[!UICONTROL Consolidated tracking]** (nms：trackingStats)表格為基礎。

此報告顯示訊息內容 (HTML 和/或文字) 以及每個連結的連結點按百分比。個人化區塊取消訂閱連結和映象頁面連結會在累計點按總數中考慮，但不會顯示在報表中。

## 追蹤統計資料 {#tracking-statistics-1}

此報表以&#x200B;**[!UICONTROL Delivery]**&#x200B;資料表(nms：delivery)為基礎。

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
   <td> URL型別等於「Transaction」的所有@totalClicks案總和。<br /> </td> 
   <td> sum(Iif([url/@type] = 5， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按<br /> </td> 
   <td> @clicks<br /> </td> 
   <td> URL型別等於「Email click」的所有@totalClicks數總和。<br /> </td> 
   <td> sum(Iif([url/@type] = 1， @totalClicks， 0))<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟<br /> </td> 
   <td> @opens<br /> </td> 
   <td> URL主索引鍵等於1.<br />的所有@totalClicks數總和 </td> 
   <td> sum(Iif([@url-id] = 1， @totalClicks， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 傳遞統計資料 {#delivery-statistics-1}

此報表以&#x200B;**[!UICONTROL Delivery and tracking statistics]**&#x200B;資料表(nms：deliveryLogStats)為基礎。

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
   <td> 已處理電子郵件<br /> </td> 
   <td> @processed<br /> </td> 
   <td> 狀態等於「就緒」、「已傳送」或「失敗」的訊息總數。<br /> </td> 
   <td> @prepared + @error + @success<br /> </td> 
  </tr> 
  <tr> 
   <td> 已傳遞<br /> </td> 
   <td> @success<br /> </td> 
   <td> 已成功處理的訊息數。<br /> </td> 
   <td> 指示器/@success<br /> </td> 
  </tr> 
  <tr> 
   <td> 硬退信<br /> </td> 
   <td> @hardBounce<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「使用者未知」的訊息總數。<br /> </td> 
   <td> @unknownUser<br /> </td> 
  </tr> 
  <tr> 
   <td> 軟退信<br /> </td> 
   <td> @softBounce<br /> </td> 
   <td> 狀態等於「失敗」且原因等於「無法聯絡」、「收件匣已滿」、「無效網域」、「已停用帳戶」、「未連線」或「已拒絕」的所有郵件總數<br /> </td> 
   <td> @unreachable + @mailBoxFull + @invalidDomain + @disabled + @notConnected + @refused<br /> </td> 
  </tr> 
  <tr> 
   <td> 開啟<br /> </td> 
   <td> @recipientOpen<br /> </td> 
   <td> 追蹤記錄中的@broadLog-ids動總數。<br /> </td> 
   <td> Countdistinct ([@broadLog-id])<br /> </td> 
  </tr> 
  <tr> 
   <td> 點按<br /> </td> 
   <td> @personClick<br /> </td> 
   <td> URL類別等於「電子郵件@source-ids擊」的總點選數。<br /> </td> 
   <td> Countdistinct(Iif([url/@type]=1， @source-id， 0)) <br /> </td> 
  </tr> 
  <tr> 
   <td> 取消訂閱<br /> </td> 
   <td> @optOut<br /> </td> 
   <td> URL類別等於「選擇退出」的使@ids者總數。<br /> </td> 
   <td> count(Iif([url/@type]=3， @id， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 開啟次數的劃分 {#breakdown-of-opens-1}

此報表是以&#x200B;**傳遞** (nms：delivery)和&#x200B;**追蹤記錄** (nms：trackingLogRcp)表格為基礎。

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
   <td> 開啟<br /> </td> 
   <td> @totalRecipientOpen<br /> </td> 
   <td> URL主鍵等於1 （開啟）的所有@id數總和。<br /> </td> 
   <td> count(Iif([@url-id] = 1， @id， 0))<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 其他指標 {#other-indicators}

透過&#x200B;**傳遞(nms：delivery) >指標**&#x200B;節點存取的&#x200B;**已傳送**&#x200B;指標(@sent)對應於傳送給服務提供者的SMS總數。 此指標僅用於SMS傳遞，不得用於其他型別的傳遞(請勿與&#x200B;**@success**&#x200B;和&#x200B;**@processed**&#x200B;指標混淆)。

## 指標同步 {#indicator-synchronization}

如果您遇到某些指示器不同步或不一致的情況，請在Adobe Campaign檔案總管中選取相關的傳送，按一下滑鼠右鍵，然後選擇&#x200B;**[!UICONTROL Action>Recompute delivery and tracking indicators]**。 按一下&#x200B;**[!UICONTROL Next]**，然後按一下&#x200B;**[!UICONTROL Finish]**。

![](assets/s_ncs_user_recalculate_indicators.png)

## 追蹤開啟次數 {#tracking-opens-}

為了讓Adobe Campaign偵測郵件開啟，收件者必須下載電子郵件中的影像。 HTML 和多重部分/替代的電子郵件包含一個 0 像素影像，讓您能夠檢測那些已開啟的訊息。由於文字格式的訊息不包含任何影像，因此無法檢測這類訊息是否已被開啟。由於與影像顯示相關的誤差範圍，根據訊息開啟次數計算的數值一定是估計值。

## 目標對象/收件者 {#targeted-persons---recipients}

在某些報表中，Adobe Campaign會區分目標人物和目標收件者。

目標收件者為傳送傳遞對象的所有收件者。

人數，包括目標收件者及所有轉寄電子郵件之人員。 每次有新瀏覽器開啟或點按（尚未在中開啟訊息）時，就會將另一個人新增到統計資料中。

例如，如果您在工作中收到電子郵件(由Adobe Campaign傳送)並開啟或點按，則您將被計為目標收件者（即recipient=1， person=1）。 如果您將此電子郵件轉寄給兩個朋友，目標收件者人數仍會等於一，而人數則等於三。 值3與新瀏覽器中的每次開啟/按一下一致。
