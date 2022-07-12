---
product: campaign
title: 傳遞
description: 瞭解有關預設交貨工作流的詳細資訊
feature: Workflows
source-git-commit: 25e8acdc449c7002e467db17e7c70e3dc017dded
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 4%

---


# 傳遞{#deliveries}

![](../../assets/common.svg)

下面詳細介紹的工作流隨 **交貨** 預設情況下為模組。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">報告彙總</span> <br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span> <br /> </td> 
   <td> 此工作流更新報表中使用的聚合。 預設情況下，每天凌晨2點觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">帳單</span> <br /> </td> 
   <td> <span class="uicontrol">帳單</span> <br /> </td> 
   <td> 此工作流通過電子郵件將系統活動報告發送給「開單」操作員。 預設情況下是每月25號的觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">別名清除</span> <br /> </td> 
   <td> <span class="uicontrol">別名清除</span> <br /> </td> 
   <td> 此工作流標準化了枚舉值。 預設情況下，每天凌晨3點觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">刷新可交付性</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> 通過此工作流，您可以建立退回郵件資格規則清單，以及平台中域和MX的清單。 此工作流僅在HTTPS埠開啟時才工作。 除非安裝了Deliverability模組，否則不會更新這些清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">資料庫清除</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>此工作流是資料庫維護工作流：它從統計和進程中進行不同的計算，並根據部署助理中定義的配置從資料庫中刪除過時的資料。 預設情況下，每天凌晨4點觸發。</p> <p>有關詳細資訊，請參閱 <a href="../../production/using/database-cleanup-workflow.md">頁</a>。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">暫停的工作流清理</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>此工作流分析嚴重性設定為正常的暫停工作流，並在暫停過長時觸發警告和通知。 一個月後，暫停的技術工作流將無條件停止。 預設情況下，每週一早上5點觸發。</p> <p>有關詳細資訊，請參閱 <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">處理暫停的工作流</a>。</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">優惠通知</span> <br /> </td> 
   <td> <span class="uicontrol">服務管理</span> <br /> </td> 
   <td> 此工作流將批准的優惠部署到線上環境以及優惠目錄中包含的每個類別。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">預測</span> <br /> </td> 
   <td> <span class="uicontrol">預測</span> <br /> </td> 
   <td> 此工作流分析保存在臨時日曆中的交貨（建立臨時日誌）。 預設情況下，每天凌晨1點觸發它。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">追蹤</span> <br /> </td> 
   <td> <span class="uicontrol">跟蹤</span> <br /> </td> 
   <td> 此工作流執行跟蹤資訊的恢復和合併。 它還確保重新計算跟蹤和傳遞統計資訊，特別是消息中心存檔工作流所使用的統計資訊。 預設情況下，每小時觸發一次。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

