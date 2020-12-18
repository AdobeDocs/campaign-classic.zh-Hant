---
solution: Campaign Classic
product: campaign
title: 網站分析
description: 進一步瞭解Web Analytics套件
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# 網站分析{#web-analytics}

依預設，下列詳細的工作流程會與&#x200B;**Web Analytics連接器**&#x200B;模組一起安裝。 有關此模組的詳細資訊，請參閱此[部分](../../platform/using/adobe-analytics-data-connector.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">傳送指標和促銷活動屬性</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> 此工作流程可讓您透過Adobe® Genesis連接器，從Adobe Campaign傳送電子郵件宣傳指標至Adobe Experience Cloud Suite。 有關指標如下：<strong>Sent</strong>(iSent)、<strong>開啟次數總計</strong>(iTotalRecipientOpen)、<strong>點按</strong>(iTotalRecipientClick)、<strong>錯誤</strong>(iError)、&lt;a8選擇退出</strong>（選擇退出）(iOptOut)。<br /><strong> </strong></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">轉換觸點的標識</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流程會為在重新行銷促銷活動後完成購買的網站訪客建立索引。 此工作流恢復的資料可在<span class="uicontrol">重新營銷效率報告</span>中訪問（請參閱此<a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign">頁</a>）。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 此工作流允許您根據<span class="uicontrol">使用期限</span>欄位中配置的期間，從資料庫欄位中刪除每個事件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Web事件的恢復</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 此工作流程每小時都會下載特定網站上網際網路使用者行為的區段，並將它們放入Adobe Campaign資料庫，然後啟動再行銷工作流程。<br /> </td> 
  </tr> 
 </tbody> 
</table>

