---
solution: Campaign Classic
product: campaign
title: 傳遞
description: 進一步瞭解預設傳送工作流程
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 7cd76b5a31ed9fc0e64a650316ea29293c628233
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 15%

---


# 傳遞{#deliveries}

依預設，以下詳細說明的工作流程會與&#x200B;**Deliveries**&#x200B;模組一起安裝。

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
   <td> 此工作流程會更新報表中使用的匯總。 預設每天2am觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">帳單</span> <br /> </td> 
   <td> <span class="uicontrol">帳單</span> <br /> </td> 
   <td> 此工作流程會透過電子郵件將系統活動報表傳送至「帳單」運算元。 預設會在每月25日觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">帳單（作用中描述檔）</span> <br /> </td> 
   <td> <span class="uicontrol">billingActiveContactCount</span> <br /> </td> 
   <td> <p>此工作流程會計算作用中描述檔的數目。 預設會在每晚1點觸發。</p> <p><strong>Profile</strong> 是指一筆代表終端客戶或潛在客戶之資訊的紀錄 (例如：nmsRecipient 表格或外部表格中的記錄，包含 cookie 識別碼、客戶識別碼、行動識別碼或特定通路相關的其他資訊)。計費只涉及「作用中」的設定檔。 如果描述檔在過去12個月內已透過任何通道鎖定或傳達，則描述檔會被視為「作用中」。</p> <p>Facebook 和 Twitter 通路不包含在內。</p> <p>您可從「管理」「促銷活動管理」「<span class="uicontrol">&gt;「客戶量度」「</span>」選單中概述「<span class="uicontrol">作用中描述檔數」。</span><span class="uicontrol"></span></span><span class="uicontrol"></span></span></p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">化名清洗</span> <br /> </td> 
   <td> <span class="uicontrol">aliasClacining</span> <br /> </td> 
   <td> 此工作流程標準化了列舉值。 預設每天3am觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">傳送能力更新</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> 此工作流程可讓您建立彈回郵件資格規則清單，以及平台中網域和MX的清單。 只有在HTTPS埠開啟時，此工作流才能運作。 除非安裝了Deliverability模組，否則不會更新這些清單。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">資料庫清除</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>此工作流是資料庫維護工作流：它根據部署助理中定義的配置從資料庫中刪除過時資料，從而與統計和進程進行不同的計算。 預設每天凌晨4點觸發。</p> <p>如需詳細資訊，請參閱此<a href="../../production/using/database-cleanup-workflow.md">頁面</a>。</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">暫停的工作流程清理</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>此工作流程會分析嚴重性設為一般的暫停工作流程，並在暫停過久時觸發警告和通知。 一個月後，暫停的技術工作流程會無條件停止。 預設情況下，每週一早上5點觸發。</p> <p>如需詳細資訊，請參閱<a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">處理暫停的工作流程</a>。</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">選件通知</span> <br /> </td> 
   <td> <span class="uicontrol">offerMagt</span> <br /> </td> 
   <td> 此工作流程會將核准的選件部署至線上環境，以及選件目錄中包含的每個類別。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">預測</span> <br /> </td> 
   <td> <span class="uicontrol">預測</span> <br /> </td> 
   <td> 此工作流程會分析儲存在臨時日曆中的傳送（建立臨時記錄）。 預設每天1am觸發。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">追蹤</span> <br /> </td> 
   <td> <span class="uicontrol">追蹤</span> <br /> </td> 
   <td> 此工作流程會執行追蹤資訊的復原與整合。 它還可確保重新計算跟蹤和傳送統計資訊，特別是郵件中心歸檔工作流中使用的統計資訊。 依預設，每小時會觸發一次。<br /> </td> 
  </tr> 
 </tbody> 
</table>

