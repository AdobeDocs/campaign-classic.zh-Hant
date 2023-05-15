---
product: campaign
title: 網站分析
description: 深入了解網頁分析套件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Analytics Integration
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 4%

---


# 網站分析{#web-analytics}



以下詳細說明的工作流程會與 **網站分析連接器** 模組。 有關此模組的詳細資訊，請參閱 [節](../../platform/using/adobe-analytics-connector.md).

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
   <td> 此工作流程可讓您透過Adobe Campaign® Analytics連接器，將電子郵件促銷活動指標從Adobe傳送至Adobe Experience Cloud套裝。 有關指標如下： <strong>已傳送</strong> （已傳送）, <strong>開啟總數</strong> (iTotalRecipientOpen), <strong>點按的收件者總數</strong> (iTotalRecipientClick), <strong>錯誤</strong> (iError), <strong>退出</strong> （選擇退出）(iOptOut)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">轉換的聯繫人的標識</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流程會為在再行銷活動後完成購買的網站訪客建立索引。 此工作流程所復原的資料可在 <span class="uicontrol">再行銷效率報表</span> (請參閱 <a href="../../platform/using/adobe-analytics-connector.md#creating-a-re-marketing-campaign"> 頁面</a>)。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 此工作流程可讓您根據 <span class="uicontrol">壽命</span> 欄位。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">恢復Web事件</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 此工作流程會每小時下載指定網站上網際網路使用者行為的區段，並將其放入Adobe Campaign資料庫並啟動再行銷工作流程。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

