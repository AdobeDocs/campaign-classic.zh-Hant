---
product: campaign
title: 互動
description: 互動
feature: Workflows, Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 7%

---


# 互動{#interaction}



以下詳述的工作流程會隨 **優惠方案引擎（互動）** 預設為附加元件。

如需詳細資訊，請參閱Campaign版本的相關章節：

![](assets/do-not-localize/v7.jpeg)[Campaign v7檔案](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


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
   <td> 此工作流程會更新 <strong>完整</strong> 彙總 <strong>優惠方案主張</strong> 立方體。 預設會每天早上6:00觸發。 此彙總會擷取下列維度：管道、傳送、行銷優惠和日期。<br /> 此 <strong>優惠方案主張</strong> 立方體接著可用來根據選件產生報表。 若要深入瞭解多維度資料集，請參閱 <a href="../../reporting/using/ac-cubes.md">本節</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter完整彙總計算</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> 此工作流程會更新 <strong>完整</strong> 彙總 <strong>訊息中心</strong> 立方體。 預設會每天凌晨3:00觸發。 此彙總會擷取下列維度：管道、日期、狀態和事件型別。<br /> 此 <strong>訊息中心</strong> 然後使用立方體來根據事件產生報表。 若要深入瞭解多維度資料集，請參閱 <a href="../../reporting/using/ac-cubes.md">本節</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

