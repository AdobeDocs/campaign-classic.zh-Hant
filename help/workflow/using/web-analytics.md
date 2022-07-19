---
product: campaign
title: 網站分析
description: 瞭解有關Web Analytics包的詳細資訊
feature: Workflows, Analytics Integration
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# 網站分析{#web-analytics}

![](../../assets/v7-only.svg)

下面詳細介紹的工作流隨 **Web Analytics連接器** 預設情況下為模組。 有關本模組的詳細資訊，請參閱本模組 [節](../../platform/using/adobe-analytics-connector.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">發送指標和市場活動屬性</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> 此工作流允許您通過Adobe®分析連接器將電子郵件促銷活動指標從Adobe Campaign發送到Adobe Experience Cloud套件。 有關指標如下： <strong>已發送</strong> （發送）, <strong>開啟總數</strong> (iTotalRecipientOpen), <strong>按一下的收件人總數</strong> (iTotalRecipientClick), <strong>錯誤</strong> (iError), <strong>選擇退出</strong> （選擇退出）(iOptOut)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">已轉換聯繫人的標識</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> 此工作流為在重新營銷活動後完成採購的站點訪問者編製索引。 此工作流恢復的資料可在 <span class="uicontrol">重新營銷效率報告</span> (請參閱 <a href="../../platform/using/adobe-analytics-connector.md#creating-a-re-marketing-campaign"> 頁</a>)。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalytics清除Web事件</span> <br /> </td> 
   <td> 此工作流允許您根據在 <span class="uicontrol">壽命</span> 的子菜單。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Web事件的恢復</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> 每小時，此工作流都會在指定站點上下載網際網路用戶行為段，將它們放入Adobe Campaign資料庫並啟動重新營銷工作流。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

