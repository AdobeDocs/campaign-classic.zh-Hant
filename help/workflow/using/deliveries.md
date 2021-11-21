---
product: campaign
title: 傳遞
description: 進一步了解預設傳送工作流程
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 794be3d196ea8292699bbf29c8a7038177763e31
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 5%

---


# 傳遞{#deliveries}

![](../../assets/common.svg)

以下詳細說明的工作流程會與 **傳遞** 模組。

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
   <td> 此工作流程會更新報表中使用的匯總。 預設會每天凌晨2:00觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">帳單</span> <br /> </td> 
   <td> <span class="uicontrol">帳單</span> <br /> </td> 
   <td> 此工作流程會透過電子郵件將系統活動報表傳送至「帳單」運算子。 預設為每月25日觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">別名清除</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleancing</span> <br /> </td> 
   <td> 此工作流程會標準化列舉值。 預設會每天凌晨3:00觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">傳送能力更新</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> 此工作流程可讓您建立退信限定規則清單，以及平台中的網域和MX清單。 此工作流程只有在HTTPS埠開啟時才有效。 除非安裝傳遞模組，否則不會更新這些清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">資料庫清除</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>此工作流是資料庫維護工作流：它會根據統計資料和進程進行不同的計算，並根據部署助理中定義的配置從資料庫中刪除過時資料。 預設會每天凌晨4:00觸發。</p> <p>如需詳細資訊，請參閱 <a href="../../production/using/database-cleanup-workflow.md">頁面</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">暫停的工作流程清除</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>此工作流程會分析嚴重性設為正常的暫停工作流程，並在暫停太久時觸發警告和通知。 一個月後，暫停的技術工作流程會無條件停止。 預設會每週一早上5點觸發。</p> <p>如需詳細資訊，請參閱 <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">處理暫停的工作流程</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">優惠方案通知</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> 此工作流程會將已核准的優惠方案部署至線上環境，以及優惠方案目錄中包含的每個類別。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">預測</span> <br /> </td> 
   <td> <span class="uicontrol">預測</span> <br /> </td> 
   <td> 此工作流程會分析儲存在臨時日曆中的傳送（建立臨時記錄）。 預設會每天凌晨1:00觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">追蹤</span> <br /> </td> 
   <td> <span class="uicontrol">追蹤</span> <br /> </td> 
   <td> 此工作流程會執行追蹤資訊的復原和整合。 它還可確保重新計算跟蹤和傳遞統計資料，特別是報文中心存檔工作流所使用的統計資料。 預設會每小時觸發一次。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

