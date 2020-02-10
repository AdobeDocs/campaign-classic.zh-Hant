---
title: 消息中心（執行）
seo-title: 消息中心（執行）
description: 消息中心（執行）
seo-description: null
page-status-flag: never-activated
uuid: 8dfb09d1-da00-43fb-9df4-243bb915cbde
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: dc3d8998-9493-4d71-b3e2-6f9531cb9bac
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 消息中心（執行）{#message-center-execution}

下面詳細介紹的工作流預設隨 **「消息中心——執行** 」模組安裝。 For more on this module, refer to this [section](../../message-center/using/about-transactional-messaging.md).

要瞭解有關如何配置與消息中心模組相關的技術工作流的更多資訊，請參 [閱本頁](../../message-center/using/technical-workflows.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">更新事件狀態</span><br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span><br /> </td> 
   <td> 此工作流程可讓您指派狀態給事件。 事件狀態如下：<br /> 
    <ul> 
     <li> <p><strong>待定</strong>:事件在隊列中。 尚未與消息模板關聯。</p> </li> 
     <li> <p><strong>待定傳送</strong>:事件在佇列中，訊息範本已與其關聯，且目前正由傳送處理。</p> </li> 
     <li> <p><strong>已傳送</strong>:此狀態會從傳送記錄複製。 這表示傳送已傳送。</p> </li> 
     <li> <p><strong>傳送忽略</strong>:此狀態會從傳送記錄複製。 這表示傳送已被忽略。</p> </li> 
     <li> <p><strong>傳送錯誤</strong>:此狀態會從傳送記錄複製。 這意味著交付失敗。</p> </li> 
     <li> <p><strong>未涵蓋的事件</strong>:事件無法與消息模板關聯。 不會重新處理事件。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">處理批次事件</span><br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span><br /> </td> 
   <td> 此工作流程可讓您在將批次事件與訊息範本建立關聯之前，先將它們放入佇列。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">處理即時事件</span><br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span><br /> </td> 
   <td> 此工作流程可讓您在將即時事件與訊息範本建立關聯之前，將即時事件放入佇列。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

