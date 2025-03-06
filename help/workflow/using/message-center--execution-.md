---
product: campaign
title: 訊息中心（執行）
description: 訊息中心（執行）
hide: true
hidefromtoc: true
feature: Workflows
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 2%

---


# 訊息中心（執行）{#message-center-execution}



依預設，以下詳細的工作流程會與&#x200B;**訊息中心 — 執行**&#x200B;附加元件一起安裝。

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
   <td> <span class="uicontrol">更新事件狀態</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> 此工作流程可讓您為事件指派狀態。 事件狀態如下： <br /> 
    <ul> 
     <li> <p><strong>擱置中</strong>：事件在佇列中。 尚未為其建立任何訊息範本的關聯。</p> </li> 
     <li> <p><strong>擱置傳遞</strong>：事件在佇列中，訊息範本已與其建立關聯，傳遞目前正在處理中。</p> </li> 
     <li> <p><strong>已傳送</strong>：此狀態是從傳遞記錄檔複製而來。 這表示傳送已進行。</p> </li> 
     <li> <p><strong>由傳遞忽略</strong>：此狀態是從傳遞記錄檔複製而來。 這表示已忽略傳送。</p> </li> 
     <li> <p><strong>傳遞錯誤</strong>：此狀態是從傳遞記錄檔複製而來。 這表示傳送失敗。</p> </li> 
     <li> <p><strong>未涵蓋的事件</strong>：事件無法與訊息範本建立關聯。 將不會重新處理事件。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">正在處理批次事件</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> 此工作流程可讓您在將批次事件與訊息範本產生關聯之前，先將批次事件放入佇列中。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">正在處理即時事件</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> 此工作流程可讓您將即時事件放入佇列中，再將其與訊息範本建立關聯。<br /> </td> 
  </tr> 
 </tbody> 
</table>

