---
product: campaign
title: 網站分析
description: 深入了解網頁分析套件
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# 網站分析{#web-analytics}

依預設，下列詳細的工作流程會與&#x200B;**Web Analytics連接器**&#x200B;模組一起安裝。 有關此模組的詳細資訊，請參閱此[節](../../platform/using/adobe-analytics-data-connector.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">傳送指標和行銷活動屬性</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> 此工作流程可讓您透過「Adobe Campaign」® 「Genesis」連接器，將電子郵件促銷活動指標從Adobe傳送至Adobe Experience Cloud套裝。 有關指標如下：<strong>已發送</strong>(iSent)、<strong>開啟總數</strong>(iTotalRecipientOpen)、 <strong>已點按</strong>(iTotalRecipientClick)、 <strong>錯誤</strong>(iError)、<strong>選擇退出</strong>（選擇退出）(iOptOut)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">轉換的聯繫人的標識</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流程會為在再行銷活動後完成購買的網站訪客建立索引。 可以在<span class="uicontrol">再行銷效率報告</span>（請參閱此<a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign">頁面</a>）中訪問此工作流恢復的資料。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 此工作流程可讓您根據<span class="uicontrol">Lifeft</span>欄位中設定的期間，從資料庫欄位中刪除每個事件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">恢復Web事件</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 此工作流程會每小時下載指定網站上網際網路使用者行為的區段，並將其放入Adobe Campaign資料庫並啟動再行銷工作流程。<br /> </td> 
  </tr> 
 </tbody> 
</table>

