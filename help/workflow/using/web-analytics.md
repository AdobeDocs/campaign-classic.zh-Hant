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

依預設，下列詳細的工作流程會隨 **Web Analytics連接器模組一起安裝** 。 For more on this module, refer to this [section](../../platform/using/adobe-analytics-data-connector.md).

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
   <td> 此工作流程可讓您透過Adobe® Genesis連接器，從Adobe Campaign傳送電子郵件宣傳指標至Adobe Experience Cloud Suite。 有關指標如下： <strong>已傳送</strong> (iSent)、開 <strong>啟總數(iTotalRecipientOpen)、點按</strong> (iTotalRecipientClick)、 <strong>iErrors</strong><strong></strong><strong></strong> (iError)、「選擇退出」(iTotalRecipientOut)的接收者總數(iTotalRout)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">轉換觸點的標識</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流程會為在重新行銷促銷活動後完成購買的網站訪客建立索引。 此工作流程所復原的資料可在「重新行銷效 <span class="uicontrol">率」報表中存取</span> (請參閱 <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> 本頁</a>)。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> 此工作流程可讓您根據「使用期限」欄位中設定的期間，從資料庫欄位刪除每 <span class="uicontrol">個事件</span> 。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Web事件的恢復</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 此工作流程每小時都會下載特定網站上網際網路使用者行為的區段，並將它們放入Adobe Campaign資料庫，然後啟動再行銷工作流程。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

