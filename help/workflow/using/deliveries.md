---
title: 交貨
seo-title: 交貨
description: 交貨
seo-description: null
page-status-flag: never-activated
uuid: d323eb4d-937b-4b37-8400-942336f0a1b4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 37612f62-68c0-4f73-a9a1-6d017aab862f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# 交貨{#deliveries}

依預設會安裝下列詳細的工作流程。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">報告匯總</span><br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span><br /> </td> 
   <td> 此工作流程會更新報表中使用的匯總。 預設會在每天凌晨2點觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">帳單</span><br /> </td> 
   <td> <span class="uicontrol">帳單</span><br /> </td> 
   <td> 此工作流程會透過電子郵件將系統活動報表傳送至「帳單」運算元。 預設會觸發每月25日。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">有效帳單設定檔數</span><br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span><br /> </td> 
   <td> <p>此工作流程會計算作用中描述檔的數目。 預設會在每晚1點觸發。</p> <p><strong>Profile</strong> 是指一筆代表終端客戶或潛在客戶之資訊的紀錄 (例如：nmsRecipient 表格或外部表格中的記錄，包含 cookie 識別碼、客戶識別碼、行動識別碼或特定通路相關的其他資訊)。計費只涉及「作用中」的設定檔。 如果描述檔在過去12個月內已透過任何通道鎖定或傳達，則描述檔會被視為「作用中」。</p> <p>Facebook 和 Twitter 通路不包含在內。</p> <p>You can have an overview of the <span class="uicontrol">Number of active profiles</span> from the <span class="uicontrol">Administration</span> &gt; <span class="uicontrol">Campaign Management</span> &gt; <span class="uicontrol">Customer metrics</span> menu.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">化名清洗</span><br /> </td> 
   <td> <span class="uicontrol">aliasClacining</span><br /> </td> 
   <td> 此工作流程標準化了列舉值。 預設每天凌晨3點觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">提供性更新</span><br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span><br /> </td> 
   <td> 此工作流程可讓您建立彈回郵件資格規則清單，以及平台中網域和MX的清單。 只有在HTTPS埠開啟時，此工作流才能運作。 除非安裝了Deliverability模組，否則不會更新這些清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">資料庫清理</span><br /> </td> 
   <td> <span class="uicontrol">清除</span><br /> </td> 
   <td> <p>此工作流是資料庫維護工作流：它根據部署助理中定義的配置從資料庫中刪除過時資料，從而與統計和進程進行不同的計算。 預設每天凌晨4點觸發。</p> <p>For more information, refer to this <a href="../../production/using/database-cleanup-workflow.md">page</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">暫停的工作流程清理</span><br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span><br /> </td> 
   <td> <p>此工作流程會分析嚴重性設為一般的暫停工作流程，並在暫停過久時觸發警告和通知。 一個月後，暫停的技術工作流程會無條件停止。 預設情況下，每週一早上5點觸發。</p> <p>如需詳細資訊，請參閱「處 <a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">理暫停的工作流程」</a>。</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">選件通知</span><br /> </td> 
   <td> <span class="uicontrol">offerMagt</span><br /> </td> 
   <td> 此工作流程會將核准的選件部署至線上環境，以及選件目錄中包含的每個類別。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">預覽</span><br /> </td> 
   <td> <span class="uicontrol">預測</span><br /> </td> 
   <td> 此工作流程會分析儲存在臨時日曆中的傳送（建立臨時記錄）。 預設會在每天凌晨1點觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">追蹤</span><br /> </td> 
   <td> <span class="uicontrol">追蹤</span><br /> </td> 
   <td> 此工作流程會執行追蹤資訊的復原與整合。 它還可確保重新計算跟蹤和傳送統計資訊，特別是郵件中心歸檔工作流中使用的統計資訊。 依預設，每小時會觸發一次。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

