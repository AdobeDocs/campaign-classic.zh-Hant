---
title: 互動
seo-title: 互動
description: 互動
seo-description: null
page-status-flag: never-activated
uuid: 5c8e2353-bb76-4e8d-95d7-61b6c111b6b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 1683477a-9233-4a25-b0d0-0c81051eb440
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 28a32c9a5300c28784ae7a2837075b4dc3aad1fa

---


# 互動{#interaction}

依預設，下面詳述的工作流程會 **與選件引擎（互動）** 模組一起安裝。 For more on this module, refer to this [section](../../interaction/using/interaction-and-offer-management.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">完全集合計算（propositionrcp立方）</span><br /> </td> 
   <td> <span class="uicontrol">agg_nmspropositionrcp_full</span><br /> </td> 
   <td> 此工作流程會更新 <strong>Offer提案立方的</strong> 「完 <strong>整匯總」</strong> 。 預設會在每天早上6點觸發。 此匯總會擷取下列維度：渠道、傳送、行銷優惠和日期。<br /> 然後 <strong>會使用</strong> 「選件」提案立方來根據選件產生報表。 您可以在本節中進一步了 <a href="../../reporting/using/about-cubes.md">解立方</a>。<br /> </td> 
  </tr> 
   <tr> 
   <td> <span class="uicontrol">MessageCenter完整聚合計算</span><br /> </td> 
   <td> <span class="uicontrol">agg_messageCenter_full</span><br /> </td> 
   <td> <br /> </td> 
  </tr> 
 </tbody> 
</table>

