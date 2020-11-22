---
solution: Campaign Classic
product: campaign
title: 互動
description: 互動
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 5%

---


# 互動{#interaction}

依預設，下列詳細的工作流程會 **與選件引擎（互動）** 模組一起安裝。 For more on this module, refer to this [section](../../interaction/using/interaction-and-offer-management.md).

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
   <td> 此工作流程會更新 <strong>Offer提案立方的</strong> 「完 <strong>整匯總」</strong> 。 預設會在每天早上6點觸發。 此匯總會擷取下列維度：渠道、傳送、行銷優惠和日期。<br /> 然後 <strong>會使用</strong> 「選件」提案立方來根據選件產生報表。 您可以在本節中進一步了 <a href="../../reporting/using/about-cubes.md">解立方</a>。<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter完整聚合計算</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

