---
title: 消息中心（控制項）
seo-title: 消息中心（控制項）
description: 消息中心（控制項）
seo-description: null
page-status-flag: never-activated
uuid: bdb3610b-a893-4e60-a9f7-f21d90b66919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 69e3e99f-d392-4316-926c-3c3c675415ad
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 消息中心（控制項）{#message-center-control}

以下詳細說明的工作流程排程為每小時執行一次。 預設情況下，它與 **消息中心——控制** 模組一起安裝。 For more on this module, refer to this [section](../../message-center/using/about-transactional-messaging.md).

要瞭解有關如何配置與消息中心模組相關的技術工作流的更多資訊，請參 [閱本頁](../../message-center/using/technical-workflows.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 消息中心&lt;external_account_name&gt;<br /> </td> 
   <td> mcSynch_&lt;external_account_name&gt;<br /> </td> 
   <td> 此工作流程：<br /> 
    <ul> 
     <li> <p>恢復由操作處理的事件清單。</p> </li> 
     <li> <p>與NmsBroadLogMsg表同步，以恢復發送消息的資格。</p> </li> 
     <li> <p>當與NmsBroadLogMsg表的同步完成時，可以立即恢復事件發送日誌。</p> </li> 
     <li> <p>與NmsTrackingUrl表同步，以便恢復傳送URL的追蹤。</p> </li> 
     <li> <p>當與NmsTrackingUrl表的同步完成時，會立即恢復事件追蹤URL。</p> </li> 
     <li> <p>可讓您在傳送傳送後每三小時恢復隔離中放置的所有電子郵件地址。</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

