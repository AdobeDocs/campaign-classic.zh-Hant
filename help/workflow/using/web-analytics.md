---
title: 網頁分析
seo-title: 網頁分析
description: 網頁分析
seo-description: null
page-status-flag: never-activated
uuid: 63742453-16d9-48c2-9a3d-d96f5b131fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: cc2d4741-2b26-4933-a28d-5dd7b5f436be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 網頁分析{#web-analytics}

依預設，下列詳細的工作流程會隨 **Web Analytics連接器模組一起安裝** 。 For more on this module, refer to this [section](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">傳送指標和促銷活動屬性</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span><br /> </td> 
   <td> 此工作流程可讓您透過Adobe® Genesis連接器，從Adobe Campaign傳送電子郵件宣傳指標至Adobe Experience Cloud Suite。 有關指標如下：已 <strong>發送</strong> (iSent)、開 <strong>啟總數(iTotalRecipientOpen)、接收者(iTotalClick)、點選</strong> Errors-Out(iOut)、點選 <strong>Opt-Out(iOtalRecipientOpen)的接收者總數</strong><strong></strong><strong></strong> (iTotalTotalCopotClipt)、點選擇退出(it)。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">轉換觸點的標識</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span><br /> </td> 
   <td> 此工作流程會為在重新行銷促銷活動後完成購買的網站訪客建立索引。 此工作流程所復原的資料可在「重新行銷效 <span class="uicontrol">率」報表中存取</span> (請參閱 <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> 本頁</a>)。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">事件清除</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span><br /> </td> 
   <td> 此工作流程可讓您根據「使用期限」欄位中設定的期間，從資料庫欄位刪除每 <span class="uicontrol">個事件</span> 。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Web事件的恢復</span><br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span><br /> </td> 
   <td> 此工作流程每小時都會下載特定網站上網際網路使用者行為的區段，並將它們放入Adobe Campaign資料庫，然後啟動再行銷工作流程。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

