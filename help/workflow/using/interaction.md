---
product: campaign
title: 互動
description: 互動
hide: true
feature: Workflows, Interaction, Offers
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 65702805-0026-5ca1-843a-144fa79f0883
    internal-label: Interaction
  - id: ea08db70-4682-59a2-9408-9aedd9548e07
    internal-label: Offers
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 2%
---

# 互動{#interaction}



依預設，下面詳細描述的工作流程會與&#x200B;**優惠方案引擎（互動）**&#x200B;附加元件一起安裝。

如需詳細資訊，請參閱Campaign版本的相關章節：

![](assets/do-not-localize/v7.jpeg) [Campaign v7檔案](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png) [Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">完整彙總計算(propositionrcp cube)</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span> <br /> </td> 
   <td> 此工作流程會更新<strong>優惠方案主張</strong> Cube的<strong>完整</strong>彙總。 預設會每天早上6:00觸發。 此彙總會擷取下列維度：管道、傳遞、行銷優惠和日期。<br /> 接著會使用<strong>優惠方案主張</strong> Cube來根據優惠方案產生報表。 您可以在<a href="../../reporting/using/ac-cubes.md">本節</a>.<br />中進一步瞭解多維度資料集 </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter完整彙總計算</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> 此工作流程會更新<strong>訊息中心</strong> Cube的<strong>完整</strong>彙總。 預設會每天凌晨3:00觸發。 此彙總會擷取下列維度：管道、日期、狀態和事件型別。<br /> 接著會使用<strong>訊息中心</strong> Cube來根據事件產生報表。 您可以在<a href="../../reporting/using/ac-cubes.md">本節</a>.<br />中進一步瞭解多維度資料集 </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

