---
product: campaign
title: 互動
description: 互動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Interaction
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 7%

---


# 互動{#interaction}



以下詳細說明的工作流程會與 **優惠方案引擎（互動）** 預設為附加元件。

如需詳細資訊，請視您的Campaign版本而定，參閱下列區段：

![](assets/do-not-localize/v7.jpeg)[  Campaign v7 文件](../../interaction/using/interaction-and-offer-management.md)

![](assets/do-not-localize/v8.png)[  Campaign v8 文件](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/interaction/interaction.html)


<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">完整聚合計算（propositircp多維資料集）</span> <br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositrcp_full</span> <br /> </td> 
   <td> 此工作流程會更新 <strong>完整</strong> 匯總 <strong>優惠方案主張</strong> 立方體。 預設會每天早上6點觸發。 此匯總會擷取下列維度：管道、傳送、行銷活動和日期。<br /> 此 <strong>優惠方案主張</strong> 然後，多維度資料集可用來根據選件產生報表。 您可以在 <a href="../../reporting/using/ac-cubes.md">本節</a>.<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter完整聚合計算</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> 此工作流程會更新 <strong>完整</strong> 匯總 <strong>訊息中心</strong> 立方體。 預設會每天凌晨3:00觸發。 此匯總會擷取下列維度：管道、日期、狀態和事件類型。<br /> 此 <strong>訊息中心</strong> 然後，多維資料集可用來根據事件產生報表。 您可以在 <a href="../../reporting/using/ac-cubes.md">本節</a>.<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

