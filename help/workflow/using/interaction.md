---
solution: Campaign Classic
product: campaign
title: 互動
description: 互動
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: affc541c480ad7e618120fe90270841add06b711
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 3%

---


# 互動{#interaction}

依預設，下面詳述的工作流程會與&#x200B;**選件引擎（互動）**&#x200B;模組一起安裝。 有關此模組的詳細資訊，請參閱此[部分](../../interaction/using/interaction-and-offer-management.md)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">完全聚合計算（propositionrcp立方）</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span> <br /> </td> 
   <td> 此工作流程會更新<strong>Full</strong><strong>Offer提案</strong>立方的匯總。 預設會在每天早上6點觸發。 此匯總會擷取下列維度：渠道、傳送、行銷優惠和日期。<br /> 然後 <strong>會</strong> 使用選件propositioncube來根據選件產生報表。您可以在<a href="../../reporting/using/about-cubes.md">本節</a>中進一步瞭解立方體。<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter完整聚合計算</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> 此工作流更新<strong>Full</strong><strong>消息中心</strong>立方的集合。 預設每天凌晨3點觸發。 此匯總會擷取下列維度：渠道、日期、狀態和事件類型。<br /> 然後 <strong>，消</strong> 息中心多維資料集用於根據事件生成報告。您可以在<a href="../../reporting/using/about-cubes.md">本節</a>中進一步瞭解立方體。<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

