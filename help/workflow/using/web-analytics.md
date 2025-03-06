---
product: campaign
title: 網站分析
description: 進一步瞭解網站分析套件
hide: true
hidefromtoc: true
feature: Workflows, Analytics Integration
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 3%

---


# 網站分析{#web-analytics}



依預設，以下詳細的工作流程會與&#x200B;**網站分析聯結器**&#x200B;模組一起安裝。 如需此模組的詳細資訊，請參閱此[區段](../../integrations/using/gs-aa.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">正在傳送指標和行銷活動屬性</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> 此工作流程可讓您透過Adobe® Analytics聯結器，從Adobe Campaign傳送電子郵件行銷活動指標至Adobe Experience Cloud套裝。 相關指標如下： <strong>已傳送</strong> (iSent)、<strong>開啟總數</strong> (iTotalRecipientOpen)、<strong>已點按</strong> (iTotalRecipientClick)的收件者總數<strong>錯誤</strong> (iError)、<strong>選擇退出</strong> （選擇退出） (iOptOut)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">已轉換連絡人的識別碼</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流程會針對在再次行銷活動後完成購買的網站訪客建立索引。 此工作流程復原的資料可在<span class="uicontrol">再行銷效率報表</span>中存取。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 此工作流程可讓您根據<span class="uicontrol">有效期限</span>欄位中設定的期間，從資料庫欄位中刪除每個事件。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">復原Web事件</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 每小時，此工作流程會下載指定網站之網際網路使用者行為的區段，將其放入Adobe Campaign資料庫並啟動再次行銷工作流程。<br /> </td> 
  </tr> 
 </tbody> 
</table>

