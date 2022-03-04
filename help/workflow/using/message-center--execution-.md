---
product: campaign
title: 訊息中心（執行）
description: 訊息中心（執行）
feature: Workflows
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 9%

---


# 訊息中心（執行）{#message-center-execution}

![](../../assets/common.svg)

下面詳細介紹的工作流隨 **消息中心 — 執行** 預設情況下為載入項。

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
   <td> <span class="uicontrol">更新事件狀態</span> <br /> </td> 
   <td> <span class="uicontrol">updateEventsStatus</span> <br /> </td> 
   <td> 此工作流允許您為事件分配狀態。 事件狀態如下：<br /> 
    <ul> 
     <li> <p><strong>待定</strong>:事件在隊列中。 尚未將郵件模板與其關聯。</p> </li> 
     <li> <p><strong>等待交貨</strong>:該事件在隊列中，消息模板已與其關聯，並且當前正由傳遞處理。</p> </li> 
     <li> <p><strong>已發送</strong>:此狀態從交貨日誌中複製。 這意味著送貨已經寄出。</p> </li> 
     <li> <p><strong>被傳遞忽略</strong>:此狀態從交貨日誌中複製。 這意味著傳遞被忽略。</p> </li> 
     <li> <p><strong>傳遞錯誤</strong>:此狀態從交貨日誌中複製。 這意味著交貨失敗。</p> </li> 
     <li> <p><strong>未涵蓋的事件</strong>:事件未能與消息模板關聯。 將不再處理該事件。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">處理批處理事件</span> <br /> </td> 
   <td> <span class="uicontrol">batchEventsProcessing</span> <br /> </td> 
   <td> 通過此工作流，您可以在將批處理事件與消息模板關聯之前，將它們放入隊列。 <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">處理即時事件</span> <br /> </td> 
   <td> <span class="uicontrol">rtEventsProcessing</span> <br /> </td> 
   <td> 通過此工作流，您可以在將即時事件與消息模板關聯之前，將它們放入隊列。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

