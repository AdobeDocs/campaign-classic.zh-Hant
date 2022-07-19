---
product: campaign
title: 訊息中心（控制）
description: 訊息中心（控制）
feature: Workflows
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 10%

---


# 訊息中心（控制）{#message-center-control}

![](../../assets/v7-only.svg)

下面詳述的工作流計畫每小時運行一次。 它隨 **消息中心 — 控制項** 預設情況下為模組。


有關此內容的詳細資訊，請參閱以下各節：

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
   <td> 消息中心 &lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> 此工作流：<br /> 
    <ul> 
     <li> <p>恢復由操作處理的事件清單。</p> </li> 
     <li> <p>與NmsBroadLogMsg表同步以恢復傳遞消息資格。</p> </li> 
     <li> <p>與NmsBroadLogMsg表的同步完成後，立即恢復事件傳遞日誌。</p> </li> 
     <li> <p>與NmsTrackingUrl表同步以恢復傳遞URL的跟蹤。</p> </li> 
     <li> <p>在完成與NmsTrackingUrl表的同步後，立即恢復事件跟蹤URL。</p> </li> 
     <li> <p>允許您在發送交貨後每三小時恢復隔離的所有電子郵件地址。</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

