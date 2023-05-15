---
product: campaign
title: 訊息中心（控制）
description: 訊息中心（控制）
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 12%

---


# 訊息中心（控制）{#message-center-control}



以下詳細說明的工作流程排程每小時執行一次。 它已與 **訊息中心 — 控制** 模組。


如需詳細資訊，請視您的Campaign版本而定，參閱下列區段：

![](assets/do-not-localize/v7.jpeg)[  Campaign v7 文件](../../message-center/using/about-transactional-messaging.md)

![](assets/do-not-localize/v8.png)[  Campaign v8 文件](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/transactional.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 訊息中心 &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> 此工作流程：<br /> 
    <ul> 
     <li> <p>恢復操作處理的事件清單。</p> </li> 
     <li> <p>與NmsBroadLogMsg表同步，以恢復傳送消息資格。</p> </li> 
     <li> <p>完成與NmsBroadLogMsg表的同步恢復後，事件傳送日誌即可。</p> </li> 
     <li> <p>與NmsTrackingUrl表格同步，以便復原傳送URL的追蹤。</p> </li> 
     <li> <p>完成與NmsTrackingUrl表格的同步後，事件追蹤URL會立即恢復。</p> </li> 
     <li> <p>可讓您在傳送後每三小時復原所有置於隔離區的電子郵件地址。</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

