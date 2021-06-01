---
product: campaign
title: 訊息中心（執行）
description: 訊息中心（執行）
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 6%

---


# 訊息中心（執行）{#message-center-execution}

下面詳述的工作流預設與&#x200B;**Message Center - Execution**&#x200B;模組一起安裝。 有關此模組的詳細資訊，請參閱此[節](../../message-center/using/about-transactional-messaging.md)。

要了解有關如何配置與消息中心模組相關的技術工作流的詳細資訊，請參閱[本頁](../../message-center/using/technical-workflows.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">更新事件狀態</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> 此工作流程可讓您指派狀態給事件。 事件狀態如下：<br /> 
    <ul> 
     <li> <p><strong>待定</strong>:事件在佇列中。尚未與其關聯任何消息模板。</p> </li> 
     <li> <p><strong>待定傳送</strong>:事件在佇列中，且訊息範本已與其相關聯，且目前由傳送處理。</p> </li> 
     <li> <p><strong>已傳送</strong>:此狀態是從傳送記錄檔複製而來。這表示已傳送傳遞。</p> </li> 
     <li> <p><strong>由傳送忽略</strong>:此狀態是從傳送記錄檔複製而來。這表示已忽略傳送。</p> </li> 
     <li> <p><strong>傳送錯誤</strong>:此狀態是從傳送記錄檔複製而來。這表示傳送失敗。</p> </li> 
     <li> <p><strong>未涵蓋的事件</strong>:事件無法與消息模板關聯。將不會重新處理事件。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">處理批次事件</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> 此工作流程可讓您先將批次事件放入佇列，再將其與訊息範本建立關聯。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">處理即時事件</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> 此工作流程可讓您在將即時事件與訊息範本建立關聯之前，將其放入佇列中。<br /> </td> 
  </tr> 
 </tbody> 
</table>

