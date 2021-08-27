---
product: campaign
title: 互動
description: 互動
audience: workflow
content-type: reference
topic-tags: technical-workflows
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 6%

---


# 互動{#interaction}

![](../../assets/common.svg)

依預設，下列詳細的工作流程會與&#x200B;**選件引擎（互動）**&#x200B;附加元件一起安裝。

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
   <td> 此工作流程會更新<strong>選件主張</strong>多維資料集的<strong>Full</strong>匯總。 預設會每天早上6點觸發。 此匯總會擷取下列維度：管道、傳送、行銷活動和日期。<br /> 接著 <strong>會</strong> 使用選件設定資料集來根據選件產生報表。您可以在<a href="../../reporting/using/about-cubes.md">此部分</a>中了解更多有關多維資料集的資訊。<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter完整聚合計算</span> <br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span> <br /> </td> 
   <td> 此工作流更新<strong>Message center</strong>多維資料集的<strong>Full</strong>聚合。 預設會每天凌晨3:00觸發。 此匯總會擷取下列維度：管道、日期、狀態和事件類型。<br /> 然 <strong>後使</strong> 用Message Centercube根據事件生成報告。您可以在<a href="../../reporting/using/about-cubes.md">此部分</a>中了解更多有關多維資料集的資訊。<br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

