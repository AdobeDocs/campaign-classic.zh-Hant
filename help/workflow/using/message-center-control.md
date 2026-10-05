---
product: campaign
title: 訊息中心（控制）
description: 訊息中心（控制）
hide: true
feature: Workflows
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 1%
---

# 訊息中心（控制）{#message-center-control}



以下詳細的工作流程已排程每小時執行一次。 預設會與&#x200B;**訊息中心 — Control**&#x200B;模組一起安裝。


如需詳細資訊，請參閱Campaign版本的相關章節：

![](assets/do-not-localize/v7.jpeg)[Campaign v7檔案](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 訊息中心&lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> 此工作流程： <br /> 
    <ul> 
     <li> <p>復原作業處理的事件清單。</p> </li> 
     <li> <p>與NmsBroadLogMsg表格同步，以復原傳遞訊息資格。</p> </li> 
     <li> <p>與NmsBroadLogMsg表格的同步一完成，就會復原事件傳送記錄檔。</p> </li> 
     <li> <p>會與NmsTrackingUrl表格同步，以復原傳遞URL的追蹤。</p> </li> 
     <li> <p>與NmsTrackingUrl表同步完成後，立即復原事件追蹤URL。</p> </li> 
     <li> <p>可讓您在傳送傳遞後，每三小時復原一次所有置於隔離的電子郵件地址。</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

